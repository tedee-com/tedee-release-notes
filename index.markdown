---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

title: Release notes
version_number: newest
layout: docs
---

{% assign latest_version = site.docs | sort: "version_number" | last %}
{% assign latest_version = latest_version.version_number %}
{% assign sort = "Android,iOS,Embedded,Portal,Integrations" | split: ',' %}

{% assign items = site.docs | where: "version_number", latest_version | reverse %}

{% for order in sort %}
 {% for item in items %}
  {% if item.title == order %}

# **{{ item.title }}**
{{ item.content }}

  {% endif %}
 {% endfor %}
{% endfor %}