---
layout: post
title:  "How to get a list of all your journals out of VIVO with URI and ISSN"
date:   2015-09-125 12:27:45
categories: VIVO Examples
---

So. This is is a quick post on a useful SPARQL query to get a list of all your journals in your VIVO. We are working on a report that shows H-Index values changing over time and one of the first things the analysts wanted was a list of all the journals with a convenient identifier like ISSN. So here it is. Thanks for reading.

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


# get a list of all your journals with title, uri and issn

select ?u ?issn ?label
  where {
  ?u <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://purl.org/ontology/bibo/Journal> .
  ?u rdfs:label ?label .
  ?u bibo:issn ?issn


}


{% endhighlight %}
