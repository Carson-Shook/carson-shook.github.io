---
layout: post
title: Building a Website From Scratch with Jekyll
published: true
---

Well, it has been an interesting couple of weeks.
I've always wanted to have a website of my own, and I guess that the dream is now a reality. Admittedly this post is quite a bit late, but I figured I should still make it. Anyway, on with the show. This is how I built my website using Jekyll.

When I first designed the look of this website, I was using only basic HTML and CSS, and I didn't entirely understand how to use Jekyll. After looking around a bit though, I found user erjjones GitHub Pages site, with a [blog post](http://erjjones.github.io/blog/How-I-built-my-blog-in-one-day/) on the very subject. Between this and looking over the source of his site, not to mention the actual Jekyll documentation, I began to understand exactly how to use it. I was pretty terrible with it at first, but once I understood the nature of the different special tags, the rest mostly fell into place. In short, there are a handful of folders that need to be in your `username.github.io` folder.

  * `_includes` contains code segments that you can then use an include tag, which is formatted as `{{ "{% include example.html %" }}}` to include the contents of the example.html file in your site. 
  * `_layouts` contains layouts for generated pages, including a `default.html` page, and I'd recommend a `post.html` page as well.The default layout is useful for maintaining the overall look of your site, and it is good to include as a base for your other layouts. To include a layout (say, default), just use `layout: default` within the YAML front matter block.
  * `_posts` contains blog posts written in Markdown, or one of several other formats. The filenames should be formatted like: `2014-12-26-Building-a-Site-From-Scratch.md`.

And that's it! It gets a lot more complex if you want it to, and  a `_drafts` folder can also be useful for those who have several draft posts in progress at any given time. Also, the configuration file is one that you will want to look into. It's use case is very specific to your individual needs, so I encourage you to check out the [Jekyll website](http://jekyllrb.com) for more information. Other than that, all you need is a `_config.yml` file, which you can customize to your own needs.

After all of this, I still needed to learn Markdown, but that was surprisingly easy, since reddit uses the same syntax, but in the event that you don't use reddit or that you aren't that familiar with it's formatting, [visit the creator's site](http://daringfireball.net/projects/markdown/).

There are still a few things that I would like to add in the future, such as a comment section, but that will come in time.

Thanks for reading, and I hope that there will be many more posts to follow.