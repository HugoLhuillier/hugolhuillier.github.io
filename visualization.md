---
layout: page
title: Visualization
permalink: /visualization/
---

{% for project in site.visualization %}

<div class="project ">
    <div class="thumbnail">
        <a href="{{ site.baseurl }}{{ project.url }}">
        {% if project.img %}
        <img class="thumbnail" src="{{ project.img }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span>
            <h3>{{ project.title }}</h3>
        </span>
        </a>
    </div>
</div>

{% endfor %}
