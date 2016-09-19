---
title: ""
layout: single
excerpt: "Engineering"
sitemap: false
permalink: /eng/
---

Engineering Blog
===============
I obtained my engineer's degree at [Departamento de Ingeniería Eléctrica](http://die.usach.cl/) from the [Universidad de Santiago de Chile](http://www.usach.cl/).
Due to the formation obtained at my University, and also, by developing and participating in several engineering projects is that I feel the need to share what I have learned
in my engineer's role.
I will try to put hints, tips, and some basic(and not so basic) calculations that not only engineers can follow, but also the people who only wants to build and not to take care
about the differential ecuations needed to solve the problem.

>The human knowledge belongs to the world

Milo Hoffman - [Antitrust](https://en.wikipedia.org/wiki/Antitrust_(film))



<h3 class="archive__subtitle">{{ site.data.ui-text[site.locale].recent_posts | default: "Recent Posts" }}</h3>

{% for post in site.posts %}
  {% if post.categories contains 'engineering' %} 
    {% include archive-single.html %}
  {% endif %}
{% endfor %}

{% include paginator.html %}