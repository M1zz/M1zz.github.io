---
title: "Post about Django"
layout: archive
permalink: /categories/django
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Django | sort:"date" | reverse %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
