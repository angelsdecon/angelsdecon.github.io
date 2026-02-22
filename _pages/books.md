---
layout: default
permalink: /misc2/
title: misc2
nav: true
nav_order: 5
pagination:
  enabled: true
  collection: posts
  permalink: /misc2/page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1
    after: 3
---

<div class="post">

{% assign blog_name_size = site.blog_name | size %}
{% assign blog_description_size = site.blog_description | size %}

{% if blog_name_size > 0 or blog_description_size > 0 %}
  <div class="header-bar">
    <h1>{{ site.blog_name }}</h1>
    <h2>{{ site.blog_description }}</h2>
  </div>
{% endif %}

{% assign featured_posts = site.posts | where: "featured", "true" %}
{% if featured_posts.size > 0 %}
<br>

<div class="container featured-posts">
{% assign is_even = featured_posts.size | modulo: 2 %}
<div class="row row-cols-{% if featured_posts.size <= 2 or is_even == 0 %}2{% else %}3{% endif %}">
{% for post in featured_posts %}
<div class="col mb-4">
<a href="{{ post.url | relative_url }}">
<div class="card hoverable">
<div class="row g-0">
<div class="col-md-12">
<div class="card-body">
<div class="float-right">
<i class="fa-solid fa-thumbtack fa-xs"></i>
</div>
<h3 class="card-title text-lowercase">{{ post.title }}</h3>
<p class="card-text">{{ post.description }}</p>

                    {% if post.external_source == blank %}
                      {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
                    {% else %}
                      {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
                    {% endif %}
                    {% assign year = post.date | date: "%Y" %}

                    <p class="post-meta">
                      {{ read_time }} min read   ·  
                      <a href="{{ year | prepend: '/blog/' | relative_url }}">
                        <i class="fa-solid fa-calendar fa-sm"></i> {{ year }} </a>
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </a>
        </div>
      {% endfor %}
      </div>
    </div>
    <hr>
{% endif %}

  <ul class="post-list">
    {% if page.pagination.enabled %}
      {% assign postlist = paginator.posts %}
    {% else %}
      {% assign postlist = site.posts %}
    {% endif %}

    {% for post in postlist %}

    {% if post.external_source == blank %}
      {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
    {% else %}
      {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
    {% endif %}
    {% assign year = post.date | date: "%Y" %}
    {% assign tags = post.tags | join: "" %}
    {% assign categories = post.categories | join: "" %}

    <li>
{% if post.thumbnail %}
<div class="row">
          <div class="col-sm-9">
{% endif %}
        <h3>
        {% if post.redirect == blank %}
          <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
        {% elsif post.redirect contains '://' %}
          <a class="post-title" href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
          <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
            <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
          </svg>
        {% else %}
          <a class="post-title" href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
        {% endif %}
      </h3>
      <p>{{ post.description }}</p>
      <p class="post-meta">
        {{ read_time }} min read   ·  
        {{ post.date | date: '%B %d, %Y' }}
        {% if post.external_source %}
          ·   {{ post.external_source }}
        {% endif %}
      </p>
      <p class="post-tags">
        <a href="{{ year | prepend: '/blog/' | relative_url }}">
          <i class="fa-solid fa-calendar fa-sm"></i> {{ year }} </a>
      </p>

{% if post.thumbnail %}
</div>
  <div class="col-sm-3">
    <img class="card-img" src="{{ post.thumbnail | relative_url }}" style="object-fit: cover; height: 90%" alt="image">
  </div>
</div>
{% endif %}
    </li>
    {% endfor %}
  </ul>

{% if page.pagination.enabled %}
{% include pagination.liquid %}
{% endif %}

</div>

<hr>

<div class="mt-5">
  <h4 class="mb-4">outside academia...</h4>
  
  <blockquote class="blockquote mb-4">
    <p>los nadie, los hijos de nadie, los dueños de nada.</p>
    <footer class="blockquote-footer">eduardo galeano</footer>
  </blockquote>

  <blockquote class="blockquote mb-5">
    <p>yo amo como aman los pobres, y me temo, que durante mucho, mucho tiempo esto seguirá siendo así.</p>
    <footer class="blockquote-footer">gata cattana</footer>
  </blockquote>

  <p>you can find books that i am reading, have read, or will read on <a href="https://www.goodreads.com/user/show/143207524" target="_blank">goodreads</a>.</p>

  <p>you can find films that i am watching, have watched, or will watch on <a href="https://boxd.it/b5MNP" target="_blank">letterbox</a>.</p>

  <p>you can find music i listen to during long coding sessions to not kill myself on <a href="https://open.spotify.com/user/1193392732?si=eH7rJxXdQNKnTGCt1lRFsA" target="_blank">spotify</a>. recommendations are more than welcome!</p>

  <p>check mate me!! <a href="https://www.chess.com" target="_blank">chess.com</a></p>
</div>
recommendations are more than welcome!

check mate me!! [chess.com]

</div>
