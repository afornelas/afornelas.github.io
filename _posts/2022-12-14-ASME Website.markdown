---
layout: post
title:  "ASME Website: asmeuci.com"
category: Engineering
---

> American Society of Mechanical Engineers at UCI - Putting our best foot forward (digitally)

The American Society of Mechanical Engineers at UCI (ASME) is a club that is dedicated towards advancing and enriching the experience of all engineers at the University of California, Irvine. In order to reduce the friction with onboarding new members and increase the outreach of the club, I took it upon myself to revamp the website as ASME's 2022-2023 webmaster. You can visit the [ASME @ UC Irvine website](https://asmeuci.com) here.

<!--more-->

# Website as of June 2022

Before I had taken on the mantle of ASME webmaster, we had already had a glowing static site in the form of Benjamen Bielecki's, my close friend, previous work on the website. This site was quick to load, integrated well with our calendar, and provided quick and easy access to the most important information. The only complication that came with the website is that the html pages were difficult to edit for people without a background in html. In order to address this concern and make it easier for people without a Computer Science degree to edit the website going forward, I ported the website to a website generator and parameterized the underlying architecture to be much more human friendly. 

# New Parameterized Website

{% include iframe.html source = "https://asmeuci.com" height = "30rem" %}

Beginning in June 2022, I completely refreshed the website to much more editable in all circumstances. In order to take the static HTML from the previous version and convert it to a more accessible format I leveraged Jekyll, a blog-aware static site generator that is able to transform easily editable plain text into custom websites built from the ground up. Jekyll is also the same technology that powers my personal website, a [detailed write up]({% post_url 2021-11-16-Website_Portfolio %}) of which can be found here.

By using Jekyll I was able to take previously existing pages such as the following and parameterize it simply and concisely as only 5 total lines, effectively reducing the total number of lines by 87.5%. More importantly, this infinitely reduces the cognitive complexity and allows the code to be significantly more maintainable.

{% raw %}

Excerpt of generated HTML:

```html
<!--Projects Committee List-->
<div style="padding-top: 0!important; text-align: left;" class="d-flex justify-content-center flex-wrap pt-5">
    <div style="width: 16rem;" data-aos="fade-up" data-aos-duration="750" class="card c-contact-card">
    <img class="card-img-top" src="/images/roster/2023/x1.jpg" alt="x1" />
    <div class="card-body">
      <h4 class="card-title">x1</h4>
      <p class="card-text">a1</p>
      <a href="/cdn-cgi/l/email-protection#375651584559525b567742545e19525342"><span class="__cf_email__" data-cfemail="066760697468636a674673656f28636273">[email&#160;protected]</span></a>
    </div>
</div>
    <div style="width: 16rem;" data-aos="fade-up" data-aos-duration="750" class="card c-contact-card">
    <img class="card-img-top" src="/images/roster/2023/x2.jpg" alt="x2" />
    <div class="card-body">
      <h4 class="card-title">x2</h4>
      <p class="card-text">a2</p>
      <a href="/cdn-cgi/l/email-protection#016273647671417462682f646574"><span class="__cf_email__" data-cfemail="2744554250576752444e09424352">[email&#160;protected]</span></a>
    </div>
</div>
<!-- And 40 more lines of boilerplate code -->
```

Entire Jekyll code:

```liquid
<!--Projects Committee List-->
{% include card.html image="2023/x1.jpg" name="x1" role="a1" email="x1@uci.edu"%}
{% include card.html image="2023/x2.jpg" name="x2" role="a2" email="x2@uci.edu"%}
{% include card.html image="2023/x3.jpg" name="x3" role="a3" email="x3@uci.edu"%}
{% include card.html image="2023/x4.jpg" name="x4" role="a4" email="x4@uci.edu"%}
{% include card.html image="2023/x5.jpg" name="x5" role="a5" email="x5@uci.edu"%}
```

{% endraw %}

In addition to simplifying complex html elements, I've implemented a blogging system that allows anyone to easily create a blog post from a markdown file. Through these changes, along with rich front matter to specify categories, authors, and more information, I've been able to create a feature rich posting system that automatically populates the homepage with relevant articles to better display the things that we do.

{% raw %}

```text
What was previously a herculean ordeal of <p>, <h1>, and <b> elements, is now as simple as 'one' #two and **three**
```

{% endraw %}

All of the formatting, theming, and linking is handled by the Github Actions workflow on the back end, with no additional input from the user outside of a .md file. Simply submit a markdown file to the Github page and refresh the page after 15 minutes and suddenly everything is set up!
