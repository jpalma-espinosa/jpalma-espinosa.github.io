---
title: ""
layout: single
excerpt: "Blog"
sitemap: false
permalink: /blog/
---

Personal Blog
===============
In here, I will post any opinion and notes that will not be related to Science or Engineering (maybe philosophy, data governance, etc).
This will be a place to discuss ideas and share my believes.  Feel free to read it.




<h3 class="archive__subtitle">{{ site.data.ui-text[site.locale].recent_posts | default: "Recent Posts" }}</h3>

{% for post in site.posts %}
  {% if post.categories contains 'science' %} 
    {% include archive-single.html %}
  {% endif %}
{% endfor %}

{% include paginator.html %}




