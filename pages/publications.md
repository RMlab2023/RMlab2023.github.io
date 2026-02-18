---
layout: default
title: Publications
subtitle: Research outputs from The Madsen Lab
permalink: /pages/publications/
---

<div class="page-header">
  <div class="container">
    <h1 class="page-title">Publications</h1>
    <p class="page-subtitle">Research outputs from The Madsen Lab</p>
  </div>
</div>

<div class="page-content">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-lg-10">

        <p class="lead mb-4">
          We are committed to open access publishing. Preprint versions of all
          articles are available on <a href="https://www.biorxiv.org" target="_blank" rel="noopener">bioRxiv</a>
          where possible.
          For a full list of Dr. Madsen's publications,
          see her
          <a href="https://scholar.google.com/citations?user=URyHn70AAAAJ&hl=en" target="_blank" rel="noopener">Google Scholar profile</a>.
        </p>

        <!-- Highlighted publications -->
        {% assign highlighted = site.data.publications | where: "highlight", true %}
        {% if highlighted.size > 0 %}
        <h2>Selected Publications</h2>
        {% for pub in highlighted %}
        <div class="publication-item">
          <div class="pub-title">{{ pub.title }}</div>
          <div class="pub-authors">{{ pub.authors }}</div>
          {% if pub.journal %}<div class="pub-journal">{{ pub.journal }} ({{ pub.year }})</div>{% endif %}
          {% if pub.description %}<p style="font-size:0.9rem; color: var(--text-muted); margin:0.4rem 0;">{{ pub.description }}</p>{% endif %}
          <div class="pub-badges mt-2 d-flex flex-wrap gap-2 align-items-center">
            {% if pub.status == "preprint" %}<span class="badge badge-preprint">Preprint</span>{% endif %}
            {% if pub.status == "published" %}<span class="badge badge-published">Published</span>{% endif %}
            {% if pub.status == "in-review" %}<span class="badge badge-review">In Review</span>{% endif %}
            {% if pub.doi and pub.doi != "" %}
            <a href="https://doi.org/{{ pub.doi }}" target="_blank" rel="noopener"
               class="btn btn-sm btn-outline-primary" style="font-size:0.78rem; padding:0.2rem 0.7rem;">
              <i class="fas fa-external-link-alt me-1"></i>Published version
            </a>
            {% endif %}
            {% if pub.preprint_doi and pub.preprint_doi != "" %}
            <a href="https://doi.org/{{ pub.preprint_doi }}" target="_blank" rel="noopener"
               class="btn btn-sm btn-outline-secondary" style="font-size:0.78rem; padding:0.2rem 0.7rem;">
              <i class="fas fa-file-alt me-1"></i>Preprint
            </a>
            {% endif %}
          </div>
        </div>
        {% endfor %}
        {% endif %}

        <!-- All publications -->
        {% assign all_pubs = site.data.publications | where_exp: "p", "p.highlight != true" %}
        {% if all_pubs.size > 0 %}
        <h2 class="mt-5">All Publications</h2>
        {% for pub in all_pubs %}
        <div class="publication-item">
          <div class="pub-title">{{ pub.title }}</div>
          <div class="pub-authors">{{ pub.authors }}</div>
          {% if pub.journal %}<div class="pub-journal">{{ pub.journal }} ({{ pub.year }})</div>{% endif %}
          <div class="pub-badges mt-2 d-flex flex-wrap gap-2 align-items-center">
            {% if pub.status == "preprint" %}<span class="badge badge-preprint">Preprint</span>{% endif %}
            {% if pub.status == "published" %}<span class="badge badge-published">Published</span>{% endif %}
            {% if pub.status == "in-review" %}<span class="badge badge-review">In Review</span>{% endif %}
            {% if pub.doi and pub.doi != "" %}
            <a href="https://doi.org/{{ pub.doi }}" target="_blank" rel="noopener"
               class="btn btn-sm btn-outline-primary" style="font-size:0.78rem; padding:0.2rem 0.7rem;">
              <i class="fas fa-external-link-alt me-1"></i>Published version
            </a>
            {% endif %}
            {% if pub.preprint_doi and pub.preprint_doi != "" %}
            <a href="https://doi.org/{{ pub.preprint_doi }}" target="_blank" rel="noopener"
               class="btn btn-sm btn-outline-secondary" style="font-size:0.78rem; padding:0.2rem 0.7rem;">
              <i class="fas fa-file-alt me-1"></i>Preprint
            </a>
            {% endif %}
          </div>
        </div>
        {% endfor %}
        {% endif %}

        {% if site.data.publications.size == 0 %}
        <div class="alert" style="background: var(--teal-pale); border: 1px solid rgba(42,157,143,0.2); border-radius: var(--radius);">
          <i class="fas fa-info-circle me-2" style="color: var(--teal);"></i>
          Publications will appear here once added to <code>_data/publications.yml</code>.
          See <a href="https://github.com/{{ site.lab.github }}/blob/main/CONTRIBUTING.md">CONTRIBUTING.md</a>
          for instructions on adding publications.
        </div>
        {% endif %}

        <hr class="my-5">
        <p class="text-muted" style="font-size:0.9rem;">
          <i class="fas fa-edit me-2"></i>
          To add a publication, edit <code>_data/publications.yml</code> in the
          <a href="https://github.com/{{ site.lab.github }}" target="_blank" rel="noopener">GitHub repository</a>.
        </p>

      </div>
    </div>
  </div>
</div>
