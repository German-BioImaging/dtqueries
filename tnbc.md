---
title: TNBC
---

{% assign back = "pubrecord" %}
{% assign next = "glioblastoma" %}
{% include_relative navigation.md %}

The first program disease area (PDA) that we were tasked
to investigation was TNBC. Unfortunately, it turned out
that the current public linked data was not particularly
rich.

{% assign sparql = site.data.tnbc %}
{% include_relative sparql.md %}

{% include_relative navigation.md %}
