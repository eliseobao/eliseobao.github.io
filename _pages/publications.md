---
layout: page
permalink: /publications/
title: publications
# description: See updated list on <a href="https://scholar.google.com/citations?user=evKkNoMAAAAJ&hl">Google Scholar</a>.
years: [2022, 2023, 2024]
categories: ['conferences', 'journals', 'theses']
catprint: ['', 'conferences', 'journals', 'theses']
nav: true
---

<div class="publications">

{% for cat_ in page.categories  %}
	{% assign ind = forloop.index %}

	{%- capture cat -%}
	{{ page.catprint[ind] }}
	{%- endcapture -%}
	
	<h4 class="font-weight-bolder">{{cat}}</h4>
	{% for y in page.years reversed  %}
		{%- capture citecount -%}
		{% bibliography_count -f papers -q @*[kind={{cat_}} && year={{y}}]* %}
		{%- endcapture -%}

		{% if citecount != "0"  %}
			{% bibliography -f papers -q @*[kind={{cat_}} && year={{y}}]* %}
		{% endif %}
	{% endfor %}
{% endfor %}

</div>
