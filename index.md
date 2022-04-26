---
title: An Intro
title: "ΔTissue Demonstrator (v0.4)"
---
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

{% assign back = "data" %}
{% assign next = "intro" %}
{% include_relative navigation.md %}

[<img src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-sa.png" width="10%">](https://creativecommons.org/licenses/by-sa/4.0/)
© 2022 Andra Waagmeester and Josh Moore

This is the first release of the ΔTissue Demonstrator which provides starting points for the exploration of public, linked data.
Linked data is core to FAIR data sharing and is a key component of the FAIR data model. In this release
we use Wikidata as a central hub for linked data related to the ΔTissue disease areas (TB, TBNC, GBM).

Resources that are reachable via data links include:
[Wikipathways](https://www.wikipathways.org/index.php/WikiPathways),
[Reactome](https://reactome.org/),
[Uniprot](https://www.uniprot.org/),
[OpenCitations](https://opencitations.net/),
[Cellosaurus](https://web.expasy.org/cellosaurus/),
[NCBI gene](https://www.ncbi.nlm.nih.gov/gene),
[Ensembl](http://www.ensembl.org/index.html),
[Pubchem](https://pubchem.ncbi.nlm.nih.gov/),
[cBioPortal](https://www.cbioportal.org/).
Other resources, like [Genomic Data Commons Data Portal](https://portal.gdc.cancer.gov/)
or [sfaira portal](https://theislab.github.io/sfaira-portal/) provide access to large
quantities of data using the same (or compatible) identifiers but which are not
directly linkable. Finally, other sites like [Scholia](https://scholia.toolforge.org/)
provide enhanced visualization of the existing data links, like the image below
showing the topics of all ΔTissue authors who could be found in Wikidata.

<img src="{{site.baseurl}}/images/cloud.png" width="50%"/>

For the purpose of this demonstrator workflows have been developed:

1. to complete publication records for a list of authors and publications
2. to make biological pathways published in the scientific literature machine readable
3. to query GDC enties via GraphQL and download related tabular data
4. to download datasets listed on the sfaira portal and load them with the sfaira Python library

In some cases, entries have been created in Wikidata and elsewhere in order to establish initial links.
This, however, has not been done systematically without the input of the domain experts.

The demonstrator is a POC to explore existing linked data on the ΔTissue disease areas in Wikidata.
Currently, the coverage of Wikidata on the ΔTissue disease areas appears to be incomplete.
Relevant data either needs to be added systematically or the existing data needs to be updated, keeping in mind that
Wikidata follows applies a CC0 license. Many resources do not. To be able to render a full picture of
the linked data cloud related to the disease areas, either more public data must be added or a linked-data
resource that hosts non-CC0 data will be needed.

Please note that the queries in this repository were written by the authors who are not domain experts in the disease areas.
Suggestions for different queries on the disease areas are welcome using this [form](https://github.com/German-BioImaging/dtqueries/issues/new) 

## Contents

<ol>
  <li><a href="intro.html">An Introduction</a> (<b>NEW</b>)
    <ol>
      <li><a href="intro.html#what-is-linked-data">What is Linked Data?</a></li>
      <li><a href="intro.html#toy-example">Toy example</a></li>
      <li><a href="intro.html#initial-project">Initial project</a></li>
      <li><a href="intro.html#outlook">Outlook</a></li>
      <li><a href="intro.html#terminology">Terminology</a></li>
    </ol>
  </li>
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
  <li><a href="data.html">Data Resources</a>
    <ol>
     <li><a href="data.html#tcga">TCGA</a></li>
     <li><a href="data.html#sfaira">sfaira</a></li>
    </ol>
  </li>
</ol>

## Future work

Future editions of this demonstrator will include:
* Direct linked-data validation and enrichment using [Shape Expressions](https://shex.io)
* Federated querying of linked data where the data is hosted on multiple sources.
* Direct download of linked data from the sources.
* Example queries on a revived linked-tcga SPARQL endpoints. 

## Impressum

This demonstration is written in Markdown with additional instructions consisting of
[SPARQL queries](https://en.wikipedia.org/wiki/SPARQL) that are dynamically loaded from https://www.wikidata.org/.
While the website itself is licensed under CC-BY-SA, all SPARQL queries in this resource can be used
under the [CCZero license/waiver](https://creativecommons.org/share-your-work/public-domain/cc0/).
Feedback can be sent via [this GitHub repository](https://github.com/German-BioImaging/dtqueries/).

{% include_relative navigation.md %}
