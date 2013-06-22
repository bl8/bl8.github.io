---
layout: page
title: Archives
long-title: Release Archives
show-sidebar: true
group: download
sidebar-group: download
order: 1
---

<p class="latest-version">Latest Version: {{site.release-info.banshee.version}} ‒ {{site.release-info.banshee.date}}</p>

To download and install the latest version, go to the [download](/download) page.

### Releases

<ul>
{% for post in site.categories.archives %}
<li><a href="{{post.url | remove:'index.html'}}">{{post.title}}</a></li>
{% endfor %}
</ul>
