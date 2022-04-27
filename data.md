---
title: Data Resources
datatable: true
---

{% assign back = "tuberculosis" %}
{% assign next = "index" %}
{% include_relative navigation.md %}

There is, however, a large amount of <i>unlinked</i> data available
on the web. Here we have investigated two examples, [sfaira](#sfaira)
and [TCGA](#tcga). Both are candidates for linking to other
resources to make a single, queryable platform.

## Contents:

<ol>
  <li><a href="#sfaira">sfaira</a></li>
  <li><a href="#tcga">TCGA</a>
     <ol>
        <li><a href="#brca">All breast cancer records</a> (<b>NEW</b>)</li>
        <li><a href="#tnbc">Mutations and slides for TNBC cases</a></li>
     </ol>
  </li>
</ol>

<br/>

----

<br/>

## sfaira

sfaira ties together single-cell data consists of over 170 datasets for numerous tissues
types in both human and mouse. A [https://theislab.github.io/sfaira-portal/](website)
allows filtering the datasets and Python code is available for downloading and caching
the various binary resources that make up a dataset. Downloading and loading the datasets can take
significant time. Here metadata from the {{ site.data.sfaira.datasets | size }}
human brain datasets has been parsed using the `sfaira` python library:

```python
    ds = sfaira.data.Universe(data_path=datadir, meta_path=metadir, cache_path=cachedir)
    ds.subset(key="organism", values=["Homo sapiens"])
    ds.subset(key="organ", values=["brain"])
    ds.download()
    ds.load(verbose=1)
    ds.streamline_features(match_to_release="104", subset_genes_to_type="protein_coding")
    ds.streamline_metadata(schema="sfaira")
```

Each column in the table displays how many cells of a given type were found in each dataset.
This is just one example of the type of queryable feature that one might want to extract from
the datasets. In the table, the columns are represented by the following numbers for readability:
<ol>
{% for rec in site.data.sfaira["datasets"] %}
   <li>{{ rec.dataset }}</li>
{% endfor %}
</ol>

<br/>

<table class="display" id="sfaira_table">
    <thead>
        <tr>
        <th>cell type</th>
{% for rec in site.data.sfaira["datasets"] %}
        <th>{{ forloop.index }}</th>
{% endfor %}
        </tr>
    </thead>
    <tbody>
{% for rec in site.data.sfaira["cell_types"] %}
        <tr>
            <td>{{ rec.cell_type }}</td>
{% for dataset in rec.datasets %}
            <td>{{ dataset }}</td>
{% endfor %}
        </tr>
{% endfor %}
    </tbody>
</table>

[Contents ↑](#contents)

<br/>

----

<br/>

## TCGA

[The Cancer Genome Atlas Program (TCGA)](https://www.cancer.gov/about-nci/organization/ccg/research/structural-genomics/tcga)
data available from the [Genomic Data Commons Data Portal](https://portal.gdc.cancer.gov/)
poses a similar problem. Though there is a [GraphQL](https://graphql.org/)
API, not all metadata is accessible. For example, the table below is critical
for identifying TNBC cases from other forms of breast cancer.

### All breast cancer records {#brca}

This single TSV file
[`nationwidechildrens.org_clinical_patient_brca.txt`](https://portal.gdc.cancer.gov/files/8162d394-8b64-4da2-9f5b-d164c54b9608)
is attached to each of the over 1000 breast cancer cases in the GDC Portal but
it must be separately downloaded to properly interpret the data. (Perhaps even
more importantly, **the interpretations here are those of the authors and may
vary from those of domain experts!**)

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="display" id="nb1_table">
  <thead>
    <tr style="text-align: right;">
      {% for field in site.data.brca.schema.fields %}
      <th>{{ field.name }}</th>
      {% endfor %}
    </tr>
  </thead>
  <tbody>
    {% for rec in site.data.brca.data %}
    <tr>
      {% for field in site.data.brca.schema.fields %}
      <td>{{ rec[field.name] }}</td>
      {% endfor %}
    </tr>
    {% endfor %}
  </tbody>
</table>
</div>

Interpretation:

 * `bcr_patient_uuid` is the GDC unique identifier for this case and is likely
   best suited for constructing a unique identifier for this [patient](https://schema.org/Patient).

* `bcr_patient_barcode` is the TCGA-submitted identifier that is frequently
  used in file names, etc. associated with this patient.

* 'er_status_by_ihc', 'pr_status_by_ihc', and 'her2_status_by_ihc' columns (or
  "breast_carcinoma_estrogen_receptor_status",
  "breast_carcinoma_progesterone_receptor_status", and
  "lab_proc_her2_neu_immunohistochemistry_receptor_status" respectively) take
  the values: `Equivocal`, `Indeterminate`, `Negative`, `Positive`,
  `[Not Available]`, and `[Not Evaluated]`. Below we've taken those entries
  with three `Negative` values to be TNBC.
  (See <https://www.biostars.org/p/279048/> for details)

* `surgical_procedure_first` with values like "Lumpectomy" and "Modified Radical Mastectomy"
  can be mapped to SNOMED 392021009 and 172043006.

* `method_initial_path_dx` values, however, can only partially be mapped to SNOMED.
   'Core needle biopsy' is 9911007 and 'Fine needle aspiration biopsy' is 48635004
   but others are less clear:
   - 'Cytology (e.g. Peritoneal or pleural fluid)'
   - 'Excisional Biopsy'
   - 'Incisional Biopsy'
   - 'Other method, specify:'
   - 'Tumor resection'
   - '[Discrepancy]'
   - '[Not Available]'

* `method_initial_path_dx_other` values have similar issues plus misspellings
   ("Patey's Suregery" vs. -"Patey's Surgery") as well as differences in
   capitalization ('SKIN BIOPSY' vs. 'Skin biopsy').

### Mutations and slides for TNBC cases {#tnbc}

Once the above table has been used to identify the {{ site.data.tcga | size }}
TNBC cases, then the GraphQL API can be used to check for other data features,
e.g., whether or not a high-impact somatic mutation was associated with the
case or if there are images of tissue slides are available:

<table class="display" id="tcga_table">
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

<br/>

[Contents ↑](#contents)

{% include_relative navigation.md %}

<script>
$(document).ready( function () {
    $('#tcga_table').DataTable();
} );
$(document).ready( function () {
    $('#sfaira_table').DataTable();
} );
$(document).ready( function () {
    $('#nb1_table').DataTable( {
          "scrollX": true
    });
} );
</script>
