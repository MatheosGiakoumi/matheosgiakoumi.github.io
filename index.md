
---
layout: default
title: Home
---

<!-- =========== HERO =========== -->
<section id="about" class="hero">
  <h1>Matheos Giakoumi</h1>
  <p class="tagline">PhD student in Petroleum and Geosystems Engineering</p>
  <div class="intro">
    <p>
      I am a PhD student at the Hildebrand Department of Petroleum and Geosystems Engineering,
      The University of Texas at Austin, working under the supervision of
      <a href="https://pge.utexas.edu/facultystaff/faculty-directory/prodanovic" target="_blank" rel="noopener">Prof.&nbsp;Maša&nbsp;Prodanović</a>.
      My research concerns digital rock physics, pore-scale simulation, and upscaling methodologies,
      with applications to carbon dioxide storage, enhanced recovery, and underground hydrogen storage.
    </p>
    <p>
      Prior to joining UT Austin, I completed an MBA in Energy and Environmental Management and Economics
      (<a href="#education">MEDEA</a>) at <a href="https://www.eni.com/en-IT/careers/training/master/medea.html" target="_blank" rel="noopener">Eni Corporate University</a>, an MEng in Natural Gas Engineering at     the <a href="https://www.ucy.ac.cy/?lang=en" target="_blank" rel="noopener">University of Cyprus</a>, and a BS in Mechanical Engineering and Materials Science and Engineering at <a href="https://www.cut.ac.cy/?languageId=1?lang=en" target="_blank" rel="noopener">Cyprus University of Technology</a>,. I have held research positions at Eni S.p.A.&#39;s Well Operations department and at <a href="https://www.feem.it/ricerca/programmi/technologies-for-the-energy-transition/" target="_blank" rel="noopener">Fondazione Eni Enrico Mattei</a>, and in Summer 2026 I will join
      <a href="https://www.lanl.gov/" target="_blank" rel="noopener">Los Alamos National Laboratory</a>
      as a Graduate Research Intern with the Earth and Environmental Sciences Division.
      I currently serve as President of the SPWLA UT Austin Student Chapter and as a
      <strong>TEX-E Fellow</strong> in the Texas Energy Entrepreneurship programme.
    </p>
  </div>
</section>

<!-- =========== AWARDS =========== -->
<section id="awards">
  <div class="section-head">
    <h2>Honours and Awards</h2>
    <span class="count">{{ site.data.awards | size }}</span>
  </div>
  <div class="awards-grid">
    {% for award in site.data.awards %}
      <div class="award">
        <div class="year">{{ award.year }}</div>
        <div class="title">
          {% if award.url %}
            <a href="{{ award.url }}" target="_blank" rel="noopener">{{ award.title }}</a>
          {% else %}
            {{ award.title }}
          {% endif %}
        </div>
        <div class="venue">{{ award.venue }}{% if award.location %} · {{ award.location }}{% endif %}</div>
        {% if award.detail %}<div class="detail">{{ award.detail }}</div>{% endif %}
      </div>
    {% endfor %}
  </div>
</section>

<!-- =========== EDUCATION =========== -->
<section id="education">
  <div class="section-head">
    <h2>Education</h2>
  </div>

  {% for edu in site.data.education %}
    <div class="edu">
      <div class="edu-head">
        <h3 class="degree">
          {% if edu.url %}<a href="{{ edu.url }}" target="_blank" rel="noopener">{{ edu.degree }}</a>
          {% else %}{{ edu.degree }}{% endif %}
        </h3>
        <span class="period">{{ edu.period }}</span>
      </div>
      <div class="institution">{{ edu.institution }}</div>
      {% if edu.department %}<div class="department">{{ edu.department }}</div>{% endif %}
      {% if edu.gpa %}<span class="gpa">{{ edu.gpa }}</span>{% endif %}

      {% if edu.highlights %}
      <ul class="highlights">
        {% for h in edu.highlights %}
          <li>
            <strong>
              {% if h.url %}<a href="{{ h.url }}" target="_blank" rel="noopener">{{ h.label }}</a>
              {% else %}{{ h.label }}{% endif %}
            </strong>{% if h.detail %} — {{ h.detail | markdownify | remove: '<p>' | remove: '</p>' }}{% endif %}
          </li>
        {% endfor %}
      </ul>
      {% endif %}

      {% if edu.thesis %}
        <div class="thesis">
          <strong>Thesis</strong>
          <em>{{ edu.thesis.title }}</em>
          {% if edu.thesis.description %} — {{ edu.thesis.description | markdownify | remove: '<p>' | remove: '</p>' }}{% endif %}
        </div>
      {% endif %}

      {% if edu.scholarship %}
        <div class="scholarship">
          <strong>Scholarship</strong>
          {{ edu.scholarship | markdownify | remove: '<p>' | remove: '</p>' }}
        </div>
      {% endif %}

      {% if edu.courses %}
        <div class="courses">
          <strong>Notable coursework</strong>
          {{ edu.courses | join: ' · ' }}
        </div>
      {% endif %}

      {% if edu.image %}
        <div class="card-images">
          <img src="{{ edu.image | relative_url }}" alt="" loading="lazy">
        </div>
      {% endif %}
    </div>
  {% endfor %}
</section>

<!-- =========== EXPERIENCE =========== -->
<section id="experience">
  <div class="section-head">
    <h2>Research Experience</h2>
    <span class="count">{{ site.data.experiences | size }}</span>
  </div>

  {% for exp in site.data.experiences %}
    <div class="exp{% if exp.current %} current{% endif %}{% if exp.upcoming %} upcoming{% endif %}">
      <div class="exp-head">
        <div class="period">
          {{ exp.period }}
          {% if exp.upcoming %}<span class="period-badge">Upcoming</span>{% endif %}
        </div>
        <h3 class="role">{{ exp.role }}</h3>
        <div class="org">
          {% if exp.organization_url %}
            <a href="{{ exp.organization_url }}" target="_blank" rel="noopener">{{ exp.organization }}</a>
          {% else %}{{ exp.organization }}{% endif %}
        </div>
        {% if exp.supervisor %}
          <div class="sup">
            Supervisor:
            {% if exp.supervisor_url %}
              <a href="{{ exp.supervisor_url }}" target="_blank" rel="noopener">{{ exp.supervisor }}</a>
            {% else %}{{ exp.supervisor }}{% endif %}
          </div>
        {% endif %}
      </div>

      {% if exp.tags %}
        <div class="tags">
          {% for t in exp.tags %}<span class="tag">{{ t }}</span>{% endfor %}
        </div>
      {% endif %}

      {% if exp.funding %}
        <div class="funding">
          <div class="f-label">Funded project — {{ exp.funding.name }}</div>
          {% if exp.funding.detail %}{{ exp.funding.detail }}. {% endif %}
          {% if exp.funding.grant_id %}({{ exp.funding.grant_id }}). {% endif %}
          {% if exp.funding.funder %}{{ exp.funding.funder }}. {% endif %}
          <strong>{{ exp.funding.amount }}</strong>.
          {% if exp.funding.achievement %} {{ exp.funding.achievement | markdownify | remove: '<p>' | remove: '</p>' }}{% endif %}
          {% if exp.funding.url %} <a href="{{ exp.funding.url }}" target="_blank" rel="noopener">Project page →</a>{% endif %}
        </div>
      {% endif %}

      {% for p in exp.projects %}
        <div class="project">
          <div class="p-title">{{ p.title }}</div>
          <p class="p-desc">{{ p.description | markdownify | remove: '<p>' | remove: '</p>' }}</p>
        </div>
      {% endfor %}

      {% if exp.images %}
        <div class="card-images">
          {% for img in exp.images %}
            <img src="{{ img | relative_url }}" alt="" loading="lazy">
          {% endfor %}
        </div>
      {% endif %}
    </div>
  {% endfor %}
</section>

<!-- =========== PUBLICATIONS =========== -->
<section id="publications">
  <div class="section-head">
    <h2>Publications</h2>
    <span class="count">{{ site.data.publications | size }}</span>
  </div>

  {% for pub in site.data.publications %}
    <div class="pub{% if pub.featured %} featured{% endif %}">
      <div class="authors">{{ pub.authors | markdownify | remove: '<p>' | remove: '</p>' }}</div>
      <div class="title">
        {% if pub.url %}
          <a href="{{ pub.url }}" target="_blank" rel="noopener">{{ pub.title }}</a>
        {% else %}{{ pub.title }}{% endif %}
      </div>
      {% if pub.venue or pub.volume or pub.date %}
        <div class="venue-line">
          {% if pub.venue %}<em>{{ pub.venue }}</em>{% endif %}
          {% if pub.volume %} · {{ pub.volume }}{% endif %}
          {% if pub.date %} · {{ pub.date }}{% endif %}
          {% if pub.note %} · <span style="color: var(--muted);">{{ pub.note }}</span>{% endif %}
        </div>
      {% endif %}
      <div class="meta">
        {% if pub.featured %}<span class="tag featured">Featured</span>{% endif %}
        <span class="tag {{ pub.status }}">
          {% case pub.status %}
            {% when 'published' %}Published
            {% when 'under_review' %}Under review
            {% when 'in_preparation' %}In preparation
            {% else %}{{ pub.status }}
          {% endcase %}
        </span>
        {% if pub.corresponding %}<span class="tag corresponding">Corresponding author</span>{% endif %}
        {% if pub.doi %}
          <a href="https://doi.org/{{ pub.doi }}" target="_blank" rel="noopener" class="doi-link">doi: {{ pub.doi }}</a>
        {% endif %}
      </div>
    </div>
  {% endfor %}
</section>

<!-- =========== CONFERENCES =========== -->
<section id="conferences">
  <div class="section-head">
    <h2>Conference Presentations</h2>
    <span class="count">{{ site.data.conferences | size }}</span>
  </div>

  {% for c in site.data.conferences %}
    <div class="pub">
      {% if c.authors %}<div class="authors">{{ c.authors | markdownify | remove: '<p>' | remove: '</p>' }}</div>{% endif %}
      <div class="title">
        {% if c.url %}<a href="{{ c.url }}" target="_blank" rel="noopener">{{ c.title }}</a>
        {% else %}{{ c.title }}{% endif %}
      </div>
      <div class="venue-line">
        <em>{{ c.venue }}</em>
        {% if c.location %} · {{ c.location }}{% endif %}
        {% if c.date %} · {{ c.date }}{% endif %}
      </div>
      <div class="meta">
        {% if c.award %}
          <span class="tag award">
            {% if c.award_url %}<a href="{{ c.award_url }}" target="_blank" rel="noopener" style="color: inherit;">{{ c.award }}</a>
            {% else %}{{ c.award }}{% endif %}
          </span>
        {% endif %}
        {% if c.status == 'upcoming' %}<span class="tag upcoming">Upcoming</span>{% endif %}
        {% if c.attendance_only %}<span class="tag">Attended</span>{% endif %}
        {% if c.doi %}
          <a href="https://doi.org/{{ c.doi }}" target="_blank" rel="noopener" class="doi-link">doi: {{ c.doi }}</a>
        {% endif %}
      </div>
    </div>
  {% endfor %}
</section>

<!-- =========== TEACHING =========== -->
<section id="teaching">
  <div class="section-head">
    <h2>Teaching</h2>
  </div>

  {% for t in site.data.teaching %}
    <div class="exp">
      <div class="exp-head">
        <div class="period">{{ t.period }}</div>
        <h3 class="role">{{ t.role }}</h3>
        <div class="org">
          {% if t.organization_url %}
            <a href="{{ t.organization_url }}" target="_blank" rel="noopener">{{ t.organization }}</a>
          {% else %}{{ t.organization }}{% endif %}
        </div>
      </div>
      {% if t.description %}<p style="font-size: 0.9rem; color: var(--ink-2);">{{ t.description }}</p>{% endif %}
      {% if t.courses %}
        <div>
          {% for c in t.courses %}
            <div class="teach-course">
              {% if c.code %}<span class="code">{{ c.code }}</span>{% endif %}
              <strong>{{ c.name }}</strong>
              {% if c.level %}<span style="color: var(--muted); font-size: 0.78rem;"> · {{ c.level }}</span>{% endif %}
              {% if c.description %}<div style="color: var(--ink-2); margin-top: 3px; font-size: 0.82rem;">{{ c.description }}</div>{% endif %}
            </div>
          {% endfor %}
        </div>
      {% endif %}
    </div>
  {% endfor %}
</section>

<!-- =========== SKILLS & CONTACT =========== -->
<section id="skills">
  <div class="section-head">
    <h2>Skills and Contact</h2>
  </div>

  <h3 style="margin-top: 0;">Technical</h3>
  <div class="skills">
    <span class="tag">Python</span>
    <span class="tag">MATLAB &amp; Simulink</span>
    <span class="tag">C++</span>
    <span class="tag">Solidity</span>
    <span class="tag">Petrel</span>
    <span class="tag">OriginLab</span>
    <span class="tag">SolidWorks</span>
    <span class="tag">PLEXOS</span>
    <span class="tag">dfnWorks</span>
    <span class="tag">CMG</span>
    <span class="tag">Lattice Boltzmann Methods</span>
    <span class="tag">Bayesian Mixture Models</span>
    <span class="tag">Finite Element Methods</span>
  </div>

  <h3>Languages</h3>
  <div class="skills">
    <span class="tag">Greek — native</span>
    <span class="tag">English — professional</span>
    <span class="tag">Italian — intermediate</span>
  </div>

  <h3>Interests</h3>
  <p style="color: var(--ink-2);">
    Basketball, full-stack development, Web3 and smart-contract development on Ethereum,
    and the geopolitics of energy.
  </p>

  <h3>Contact</h3>
  <p>
    Correspondence is best directed to
    <a href="mailto:{{ site.author.email }}">{{ site.author.email }}</a>,
    or through the professional profiles listed in the sidebar.
  </p>
</section>

