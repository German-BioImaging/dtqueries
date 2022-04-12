---
title: Data Resources
---

## TCGA

The following cases from https://portal.gdc.cancer.gov/ have been identified
as TNBC by downloading the `nationwidechildrens.org_clinical_patient_brca.txt` file
associated with the data and checking for a value of `Negative` in the
'er_status_by_ihc', 'pr_status_by_ihc', and 'her2_status_by_ihc' columns. (See
https://www.biostars.org/p/279048/ for details)

{% assign gdc = "https://portal.gdc.cancer.gov/cases "}
{% assign slides = "https://portal.gdc.cancer.gov/repository?filters=%7B%22content%22%3A%5B%7B%22content%22%3A%7B%22field%22%3A%22cases.case_id%22%2C%22value%22%5D%7D%2C%22op%22%3A%22in%22%7D%2C%7B%22content%22%3A%7B%22field%22%3A%22files.experimental_strategy%22%2C%22value%22%3A%5B%22Tissue%20Slide%22%5D%7D%2C%22op%22%3A%22in%22%7D%5D%2C%22op%22%3A%22and%22%7D&searchTableTab=files%22%3A%5B%22" %}

<div class="datatable-begin"></div>
TCGA Case | High-impact somatic mutations | Images available
--------- | ----------------------------- | ----------------
{%- for rec in site.data.tcga -%}
[{{rec.case}}]({{gdc}}/{{ rec.case }}) | {% for gene in rec.genes %}{{gene["symbol"]}} {% unless forloop.last %},{% endunless %}{% endfor %} | {% if rec.slides %}[yes]({{slides}}{{rec.case}}){%else %}no{% endif %}
{%- endfor -%}
</div class="datatable-end"></div>
