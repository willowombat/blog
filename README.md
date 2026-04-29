# willowombat's blog

A personal Jekyll blog hosted on GitHub Pages.

## Content

* [Page Details](#page-details)
    * [Home](#home)
    * [Archives](#archives)
    * [Categories](#categories)
    * [Tags](#tags)
    * [Collections](#collections)
    * [About](#about)
    * [Comments](#comments)
    * [Post Contents](#post-contents)
    * [Code Highlight](#code-highlight)
    * [Mobile Adaptation](#mobile-adaptation)
    * [Footer](#footer)
    * [Statistical Analysis](#statistical-analysis)
* [Usage](#usage)
    * [1. Install ruby and jekyll environment](#1-install-ruby-and-jekyll-environment)
    * [2. Clone the repo](#2-clone-the-repo)
    * [3. Change parameter](#3-change-parameter)
        * [Basic info](#basic-info)
        * [Link info](#link-info)
        * [Comments info](#comments-info)
        * [Statistical analysis info](#statistical-analysis-info)
    * [4. Write post](#4-write-post)
    * [5. Local launch](#5-local-launch)
    * [6. Push to GitHub](#6-push-to-github)

## Page Details

### Home

Index page shows 5 posts excerpt as a default. Readers can click article title or read more button to see full post. There are recent posts area, categories area and tags area at the right part of the index page.

### Archives

Archive posts according to the year.

### Categories

Show posts according to the category.

### Tags

Show posts according to the tags.

### Collections

Collect favorite article links with `markdown` syntax.

### About

Write an introduction about yourself and your site with `markdown` syntax.

### Comments

This theme supports [disqus](https://disqus.com/) comments. Configure your short name in `_config.yml`:

```yml
# comments
disqus_shortname: xxx
```

### Post Contents

The post contents is fixed at the right side while the page is scrolling.

### Code Highlight

Uses GitHub flavored markdown for code blocks.

More info: [syntax-highlighter-changed](https://jekyllrb.com/docs/upgrading/2-to-3/#syntax-highlighter-changed).

### Mobile Adaptation

Fully mobile responsive.

### Footer

Site footer with links and attribution.

### Statistical Analysis

Supports Google Analytics:

```yml
google_analytics_id: UA-xxxxxxxx
```

## Usage

### 1. Install ruby and jekyll environment

Windows users can use [RubyInstaller](http://rubyinstaller.org/) to install ruby. Then install jekyll:

```
gem install jekyll
```

For more details see the jekyll official website: [https://jekyllrb.com/](https://jekyllrb.com/)

### 2. Clone the repo

Clone or download this repo to your local machine.

### 3. Change parameter

Edit `_config.yml` and add your own `favicon.ico`.

#### Basic info

```yml
# Site settings
title: Your Blog Title
brief-intro: Your tagline here
baseurl: "/blog" # the subpath of your site
url: "https://yourusername.github.io"
```

#### Link info

```yml
github_username: yourusername
email: youremail@example.com
```

#### Comments info

Get your own `short_name` at https://disqus.com/:

```yml
disqus_shortname: xxxx
```

#### Statistical analysis info

Get your Google Analytics id at https://www.google.com/analytics/:

```yml
google_analytics_id: UA-xxxxxxxx
```

### 4. Write post

Write posts in the `_posts` folder. Each post should begin with:

```
---
layout: post
title:  "Your Post Title"
date:   2026-01-01 12:00:00
categories: category
tags: tag1 tag2
---
```

Use markdown syntax throughout. Use 4 blank lines as an excerpt separator — text before the separator appears on the index page.

### 5. Local launch

```
jekyll s
```

Then visit [http://localhost:4000](http://localhost:4000) to preview your blog.

### 6. Push to GitHub

Once everything looks good, push to GitHub and GitHub Pages will build your site automatically.

## License

[MIT License](LICENSE)
