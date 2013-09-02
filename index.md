---
layout: page
title: Htedsv Backyard
tagline: index
---
{% include JB/setup %}

<ul class="posts">
    {% for post in site.posts %}
    <li>
        <a style="text-align: center; font-size:40px; margin-top: 20px;" href="{{ post.url }}">{{ post.title }}</a>
        <p>{{ post.content}}</p>
    </li>
    {% endfor %}
</ul>

