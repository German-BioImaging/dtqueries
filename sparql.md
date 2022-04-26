
## Contents:

<ol>
{% for rec in sparql %}
  <li><a href="#{{ rec.name | slugify }}">{{ rec.name }}</a></li>
{% endfor %}
</ol>

<br/>

{% for rec in sparql %}

----

<br/>

## {{ rec.name }}

{% include_relative iframe.md rec=rec %}

<br/>

[Contents ↑](#contents)

<br/>

{% endfor %}
