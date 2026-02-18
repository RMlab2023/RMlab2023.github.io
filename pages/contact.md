---
layout: default
title: Contact
subtitle: Get in touch with The Madsen Lab
permalink: /pages/contact/
---

<div class="page-header">
  <div class="container">
    <h1 class="page-title">Contact</h1>
    <p class="page-subtitle">We'd love to hear from you</p>
  </div>
</div>

<div class="page-content">
  <div class="container">
    <div class="row g-5 justify-content-center">

      <!-- Contact info -->
      <div class="col-lg-5">
        <span class="section-eyebrow">Find Us</span>
        <h2 class="section-title mt-1">Get in Touch</h2>
        <hr class="divider-teal left">

        <p>We welcome enquiries from prospective students, postdocs, collaborators, and anyone
        interested in our work.</p>

        <div class="contact-info-item">
          <div class="contact-info-icon">
            <i class="fas fa-envelope"></i>
          </div>
          <div>
            <strong>Email</strong><br>
            <a href="mailto:{{ site.lab.email }}">{{ site.lab.email }}</a>
          </div>
        </div>

        <div class="contact-info-item">
          <div class="contact-info-icon">
            <i class="fas fa-map-marker-alt"></i>
          </div>
          <div>
            <strong>Address</strong><br>
            CRUK Scotland Institute<br>
            Garscube Estate<br>
            Switchback Road<br>
            Bearsden<br>
            G61 1BD<br>
            United Kingdom
          </div>
        </div>

        <div class="contact-info-item">
          <div class="contact-info-icon">
            <i class="fab fa-github"></i>
          </div>
          <div>
            <strong>GitHub</strong><br>
            <a href="https://github.com/{{ site.lab.github }}" target="_blank" rel="noopener">
              github.com/{{ site.lab.github }}
            </a>
          </div>
        </div>

        {% if site.lab.twitter and site.lab.twitter != "" %}
        <div class="contact-info-item">
          <div class="contact-info-icon">
            <i class="fab fa-x-twitter"></i>
          </div>
          <div>
            <strong>Twitter/X</strong><br>
            <a href="https://twitter.com/{{ site.lab.twitter }}" target="_blank" rel="noopener">
              @{{ site.lab.twitter }}
            </a>
          </div>
        </div>
        {% endif %}

        <div class="mt-4">
          <h5>For prospective students and postdocs</h5>
          <p style="font-size:0.92rem;">
            Please read the <a href="{{ '/pages/supervision/' | relative_url }}">Supervision page</a>
            before getting in touch — it describes our supervision philosophy and what we look
            for in prospective lab members.
          </p>
        </div>

      </div>

      <!-- Map / Directions placeholder -->
      <div class="col-lg-5">
        <div class="contact-card" style="height:100%; min-height: 400px;">
          <h5 class="mb-3">Location</h5>
          <!--
            To embed a Google Maps iframe, replace the placeholder below with your embed code.
            Go to Google Maps → share → embed a map → copy the iframe code.
          -->
          <div style="background: var(--bg-light); border-radius: var(--radius); height: 280px;
                      display: flex; align-items: center; justify-content: center; flex-direction: column;
                      color: var(--text-muted); border: 1px dashed var(--border);">
            <i class="fas fa-map-marked-alt" style="font-size:2.5rem; margin-bottom:1rem; color: var(--teal);"></i>
            <p class="text-center mb-1">CRUK Scotland Institute</p>
            <p class="text-center" style="font-size:0.85rem;">Switchback Road, Bearsden, Glasgow</p>
            <a href="https://maps.google.com/?q=CRUK+Scotland+Institute,+Switchback+Road,+Bearsden,+G61+1BD"
               target="_blank" rel="noopener" class="btn btn-sm btn-outline-primary mt-2">
              <i class="fas fa-directions me-1"></i>Get directions
            </a>
          </div>
          <p class="mt-3 text-muted" style="font-size:0.85rem;">
            <i class="fas fa-train me-2"></i>
            Nearest station: Bearsden (ScotRail from Glasgow Queen Street)
          </p>
        </div>
      </div>

    </div>
  </div>
</div>
