---
layout: page
title: "News"
permalink: /news/
show_sidebar: false
hero_height: is-fullwidth
hide_footer: true
---


{% assign news_posts = site.posts
  | where_exp: "p", "p.categories contains 'news'"
  | sort: "date" | reverse %}

{% if news_posts == empty %}
<p>No news yet — check back soon.</p>
{% else %}
  {% for post in news_posts %}
  <article class="content mb-6">
    <h2 class="title is-4">
      <a href="{{ post.url | absolute_url }}">{{ post.title }}</a>
    </h2>
    <p class="has-text-grey is-size-7">{{ post.date | date: "%-d %b %Y" }}</p>

    {{ post.content }}

  </article>

  <hr class="my-6">
  {% endfor %}
{% endif %}

