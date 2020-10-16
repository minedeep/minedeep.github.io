---
layout: page
title: technotes
description: Technical Notes
permalink: /technotes/
---

<ul>
  {% for post in site.categories.technotes %}
    <li>
        <span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
