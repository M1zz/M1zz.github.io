---
title: "Post about Java"
layout: archive
permalink: /categories/java
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Java | sort:"date" %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}