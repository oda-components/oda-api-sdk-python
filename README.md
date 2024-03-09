# Build
Building the ODA Open API SDK for Python.

## Tooling
* Install [Python](https://www.python.org/downloads)
* Install [OpenAPI Generator](https://openapi-generator.tech/docs/installation)

# Generate
Generate a client and server for each ODA Open API.

## TMF634
```bash
openapi-generator-cli generate --generator-name python --output tmf634/client --additional-properties packageName=oda_sdk_tmf634 -i https://raw.githubusercontent.com/tmforum-apis/TMF634_ResourceCatalog/master/TMF634-ResourceCatalog-v4.1.0.swagger.json
openapi-generator-cli generate --generator-name python-flask --output tmf634/server --additional-properties packageName=oda_sdk_tmf634 -i https://raw.githubusercontent.com/tmforum-apis/TMF634_ResourceCatalog/master/TMF634-ResourceCatalog-v4.1.0.swagger.json
```

## TMF639
```bash
openapi-generator-cli generate --generator-name python --output tmf639/client --additional-properties packageName=oda_sdk_tmf639 -i https://raw.githubusercontent.com/tmforum-apis/TMF639_ResourceInventory/master/TMF639-ResourceInventory-v4.0.0.swagger.json
openapi-generator-cli generate --generator-name python-flask --output tmf639/server --additional-properties packageName=oda_sdk_tmf639 -i https://raw.githubusercontent.com/tmforum-apis/TMF639_ResourceInventory/master/TMF639-ResourceInventory-v4.0.0.swagger.json
```

## Replacement

Change GIT_USER_ID and GIT_REPO_ID:
```bash
$ sed -i "s/GIT_USER_ID\/GIT_REPO_ID/oda-components\/oda-api-sdk-python/g" tmf*/*/*.toml # Replace GIT_USER_ID and GIT_REPO_ID
$ sed -i "s/GIT_USER_ID\/GIT_REPO_ID/oda-components\/oda-api-sdk-python/g" tmf*/*/*.md   # Replace GIT_USER_ID and GIT_REPO_ID
```

# Build & Test

## Build TMF 634 server
```bash
$ cd tmf634/server
$ pip3 install -r requirements.txt
$ python3 -m oda_sdk_tmf634
```

## Test request to TMF 634 server
```bash
$ curl -vs -H 'Accept: application/json' http://localhost:8080/tmf-api/resourceCatalog/v4/resourceSpecification
```
