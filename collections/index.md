---
title: Collections
permalink: /collections/
---

<style>
.col-box{border:1px solid rgba(0,0,0,.12);border-radius:10px;padding:18px 18px 10px;margin:18px 0 26px;background:#fff;}
.col-title{text-align:center;letter-spacing:.12em;font-weight:800;margin:2px 0 14px;position:relative;}
.col-title:before,.col-title:after{content:"";position:absolute;top:50%;width:36%;height:1px;background:rgba(0,0,0,.15);}
.col-title:before{left:0;} .col-title:after{right:0;}
.paper-card{border-top:1px solid rgba(0,0,0,.10);padding:14px 0;}
.paper-card:first-of-type{border-top:none;padding-top:0;}
.badge{display:inline-block;padding:2px 8px;border:1px solid rgba(0,0,0,.18);border-radius:999px;font-size:.85em;margin-right:6px;}
.vars{margin-top:10px;padding-left:18px;} .var-name{font-weight:700;} .small{opacity:.9;}
.btn{
  display:inline-block; padding:6px 10px; border:1px solid rgba(0,0,0,.18);
  border-radius:10px; text-decoration:none; font-weight:650; margin-right:8px; margin-top:10px;
}
.btn:hover{ text-decoration:none; transform: translateY(-1px); }
</style>

# Collections

A curated database of **variables + constructions** from top papers.

<div class="col-box">
  <div class="col-title">COLLECTIONS</div>

  {% assign items = site.data.collections | sort: "year" | reverse %}
  {% for p in items %}
    <div class="paper-card">
      <div>
        {% if p.year %}<span class="badge">{{ p.year }}</span>{% endif %}
        {% if p.field %}<span class="badge">{{ p.field }}</span>{% endif %}
      </div>

      <div style="font-weight:800; margin-top:6px;">
        {% if p.doi_url and p.doi_url != "" %}
          <a href="{{ p.doi_url }}">{{ p.title }}</a>
        {% elsif p.publisher_url and p.publisher_url != "" %}
          <a href="{{ p.publisher_url }}">{{ p.title }}</a>
        {% elsif p.link and p.link != "" %}
          <a href="{{ p.link }}">{{ p.title }}</a>
        {% else %}
          {{ p.title }}
        {% endif %}
      </div>

      <div class="small" style="margin-top:4px;">
        {% if p.authors %}{{ p.authors }}{% endif %}{% if p.venue and p.venue != "" %} — {{ p.venue }}{% endif %}
      </div>

      <div>
        {% if p.pdf_path and p.pdf_path != "" %}
          <a class="btn" href="{{ site.baseurl }}{{ p.pdf_path }}">PDF</a>
        {% endif %}
        {% if p.doi_url and p.doi_url != "" %}
          <a class="btn" href="{{ p.doi_url }}">DOI</a>
        {% endif %}
        {% if p.publisher_url and p.publisher_url != "" %}
          <a class="btn" href="{{ p.publisher_url }}">Publisher</a>
        {% endif %}
        {% if p.ssrn_url and p.ssrn_url != "" %}
          <a class="btn" href="{{ p.ssrn_url }}">SSRN</a>
        {% endif %}
        {% if p.slides_path and p.slides_path != "" %}
          <a class="btn" href="{{ site.baseurl }}{{ p.slides_path }}">Slides</a>
        {% endif %}
      </div>

      {% if p.takeaway and p.takeaway != "" %}
        <div style="margin-top:10px;">{{ p.takeaway }}</div>
      {% endif %}

      {% if p.variables and p.variables.size > 0 %}
        <ul class="vars">
          {% for v in p.variables %}
            <li>
              <span class="var-name">{{ v.name }}</span> — {{ v.definition }}<br/>
              <span class="small">
                <strong>Construction:</strong> {{ v.construction }}
                {% if v.frequency and v.frequency != "" %} · <strong>Freq:</strong> {{ v.frequency }}{% endif %}
                {% if v.sample and v.sample != "" %} · <strong>Sample:</strong> {{ v.sample }}{% endif %}
                {% if v.source and v.source != "" %} · <strong>Source:</strong> {{ v.source }}{% endif %}
                {% if v.notes and v.notes != "" %}<br/><strong>Notes:</strong> {{ v.notes }}{% endif %}
              </span>
            </li>
          {% endfor %}
        </ul>
      {% endif %}
    </div>
  {% endfor %}
</div>

<p style="margin-top:18px;">
  <a href="{{ site.baseurl }}/">← Back to Home</a>
</p>
