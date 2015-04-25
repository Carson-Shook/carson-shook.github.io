---
layout: post
title: BetterPonymotes - Now On Safari!
published: true
comments: true
---
Happy day everypony on reddit! [BetterPonymotes](http://ponymotes.net) is now [available natively on Safari](/BetterPonymotes-for-Safari). After hearing about Typhos dropping support for Safari because of his lack of resources and a low number of users, I was a bit disappointed since I was one of those users. After close to a year (or has it been longer?) of waiting for someone to create a port of BPM, I decided that thirty minutes on [CodeCademy](http://codecademy.com) should be enough to at least get me started. 

### Simple jQuery Emote Viewer

I learned a lot about JavaScript while working on this. I knew pretty much nothing about JavaScript going into it, or browser based message passing for that matter, but it all seems mostly trivial now looking back. To start development, I did as Typhos suggested and dismantled the Firefox version of the add-on, and then I spent about three days poking and prodding at it to figure out which parts did what. Eventually I began to understand how the program was put together. The bmp-`resources.js` file was the key to the entire process, as it had a codified version of every emote's data. I also found that `Store` (in the `betterponymotes.js` file) contained the most important functions of the entire program. Since I still wasn't sure that modifying the entire program was within my ability, I tried to skirt around this, and opted to create a slimmed down viewer extension instead. I started off with a little bit of jQuery that selected each anchor tag (since that's what each `[](/emote)` becomes when processed by markdown) that began with a forward slash, pulled it's `href` contents, appended the `bpmote-` prefix to them, and finally set the CSS class equal to that value. The CSS took care of the rest, but it didn't allow the "click to hide" ability or the NSFW filtering of the original. I figured that wouldn't be good to release, so I decided to look into the problem a little bit further.

I decided that I needed to include some of the functionality from the `Store` to search through the emote data file, and determine which emotes were NSFW. I learned a lot about message passing, and how no browser seems to do it quite the same, especially Safari. Firefox only takes one parameter, Chrome, it seems, can take either one or two (for either a shot in the dark, or for a specific message handler, as far as I can tell), and Safari takes two, the first being a string that becomes `[eventName].name`, and the second that becomes `[eventName].message`. Additionally (though I didn't find this out until much later), Safari cannot natively pass JavaScript objects in messages, so the only solution is to use JSON to stringify the object before sending. These presented a couple of problems for me when creating this viewer because the Store was not working in the injected script, leading me to place it in the `global.html` file. This meant that every emote that I encountered in the injected script would need to send a message to the global page and then receive a response. Having worked a little bit with Objective-C, I thought that would be no big deal, but I had never encountered asynchronous messages before. 

In safari, the general format of message passing is something like this:

*injectectedScript.js*

    // This is the message handler for an injected script
    safari.self.addEventListener("message", function(event) {
        switch(event.name) {
            if ("readyForThingOne") {
                ... do things ...
            } else if ("readyForThingTwo") {
                ... do other thing ...
            }
        }
    }, false);
    
    // And here we are actually sending a message
    safari.self.tab.dispatchMessage("doThingOne", data);

*global.html*

    // This is the message handler for the global page file
    safari.application.addEventListener("message, function(event) {
        switch(event.name) {
            if ("doThingOne") {
                message.target.page.dispatchMessage("readyForThingOne", data);
            } else if ("doThingTwo") {
                message.target.page.dispatchMessage("readyForThingTwo", data);
            }
        }
    }, false);

There was no way that it would work with how I was trying to use it because I was relying on responses from sent out messages that wouldn't necessarily come back in time (and they *never* came back in time). So I attempted to modify the entire design to send out a bunch of messages, and then actually do something when I get a response, but with no guarantee of anything happening unless a message was received (just like the above example). That worked okay, and I finally got the entire show and dance working. Finally, I was ready to add support for a NSFW toggle. This required a separate event listener for the settings, and that was easy enough: `safari.extension.settings.addEventListener("change", settingsHandler, false)`. After all this work, however, I felt that I could do more. I considered adding in most of the functionality of BPM manually (which I could do almost all of, save for disabling of individual subreddits, blacklisting, and whitelisting. I might have been able to find a way to jury rig the entire thing, but I figured it wouldn't be worth it, but I did start thinking. If I now understood the ins and outs of message passing in Safari, couldn't I add support by replacing Firefox's `main.js` file with the `global.html`? Well, the answer was yes!

### Building BetterPonymotes

I began by looking around the main.js file for similarities to and differences from Safari's way of handling such things. I was able to transplant almost all of the code, chaining only minor things, such as replacing Firefox's data stores with Safari's `localStorage`. Message handling on the back end was the only other major thing that needed changing, and that was as simple as adding `.message` to the middle of each `message.method` reference, since Safari wraps it's data in `.message` when sending a message. It got a little confusing, but I didn't want to alter the code too much, though I could always go back and do so. Just to recap, BPM sends data so that it contains an object with a method name (which Safari doesn't need since it uses `.name	`), and the rest of the data. Unfortunately that means that it is wrapped in an additional unnecessary layer when Safari deals with it, but again, it was only a minor annoyance.

Once the backend was handled properly, it was time to add the necessary hooks to the front end. This consisted of setting up a detection method for determining that the browser was Safari and not Chrome or Firefox. I also took the liberty to add an additional window check to ensure that the program won't run in ad frames or anything like that (since that was causing YouTube and other sites to run really slowly due to the volume of erroneous messages). BPM then uses a switch statement to set up a universal method to send and receive messages, and this is based on the platform that gets determined at the start. After a little trial and error, I was able to send and receive everything in the correct format, and the resulting case looked like this:

*betterponymotes.js*

    case "safari-ext":
    _send_message = function(method, data) {
        if(data === undefined) {
            data = {};
        }
        data.method = method;
        log_debug("_send_message:", data);
        safari.self.tab.dispatchMessage(data.method, data);
    };
 
    safari.self.addEventListener("message", catch_errors(function(message) {
        log_debug("_message_handler: " + message);
        switch(message.message.method) {
            case "initdata":
                _complete_setup(message.message);
                break;
                                     
            default:
                log_error("Unknown request from Safari background script: '" + message.message.method + "'");
                break;
        }
    }), false);
 
    make_css_link = function(filename, callback) {
        var tag = stylesheet_link(safari.extension.baseURI + filename.substr(1));
        callback(tag);
    };
 
    linkify_options = function(element) {
        element.href = safari.extension.baseURI + 'options.html';
        element.target = "_blank";
    };

I set up a similar thing in the `options.js` file, and the core of the add-on was actually working! Or so I thought...
The only thing that I had overlooked was Safari's inability to send key:value pairs as an object. As a result, the preferences were not being set or retrieved on the preference page. After a few hours of searching, I concluded that the only thing to do was to use JSON to stringify the data, but I had no idea how to do that. Fortunately, way back in the day, someone tossed up the source code for BPM [in it's entirety on GitHub](https://github.com/CoRD-Dev/bpm-ancient) (speaking of which, Typhos, shouldn't you have the current source code available somewhere since it's licensed under the GPL?), and there I found that Chrome had this same problem, and thus required the same solution. So with that knowledge, I was finally able to retrieve and store preferences from Safari's localStorage.

Finally, I was done. Now all I have to do is maintain it.

Thank you for reading, and if you haven't done so already, you can pick up the add-on [here](/BetterPonymotes-for-Safari).