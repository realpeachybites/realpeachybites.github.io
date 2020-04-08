---
layout: default
title: Post by Month
permalink: /monthview/
active: archivebydate
sitemap: false
---
Browse By:-
[Category ]({{"/categoryview" | prepend: site.baseurl}}) | [ Tag Cloud]({{"/tagcloudview" | prepend: site.baseurl}})

<div id="index">
{% for post in site.posts %}{% unless post.next %}<h2 class="archivetitletopbottom">{{ post.date | date: '%Y' }}</h2>{% else %}{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}{% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}{% if year != nyear %}<h2 class="archivetitletopbottom">{{ post.date | date: '%Y' }}</h2>{% endif %}{% endunless %}{% capture month %}{{ post.date | date: '%m%Y' }}{% endcapture %}{% capture nmonth %}{{ post.next.date | date: '%m%Y' }}{% endcapture %}{% if month != nmonth %}{% if forloop.index != 1 %}</ul>{% endif %}<h2 class="archivetitle">{{ post.date | date: '%B %Y' }}</h2><ul>{% endif %}{% if post.link %}<h3 class="link-post"><a href="{{ site.baseurl }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a><a href="{{ post.link }}" target="_blank" title="{{ post.title }}"></a></h3>{% else %}<li><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a> {% if post.author %} • {{ post.author }}{% endif %}{% if post.date %} • {{ post.date | date: "%B %e, %Y" }}<p>{{ post.excerpt | strip_html | truncate: 80 }}</p>{% endif %}</li>{% endif %}{% endfor %}</ul></div>