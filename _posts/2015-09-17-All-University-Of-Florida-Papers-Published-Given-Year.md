---
layout: post
title:  "All University of Florida papers published in journals for a given year."
date:   2015-09-17 14:00:45
categories: VIVO
---
I recently received a request for a count of papers at UF by year for the last few years so a hacked up one of mconlon17's SPARQL examples. Check him out here at [mconlon17's GitHub repo][mconlon17-gh]. Check out the CSV file output for the query, for the years 2010-2014. The CSV data files contain the URI of the publication, the ISSN of the journal it was publshed in and the title of the article.

[UF-2010-AllJournalPapers.csv](../../../../files/UF-2010-AllJournalPapers.csv)&nbsp;&nbsp;[UF-2010-AllJournalPapers.json](../../../../files/UF-2010-AllJournalPapers.json)&nbsp;&nbsp;[UF-2010-AllJournalPapers.rdf](../../../../files/UF-2010-AllJournalPapers.rdf)

[UF-2011-AllJournalPapers.csv](../../../../files/UF-2011-AllJournalPapers.csv)&nbsp;&nbsp;[UF-2011-AllJournalPapers.json](../../../../files/UF-2011-AllJournalPapers.json)&nbsp;&nbsp;[UF-2011-AllJournalPapers.rdf](../../../../files/UF-2011-AllJournalPapers.rdf)

[UF-2012-AllJournalPapers.csv](../../../../files/UF-2012-AllJournalPapers.csv)&nbsp;&nbsp;[UF-2012-AllJournalPapers.json](../../../../files/UF-2012-AllJournalPapers.json)&nbsp;&nbsp;[UF-2012-AllJournalPapers.rdf](../../../../files/UF-2012-AllJournalPapers.rdf)

[UF-2013-AllJournalPapers.csv](../../../../files/UF-2013-AllJournalPapers.csv)&nbsp;&nbsp;[UF-2013-AllJournalPapers.json](../../../../files/UF-2013-AllJournalPapers.json)&nbsp;&nbsp;[UF-2013-AllJournalPapers.rdf](../../../../files/UF-2013-AllJournalPapers.rdf)

[UF-2014-AllJournalPapers.csv](../../../../files/UF-2014-AllJournalPapers.csv)&nbsp;&nbsp;[UF-2014-AllJournalPapers.json](../../../../files/UF-2014-AllJournalPapers.json)&nbsp;&nbsp;[UF-2014-AllJournalPapers.rdf](../../../../files/UF-2014-AllJournalPapers.rdf)


SPARQL code snippets:

{% highlight sparql %}
PREFIX rdf:      <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:     <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:      <http://www.w3.org/2001/XMLSchema#>
PREFIX owl:      <http://www.w3.org/2002/07/owl#>
PREFIX swrl:     <http://www.w3.org/2003/11/swrl#>
PREFIX swrlb:    <http://www.w3.org/2003/11/swrlb#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/0.7#>
PREFIX bibo:     <http://purl.org/ontology/bibo/>
PREFIX c4o:      <http://purl.org/spar/c4o/>
PREFIX cito:     <http://purl.org/spar/cito/>
PREFIX event:    <http://purl.org/NET/c4dm/event.owl#>
PREFIX fabio:    <http://purl.org/spar/fabio/>
PREFIX foaf:     <http://xmlns.com/foaf/0.1/>
PREFIX geo:      <http://aims.fao.org/aos/geopolitical.owl#>
PREFIX p1:       <http://purl.org/dc/elements/1.1/>
PREFIX p2:       <http://purl.org/dc/terms/>
PREFIX obo:      <http://purl.obolibrary.org/obo/>
PREFIX ocrer:    <http://purl.org/net/OCRe/research.owl#>
PREFIX ocresd:   <http://purl.org/net/OCRe/study_design.owl#>
PREFIX p3:       <http://vivoweb.org/ontology/provenance-support#>
PREFIX skos:     <http://www.w3.org/2004/02/skos/core#>
PREFIX ufVivo:   <http://vivo.ufl.edu/ontology/vivo-ufl/>
PREFIX vcard:    <http://www.w3.org/2006/vcard/ns#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/public#>
PREFIX vivo:     <http://vivoweb.org/ontology/core#>
PREFIX scires:   <http://vivoweb.org/ontology/scientific-research#>

#
#
# Find papers published in 2014

SELECT ?uri ?issn ?jname ?atitle
WHERE {
	?uri a bibo:AcademicArticle .
	?uri vivo:dateTimeValue ?dtv .
	?dtv vivo:dateTime ?dt .
	FILTER (regex(?dt,"^2014"))
	?uri vivo:hasPublicationVenue ?journal .
	?journal bibo:issn ?issn .
        ?journal rdfs:label ?jname .
        ?uri rdfs:label ?atitle .
	}
{% endhighlight %}
