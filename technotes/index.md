---
layout: page
title: Notebook
description: Technical Notes
permalink: /technotes/
---

“Do one thing every day that scares you.”
― Eleanor Roosevelt
<ul>
  {% for post in site.categories.notebook %}
    <li>
        <span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
