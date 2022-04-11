
Leap D1 Demonstrator
====================

# Tuberculosis
## Translations of the Disease Ontology term DOID:399 (Tuberculosis)
  
```sparql
#title: Translations of the Disease Ontology term DOID:399 (Tuberculosis)  
SELECT ?English ?language ?label WHERE {  
  ?disease wdt:P699 "DOID:399";  
             rdfs:label ?English;  
             rdfs:label ?label .  
  BIND(LANG(?label) as ?languageCode)  
  ?wdLanguage wdt:P424 ?languageCode;  
              rdfs:label ?language .  
    FILTER EXISTS {?wdLanguage wdt:P31?/wdt:P279+ wd:Q17376908}  
  FILTER (LANG(?English)="en")  
  FILTER (LANG(?language)="en")  
} ORDER BY ?language  
  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Translations%20of%20the%20Disease%20Ontology%20term%20DOID%3A399%20%28Tuberculosis%29%0ASELECT%20%3FEnglish%20%3Flanguage%20%3Flabel%20WHERE%20%7B%0A%20%20%3Fdisease%20wdt%3AP699%20%22DOID%3A399%22%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20rdfs%3Alabel%20%3FEnglish%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20rdfs%3Alabel%20%3Flabel%20.%0A%20%20BIND%28LANG%28%3Flabel%29%20as%20%3FlanguageCode%29%0A%20%20%3FwdLanguage%20wdt%3AP424%20%3FlanguageCode%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20rdfs%3Alabel%20%3Flanguage%20.%0A%20%20%20%20FILTER%20EXISTS%20%7B%3FwdLanguage%20wdt%3AP31%3F/wdt%3AP279%2B%20wd%3AQ17376908%7D%0A%20%20FILTER%20%28LANG%28%3FEnglish%29%3D%22en%22%29%0A%20%20FILTER%20%28LANG%28%3Flanguage%29%3D%22en%22%29%0A%7D%20ORDER%20BY%20%3Flanguage%0A%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Genes involved in the immune response to tuberculosis
  
```sparql
#title: Genes involved in the immune response to tuberculosis  
SELECT ?gene ?geneLabel WHERE {  
   ?item wdt:P31 wd:Q4915012 ;  
         wdt:P527 ?gene ;  
         wdt:P1050 wd:Q12204 .  
  ?gene wdt:P31 wd:Q7187 .  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Genes%20involved%20in%20the%20immune%20response%20to%20tuberculosis%0ASELECT%20%3Fgene%20%3FgeneLabel%20WHERE%20%7B%0A%20%20%20%3Fitem%20wdt%3AP31%20wd%3AQ4915012%20%3B%0A%20%20%20%20%20%20%20%20%20wdt%3AP527%20%3Fgene%20%3B%0A%20%20%20%20%20%20%20%20%20wdt%3AP1050%20wd%3AQ12204%20.%0A%20%20%3Fgene%20wdt%3AP31%20wd%3AQ7187%20.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Top 100 authors of publications covering tuberculosis (according to Wikidata)
  
```sparql
#title: Top 100 authors of publications covering tuberculosis (according to Wikidata)  
#defaultView:BubbleChart  
SELECT ?author ?authorLabel (COUNT(?author) AS ?counts) WHERE {  
   ?item wdt:P31 wd:Q13442814 ;  
         wdt:P50 ?author ;  
         wdt:P921 wd:Q12204 .  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
GROUP BY ?author ?authorLabel  
ORDER BY desc(?counts)  
LIMIT 100  
  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Top%20100%20authors%20of%20publications%20covering%20tuberculosis%20%28according%20to%20Wikidata%29%0A%23defaultView%3ABubbleChart%0ASELECT%20%3Fauthor%20%3FauthorLabel%20%28COUNT%28%3Fauthor%29%20AS%20%3Fcounts%29%20WHERE%20%7B%0A%20%20%20%3Fitem%20wdt%3AP31%20wd%3AQ13442814%20%3B%0A%20%20%20%20%20%20%20%20%20wdt%3AP50%20%3Fauthor%20%3B%0A%20%20%20%20%20%20%20%20%20wdt%3AP921%20wd%3AQ12204%20.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20%3Fauthor%20%3FauthorLabel%0AORDER%20BY%20desc%28%3Fcounts%29%0ALIMIT%20100%0A%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


# publication records

## Publications and their topics
  
```sparql
#title:Publications and their topics  
#defaultView:BubbleChart  
  
PREFIX wd: <http://www.wikidata.org/entity/>  
PREFIX wdt: <http://www.wikidata.org/prop/direct/>  
PREFIX wikibase: <http://wikiba.se/ontology#>  
PREFIX bd: <http://www.bigdata.com/rdf#>  
  
SELECT DISTINCT ?topic ?topicLabel (COUNT(?leapauthor) AS ?counts)  WHERE {  
   VALUES ?leapauthor {wd:Q59830751 wd:Q59679079 wd:Q59679079 wd:Q59674360 wd:Q5107972 wd:Q39049575 wd:Q30004330 
wd:Q55101059 wd:Q88590244 wd:Q88797604 wd:Q5638525 wd:Q96210212 wd:Q49516549}  
  
  ?publication wdt:P50 ?leapauthor ;  
               wdt:P921 ?topic .  
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
GROUP BY ?topic ?topicLabel  
ORDER BY desc(?counts)  
  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3APublications%20and%20their%20topics%0A%23defaultView%3ABubbleChart%0A%0APREFIX%20wd%3A%20%3Chttp%3A//www.wikidata.org/entity/%3E%0APREFIX%20wdt%3A%20%3Chttp%3A//www.wikidata.org/prop/direct/%3E%0APREFIX%20wikibase%3A%20%3Chttp%3A//wikiba.se/ontology%23%3E%0APREFIX%20bd%3A%20%3Chttp%3A//www.bigdata.com/rdf%23%3E%0A%0ASELECT%20DISTINCT%20%3Ftopic%20%3FtopicLabel%20%28COUNT%28%3Fleapauthor%29%20AS%20%3Fcounts%29%20%20WHERE%20%7B%0A%20%20%20VALUES%20%3Fleapauthor%20%7Bwd%3AQ59830751%20wd%3AQ59679079%20wd%3AQ59679079%20wd%3AQ59674360%20wd%3AQ5107972%20wd%3AQ39049575%20wd%3AQ30004330%20wd%3AQ55101059%20wd%3AQ88590244%20wd%3AQ88797604%20wd%3AQ5638525%20wd%3AQ96210212%20wd%3AQ49516549%7D%0A%0A%20%20%3Fpublication%20wdt%3AP50%20%3Fleapauthor%20%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP921%20%3Ftopic%20.%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20%3Ftopic%20%3FtopicLabel%0AORDER%20BY%20desc%28%3Fcounts%29%0A%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Leap group leaders
  
```sparql
#title:Leap group leaders  
SELECT * WHERE {  
   VALUES ?leapauthor {  
       wd:Q59830751  
       wd:Q59679079  
       wd:Q59674360  
       wd:Q5107972  
       wd:Q39049575  
       wd:Q30004330  
       wd:Q55101059  
       wd:Q88590244  
       wd:Q88797604  
       wd:Q5638525  
       wd:Q96210212  
       wd:Q49516549  
      }  
  
  ?leapauthor rdfs:label ?leapauthorLabel .  
  
  FILTER (lang(?leapauthorLabel)="en")  
}  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3ALeap%20group%20leaders%0ASELECT%20%2A%20WHERE%20%7B%0A%20%20%20VALUES%20%3Fleapauthor%20%7B%0A%20%20%20%20%20%20%20wd%3AQ59830751%0A%20%20%20%20%20%20%20wd%3AQ59679079%0A%20%20%20%20%20%20%20wd%3AQ59674360%0A%20%20%20%20%20%20%20wd%3AQ5107972%0A%20%20%20%20%20%20%20wd%3AQ39049575%0A%20%20%20%20%20%20%20wd%3AQ30004330%0A%20%20%20%20%20%20%20wd%3AQ55101059%0A%20%20%20%20%20%20%20wd%3AQ88590244%0A%20%20%20%20%20%20%20wd%3AQ88797604%0A%20%20%20%20%20%20%20wd%3AQ5638525%0A%20%20%20%20%20%20%20wd%3AQ96210212%0A%20%20%20%20%20%20%20wd%3AQ49516549%0A%20%20%20%20%20%20%7D%0A%0A%20%20%3Fleapauthor%20rdfs%3Alabel%20%3FleapauthorLabel%20.%0A%0A%20%20FILTER%20%28lang%28%3FleapauthorLabel%29%3D%22en%22%29%0A%7D"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Group leaders and their publication records
  
```sparql
#title:Group leaders and their publication records  
#defaultView:Tree  
  
PREFIX wd: <http://www.wikidata.org/entity/>  
PREFIX wdt: <http://www.wikidata.org/prop/direct/>  
PREFIX wikibase: <http://wikiba.se/ontology#>  
PREFIX bd: <http://www.bigdata.com/rdf#>  
  
SELECT DISTINCT ?leapauthor ?leapauthorLabel ?publication ?publicationLabel ?pmid ?doi  WHERE {  
   VALUES ?leapauthor {wd:Q59830751 wd:Q59679079 wd:Q59679079 wd:Q59674360 wd:Q5107972 wd:Q39049575 wd:Q30004330 
wd:Q55101059 wd:Q88590244 wd:Q88797604 wd:Q5638525 wd:Q96210212 wd:Q49516549}  
  
  ?publication wdt:P50 ?leapauthor .  
  
  OPTIONAL {?publication wdt:P698 ?pmid .}  
  OPTIONAL {?publication wdt:P356 ?doi .}  
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3AGroup%20leaders%20and%20their%20publication%20records%0A%23defaultView%3ATree%0A%0APREFIX%20wd%3A%20%3Chttp%3A//www.wikidata.org/entity/%3E%0APREFIX%20wdt%3A%20%3Chttp%3A//www.wikidata.org/prop/direct/%3E%0APREFIX%20wikibase%3A%20%3Chttp%3A//wikiba.se/ontology%23%3E%0APREFIX%20bd%3A%20%3Chttp%3A//www.bigdata.com/rdf%23%3E%0A%0ASELECT%20DISTINCT%20%3Fleapauthor%20%3FleapauthorLabel%20%3Fpublication%20%3FpublicationLabel%20%3Fpmid%20%3Fdoi%20%20WHERE%20%7B%0A%20%20%20VALUES%20%3Fleapauthor%20%7Bwd%3AQ59830751%20wd%3AQ59679079%20wd%3AQ59679079%20wd%3AQ59674360%20wd%3AQ5107972%20wd%3AQ39049575%20wd%3AQ30004330%20wd%3AQ55101059%20wd%3AQ88590244%20wd%3AQ88797604%20wd%3AQ5638525%20wd%3AQ96210212%20wd%3AQ49516549%7D%0A%0A%20%20%3Fpublication%20wdt%3AP50%20%3Fleapauthor%20.%0A%0A%20%20OPTIONAL%20%7B%3Fpublication%20wdt%3AP698%20%3Fpmid%20.%7D%0A%20%20OPTIONAL%20%7B%3Fpublication%20wdt%3AP356%20%3Fdoi%20.%7D%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Group leaders and their past and present affiliations
  
```sparql
#title: Group leaders and their past and present affiliations  
PREFIX wd: <http://www.wikidata.org/entity/>  
PREFIX wdt: <http://www.wikidata.org/prop/direct/>  
PREFIX wikibase: <http://wikiba.se/ontology#>  
PREFIX bd:<http://www.bigdata.com/rdf#>  
  
SELECT DISTINCT ?leapauthor ?leapauthorLabel ?affiliation ?affiliationLabel WHERE {  
   VALUES ?leapauthor {wd:Q59830751 wd:Q59679079 wd:Q59679079 wd:Q59674360 wd:Q5107972 wd:Q39049575 wd:Q30004330 
wd:Q55101059 wd:Q88590244 wd:Q88797604 wd:Q5638525 wd:Q96210212 wd:Q49516549}  
  
  ?leapauthor wdt:P108 ?affiliation .  
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
ORDER BY ?leapauthor  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Group%20leaders%20and%20their%20past%20and%20present%20affiliations%0APREFIX%20wd%3A%20%3Chttp%3A//www.wikidata.org/entity/%3E%0APREFIX%20wdt%3A%20%3Chttp%3A//www.wikidata.org/prop/direct/%3E%0APREFIX%20wikibase%3A%20%3Chttp%3A//wikiba.se/ontology%23%3E%0APREFIX%20bd%3A%3Chttp%3A//www.bigdata.com/rdf%23%3E%0A%0ASELECT%20DISTINCT%20%3Fleapauthor%20%3FleapauthorLabel%20%3Faffiliation%20%3FaffiliationLabel%20WHERE%20%7B%0A%20%20%20VALUES%20%3Fleapauthor%20%7Bwd%3AQ59830751%20wd%3AQ59679079%20wd%3AQ59679079%20wd%3AQ59674360%20wd%3AQ5107972%20wd%3AQ39049575%20wd%3AQ30004330%20wd%3AQ55101059%20wd%3AQ88590244%20wd%3AQ88797604%20wd%3AQ5638525%20wd%3AQ96210212%20wd%3AQ49516549%7D%0A%0A%20%20%3Fleapauthor%20wdt%3AP108%20%3Faffiliation%20.%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AORDER%20BY%20%3Fleapauthor%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Author name strings and their publications
  
```sparql
#title:Author name strings and their publications  
#description:Finds publications by author name strings  
  
PREFIX wd: <http://www.wikidata.org/entity/>  
PREFIX wdt: <http://www.wikidata.org/prop/direct/>  
PREFIX wikibase: <http://wikiba.se/ontology#>  
PREFIX bd: <http://www.bigdata.com/rdf#>  
  
SELECT DISTINCT ?leapauthor ?publication ?publicationLabel ?pmid ?doi  WHERE {  
   VALUES ?leapauthor { "Adrie Jc Steyn"  
                        "Assaf Zaritsky"  
                        "Michael Roukes"  
                        "Chris Sander"  
                        "Fabian J. Theis"  
                        "Maddy Parsons"  
                        "Gregory Hannon"  
                        "Virginie Rozot"  
                        "Denise Kirschner"  
                        "Hagan Bayley"  
                        "Stéphane Pagès"  
                        "Joerg Bewersdorf"}  
  
  ?publication wdt:P2093 ?leapauthor .  
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
  OPTIONAL {?publication wdt:P698 ?pmid .}  
  OPTIONAL {?publication wdt:P356 ?doi .}  
}  
  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3AAuthor%20name%20strings%20and%20their%20publications%0A%23description%3AFinds%20publications%20by%20author%20name%20strings%0A%0APREFIX%20wd%3A%20%3Chttp%3A//www.wikidata.org/entity/%3E%0APREFIX%20wdt%3A%20%3Chttp%3A//www.wikidata.org/prop/direct/%3E%0APREFIX%20wikibase%3A%20%3Chttp%3A//wikiba.se/ontology%23%3E%0APREFIX%20bd%3A%20%3Chttp%3A//www.bigdata.com/rdf%23%3E%0A%0ASELECT%20DISTINCT%20%3Fleapauthor%20%3Fpublication%20%3FpublicationLabel%20%3Fpmid%20%3Fdoi%20%20WHERE%20%7B%0A%20%20%20VALUES%20%3Fleapauthor%20%7B%20%22Adrie%20Jc%20Steyn%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Assaf%20Zaritsky%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Michael%20Roukes%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Chris%20Sander%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Fabian%20J.%20Theis%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Maddy%20Parsons%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Gregory%20Hannon%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Virginie%20Rozot%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Denise%20Kirschner%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Hagan%20Bayley%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22St%C3%A9phane%20Pag%C3%A8s%22%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22Joerg%20Bewersdorf%22%7D%0A%0A%20%20%3Fpublication%20wdt%3AP2093%20%3Fleapauthor%20.%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%20%20OPTIONAL%20%7B%3Fpublication%20wdt%3AP698%20%3Fpmid%20.%7D%0A%20%20OPTIONAL%20%7B%3Fpublication%20wdt%3AP356%20%3Fdoi%20.%7D%0A%7D%0A%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


# Triple-negative breast cancer

## Genes list linked through pathways on triple-negative breast cancer
  
```sparql
#title: Genes list linked through pathways on triple-negative breast cancer  
PREFIX wd:<http://www.wikidata.org/entity/>  
PREFIX wdt: <http://www.wikidata.org/prop/direct/>  
PREFIX wikibase:<http://wikiba.se/ontology#>  
PREFIX bd:<http://www.bigdata.com/rdf#>  
  
SELECT DISTINCT ?gene ?geneLabel WHERE {  
    VALUES ?disease {wd:Q7843332} # with a main subject of triple negative breast cancer  
    ?pathway wdt:P2410 ?wpid ;      # pathways with a Wikipathways ID  
             wdt:P921 ?disease ;  
             wdt:P527 ?gene .      # which has various parts  
    ?gene wdt:P31 wd:Q7187 .       # part is of part gene  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Genes%20list%20linked%20through%20pathways%20on%20triple-
negative%20breast%20cancer%0APREFIX%20wd%3A%3Chttp%3A//www.wikidata.org/entity/%3E%0APREFIX%20wdt%3A%20%3Chttp%3A//www.wikidata.org/prop/direct/%3E%0APREFIX%20wikibase%3A%3Chttp%3A//wikiba.se/ontology%23%3E%0APREFIX%20bd%3A%3Chttp%3A//www.bigdata.com/rdf%23%3E%0A%0ASELECT%20DISTINCT%20%3Fgene%20%3FgeneLabel%20WHERE%20%7B%0A%20%20%20%20VALUES%20%3Fdisease%20%7Bwd%3AQ7843332%7D%20%23%20with%20a%20main%20subject%20of%20triple%20negative%20breast%20cancer%0A%20%20%20%20%3Fpathway%20wdt%3AP2410%20%3Fwpid%20%3B%20%20%20%20%20%20%23%20pathways%20with%20a%20Wikipathways%20ID%0A%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP921%20%3Fdisease%20%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP527%20%3Fgene%20.%20%20%20%20%20%20%23%20which%20has%20various%20parts%0A%20%20%20%20%3Fgene%20wdt%3AP31%20wd%3AQ7187%20.%20%20%20%20%20%20%20%23%20part%20is%20of%20part%20gene%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Cell types related to breast cancer via markers
  
```sparql
#title: Cell types related to breast cancer via markers  
  
PREFIX wd: <http://www.wikidata.org/entity/>  
PREFIX wdt: <http://www.wikidata.org/prop/direct/>  
  
SELECT ?cellTypeLabel ?geneLabel ?diseaseLabel  
WHERE {  
    VALUES ?disease { wd:Q128581} # breast cancer  
    ?disease wdt:P2293 ?diseaseGene ;  # Breast cancer --> genetic association --> gene  
        rdfs:label ?diseaseLabel .  
    ?cellType wdt:P8872 ?diseaseGene ; # Cell type --> has marker --> gene  
        rdfs:label ?cellTypeLabel .  
  
    ?diseaseGene rdfs:label ?geneLabel .  
  
    FILTER (LANG(?cellTypeLabel) = "en")  
    FILTER (LANG(?diseaseLabel) = "en")  
    FILTER (LANG(?geneLabel) = "en")  
}  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Cell%20types%20related%20to%20breast%20cancer%20via%20markers%0A%0APREFIX%20wd%3A%20%3Chttp%3A//www.wikidata.org/entity/%3E%0APREFIX%20wdt%3A%20%3Chttp%3A//www.wikidata.org/prop/direct/%3E%0A%0ASELECT%20%3FcellTypeLabel%20%3FgeneLabel%20%3FdiseaseLabel%0AWHERE%20%7B%0A%20%20%20%20VALUES%20%3Fdisease%20%7B%20wd%3AQ128581%7D%20%23%20breast%20cancer%0A%20%20%20%20%3Fdisease%20wdt%3AP2293%20%3FdiseaseGene%20%3B%20%20%23%20Breast%20cancer%20--%3E%20genetic%20association%20--%3E%20gene%0A%20%20%20%20%20%20%20%20rdfs%3Alabel%20%3FdiseaseLabel%20.%0A%20%20%20%20%3FcellType%20wdt%3AP8872%20%3FdiseaseGene%20%3B%20%23%20Cell%20type%20--%3E%20has%20marker%20--%3E%20gene%0A%20%20%20%20%20%20%20%20rdfs%3Alabel%20%3FcellTypeLabel%20.%0A%0A%20%20%20%20%3FdiseaseGene%20rdfs%3Alabel%20%3FgeneLabel%20.%0A%0A%20%20%20%20FILTER%20%28LANG%28%3FcellTypeLabel%29%20%3D%20%22en%22%29%0A%20%20%20%20FILTER%20%28LANG%28%3FdiseaseLabel%29%20%3D%20%22en%22%29%0A%20%20%20%20FILTER%20%28LANG%28%3FgeneLabel%29%20%3D%20%22en%22%29%0A%7D%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Chemical compounds part of a pathway on triple-negative breast cancer
  
```sparql
#title: Chemical compounds part of a pathway on triple-negative breast cancer  
  
PREFIX wd: <http://www.wikidata.org/entity/>  
PREFIX wdt: <http://www.wikidata.org/prop/direct/>  
PREFIX wikibase: <http://wikiba.se/ontology#>  
PREFIX bd: <http://www.bigdata.com/rdf#>  
  
SELECT DISTINCT ?compound ?compoundLabel WHERE {  
    ?pathway wdt:P2410 ?wpid ;      # pathways with a Wikipathways ID  
             wdt:P921 wd:Q7843332 ; # with a main subject of triple negative breast cancer  
             wdt:P527 ?compound .      # which has various parts  
    ?compound wdt:P279*/wdt:P31 wd:Q11173 .       # part is subclass of of chemical compound  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Chemical%20compounds%20part%20of%20a%20pathway%20on%20triple-
negative%20breast%20cancer%0A%0APREFIX%20wd%3A%20%3Chttp%3A//www.wikidata.org/entity/%3E%0APREFIX%20wdt%3A%20%3Chttp%3A//www.wikidata.org/prop/direct/%3E%0APREFIX%20wikibase%3A%20%3Chttp%3A//wikiba.se/ontology%23%3E%0APREFIX%20bd%3A%20%3Chttp%3A//www.bigdata.com/rdf%23%3E%0A%0ASELECT%20DISTINCT%20%3Fcompound%20%3FcompoundLabel%20WHERE%20%7B%0A%20%20%20%20%3Fpathway%20wdt%3AP2410%20%3Fwpid%20%3B%20%20%20%20%20%20%23%20pathways%20with%20a%20Wikipathways%20ID%0A%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP921%20wd%3AQ7843332%20%3B%20%23%20with%20a%20main%20subject%20of%20triple%20negative%20breast%20cancer%0A%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP527%20%3Fcompound%20.%20%20%20%20%20%20%23%20which%20has%20various%20parts%0A%20%20%20%20%3Fcompound%20wdt%3AP279%2A/wdt%3AP31%20wd%3AQ11173%20.%20%20%20%20%20%20%20%23%20part%20is%20subclass%20of%20of%20chemical%20compound%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


# Glioblastoma

## Gene list linked through pathways on glioblastoma
  
```sparql
#title: Gene list linked through pathways on glioblastoma  
#description: This query returns a list of genes linked through pathways on glioblastoma.  
PREFIX wd: <http://www.wikidata.org/entity/>  
PREFIX wdt: <http://www.wikidata.org/prop/direct/>  
PREFIX wikibase: <http://wikiba.se/ontology#>  
PREFIX bd: <http://www.bigdata.com/rdf#>  
  
SELECT DISTINCT ?gene ?geneLabel WHERE {  
    VALUES ?disease {wd:Q282142} # with a main subject of glioblastoma  
    ?pathway wdt:P2410 ?wpid ;      # pathways with a Wikipathways ID  
             wdt:P921 ?disease ;  
             wdt:P527 ?gene .      # which has various parts  
    ?gene wdt:P31 wd:Q7187 .       # part is of part gene  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Gene%20list%20linked%20through%20pathways%20on%20glioblastoma%0A%23description%3A%20This%20query%20returns%20a%20list%20of%20genes%20linked%20through%20pathways%20on%20glioblastoma.%0APREFIX%20wd%3A%20%3Chttp%3A//www.wikidata.org/entity/%3E%0APREFIX%20wdt%3A%20%3Chttp%3A//www.wikidata.org/prop/direct/%3E%0APREFIX%20wikibase%3A%20%3Chttp%3A//wikiba.se/ontology%23%3E%0APREFIX%20bd%3A%20%3Chttp%3A//www.bigdata.com/rdf%23%3E%0A%0ASELECT%20DISTINCT%20%3Fgene%20%3FgeneLabel%20WHERE%20%7B%0A%20%20%20%20VALUES%20%3Fdisease%20%7Bwd%3AQ282142%7D%20%23%20with%20a%20main%20subject%20of%20glioblastoma%0A%20%20%20%20%3Fpathway%20wdt%3AP2410%20%3Fwpid%20%3B%20%20%20%20%20%20%23%20pathways%20with%20a%20Wikipathways%20ID%0A%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP921%20%3Fdisease%20%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP527%20%3Fgene%20.%20%20%20%20%20%20%23%20which%20has%20various%20parts%0A%20%20%20%20%3Fgene%20wdt%3AP31%20wd%3AQ7187%20.%20%20%20%20%20%20%20%23%20part%20is%20of%20part%20gene%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## Chemical compounds part of a pathway on glioblastoma
  
```sparql
#title: Chemical compounds part of a pathway on glioblastoma  
SELECT DISTINCT ?compound ?compoundLabel WHERE {  
    ?pathway wdt:P2410 ?wpid ;      # pathways with a Wikipathways ID  
             wdt:P921 wd:Q7843332 ; # with a main subject of triple negative breast cancer  
             wdt:P527 ?compound .      # which has various parts  
    ?compound wdt:P279*/wdt:P31 wd:Q11173 .       # part is subclass of of chemical compound  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }  
}  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20Chemical%20compounds%20part%20of%20a%20pathway%20on%20glioblastoma%0ASELECT%20DISTINCT%20%3Fcompound%20%3FcompoundLabel%20WHERE%20%7B%0A%20%20%20%20%3Fpathway%20wdt%3AP2410%20%3Fwpid%20%3B%20%20%20%20%20%20%23%20pathways%20with%20a%20Wikipathways%20ID%0A%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP921%20wd%3AQ7843332%20%3B%20%23%20with%20a%20main%20subject%20of%20triple%20negative%20breast%20cancer%0A%20%20%20%20%20%20%20%20%20%20%20%20%20wdt%3AP527%20%3Fcompound%20.%20%20%20%20%20%20%23%20which%20has%20various%20parts%0A%20%20%20%20%3Fcompound%20wdt%3AP279%2A/wdt%3AP31%20wd%3AQ11173%20.%20%20%20%20%20%20%20%23%20part%20is%20subclass%20of%20of%20chemical%20compound%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  


## All cell lines associated with glioblastoma
  
```sparql
#title: All cell lines associated with glioblastoma  
SELECT ?disease ?diseaseLabel ?cellLines ?cellLinesLabel ?cellosaurusId WHERE {  
  VALUES ?diseaseRoot {  wd:Q282142 }  
  ?cellLines wdt:P3289 ?cellosaurusId ;  
                wdt:P5166 ?disease .  
   ?disease wdt:P279* ?diseaseRoot .  
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en" } .  
}  
  
```



<iframe style="width: 80vw; height: 50vh; border: none;" 
src="https://query.wikidata.org/embed.html#%23title%3A%20All%20cell%20lines%20associated%20with%20glioblastoma%0ASELECT%20%3Fdisease%20%3FdiseaseLabel%20%3FcellLines%20%3FcellLinesLabel%20%3FcellosaurusId%20WHERE%20%7B%0A%20%20VALUES%20%3FdiseaseRoot%20%7B%20%20wd%3AQ282142%20%7D%0A%20%20%3FcellLines%20wdt%3AP3289%20%3FcellosaurusId%20%3B%0A%20%20%20%20%20%20%20%20%20%20%09wdt%3AP5166%20%3Fdisease%20.%0A%20%20%20%3Fdisease%20wdt%3AP279%2A%20%3FdiseaseRoot%20.%0A%09SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22%20%7D%20.%0A%7D%0A%0A"
 referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

  

  

