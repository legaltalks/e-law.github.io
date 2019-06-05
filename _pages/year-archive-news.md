---
layout: archive
title: "연도별 새소식"
permalink: /news/
collection: news
author_profile: true
---

<ul class="taxonomy__index">
  {% assign newsInYear = site.news | group_by_exp: 'news', 'news.date | date: "%Y"' %}
  {% for year in newsInYear %}
    <li>
      <a href="#{{ year.name }}">
        <strong>{{ year.name }}</strong> <span class="taxonomy__count">{{ year.items | size }}</span>
      </a>
    </li>
  {% endfor %}
</ul>

{% assign newsByYear = site.news | group_by_exp: 'news', 'news.date | date: "%Y"' %}
{% for year in newsByYear %}
 <section id="{{year.name}}" class="taxonomy_section">
  <h2 class="archive_subtitle">{{year.name}}</h2>
  <div class="entries-{{ page.entries_layout | default: 'list' }}">
    {% for news in year.items %}
    {% include documents-collection.html %}
   <a href="{{ news.url }}"> {{ news.title }}</a>  issued at {{ news.date | date: "%b  %d" }}<br>
    {{ news.excerpt }} <br><br>
{% endfor %}
 </div>
    <a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a>
  </section>
{% endfor %}
