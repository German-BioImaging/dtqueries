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

This book is written in Markdown with additional instructions that are preprocessed.
Wishes, comments, and pull requests can be sent to
[this GitHub repository](https://github.com/German-BioImaging/dtqueries/). If you like this effort, please
star this GitHub repository! While the book itself has the CC-BY-SA, all SPARQL queries in this book can be used
under the [CCZero license/waiver](https://creativecommons.org/share-your-work/public-domain/cc0/).

## Contents
1. [Publication Records](pubrecord.md)
{% for rec in site.data.pubrecord %}
   1. {{ rec.name }}
{% endfor %}
2. [Tuberculosis](tuberculosis.md)
{% for rec in site.data.tuberculosis %}
   1. {{ rec.name }}
{% endfor %}
3. [Triple-negative breast cancer](tnbc.md)
{% for rec in site.data.tnbc %}
   1. {{ rec.name }}
{% endfor %}
4. [Glioblastoma](glioblastoma.md)
{% for rec in site.data.glioblastoma %}
   1. {{ rec.name }}
{% endfor %}
