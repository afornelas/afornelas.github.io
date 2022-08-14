---
layout: post
title:  "Website Portfolio"
category: Projects
---

> An opportunity to learn web development and show off my projects all at once

While I did not need to code a website in order to create a portfolio, it had been years since I had last touched HTML and CSS. I then took this opportunity to brush up my skills while simultaneously creating a space online where I can share and host my projects.

<!--more-->

My website is currently hosted at [afornelas.github.io](https://afornelas.github.io) courtesy of GitHub Pages. The underlying web technology that I used in developing this has been the [Jekyll](https://jekyllrb.com/) static site generator to facilitate the development of individual pages showcasing projects.

## Jekyll

> Jekyll is a static site generator. It takes text written in your favorite markup language and uses layouts to create a static website. You can tweak the site’s look and feel, URLs, the data displayed on the page, and more

The heart of this project is Jekyll's markdown to html conversion, which facilitates the process of writing posts to update my website with my latest projects.

In order to create a new post, I simply have to append a `.markdown` to my website directory, which is then converted into a usable webpage based on my customized settings.

## HTML Blocks

While Jekyll abstracts the creation of new webpages, I still did the majority of the HTML "blocks" it uses to decorate my site myself. In certain circumstances, I created entire pages in pure HTML and CSS myself so that I can tune them exactly how I feel is best on a per case basis.

For the majority of posts however, the webpage is instead created in a simple markdown editor in order to remove the friction between writing a project page and having to write the html from scratch every time.

Some of my favorite blocks are:

{% include button_square.html url="" text="This cute button"%}

And this easy to use embedded PDF viewer which relies on the browser's PDF engine:

{% include pdf.html pdf="misc/test.pdf" height="200px"%}

And lastly an easy way to include video on my site:

{% include youtube_embed.html id="rgcKyu4Nejg" %}

## Liquid

The HTML embedded widgets above, and the majority of this site is brought together by Liquid's markdown extensions. This forms a powerful bridge between having to create user elements from scatch in HTML and having a user friendly manner of calling modules easily. While the majority of time, the abstraction is kept simple in the form of 

{% raw %}

```liquid
{% include button_square.html url="" text="Hello World"%}
```

{% endraw %}

Becoming

{% include button_square.html url="" text="Hello World"%}

The Liquid template language also offers powerful logic to create dynamic pages that automatically update as new content is added. For example, on my home page at [afornelas.github.io](afornelas.github.io), this Liquid and HTML code controls the post stream that shows off previews of my projects when scrolling down:

{% raw %}

```liquid
<div class="home">
    <ul class="post-list">
    {%- for post in site.categories.Projects -%}
    <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.date | date: date_format }}</span>
        <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
        </a>
        </h3>
        {%- if site.show_excerpts -%}
        {{ post.excerpt }}
        {%- endif -%}
    </li>
    {%- endfor -%}
    </ul>
</div>
```

{% endraw %}
