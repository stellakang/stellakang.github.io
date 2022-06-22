---
layout: page
comments: false
title: Opinion
banner: false
---

<div class="posts">
    {% for post in site.posts %}
    <article>
        <a href="{{ post.url }}" class="image"><img src="assets/images/pic09.jpg" alt="" /></a>
        <h3>{{ post.title }}</h3>
        <p>{{ post.date }}</p>
        <ul class="actions">
            <li><a href="{{ post.url }}" class="button">More</a></li>
        </ul>
    </article>
    {% endfor %}
</div>