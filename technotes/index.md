---
layout: page
title: technotes
description: Technical Notes
permalink: /technotes/
---

<ul>
  {% for post in site.category.technotes %}
    <li>
        <span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
