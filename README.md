[![Build Status](https://github.com/EURODEO/rodeo-edr-profile/workflows/build%20specification/badge.svg)](https://github.com/EURODEO/rodeo-edr-profile/actions/workflows/main.yml)

# RODEO EDR Profile

## Purpose

The purpose of these EDR profiles is to constrain the OGC-API EDR standard such that clients can consume meteorological data from multiple EDR API services without having to write custom code for each of those APIs.

The profiles are meant to be used as described by OGC-API EDR Part 3  (https://github.com/opengeospatial/ogcapi-environmental-data-retrieval/issues/404).

## Status 2025-02-28

The profile for insitu-observations is incomplete, but test implementations and feedback are very much welcome. Also, an OpenAPI 3.1 document of the profile is planned, but does not exist yet.

Work on profiles for other data types have not yet begun.

## Approach

Build an OpenAPI specification for each profile, along with human readable documentation and an automatic validation tool.

The OpenAPI specification can be used to validate that a service is compliant with the profile. It could potentially also be used to generate client and server code in multiple programming languages.

We plan to build a set of profiles roughly mirroring the data types handled by the [RODEO project](https://rodeo-project.eu/): That is, a separate profile for:

- observations / climate data
- radar
- warnings
- forecast

The work is 100% open source and the goal is to have a community driven effort that can be used by everyone.

Lastly, we want to make the job of implementing clients and servers compliant with the profile as simple as possible. Hence, we plan to build supporting validation tools and link to examples of clients and servers.

An experimental and incomplete validation tool can be found here: https://github.com/metno/sedr.

## Roadmap

A tentative plan for what to do when.

### Starting august 2024: Insitu observations

Define the profile needs for meteorological insitu observations data.

Work roughly in this order:

0. Create a rough set of annotated examples of `/collections` and data query response, to document how responses from a compliant service will look.

1. We want to tackle the metadata about parameters, units and coordinate systems, e.g decide on which vocabularies to use.

2. How to map observations into collections? One collection pr. country, one pr. station? Or rather pr. parameter or pr. data type (core / recommended etc.)?

3. work more directly on the OpenAPI specification, with things like:

    - the details of the content of `/collections`.
    - which queries to support
    - response formats for the data queries.

Lastly, there are some open questions about scope: Should the profile include constraints on how to publish metadata? E.g specific rules on using OGC-API Records to publish metadata about stations? Are there overlaps between the job of WIGOS and Oscar (WMDS, WMDR?) and this profile? Also, as a matter of practicality the profile needs to be built with some understanding of how WIS2 is implemented.

## License

Shield: [![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
