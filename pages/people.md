---
layout: default
title: People
subtitle: The Madsen Lab team
permalink: /pages/people/
---

<div class="page-header">
  <div class="container">
    <h1 class="page-title">People</h1>
    <p class="page-subtitle">The Madsen Lab team</p>
  </div>
</div>

<div class="page-content">
  <div class="container">

    <!-- Principal Investigator -->
    {% assign pi = site.data.team | where: "group", "pi" %}
    {% if pi.size > 0 %}
    <div class="row mb-5">
      <div class="col-12">
        <span class="section-eyebrow">Principal Investigator</span>
        <h2 class="section-title mt-1">Lab Head</h2>
        <hr class="divider-teal left">
      </div>
      {% for member in pi %}
      <div class="col-lg-8">
        <div class="row g-4 align-items-start">
          <div class="col-auto">
            {% if member.photo and member.photo != "" %}
            <img src="{{ '/assets/images/team/' | append: member.photo | relative_url }}"
                 alt="{{ member.name }}" class="person-photo" style="width:160px;height:160px;">
            {% else %}
            <div class="person-photo-placeholder" style="width:160px;height:160px;">
              <i class="fas fa-user"></i>
            </div>
            {% endif %}
          </div>
          <div class="col">
            <div class="person-name" style="font-size:1.4rem;">{{ member.name }}</div>
            <div class="person-role">{{ member.role }}</div>
            <p class="mt-2">{{ member.bio }}</p>
            <div class="person-links mt-2">
              {% if member.email and member.email != "" %}
              <a href="mailto:{{ member.email }}" title="Email"><i class="fas fa-envelope"></i></a>
              {% endif %}
              {% if member.twitter and member.twitter != "" %}
              <a href="https://twitter.com/{{ member.twitter }}" target="_blank" rel="noopener" title="Twitter/X"><i class="fab fa-x-twitter"></i></a>
              {% endif %}
              {% if member.github and member.github != "" %}
              <a href="https://github.com/{{ member.github }}" target="_blank" rel="noopener" title="GitHub"><i class="fab fa-github"></i></a>
              {% endif %}
              {% if member.orcid and member.orcid != "" %}
              <a href="https://orcid.org/{{ member.orcid }}" target="_blank" rel="noopener" title="ORCID"><i class="fab fa-orcid"></i></a>
              {% endif %}
              {% if member.google_scholar and member.google_scholar != "" %}
              <a href="{{ member.google_scholar }}" target="_blank" rel="noopener" title="Google Scholar"><i class="fas fa-graduation-cap"></i></a>
              {% endif %}
              {% if member.website and member.website != "" %}
              <a href="{{ member.website }}" target="_blank" rel="noopener" title="Website"><i class="fas fa-globe"></i></a>
              {% endif %}
            </div>
          </div>
        </div>
      </div>
      {% endfor %}
    </div>
    {% endif %}

    <!-- PhD Students -->
    {% assign phd = site.data.team | where: "group", "phd" %}
    {% if phd.size > 0 %}
    <div class="row mb-5">
      <div class="col-12">
        <span class="section-eyebrow">Current Members</span>
        <h2 class="section-title mt-1">PhD Students</h2>
        <hr class="divider-teal left">
      </div>
      {% for member in phd %}
      <div class="col-sm-6 col-lg-4 mb-4">
        <div class="person-card">
          {% if member.photo and member.photo != "" %}
          <img src="{{ '/assets/images/team/' | append: member.photo | relative_url }}"
               alt="{{ member.name }}" class="person-photo">
          {% else %}
          <div class="person-photo-placeholder"><i class="fas fa-user"></i></div>
          {% endif %}
          <div class="person-name">{{ member.name }}</div>
          <div class="person-role">{{ member.role }}</div>
          <p class="person-bio">{{ member.bio }}</p>
          <div class="person-links">
            {% if member.email and member.email != "" %}
            <a href="mailto:{{ member.email }}" title="Email"><i class="fas fa-envelope"></i></a>
            {% endif %}
            {% if member.twitter and member.twitter != "" %}
            <a href="https://twitter.com/{{ member.twitter }}" target="_blank" rel="noopener" title="Twitter/X"><i class="fab fa-x-twitter"></i></a>
            {% endif %}
            {% if member.github and member.github != "" %}
            <a href="https://github.com/{{ member.github }}" target="_blank" rel="noopener" title="GitHub"><i class="fab fa-github"></i></a>
            {% endif %}
            {% if member.orcid and member.orcid != "" %}
            <a href="https://orcid.org/{{ member.orcid }}" target="_blank" rel="noopener" title="ORCID"><i class="fab fa-orcid"></i></a>
            {% endif %}
          </div>
        </div>
      </div>
      {% endfor %}
    </div>
    {% endif %}

    <!-- Postdocs -->
    {% assign postdocs = site.data.team | where: "group", "postdoc" %}
    {% if postdocs.size > 0 %}
    <div class="row mb-5">
      <div class="col-12">
        <h2 class="section-title">Postdoctoral Researchers</h2>
        <hr class="divider-teal left">
      </div>
      {% for member in postdocs %}
      <div class="col-sm-6 col-lg-4 mb-4">
        <div class="person-card">
          {% if member.photo and member.photo != "" %}
          <img src="{{ '/assets/images/team/' | append: member.photo | relative_url }}"
               alt="{{ member.name }}" class="person-photo">
          {% else %}
          <div class="person-photo-placeholder"><i class="fas fa-user"></i></div>
          {% endif %}
          <div class="person-name">{{ member.name }}</div>
          <div class="person-role">{{ member.role }}</div>
          <p class="person-bio">{{ member.bio }}</p>
          <div class="person-links">
            {% if member.email and member.email != "" %}
            <a href="mailto:{{ member.email }}" title="Email"><i class="fas fa-envelope"></i></a>
            {% endif %}
            {% if member.github and member.github != "" %}
            <a href="https://github.com/{{ member.github }}" target="_blank" rel="noopener" title="GitHub"><i class="fab fa-github"></i></a>
            {% endif %}
          </div>
        </div>
      </div>
      {% endfor %}
    </div>
    {% endif %}

    <!-- Alumni -->
    {% assign alumni = site.data.team | where: "group", "alumni" %}
    {% if alumni.size > 0 %}
    <div class="row mb-4">
      <div class="col-12">
        <h2 class="section-title">Alumni</h2>
        <hr class="divider-teal left">
        <ul class="list-unstyled">
          {% for member in alumni %}
          <li class="mb-2">
            <strong>{{ member.name }}</strong> — {{ member.role }}
            {% if member.bio %}<br><small class="text-muted">{{ member.bio }}</small>{% endif %}
          </li>
          {% endfor %}
        </ul>
      </div>
    </div>
    {% endif %}

    <!-- Join us -->
    <div class="row mt-4">
      <div class="col-lg-8">
        <div class="contact-card" style="background: var(--teal-pale); border: 1px solid rgba(42,157,143,0.2);">
          <h3 style="color: var(--navy);">Join the Lab</h3>
          <p>We are always interested in hearing from motivated scientists who are excited about
          quantitative biology and PI3K signalling. Whether you are looking for a postdoc,
          PhD rotation, or project placement, please reach out.</p>
          <a href="{{ '/pages/contact/' | relative_url }}" class="btn btn-primary">
            <i class="fas fa-paper-plane me-2"></i>Get in Touch
          </a>
        </div>
      </div>
    </div>

  </div>
</div>
