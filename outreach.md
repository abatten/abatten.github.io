---
layout: page2
title: Science Outreach
---

<br>

{% assign tutorials = site['outreach'] | sort: "date" %}

<div class="d-flex flex-wrap">
{% for tutorial in tutorials %}
      <div>
        <div class="card p-0 my-auto tutorial-card">
        <a href="{{ tutorial.url }}" class="stretched-link"></a>
            <img src="{{ tutorial.thumbnail }}" class="card-img-tutorial">
            <div class="card-body">
            <h5 class="card-title"> {{ tutorial.title }}</h5>
            <p class="card-subtitle small text-muted mb-1"> {{ tutorial.subtitle}}</p>
	    <p class="card-text"><small class="text-muted"> Date: {{ tutorial.date | date_to_string }}</small></p>
          </div>
        </div>
      </div>
{% endfor %}

</div>
