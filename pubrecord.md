---
title: Publication records
---

{% assign back = "intro" %}
{% assign next = "tnbc" %}
{% include_relative navigation.md %}

Projects like
[Pubmed](https://pubmed.ncbi.nlm.nih.gov/),
[Crossref](https://crossref.org),
and [WikiCite](http://wikicite.org/) have created a wealth
of publicly linked citation data that serves as an ideal
example of linked data. Below we have investigated which
entries currently exist for the Performers participating
in ΔTissue. A useful first experiment with creating linked
data is to verify your own publication records, creating
an entry if necessary.

{% assign sparql = site.data.pubrecord %}
{% include_relative sparql.md %}

{% include_relative navigation.md %}
