---
title: Tuberculosis
---

## Contents:
{% for rec in site.data.tuberculosis %}
 - [{{ rec.name }}]({{ rec.name | slugify }})
{% endfor %}

{% for rec in site.data.tuberculosis %}
## {{ rec.name }}

```sparql
{{ rec.rq }}
```

<iframe style="width: 100%; height: 50vh; border: none;"
        src="https://query.wikidata.org/embed.html#{{ rec.rq | uri_escape }}"
        referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups">
</iframe>

{% endfor %}
