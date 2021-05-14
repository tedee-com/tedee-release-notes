---
layout: home
title: Home
nav_order: -999
permalink: /
---

{% assign docs = '' | split: '' %}
{% for doc in site.docs %}
 {% if doc.title contains "." %}
  {% assign docs = docs | push: doc %}
 {% endif %}
{% endfor %}

{% assign latest_version = docs | sort: "title" | last %}
{% assign latest_version = latest_version.title %}
{% assign sort = "Android,iOS,Embedded,Portal,Integrations" | split: ',' %}

{% assign items = docs | where: "title", latest_version | reverse %}

{% for order in sort %}
 {% for item in items %}
  {% if item.parent == order %}

# **{{ item.parent }} - {{ item.title }}**
{{ item.content }}

  {% endif %}
 {% endfor %}
{% endfor %}