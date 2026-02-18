---
layout: default
title: Home
---

<!-- ======================================================
     HERO
     ====================================================== -->
<section class="hero">
  <div class="container">
    <div class="row align-items-center g-5">
      <div class="col-lg-7">
        <span class="hero-eyebrow">UKRI Future Leaders Fellowship Lab</span>
        <h1>
          Decoding the <span>PI3K</span><br>Signalling Code
        </h1>
        <p class="lead">
          We are a quantitative systems biology lab at the CRUK Scotland Institute. Our mission
          is to understand how cellular context shapes the output of oncogenic
          <em>PIK3CA</em> activation — and to translate that understanding into
          novel <strong>state-gating</strong> therapeutic strategies.
        </p>
        <div class="d-flex flex-wrap gap-2 align-items-center">
          <a href="{{ '/pages/research/' | relative_url }}" class="btn-hero-primary">
            Our Research
          </a>
          <a href="{{ '/pages/people/' | relative_url }}" class="btn-hero-outline">
            Meet the Team
          </a>
        </div>
      </div>
      <div class="col-lg-5 hero-image-col d-none d-lg-flex">
        <img src="{{ '/assets/images/hero.png' | relative_url }}"
             alt="The Madsen Lab" class="img-fluid" style="border-radius: 1rem;">
      </div>
    </div>
  </div>
</section>

<!-- ======================================================
     STATS STRIP
     ====================================================== -->
<section class="stats-strip">
  <div class="container">
    <div class="row g-0 justify-content-center">
      <div class="col-6 col-md-3 stat-item">
        <div class="stat-number">2023</div>
        <div class="stat-label">Lab Founded</div>
      </div>
      <div class="col-6 col-md-3 stat-item">
        <div class="stat-number">FLF</div>
        <div class="stat-label">UKRI Future Leaders Fellowship</div>
      </div>
      <div class="col-6 col-md-3 stat-item">
        <div class="stat-number">PI3K</div>
        <div class="stat-label">Research Focus</div>
      </div>
      <div class="col-6 col-md-3 stat-item">
        <div class="stat-number">Open</div>
        <div class="stat-label">Science Committed</div>
      </div>
    </div>
  </div>
</section>

<!-- ======================================================
     RESEARCH HIGHLIGHTS
     ====================================================== -->
<section class="section-research">
  <div class="container">
    <div class="row mb-5">
      <div class="col-lg-8">
        <span class="section-eyebrow">What We Do</span>
        <h2 class="section-title">Research Areas</h2>
        <p class="section-lead">
          We combine quantitative experimental approaches with computational modelling
          to understand PI3K signalling in the context of oncogenic mutation,
          cellular plasticity, and targeted therapy.
        </p>
        <hr class="divider-teal left mt-3">
      </div>
    </div>
    <div class="row g-4">
      <div class="col-md-6 col-lg-3">
        <div class="research-card">
          <div class="research-icon">
            <i class="fas fa-project-diagram"></i>
          </div>
          <h4>PI3K Signalling Networks</h4>
          <p>Mapping how class IA PI3K processes information and how oncogenic
          <em>PIK3CA</em> mutations corrupt this logic.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="research-card">
          <div class="research-icon">
            <i class="fas fa-shapes"></i>
          </div>
          <h4>Cellular Context & Plasticity</h4>
          <p>Understanding how cell state and microenvironmental context
          shape the signalling outputs of oncogenic activation.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="research-card">
          <div class="research-icon">
            <i class="fas fa-flask"></i>
          </div>
          <h4>Single-Cell Quantification</h4>
          <p>Developing and deploying new frameworks for high-precision
          measurement of PI3K signalling at single-cell resolution.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="research-card">
          <div class="research-icon">
            <i class="fas fa-pills"></i>
          </div>
          <h4>State-Gating Therapies</h4>
          <p>Translating systems-level understanding into novel therapeutic
          strategies that exploit context-dependent vulnerabilities.</p>
        </div>
      </div>
    </div>
    <div class="mt-4 text-center">
      <a href="{{ '/pages/research/' | relative_url }}" class="btn btn-outline-primary">
        Full Research Overview <i class="fas fa-arrow-right ms-2"></i>
      </a>
    </div>
  </div>
</section>

<!-- ======================================================
     LATEST NEWS
     ====================================================== -->
<section class="section-news">
  <div class="container">
    <div class="row mb-5">
      <div class="col-lg-8">
        <span class="section-eyebrow">Lab Updates</span>
        <h2 class="section-title">Latest News</h2>
        <hr class="divider-teal left mt-3">
      </div>
    </div>
    <div class="row g-4">
      {% assign recent_posts = site.posts | limit: 3 %}
      {% for post in recent_posts %}
      <div class="col-md-4">
        <div class="news-card">
          <div class="news-card-body">
            <div class="news-date">{{ post.date | date: "%B %-d, %Y" }}</div>
            <h4><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h4>
            <p>{{ post.excerpt | strip_html | truncate: 120 }}</p>
            <a href="{{ post.url | relative_url }}" class="read-more">
              Read more <i class="fas fa-arrow-right ms-1"></i>
            </a>
          </div>
        </div>
      </div>
      {% endfor %}
    </div>
    <div class="mt-4 text-center">
      <a href="{{ '/news/' | relative_url }}" class="btn btn-outline-primary">
        All News <i class="fas fa-arrow-right ms-2"></i>
      </a>
    </div>
  </div>
</section>

<!-- ======================================================
     OPEN SCIENCE HIGHLIGHT
     ====================================================== -->
<section style="padding: 5rem 0; background: var(--navy);">
  <div class="container">
    <div class="row align-items-center g-5">
      <div class="col-lg-6">
        <span class="section-eyebrow" style="color: var(--teal-light);">Commitment</span>
        <h2 class="section-title" style="color: var(--white);">Open Science</h2>
        <p style="color: rgba(255,255,255,0.78); font-size: 1.05rem;">
          We are committed to open, trustworthy, and rigorous science.
        </p>
        <a href="{{ '/pages/open-science/' | relative_url }}" class="btn btn-outline-primary"
           style="color: var(--teal-light); border-color: var(--teal-light);">
          Our Research Integrity Practices <i class="fas fa-arrow-right ms-2"></i>
        </a>
      </div>
      <div class="col-lg-6">
        <div class="row g-3">
          <div class="col-6">
            <div class="feature-card" style="background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.1);">
              <div class="feature-icon" style="color: var(--gold);"><i class="fas fa-lock-open"></i></div>
              <h4 style="color: var(--white); font-size: 0.95rem;">Open Access</h4>
              <p style="color: rgba(255,255,255,0.6); font-size: 0.85rem; margin:0;">All publications made freely available.</p>
            </div>
          </div>
          <div class="col-6">
            <div class="feature-card" style="background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.1);">
              <div class="feature-icon" style="color: var(--gold);"><i class="fab fa-github"></i></div>
              <h4 style="color: var(--white); font-size: 0.95rem;">Open Code</h4>
              <p style="color: rgba(255,255,255,0.6); font-size: 0.85rem; margin:0;">Analysis code published on GitHub or the Open Science Framework.</p>
            </div>
          </div>
          <div class="col-6">
            <div class="feature-card" style="background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.1);">
              <div class="feature-icon" style="color: var(--gold);"><i class="fas fa-database"></i></div>
              <h4 style="color: var(--white); font-size: 0.95rem;">Open Data</h4>
              <p style="color: rgba(255,255,255,0.6); font-size: 0.85rem; margin:0;">Datasets deposited in public repositories.</p>
            </div>
          </div>
          <div class="col-6">
            <div class="feature-card" style="background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.1);">
              <div class="feature-icon" style="color: var(--gold);"><i class="fas fa-check-double"></i></div>
              <h4 style="color: var(--white); font-size: 0.95rem;">Research Integrity</h4>
              <p style="color: rgba(255,255,255,0.6); font-size: 0.85rem; margin:0;">We have a dedicated research integrity champion.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
