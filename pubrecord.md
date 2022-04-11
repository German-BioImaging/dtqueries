---
toc: true
classes:
 - wide
---
# Publication Records

{% for rec in site.data.pubrecord %}
## {{ rec.name }}

```sparql
{{ rec.rq }}
```

<iframe style="width: 80vw; height: 50vh; border: none;"
        src="https://query.wikidata.org/embed.html#{{ rec.rq | uri_escape }}"
        referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups">
</iframe>

{% endfor %}
