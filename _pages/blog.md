---
title: "Blog"
---

A place where I write something I'm interested with. Mostly in Indonesian, but English is used as well if the post is important.

{% for post in site.posts %}
[{{ post.title }} >>]({{ post.url }})
{% endfor %}
