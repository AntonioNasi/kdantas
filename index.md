---
layout: default
title: Início
---

<section class="sec-prev">
    <div class="cx-prev">
        {% for post in site.posts limit:4 %}
        <article class="post-preview">    
            {% if post.image %}
                <a class="a-img" href="{{ post.url | relative_url }}">
                    <img src="{{ post.image }}" alt="{{ post.title }}" class="post-thumb">
                </a>
            {% endif %}
            <div class="cx-txt-preview">
                <h2>
                    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                </h2>
                <p class="post-meta">
                    {{ post.date | date: "%d/%m/%Y" }}
                    {% if post.categories and post.categories.size > 0 %}
                    •
                    {% for category in post.categories %}
                    <a href="/categories/{{ category | slugify }}/"  class="preview-category">
                        {{ category }}
                    </a>{% unless forloop.last %} {% endunless %}
                    {% endfor %}
                    {% endif %}
                </p>
                <p>{{ post.excerpt | strip_html | truncatewords: 15 }}</p>
            </div>
        </article>
        {% endfor %}
    </div>
</section>