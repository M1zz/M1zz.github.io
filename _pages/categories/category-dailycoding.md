---
title: "Post about Dailycoding"
layout: archive
permalink: /categories/dailycoding
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Dailycoding | sort:"date" | reverse %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
