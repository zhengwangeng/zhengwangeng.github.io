---
layout: page
title: About
description: 没有一颗心会因为追求梦想而受伤
keywords: 爱, 幸福, 感悟爱与幸福
comments: true
menu: 关于
permalink: /about/
---

Stay hungry

Stay foolish

## 孤独与游戏

* 我必须承认生命中大部分时光是属于孤独的,努力成长是在孤独里可以进行的最好的游戏


## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
