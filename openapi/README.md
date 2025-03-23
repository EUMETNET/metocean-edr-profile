## How to use https://vocab.nerc.ac.uk/

## How to use https://www.qudt.org

### SPARQL search

Go to `https://www.qudt.org/fuseki/#/dataset/qudt/query`

Search for units by adding the following to the SPARQL endoint text field:

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> 
prefix qudt: <http://qudt.org/schema/qudt/>


select distinct ?uri ?value ?symbol where {
  ?uri rdfs:label ?value .
  ?uri qudt:symbol ?symbol .
  ?uri rdf:type qudt:Unit .
  FILTER (lang(?value)= 'en') .
}
```
Click on the arrow icon to the right.

In the resulting list, use `uri` as value for the `unit.symbol.type` and the `symbol` as value for `observedProperty.symbol.value

## How to specify CRS

WKT version seems to be: https://docs.ogc.org/is/18-010r7/18-010r7.html

Use this page to find stuff: https://spatialreference.org/ref/ogc/CRS84/.