---
layout: default
title: Post by Category
permalink: /categoryview/
active: archivebycategory
sitemap: false
---
<h1>Archive by Category</h1>

<h3>Other Archive Pages:- </h3>[By Date ]({{"/monthview" | prepend: site.baseurl}}) | [ By Tag]({{"/tagcloudview" | prepend: site.baseurl}})

{% assign tags = site.categories | sort %}
{% assign sorted_posts = site.posts | sort: 'title' %}
<div> 
{% for tag in tags %}
<a href="#{{ tag | first | slugify }}">{{ tag | first | replace: '-', ' ' }}({{ tag | last | size }})</a>{% if forloop.last == false %} • {% endif %}{% endfor %}
</div>
<p>&nbsp;</p>

{% for tag in tags %}
<p><a name="{{ tag | first | slugify }}"></a>&nbsp;</p>
<h3 class="archivetitle">{{ tag | first | replace:'-', ' ' }}{{ tag | last | size }}</h3>

<ul>{% for post in sorted_posts %}{%if post.categories contains tag[0]%}<li><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a> {% if post.author %} • {{ post.author }}{% endif %}{% if post.date %} • {{ post.date | date: "%B %e, %Y" }}<p>{{ post.excerpt | strip_html | truncate: 80 }}</p>{% endif %}</li>{%endif%}{% endfor %}</ul>
{% endfor %}
