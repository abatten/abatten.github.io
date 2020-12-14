---
layout: page2
title: Tutorials
---

<br>

{% assign tutorials = site['tutorials'] | sort: "date" %}

<div class="d-flex flex-wrap">
{% for tutorial in tutorials %}

      <div>
        <div class="card h-100 tutorial-card">
        <a href="{{ tutorial.url }}" class="stretched-link"></a>
            <img src="{{ tutorial.thumbnail }}" class="card-img-tutorial px-2 pt-2 py-0" alt="...">
          <div class="card-body py-0">
            <h4 class="card-title"> {{ tutorial.title }}</h4>
            <p class="card-subtitle small text-muted mb-1"> {{ tutorial.subtitle}}</p>
	    <p class="card-subtitle"><small class="text-muted"> Last Updated: {{ tutorial.lastupdated | date_to_string }}</small></p>
          </div>
        </div>
      </div>
{% endfor %}

</div>
