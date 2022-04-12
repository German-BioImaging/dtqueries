---
title: Triple-negative breast cancer
---

{% assign sparql = site.data.tnbc %}
{% include_relative sparql.md %}

## TCGA Cases:

The following cases from https://portal.gdc.cancer.gov/ have been identified
as TNBC by downloading the `nationwidechildrens.org_clinical_patient_brca.txt` file
associated with the data and checking for a value of `Negative` in the
'er_status_by_ihc', 'pr_status_by_ihc', and 'her2_status_by_ihc' columns. (See
https://www.biostars.org/p/279048/ for details)



<table>
    <thead>
        <tr>
        <th>TCGA Case</th>
        <th>High-impact somatic mutations</th>
        <th>Images available</th>
        </tr>
    </thead>
    <tbody>
{% for rec in site.data.tcga %}
        <tr>
            <td><a href="https://portal.gdc.cancer.gov/cases/{{ rec.case }}">{{rec.case}}</a></td>
            <td>{% for gene in rec.genes%}
                {{gene}} {% unless forloop.last %},{% endunless %}
                {% endfor %}
            </td>
            <td>rec.slides</td>
        </tr>
{% endfor %}
    </tbody>
</table>
