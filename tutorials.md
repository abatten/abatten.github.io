---
layout: page2
title: Tutorials
---

{% assign tutorials = site['tutorials'] | sort: "date" %}

<div class="d-flex flex-row">
    {% for tutorial in tutorials %}
      <div>
        <div class="card box-shadow-hover pointer" style="max-width: 300px;">
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
