---
title: General Development
subtitle: General
layout: "default"
icon: fa-code
order: 6
---

{%- assign _posts = site.posts | sort: 'date' -%}
{%- include header.html scrolly_nav=_posts -%}
<!-- Main -->
<div id="main">
	<!-- Posts List -->
    {%- for _post in _posts -%}
        {% if _post.path contains 'general_development' %}
            {%- capture _title -%}
                <a href="{{- _post.url | absolute_url -}}">{{- _post.title -}}</a>
            {%- endcapture -%}
            {%- assign _content = _excerpt | append: _link -%}
            {%- include section.html title=_title subtitle=_subtitle content=_content -%}
        {% endif %}
	{%- endfor -%}
</div>