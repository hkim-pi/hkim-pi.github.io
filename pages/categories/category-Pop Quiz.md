---
title: "Pop Quiz"
layout: archive
permalink: categories/quiz
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories['Pop Quiz'] %}

{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
