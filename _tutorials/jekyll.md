---
title: Jekyll Framework
layout: tutorial
pageId: jekyll
parentId: tech
---

{% include toc.html %}

### Jekyll in a nutshell

Jekyll is the framework by which this site is built. It is relatively simple, allows for some nice shortcuts to be made, and is the default framework for github-pages. Here is the [documentation](https://jekyllrb.com/) and a [quickstart guide](https://jekyllrb.com/docs/).

A deep dive into how webpages work is for another tutorial. Suffice to say that when you access a webpage from some server somewhere, it will send back an `html` file. This file often prompts your browser to download some `css` files, maybe some images, perhaps some `js` files...

With something simple like a static blog, all you really need is some `html` to describe the content and structure of the page, and some `css` which styles the site to make it look a bit nicer. The `css` will often be the same on every page. The `html` structure might vary between pages, but there will definitely be some repeated boilerplate and common elements between pages. An example is a top menu or navbar, which will appear on every page with identical code. 

The Jekyll framework is designed to so that the common elements are kept separately from the unique content of each page. When the site is ready to be read, Jekyll will "build" the site by combining all the common elements with all the unique content and creating the `html` and `css` files needed. This way you only need to focus on generating the unique content (usually blog posts) and rarely do you need to look at or alter the more technical common elements.

### Themes

Themes are the mechanic that Jekyll uses to handle the default site structure. When not otherwise specified Jekyll uses the [`minima` theme](https://github.com/jekyll/minima/tree/master), which gives a simple style to each page. The homepage becomes a list of links to all the blog posts, and some headers and footers are added to the homepage and all the posts.

The important idea with themes is that they just define default behaviour for when it doesn't matter or for when it's too time consuming to create your own behaviour. When building the site, Jekyll will look for all the layouts, styles, content, etc in your site's directory, but if it cannot find what it's looking for, it will check the theme instead. For example, on my machine I have the theme installed here: `/Users/{my_username}/.gem/ruby/3.1.3/gems/minima-2.5.1`, and every missing file for creating the site will be taken from there instead.

Creating your own file with the same name in the site's directory will cause Jekyll to skip searching for that file in the theme, and by changing one file at a time you can alter how the site works in an incremental way rather than having to write the whole thing from scratch.

### Markdown

[Markdown](https://daringfireball.net/projects/markdown/) is a simple markup language used for formatting a document, and it is far more widespread than Jekyll. It is easy to read before being parsed and is commonly used to turn something human-readable into an `html` document. The specifics of markdown are not worth getting into, but it helps to know that Jekyll will convert posts and pages from markdown into `html` for you, making your site easier to generate and maintain.

It is worth pointing out that Jekyll isn't actually doing the conversion, but is calling another tool to do it. By default, the tool used is kramdown, although by editing the `_config.yml` you can change it to something else. I've been using kramdown for this site and it seems to be a suitable solution.

### Liquid

[Liquid](https://shopify.github.io/liquid/) is a system developed by Shopify and used by Jekyll for storing variables and programmatically injecting them into your site's `html` or markdown (and later `html`) files. For example, a list with links to all of your blog posts would require editing after each new post, and such manual editing is error-prone (never trust humans to do a machine's job). Liquid is ideal for this, as it can generate such a list automatically after only being coded up once.

On this site, I use the following snippet to generate a link to a specific page, and I do not need to worry about changes to urls or directory structure to keep it working:

```
{%- raw -%}
{% for page in site.pages %}
{% if page.title == "Tutorials" %}
{% assign tutorial = page %}
{% endif %}
{% endfor %}

#### Return to [{{ tutorial.title }}]({{tutorial.url}})
{% endraw %}
```

Every brace `{}` is containing a liquid-parseable statement. These variables are defined either in the `_config.yml` file that lives in the base directory of a Jekyll site, in the front matter (soon to be discussed) at the top of a file, or through an `assign` liquid command.

### Front Matter

This is another system used by Jekyll for defining things related an entire file. Front matter seems to be a series of variables defined at the top of a file between two sets of triple hyphens: `---`. These variables can be used by liquid. They are also used by Jekyll when building the site, as they define things like the page's title and layout.

For example, the front matter `layout: home` variable will tell Jekyll to look for `_layouts/home.html` in either your site's directory or in your theme's directory. It will then take the content of your file (the stuff after the front matter) and plug it into the location in the layout file where we have the liquid statement `{page.content}`. This can be nested as the layout file itself might reference other layouts. A similar process happens for the files found in the `_include/` directory.

### Building the Site

Assuming you have set everything up right (or just followed the quickstart guide) then your site should be buildable. Testing it can be done locally by running the following command from the base directory of the site:

`bundle exec jekyll serve`

Navigating to `http://localhost:4000` with a browser will allow you to view your site. Much of the time you'll be able to make an edit in the code, save the file, and Jekyll will build the site again allowing you to refresh the browser to see the changes. There exists a `--livereload` option which might let you skip the refreshes, but it seems superfluous to me. My front-end developer friends disagree.

When built, unless we've tinkered with the `_config.yml` file, the output overwrites the `_site/` directory. When we upload to github-pages, github takes control over the building of the site for us, but it seems to behave mostly in the same way as it does locally.

### Ruby and the Gemfile

Ruby is a programming language of middling popularity. A gem seems similar conceptually to a library written in Ruby that can be incorporated into another project. Jekyll is a gem. The `Gemfile` is a list of all the gems (it looks like `Gemfile.lock` has their dependencies too) that are needed to build a codebase. `Bundler` is another gem, but it's role is more meta. It downloads all the needed gems, their dependencies, and is used in the building process.
