---
layout: page
title: Tags 

---

<div class="page-content wc-container">
	<div class="post">
		<h1>Tags</h1>  
		<ul>
			{% for tag in site.tags %}
			<li>
                <a href="{{ '/tag/' | append:tag[0] | relative_url }}">{{ tag[0] }}</a>
                {% for page in site.pages %}
                    {{page.content}}
                    {% if page.layout == "tag_index" %}
                        <p>{{page.discription}}</p>
                    {% endif %}
                {% endfor %}
            </li>
			{% endfor %}
		</ul>
	</div>
</div>
