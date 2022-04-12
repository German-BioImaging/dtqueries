---
title: Data Resources
---

## TCGA

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
                {{gene["symbol"]}} {% unless forloop.last %},{% endunless %}
                {% endfor %}
            </td>
            <td>
                {% if rec.slides %}
                <a href="https://portal.gdc.cancer.gov/repository?filters=%7B%22content%22%3A%5B%7B%22content%22%3A%7B%22field%22%3A%22cases.case_id%22%2C%22value%22%3A%5B%22{{rec.case}}%22%5D%7D%2C%22op%22%3A%22in%22%7D%2C%7B%22content%22%3A%7B%22field%22%3A%22files.experimental_strategy%22%2C%22value%22%3A%5B%22Tissue%20Slide%22%5D%7D%2C%22op%22%3A%22in%22%7D%5D%2C%22op%22%3A%22and%22%7D&searchTableTab=files">
                    yes
                </a>
                {% else %}
                no
                {%endif %}
            </td>
        </tr>
{% endfor %}
    </tbody>
</table>
