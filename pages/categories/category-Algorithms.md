---
title: "Algorithms"
layout: archive
permalink: categories/algo
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Algorithms %}

{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
