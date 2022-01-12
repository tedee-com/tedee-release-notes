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

{% assign latest_android = docs | where: "parent", "Android" | sort: "title" | last %}
{% assign latest_ios = docs | where: "parent", "iOS" | sort: "title" | last %}
{% assign latest_lock = docs | where: "parent", "Lock" | sort: "title" | last %}
{% assign latest_bridge = docs | where: "parent", "Bridge" | sort: "title" | last %}
{% assign latest_keypad = docs | where: "parent", "Keypad" | sort: "title" | last %}

{% assign order = "Android,iOS,Lock,Bridge,Keypad" | split: ',' %}

{% assign items = docs | where: "title", latest_version | reverse %}

{% for item in order %}
{% case item %}
  {% when "Android" %}
    {% assign doc = latest_android %}
  {% when "iOS" %}
    {% assign doc = latest_ios %}
  {% when "Lock" %}
    {% assign doc = latest_lock %}
  {% when "Bridge" %}
    {% assign doc = latest_bridge %}
  {% when "Keypad" %}
    {% assign doc = latest_keypad %}
{% endcase %}

{% if doc == nil %}
  {% continue %}
{% endif %}

# **{{ doc.parent }} - {{ doc.title }}**
{{ doc.content }}

{% endfor %}