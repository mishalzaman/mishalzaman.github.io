---
title: Ruby on Rails
subtitle: Framework
layout: "default"
icon: fa-gem
order: 4
---

{%- assign _posts = site.posts | sort: 'date' -%}
{%- include header.html scrolly_nav=_posts -%}
<!-- Main -->
<div id="main">
	<!-- Posts List -->
    {%- for _post in _posts -%}
        {% if _post.path contains 'ruby_on_rails' %}
            {%- capture _title -%}
                <a href="{{- _post.url | absolute_url -}}">{{- _post.title -}}</a>
            {%- endcapture -%}
            {%- assign _content = _excerpt | append: _link -%}
            {%- include section.html title=_title subtitle=_subtitle content=_content -%}
        {% endif %}
	{%- endfor -%}
</div>