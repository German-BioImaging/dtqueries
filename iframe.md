{{ rec.md }}

```sparql
{{ rec.rq }}
```

<iframe style="width: 100%; border: none; height: {{ rec.height | default: 30 }}vh"
        src="{{ rec.srv | default: 'https://query.wikidata.org' }}/embed.html#{{ rec.rq | uri_escape }}"
        referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups">
</iframe>

{{ rec.post }}
