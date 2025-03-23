# Profile documentation

## OpenAPI

The OpenAPI documents in this repo is based on the documents from https://github.com/opengeospatial/ogcapi-environmental-data-retrieval.

[openapi/oas31](openapi/oas31/) is the openapi documents for the core profile

[openapi/oas31-insitu-observations](openapi/oas31-insitu-observations) is the openapi documents for the core profile.


## Validate your service for compliance

[https://github.com/metno/sedr](https://github.com/metno/sedr) is an experimental validator tool in Python. It will validate the requirements in the profile and some of the requirements from the EDR spec itself.

## Mock service

Start a mock insitu-observations profile service using the OpenAPI document of the profile.

You can use this to get some live examples while implementing your own service.

### Setup on MacOS

```shell
brew install redocly-cli
brew install jq
cd openapi
npm install @stoplight/prism-cli
```

### Setup on Ubuntu

```shell
npm install @redocly/cli@latest
sudo apt-get install jq
cd openapi
npm install @stoplight/prism-cli
```

### Usage
Start mock service:

```shell
cd openapi
redocly bundle ogcapi-edr-rodeo-insitu-observations-oas31.yaml --output insitu-observations-bundle.yaml
prism mock insitu-observations-bundle.yaml
```

Test mock service in another shell:

```shell
curl http://127.0.0.1:4010/collections |jq "."
```

## Vocabularies

The profile mandates usage of various vocabularies to define metadata.

### How to use https://vocab.nerc.ac.uk/

Only the https://vocab.nerc.ac.uk/standard_name/ vocabulary is used currently. Go to that web site to get a list of all the available terms.

### How to use https://www.qudt.org

#### SPARQL search of QUDT

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

### How to specify CRS

A good resource for finding CRSs and the related WKT-definitions are: https://spatialreference.org/.

E.g for OGC:CRS84: https://spatialreference.org/ref/ogc/CRS84/.
