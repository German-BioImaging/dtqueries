<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "Book",
  "inLanguage": "en-US",
  "name": "ΔTissue Demonstrator",
  "publisher": {
    "@type": "Organization",
    "name": "GitHub"
  },
  "copyrightYear": "2022",
  "discussionUrl": "https://github.com/German-BioImaging/dtqueries/issues"
}
</script>

# ΔTissue Demonstrator (v0.0.1)

© 2022 Andra Waagmeester and Josh Moore

License: [<img src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-sa.png" width=200>](https://creativecommons.org/licenses/by-sa/4.0/)

## Introduction

![topic cloud]({{{site.baseurl}}/images/cloud.png)
This is the first release of the ΔTissue Demonstrator. The demonstrator intends to provide a way to explore a linke-data.
Linked data is core to FAIR data sharing and is a key component of the FAIR data model. In this release
we will use Wikidata as a central hub for linked data related to the ΔTissue disease areas (TB, TBNC, GBM). Currently, the coverage of Wikidata on the
ΔTissue disease areas appears to be incomplete. Relevant data either needs to be added or the existing data needs to be updated.

For the purpose of this demonstrator two workflows have been developed:
1. One to complete publication records for a list of authors and publications.
2. One to make biological pathways published in the scientific literature machine readable.

Currently, the demonstrator is a POC to explore linked data on the ΔTissue disease areas in Wikidata only.
Wikidata follows applies a CC0 license. Many resources do not. To be able to render a full picture of the linked data cloud related to the disease areas,
we need to either add more public data or include a linked-data cloud that hosts non-CC0 data.

The queries in this repository were written by authors who are not domain experts in the disease areas.

Suggestions for different queries on the diease areas are welcome. Please this [form](https://github.com/German-BioImaging/dtqueries/issues/new) 


This site demonstrates the available, public linked data related to the
Wellcome Leap Delta Tissue (ΔT) program. The primary linking resource in
this demonstrator is [Wikidata](https://wikidata.org/).

Resources that are reachable via data links include:

* [Wikipathways](https://www.wikipathways.org/index.php/WikiPathways)
* [Reactome](https://reactome.org/)
* [Uniprot](https://www.uniprot.org/)
* [OpenCitations](https://opencitations.net/)
* [Cellosaurus](https://web.expasy.org/cellosaurus/)
* [NCBI gene](https://www.ncbi.nlm.nih.gov/gene)
* [Ensembl](http://www.ensembl.org/index.html)
* [Pubchem](https://pubchem.ncbi.nlm.nih.gov/)
* [cBioPortal](https://www.cbioportal.org/)

Other sites like [Scholia](https://scholia.toolforge.org/) provide enhanced
visualization of the existing data links.

## Contents

<ol>
  <li><a href="pubrecord.html">Publication Record</a>
    <ol>
{% for rec in site.data.pubrecord %}
   <li><a href="pubrecord.html#{{rec.name | slugify }}">{{ rec.name  }}</a></li>
{% endfor %}
    </ol>
  </li>
  <li><a href="tnbc.html">Triple-negative breast record</a>
    <ol>
{% for rec in site.data.tnbc %}
   <li><a href="tnbc.html#{{rec.name | slugify }}">{{ rec.name  }}</a></li>
{% endfor %}
    </ol>
  </li>
  <li><a href="glioblastoma.html">Glioblastoma</a>
    <ol>
{% for rec in site.data.glioblastoma%}
   <li><a href="glioblastoma.html#{{rec.name | slugify }}">{{ rec.name  }}</a></li>
{% endfor %}
    </ol>
  </li>
  <li><a href="tuberculosis.html">Tuberculosis</a>
    <ol>
{% for rec in site.data.tuberculosis %}
   <li><a href="tuberculosis.html#{{rec.name | slugify }}">{{ rec.name  }}</a></li>
{% endfor %}
    </ol>
  </li>
</ol>

This demonstration is written in Markdown with additional instructions consisting of
[SPARQL queries](https://en.wikipedia.org/wiki/SPARQL) that are dynamically loaded from https://www.wikidata.org/.
Feedback can be sent via [this GitHub repository](https://github.com/German-BioImaging/dtqueries/).
While the website itself is licensed under CC-BY-SA, all SPARQL queries in this resource can be used
under the [CCZero license/waiver](https://creativecommons.org/share-your-work/public-domain/cc0/).

