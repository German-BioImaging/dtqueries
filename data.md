---
title: Data Resources
datatable: true
---

{% assign back = "tuberculosis" %}
{% assign next = "index" %}
{% include_relative navigation.md %}

There is, however, a large amount of <i>unlinked</i> data available
on the web. Here we have investigated two examples, [TCGA](#tcga)
and [sfaira](#sfaira)). Both are candidates for linking to other
resources to make a single, queryable platform.

## Contents:

<ol>
  <li><a href="#tcga">TCGA</a></li>
  <li><a href="#sfaira">sfaira</a></li>
</ol>

<br/>

----

<br/>

## TCGA

The following cases from https://portal.gdc.cancer.gov/ have been identified
as TNBC by downloading the `nationwidechildrens.org_clinical_patient_brca.txt` file
associated with the data and checking for a value of `Negative` in the
'er_status_by_ihc', 'pr_status_by_ihc', and 'her2_status_by_ihc' columns. (See
https://www.biostars.org/p/279048/ for details)

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

----

<br/>

## sfaira

sfaira ties together single-cell data for over 170 datasets for numerous tissues
types in both human and mouse. Downloading and loading the datasets can take
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

Each column in the table displays how many cells of a given type were found in each dataset:
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


### TCGA Patient Table

This notebook creates RDF with relevant ontologies found through EBI-OLS:
https://www.ebi.ac.uk/ols/index. The semantic model is a reflection of the
personal interpretation of Andra Waagmeester who is no expert on the data. The
generated linked data should be treated as such, exemplary data of a possible
semantic model. This model and the (arbitrary) choices for the selected
ontological terms need to be reviewed or redesigned by a field expert. 

https://portal.gdc.cancer.gov/files/8162d394-8b64-4da2-9f5b-d164c54b9608


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
      <th></th>
      <th>bcr_patient_uuid</th>
      <th>bcr_patient_barcode</th>
      <th>form_completion_date</th>
      <th>prospective_collection</th>
      <th>retrospective_collection</th>
      <th>birth_days_to</th>
      <th>gender</th>
      <th>menopause_status</th>
      <th>race</th>
      <th>ethnicity</th>
      <th>history_other_malignancy</th>
      <th>history_neoadjuvant_treatment</th>
      <th>tumor_status</th>
      <th>vital_status</th>
      <th>last_contact_days_to</th>
      <th>death_days_to</th>
      <th>radiation_treatment_adjuvant</th>
      <th>pharmaceutical_tx_adjuvant</th>
      <th>histologic_diagnosis_other</th>
      <th>initial_pathologic_dx_year</th>
      <th>age_at_diagnosis</th>
      <th>method_initial_path_dx</th>
      <th>method_initial_path_dx_other</th>
      <th>surgical_procedure_first</th>
      <th>first_surgical_procedure_other</th>
      <th>margin_status</th>
      <th>surgery_for_positive_margins</th>
      <th>surgery_for_positive_margins_other</th>
      <th>margin_status_reexcision</th>
      <th>axillary_staging_method</th>
      <th>axillary_staging_method_other</th>
      <th>micromet_detection_by_ihc</th>
      <th>lymph_nodes_examined</th>
      <th>lymph_nodes_examined_count</th>
      <th>lymph_nodes_examined_he_count</th>
      <th>lymph_nodes_examined_ihc_count</th>
      <th>ajcc_staging_edition</th>
      <th>ajcc_tumor_pathologic_pt</th>
      <th>ajcc_nodes_pathologic_pn</th>
      <th>ajcc_metastasis_pathologic_pm</th>
      <th>...</th>
      <th>nte_er_positivity_define_method</th>
      <th>nte_pr_status_by_ihc</th>
      <th>nte_pr_status_ihc__positive</th>
      <th>nte_pr_ihc_intensity_score</th>
      <th>nte_pr_positivity_other_scale</th>
      <th>nte_pr_positivity_define_method</th>
      <th>nte_her2_status</th>
      <th>nte_her2_status_ihc__positive</th>
      <th>nte_her2_positivity_ihc_score</th>
      <th>nte_her2_positivity_other_scale</th>
      <th>nte_her2_positivity_method</th>
      <th>nte_her2_fish_status</th>
      <th>nte_her2_signal_number</th>
      <th>nte_cent_17_signal_number</th>
      <th>her2_cent17_counted_cells_count</th>
      <th>nte_cent_17_her2_ratio</th>
      <th>nte_cent17_her2_other_scale</th>
      <th>nte_her2_fish_define_method</th>
      <th>anatomic_neoplasm_subdivision</th>
      <th>clinical_M</th>
      <th>clinical_N</th>
      <th>clinical_T</th>
      <th>clinical_stage</th>
      <th>days_to_initial_pathologic_diagnosis</th>
      <th>days_to_patient_progression_free</th>
      <th>days_to_tumor_progression</th>
      <th>disease_code</th>
      <th>extranodal_involvement</th>
      <th>histological_type</th>
      <th>icd_10</th>
      <th>icd_o_3_histology</th>
      <th>icd_o_3_site</th>
      <th>informed_consent_verified</th>
      <th>metastatic_tumor_indicator</th>
      <th>patient_id</th>
      <th>project_code</th>
      <th>site_of_primary_tumor_other</th>
      <th>stage_other</th>
      <th>tissue_source_site</th>
      <th>tumor_tissue_site</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6E7D5EC6-A469-467C-B748-237353C23416</td>
      <td>TCGA-3C-AAAU</td>
      <td>2014-1-13</td>
      <td>NO</td>
      <td>YES</td>
      <td>-20211</td>
      <td>FEMALE</td>
      <td>Pre (&lt;6 months since LMP AND no prior bilatera...</td>
      <td>WHITE</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>WITH TUMOR</td>
      <td>Alive</td>
      <td>3767</td>
      <td>[Not Applicable]</td>
      <td>NO</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2004</td>
      <td>55</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Modified Radical Mastectomy</td>
      <td>[Not Available]</td>
      <td>Negative</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Sentinel lymph node biopsy plus axillary disse...</td>
      <td>[Not Available]</td>
      <td>YES</td>
      <td>YES</td>
      <td>13</td>
      <td>4</td>
      <td>[Not Available]</td>
      <td>6th</td>
      <td>TX</td>
      <td>NX</td>
      <td>MX</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Left Lower Outer Quadrant</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Lobular Carcinoma</td>
      <td>C50.9</td>
      <td>8520/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>AAAU</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>3C</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>1</th>
      <td>55262FCB-1B01-4480-B322-36570430C917</td>
      <td>TCGA-3C-AALI</td>
      <td>2014-7-28</td>
      <td>NO</td>
      <td>YES</td>
      <td>-18538</td>
      <td>FEMALE</td>
      <td>Post (prior bilateral ovariectomy OR &gt;12 mo si...</td>
      <td>BLACK OR AFRICAN AMERICAN</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>3801</td>
      <td>[Not Applicable]</td>
      <td>YES</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2003</td>
      <td>50</td>
      <td>Core needle biopsy</td>
      <td>[Not Applicable]</td>
      <td>Lumpectomy</td>
      <td>[Not Available]</td>
      <td>Negative</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Sentinel lymph node biopsy plus axillary disse...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>YES</td>
      <td>15</td>
      <td>1</td>
      <td>[Not Available]</td>
      <td>6th</td>
      <td>T2</td>
      <td>N1a</td>
      <td>M0</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Right Upper Outer Quadrant</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Ductal Carcinoma</td>
      <td>C50.9</td>
      <td>8500/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>AALI</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>3C</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>2</th>
      <td>427D0648-3F77-4FFC-B52C-89855426D647</td>
      <td>TCGA-3C-AALJ</td>
      <td>2014-7-28</td>
      <td>NO</td>
      <td>YES</td>
      <td>-22848</td>
      <td>FEMALE</td>
      <td>Post (prior bilateral ovariectomy OR &gt;12 mo si...</td>
      <td>BLACK OR AFRICAN AMERICAN</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>1228</td>
      <td>[Not Applicable]</td>
      <td>NO</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2011</td>
      <td>62</td>
      <td>Core needle biopsy</td>
      <td>[Not Applicable]</td>
      <td>Modified Radical Mastectomy</td>
      <td>[Not Available]</td>
      <td>Negative</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>YES</td>
      <td>23</td>
      <td>1</td>
      <td>[Not Available]</td>
      <td>7th</td>
      <td>T2</td>
      <td>N1a</td>
      <td>M0</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Right</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Ductal Carcinoma</td>
      <td>C50.9</td>
      <td>8500/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>AALJ</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>3C</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C31900A4-5DCD-4022-97AC-638E86E889E4</td>
      <td>TCGA-3C-AALK</td>
      <td>2014-7-28</td>
      <td>NO</td>
      <td>YES</td>
      <td>-19074</td>
      <td>FEMALE</td>
      <td>[Unknown]</td>
      <td>BLACK OR AFRICAN AMERICAN</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>1217</td>
      <td>[Not Applicable]</td>
      <td>[Unknown]</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2011</td>
      <td>52</td>
      <td>Core needle biopsy</td>
      <td>[Not Applicable]</td>
      <td>Simple Mastectomy</td>
      <td>[Not Available]</td>
      <td>Close</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Sentinel node biopsy alone</td>
      <td>[Not Available]</td>
      <td>YES</td>
      <td>YES</td>
      <td>2</td>
      <td>0</td>
      <td>1</td>
      <td>7th</td>
      <td>T1c</td>
      <td>N0 (i+)</td>
      <td>M0</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Right</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Ductal Carcinoma</td>
      <td>C50.9</td>
      <td>8500/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>AALK</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>3C</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6623FC5E-00BE-4476-967A-CBD55F676EA6</td>
      <td>TCGA-4H-AAAK</td>
      <td>2014-11-13</td>
      <td>YES</td>
      <td>NO</td>
      <td>-18371</td>
      <td>FEMALE</td>
      <td>Post (prior bilateral ovariectomy OR &gt;12 mo si...</td>
      <td>WHITE</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>158</td>
      <td>[Not Applicable]</td>
      <td>NO</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2013</td>
      <td>50</td>
      <td>Core needle biopsy</td>
      <td>[Not Applicable]</td>
      <td>Modified Radical Mastectomy</td>
      <td>[Not Available]</td>
      <td>Negative</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Axillary lymph node dissection alone</td>
      <td>[Not Available]</td>
      <td>NO</td>
      <td>YES</td>
      <td>14</td>
      <td>4</td>
      <td>[Not Available]</td>
      <td>7th</td>
      <td>T2</td>
      <td>N2a</td>
      <td>M0</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Left|Left Upper Outer Quadrant</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Lobular Carcinoma</td>
      <td>C50.9</td>
      <td>8520/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>AAAK</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>4H</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1092</th>
      <td>5CD79093-1571-4F71-8136-0D84CCABDCAC</td>
      <td>TCGA-WT-AB44</td>
      <td>2014-7-16</td>
      <td>NO</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>FEMALE</td>
      <td>Post (prior bilateral ovariectomy OR &gt;12 mo si...</td>
      <td>WHITE</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>791</td>
      <td>[Not Applicable]</td>
      <td>YES</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2012</td>
      <td>77</td>
      <td>Core needle biopsy</td>
      <td>[Not Applicable]</td>
      <td>Lumpectomy</td>
      <td>[Not Available]</td>
      <td>Negative</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>No axillary staging</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>YES</td>
      <td>4</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>7th</td>
      <td>T1c</td>
      <td>N0 (i-)</td>
      <td>MX</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Left</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Lobular Carcinoma</td>
      <td>C50.9</td>
      <td>8520/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>AB44</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>WT</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>1093</th>
      <td>F89588E9-CA73-4465-A7FB-7246EDB45E3A</td>
      <td>TCGA-XX-A899</td>
      <td>2014-2-21</td>
      <td>NO</td>
      <td>YES</td>
      <td>-17022</td>
      <td>FEMALE</td>
      <td>Post (prior bilateral ovariectomy OR &gt;12 mo si...</td>
      <td>WHITE</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>292</td>
      <td>[Not Applicable]</td>
      <td>YES</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2013</td>
      <td>46</td>
      <td>Core needle biopsy</td>
      <td>[Not Applicable]</td>
      <td>Modified Radical Mastectomy</td>
      <td>[Not Available]</td>
      <td>Negative</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Sentinel lymph node biopsy plus axillary disse...</td>
      <td>[Not Available]</td>
      <td>NO</td>
      <td>YES</td>
      <td>22</td>
      <td>5</td>
      <td>0</td>
      <td>7th</td>
      <td>T1c</td>
      <td>N2a</td>
      <td>MX</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Right Lower Outer Quadrant</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Lobular Carcinoma</td>
      <td>C50.9</td>
      <td>8520/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>A899</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>XX</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>1094</th>
      <td>CA20249F-B7EA-4FD9-9ECB-34F74755AE35</td>
      <td>TCGA-XX-A89A</td>
      <td>2014-2-21</td>
      <td>NO</td>
      <td>YES</td>
      <td>-25000</td>
      <td>FEMALE</td>
      <td>Post (prior bilateral ovariectomy OR &gt;12 mo si...</td>
      <td>WHITE</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>278</td>
      <td>[Not Applicable]</td>
      <td>YES</td>
      <td>NO</td>
      <td>[Not Applicable]</td>
      <td>2013</td>
      <td>68</td>
      <td>Core needle biopsy</td>
      <td>[Not Applicable]</td>
      <td>Simple Mastectomy</td>
      <td>[Not Available]</td>
      <td>Negative</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>YES</td>
      <td>11</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>7th</td>
      <td>T3</td>
      <td>N0</td>
      <td>MX</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Left Upper Outer Quadrant</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Lobular Carcinoma</td>
      <td>C50.9</td>
      <td>8520/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>A89A</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>XX</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>1095</th>
      <td>23F438BD-1DBB-4D46-972F-1E8E74DDBD37</td>
      <td>TCGA-Z7-A8R5</td>
      <td>2014-7-9</td>
      <td>NO</td>
      <td>YES</td>
      <td>-22280</td>
      <td>FEMALE</td>
      <td>Post (prior bilateral ovariectomy OR &gt;12 mo si...</td>
      <td>WHITE</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>Yes</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>3042</td>
      <td>[Not Applicable]</td>
      <td>NO</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2005</td>
      <td>61</td>
      <td>Core needle biopsy</td>
      <td>[Not Applicable]</td>
      <td>Other</td>
      <td>Segmental Mastectomy</td>
      <td>Positive</td>
      <td>[Unknown]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Sentinel lymph node biopsy plus axillary disse...</td>
      <td>[Not Available]</td>
      <td>YES</td>
      <td>YES</td>
      <td>5</td>
      <td>3</td>
      <td>3</td>
      <td>6th</td>
      <td>T3</td>
      <td>N1a</td>
      <td>MX</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Left Upper Outer Quadrant</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Lobular Carcinoma</td>
      <td>C50.9</td>
      <td>8520/3</td>
      <td>C50.9</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>A8R5</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Z7</td>
      <td>Breast</td>
    </tr>
    <tr>
      <th>1096</th>
      <td>B1D44C81-747D-471F-9093-AEB262A17975</td>
      <td>TCGA-Z7-A8R6</td>
      <td>2014-7-9</td>
      <td>NO</td>
      <td>YES</td>
      <td>-16955</td>
      <td>FEMALE</td>
      <td>Pre (&lt;6 months since LMP AND no prior bilatera...</td>
      <td>WHITE</td>
      <td>NOT HISPANIC OR LATINO</td>
      <td>No</td>
      <td>No</td>
      <td>TUMOR FREE</td>
      <td>Alive</td>
      <td>2800</td>
      <td>[Not Applicable]</td>
      <td>NO</td>
      <td>YES</td>
      <td>[Not Applicable]</td>
      <td>2005</td>
      <td>46</td>
      <td>Tumor resection</td>
      <td>[Not Applicable]</td>
      <td>Lumpectomy</td>
      <td>[Not Available]</td>
      <td>Negative</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Sentinel lymph node biopsy plus axillary disse...</td>
      <td>[Not Available]</td>
      <td>YES</td>
      <td>YES</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>6th</td>
      <td>T1c</td>
      <td>N0</td>
      <td>M0</td>
      <td>...</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>Left Upper Outer Quadrant</td>
      <td>[Not Applicable]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>0</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>Infiltrating Lobular Carcinoma</td>
      <td>C50.8</td>
      <td>8022/3</td>
      <td>C50.8</td>
      <td>YES</td>
      <td>[Not Available]</td>
      <td>A8R6</td>
      <td>[Not Available]</td>
      <td>[Not Applicable]</td>
      <td>[Not Available]</td>
      <td>Z7</td>
      <td>Breast</td>
    </tr>
  </tbody>
</table>
<p>1097 rows × 112 columns</p>
</div>


Looking a bit closer:
 * the values for `margin_status` are: 'Close', 'Negative', 'Positive', '[Not Available]', '[Unknown]'.
 * `bcr_patient_uuid` can be mapped to https://schema.org/Patient


```
    if (row["gender"] == "FEMALE"):
        kg.add((patientURI, schema.gender, schema.Female))
        kg.add((patientURI, schema.gender, wikidata.Q6581072))
    elif(row["gender"] == "MALE"):
        kg.add((patientURI, schema.gender, schema.Female))
        kg.add((patientURI, schema.gender, wikidata.Q6581097))
        
    # diagnosis
    diagnosis = BNode()
    kg.add((patientURI, obo.RO_0016002, diagnosis))
    kg.add((diagnosis, RDF.type, obo.NCIT_C71732))
    kg.add((obo.NCIT_C71732, RDFS.label, Literal("triple-negative breast cancer", lang="en")))
    kg.add((obo.NCIT_C71732, SKOS.exactMatch, wikidata.Q7843332))
    
    # TCGA BAR code
    kg.add((diagnosis, DCTERMS.identifier, Literal(row["bcr_patient_barcode"],datatype=XSD.string)))
    kg.add((diagnosis, DC.identifier, tcga[row["bcr_patient_barcode"]]))
    
    # age at diagnosis
    age_at_diagnosis = BNode()
    kg.add((diagnosis, sio.SIO_000008 ,age_at_diagnosis ))
    #kg.parse(sio.SIO_000008)
    kg.add((age_at_diagnosis, RDF.value, Literal(row["age_at_diagnosis"], datatype=XSD.integer)))
    kg.add((age_at_diagnosis, RDF.type, obo.NCIT_C156420))
    kg.add((obo.NCIT_C156420, RDFS.label, Literal("Age at Diagnosis", lang="en")))
    # year of diagnosis
    year_of_diagnosis = BNode()
    kg.add((diagnosis, sio.SIO_000008, year_of_diagnosis))
    kg.add((year_of_diagnosis, RDF.value, Literal(row["initial_pathologic_dx_year"], datatype=XSD.gYear)))
    kg.add((year_of_diagnosis, RDF.type, obo.NCIT_C168823))
    kg.add((year_of_diagnosis, RDFS.label, Literal("Year of Diagnosis", lang="en")))
    
    # first surgical procedure
    first_surgical_procedure = BNode()
    if row["surgical_procedure_first"] == "Lumpectomy":
        kg.add((first_surgical_procedure, RDF.type, snomed["392021009"]))
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
    if row["surgical_procedure_first"] == "Modified Radical Mastectomy":
        kg.add((first_surgical_procedure, RDF.type, obo.NCIT_C15278))
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
    if row["surgical_procedure_first"] == "Modified Radical Mastectomy":
        kg.add((first_surgical_procedure, RDF.type, snomed["172043006"]))
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
        
    # method_initial_path_dx
    ## Using the same model as above
    ### {'Core needle biopsy',
    ### 'Cytology (e.g. Peritoneal or pleural fluid)',
    ###'Excisional Biopsy',
    ###'Fine needle aspiration biopsy',
    ###'Incisional Biopsy',
    ###'Other method, specify:',
    ###'Tumor resection',
    ###'[Discrepancy]',
    ### '[Not Available]'}
    if row["method_initial_path_dx"] == "Core needle biopsy":
        kg.add((first_surgical_procedure, RDF.type, snomed["9911007"])) ## Snomed has exact label
        kg.add((first_surgical_procedure, RDF.type, obo.NCIT_C15680)) ## NCIT lacks "Needle", but definition aligns
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx"] == "Cytology":
        kg.add((first_surgical_procedure, RDF.type, obo.NCIT_C16491)) 
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx"] == "Excisional Biopsy":
        kg.add((first_surgical_procedure, RDF.type, obo.NCIT_C15385)) 
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx"] == "Fine needle biopsy":
        kg.add((first_surgical_procedure, RDF.type, snomed["48635004"])) ## Snomed has exact label
        kg.add((first_surgical_procedure, RDF.type, obo.NCIT_C15361)) ## Fine needle aspiration
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx"] == "Incisional Biopsy":
        kg.add((first_surgical_procedure, RDF.type, obo.NCIT_C15386)) 
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx"] == "Tumor resection":
        kg.add((first_surgical_procedure, RDF.type, obo.NCIT_C164212)) 
        kg.add((first_surgical_procedure, obo.NCIT_R180, diagnosis))
     
    # method_initial_path_dx_other
    ## Using the same model as above
    ###{'Biopsy not specified',
    ###'Biopsy, NOS',
    ###'Lumpectomy',
    ###'Modified Radical Masectomy',
    ###"Patey's Suregery",
    ###"Patey's Surgery",
    ###'SKIN BIOPSY',
    ###'Skin biopsy',
    ###'Ultrasound-guided biopsy',
    ###'Ultrasound-guided mammotome biopsy',
    ###'Wide local incision',
    ###'[Not Applicable]',
    ###'[Not Available]',
    ###'[Unknown]',
    ###'biopsy, NOS',
    ###'intraoperative examination',
    ###'stereotactic biopsy'}
    method_initial_path_dx_other = BNode()
    if row["method_initial_path_dx_other"] in  ["Biopsy not specified", 'Biopsy, NOS', 'biopsy, NOS'] :
        kg.add((method_initial_path_dx_other, RDF.type, obo.NCIT_C15189)) 
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx_other"] == "Lumpectomy": 
        kg.add((method_initial_path_dx_other, RDF.type, obo.NCIT_C15755)) 
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx_other"] == "Modified Radical Masectomy": 
        kg.add((method_initial_path_dx_other, RDF.type, obo.NCIT_C15278)) 
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx_other"] in  ["Patey's Suregery", "Patey's Surgery"] :
        kg.add((method_initial_path_dx_other, RDF.type, snomed["395702000"])) 
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx_other"] in  ["SKIN BIOPSY", "Skin biopsy"] :
        kg.add((method_initial_path_dx_other, RDF.type, obo.NCIT_C51692)) 
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx_other"] in  ["Ultrasound-guided biopsy", "Ultrasound-guided mammotome biopsy"] :
        kg.add((method_initial_path_dx_other, RDF.type, obo.NCIT_C93022)) 
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx_other"] == "Wide local incision": 
        kg.add((method_initial_path_dx_other, RDF.type, obo.NCIT_C94441)) ## NCIT does not contain WLincision, but WLexision
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx_other"] == "intraoperative examination": 
        kg.add((method_initial_path_dx_other, RDF.type, snomed["73443006"])) ## snomed: Intraoperative state (finding)
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis))
    if row["method_initial_path_dx_other"] == "stereotactic biopsy": 
        kg.add((method_initial_path_dx_other, RDF.type, obo.NCIT_C51654)) ## snomed: Intraoperative state (finding)
        kg.add((method_initial_path_dx_other, obo.NCIT_R180, diagnosis)) 
    
```

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
