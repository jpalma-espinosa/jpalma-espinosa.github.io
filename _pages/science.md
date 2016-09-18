---
title: ""
layout: single
excerpt: "About this website."
sitemap: false
permalink: /about.html
---

Science Blog
===============
As a scientist (or trying to become one) I feel the compulsory need not only to write my things the best way I could, but also to 
share my thoughs, ideas and, what is more important, THE DATA!.
I will use this space to put my projects, [jupyter notebooks](http://jupyter-notebook.readthedocs.io/en/latest/), notes, and also
an analysis and simplification to plain-human to several papers that I will/have/must read. Enjoy!

{% for post in site.posts %}
  {% if post.categories contains 'science' %}
    <div class="post">
        <h3 class="title"><a href="{{ post.url }}">{{ post.title }}</a></h3>
        <p class="meta">Date: {{ post.date }}</p>
    </div>
  {% endif %}
{% endfor %}
