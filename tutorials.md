---
layout: page2
title: Tutorials
---

{% assign tutorials = site['tutorials'] | sort: "date" %}

<div class="row row-cols-3 row-cols-md-4">
    {% for tutorial in tutorials %}
      <div class="col sm-6 mb-4">
        <div class="card h-100 box-shadow-hover pointer">
          <img src="{{ tutorial.thumbnail }}" class="card-img-" alt="...">
          <div class="card-body">
            <h4 class="card-title"> {{ tutorial.title }}</h4>
            <p class="card-subtitle small text-muted mb-2"> {{ tutorial.subtitle}}</p>
	    <p class="card-text"><small class="text-muted"> {{ tutorial.date | date: "%-d %B %Y" }}</small></p>
            <a href="{{ tutorial.url }}" class="stretched-link"></a>
          </div>
        </div>
      </div>
    {% endfor %}
</div>
