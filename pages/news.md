---
layout: default
title: News
subtitle: Latest updates from The Madsen Lab
permalink: /news/
---

<div class="page-header">
  <div class="container">
    <h1 class="page-title">Lab News</h1>
    <p class="page-subtitle">Updates from The Madsen Lab</p>
  </div>
</div>

<div class="page-content">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-lg-9">

        {% if site.posts.size == 0 %}
        <p class="text-muted">No posts yet — check back soon!</p>
        {% endif %}

        <div class="news-archive">
          {% for post in site.posts %}
          <div class="news-list-item">
            <div class="row g-3 align-items-start">
              <div class="col-auto" style="min-width:90px;">
                <div class="news-date" style="font-size:0.82rem; white-space:nowrap;">
                  {{ post.date | date: "%b %-d, %Y" }}
                </div>
              </div>
              <div class="col">
                <h4 style="font-size:1.05rem; margin-bottom:0.4rem;">
                  <a href="{{ post.url | relative_url }}" style="color: var(--navy);">{{ post.title }}</a>
                </h4>
                <p style="font-size:0.9rem; color: var(--text-muted); margin-bottom:0.5rem;">
                  {{ post.excerpt | strip_html | truncate: 200 }}
                </p>
                <a href="{{ post.url | relative_url }}" class="read-more" style="font-size:0.85rem; color: var(--teal); font-weight:600;">
                  Read more <i class="fas fa-arrow-right ms-1"></i>
                </a>
              </div>
            </div>
          </div>
          {% endfor %}
        </div>

      </div>
    </div>
  </div>
</div>
