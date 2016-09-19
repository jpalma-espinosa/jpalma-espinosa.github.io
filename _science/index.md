---
title: ""
layout: single
excerpt: "Science"
sitemap: false
permalink: /science/
---

Science Blog
===============
As a scientist (or trying to become one) I feel the compulsory need not only to write my things the best way I could, but also to 
share my thoughs, ideas and, what is more important, THE DATA!.
I will use this space to put my projects, [jupyter notebooks](http://jupyter-notebook.readthedocs.io/en/latest/), notes, and also
an analysis and simplification to plain-human to several papers that I will/have/must read. Enjoy!




{% for post in site.posts %}
  {% include archive-single.html %}
  {% if post.categories contains 'science' %}
	<div class="post">
		<h3 class="title"><a href="{{ post.url }}">{{ post.title }}</a></h3>
		<p class="meta">Date: {{ post.date }}</p>
		<div class="entry">
			{{ post.content | strip_html | truncatewords: 100 }}
		</div>
	</div>
  {% endif %}
{% endfor %}







