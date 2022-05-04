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
© 2022 [Andra Waagmeester](https://scholia.toolforge.org/author/Q19845625) and [Josh Moore](https://scholia.toolforge.org/author/Q56512375).

This is the first release of the ΔTissue Demonstrator which provides starting points for the exploration of public, linked data.
Linked data is core to FAIR data sharing and is a key component of the FAIR data model. In this release
we use Wikidata as a central hub for linked data related to the ΔTissue disease areas (TB, TBNC, GBM).

Resources that are reachable via data links include:
[Wikipathways](https://www.wikipathways.org/index.php/WikiPathways) [[1]](#1),
[Reactome](https://reactome.org/) [[2]](#2),
[Uniprot](https://www.uniprot.org/) [[3]](#3) ,
[OpenCitations](https://opencitations.net/) [[4]](#4),
[Cellosaurus](https://web.expasy.org/cellosaurus/) [[5]](#5),
[NCBI gene](https://www.ncbi.nlm.nih.gov/gene) [[6]](#6),
[Ensembl](http://www.ensembl.org/index.html) [[7]](#7),
[Pubchem](https://pubchem.ncbi.nlm.nih.gov/) [[8]](#8),
[cBioPortal](https://www.cbioportal.org/) [[9]](#9).
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
     <li><a href="data.html#sfaira">sfaira</a></li>
     <li><a href="data.html#tcga">TCGA</a>
       <ol>
          <li><a href="data.html#brca">All breast cancer records</a> (<b>NEW</b>)</li>
          <li><a href="data.html#tnbc">Mutations and slides for TNBC cases</a></li>
       </ol>
     </li>
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

## References
<a id="1">[1]</a> Pico AR, Kelder T, van Iersel MP, Hanspers K, Conklin BR, Evelo C. (2008) WikiPathways: Pathway Editing for the People. PLoS Biol 6(7) https://doi.org/10.1371%2FJOURNAL.PBIO.0060184 [Scholia (wikidata)](https://scholia.toolforge.org/work/Q21092742)

<a id="2">[2]</a> Marc Gillespie, Bijay Jassal, Ralf Stephan, Marija Milacic, Karen Rothfels, Andrea Senff-Ribeiro, Johannes Griss, Cristoffer Sevilla, Lisa Matthews, Chuqiao Gong, Chuan Deng, Thawfeek Varusai, Eliot Ragueneau, Yusra Haider, Bruce May, Veronica Shamovsky, Joel Weiser, Timothy Brunson, Nasim Sanati, Liam Beckman, Xiang Shao, Antonio Fabregat, Konstantinos Sidiropoulos, Julieth Murillo, Guilherme Viteri, Justin Cook, Solomon Shorser, Gary Bader, Emek Demir, Chris Sander, Robin Haw, Guanming Wu, Lincoln Stein, Henning Hermjakob, Peter D’Eustachio, The reactome pathway knowledgebase 2022, Nucleic Acids Research, Volume 50, Issue D1, 7 January 2022, Pages D687–D692, https://doi.org/10.1093/nar/gkab1028
[Scholia (wikidata)](https://scholia.toolforge.org/work/Q111440803)

<a id="3">[3]</a> UniProt: the universal protein knowledgebase in 2021 Nucleic Acids Res. 49:D1 (2021) https://doi.org/10.1093%2FNAR%2FGKAA1100 [Scholia (wikidata)](https://scholia.toolforge.org/work/Q102383737)

<a id="4">[4]</a> Silvio Peroni, David Shotton (2020). OpenCitations, an infrastructure organization for open scholarship. Quantitative Science Studies, 1(1): 428-444. https://doi.org/10.1162/qss_a_00023 [Scholia (wikidata)](https://scholia.toolforge.org/work/Q86246929) 


<a id="5">[5]</a> The Cellosaurus, a cell line knowledge resource. J. Biomol. Tech. 29:25-38(2018) https://doi.org/10.7171/jbt.18-2902-002 [Scholia (wikidata)](https://scholia.toolforge.org/work/Q54370168) 

<a id="6">[6]</a> Agarwala RBarrett TBeck JBenson DABollin CBolton EBourexis DBrister JRBryant SHCanese KCavanaugh MCharowhas CClark KDondoshansky IFeolo MFitzpatrick LFunk KGeer LYGorelenkov VGraeff AHlavina WHolmes BJohnson MKattman BKhotomlianski VKimchi AKimelman MKimura MKitts PKlimke WKotliarov AKrasnov SKuznetsov ALandrum MJLandsman DLathrop SLee JMLeubsdorf CLu ZMadden TLMarchler-Bauer AMalheiro AMeric PKarsch-Mizrachi IMnev AMurphy TOrris ROstell JO'Sullivan CPalanigobu VPanchenko ARPhan LPierov BPruitt KDRodarmer KSayers EWSchneider VSchoch CLSchuler GDSherry STSiyan KSoboleva ASoussov VStarchenko GTatusova TAThibaud-Nissen FTodorov KTrawick BWVakatov DWard MYaschenko EZasypkin AZbicz KCoordinators NRNCBI Resource Coordinators (2018) Database resources of the National Center for Biotechnology Information Nucleic Acids Research 46:D8–D13. https://doi.org/10.1093/nar/gkx1095

<a id="7">[7]</a> Zerbino DRAchuthan PAkanni WAmode MRBarrell DBhai JBillis KCummins CGall AGirón CGGil LGordon LHaggerty LHaskell EHourlier TIzuogu OGJanacek SHJuettemann TTo JKLaird MRLavidas ILiu ZLoveland JEMaurel TMcLaren WMoore BMudge JMurphy DNNewman VNuhn MOgeh DOng CKParker APatricio MRiat HSSchuilenburg HSheppard DSparrow HTaylor KThormann AVullo AWalts BZadissa AFrankish AHunt SEKostadima MLangridge NMartin FJMuffato MPerry ERuffier MStaines DMTrevanion SJAken BLCunningham FYates AFlicek P (2018) Ensembl 2018 Nucleic Acids Research 46:D754–D761. https://doi.org/10.1093/nar/gkx1098

<a id ="8">[8]</a>Wang YXiao JSuzek TOZhang JWang JBryant SH (2009) PubChem: a public information system for analyzing bioactivities of small molecules Nucleic Acids Research 37:W623–W633. https://doi.org/10.1093/nar/gkp456 [Scholia](https://scholia.toolforge.org/work/Q28842768)

<a id = "9">[9]</a>Cerami et al. The cBio Cancer Genomics Portal: An Open Platform for Exploring Multidimensional Cancer Genomics Data. Cancer Discovery. May 2012 2; 401. [Scholia (wikidata)](https://scholia.toolforge.org/work/Q28266682)
{% include_relative navigation.md %}
