# Meteorological observations EDR profile

Example service (not fully compliant with profile yet): https://observations.eumetnet.eu/


## How to use

### Mock service

#### Setup on MacOS

Required tools:

```shell
brew install redocly-cli
brew install jq
cd standard/openapi
npm install @stoplight/prism-cli
```

Start mock service:

```shell
cd standard/openapi
redocly bundle ogcapi-edr-rodeo-insitu-observations-oas31.yaml --output insitu-observations-bundle.yaml
prism mock insitu-observations-bundle.yaml
```

Test mock service in another shell:

```shell
curl http://127.0.0.1:4010/collections |jq "."
```