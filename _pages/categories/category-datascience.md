---
title: "Post about Datascience"
layout: archive
permalink: /categories/datascience
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Datascience | sort:"date" | reverse %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
