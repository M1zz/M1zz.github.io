---
title: "Post about Spring"
layout: archive
permalink: /categories/spring
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Spring | sort:"date" %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
