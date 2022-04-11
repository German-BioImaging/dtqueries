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
  "copyrightYear": "2021",
  "discussionUrl": "https://github.com/German-BioImaging/dtqueries/issues"
}
</script>

# ΔTissue Demonstrator

© 2022 Andra Waagmeester and Josh Moore

License: [CC-BY-SA 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)

This demonstration is written in Markdown with additional instructions consisting of
[SPARQL queries](https://en.wikipedia.org/wiki/SPARQL) that are dynamically loaded from https://www.wikidata.org/.
Feedback can be sent via [this GitHub repository](https://github.com/German-BioImaging/dtqueries/).
While the website itself is licensed under CC-BY-SA, all SPARQL queries in this resource can be used
under the [CCZero license/waiver](https://creativecommons.org/share-your-work/public-domain/cc0/).

## Introduction

![topic cloud]({{{site.baseurl}}/images/cloud.png)

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
