# BioThings API Specifications 

### Endpoints
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BioThings API supports the following endpoints:
  - Query Service --- make query about a specific field, and return a list of matching entities
```
      http://myvariant.info/v1/query?q=_exists_:exac
```
  - Entity Retrieval Service --- retrieve annotation based on an ID, e.g. HGVS ID
```
      http://myvariant.info/v1/variant/chr6:g.26093141G>A
```
  - Metadata Retrieval Service --- retrieve metadata about the data available
```
      http://myvariant.info/v1/metadata
```
### Versioning
  - Include the version number (as "v1", "v2", "v3", and so on) to the endpoint URLs(e.g. http://myvariant.info/v1/variant endpoint)
  - Increase version number when breaking changes are introduced to the API
  - Should notify your user whenever you have a new version of API release
### Supported HTTP Methods
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BioThings API endpoints support two basic actions, e.g. ‘GET’ and ‘POST’.
  - GET: perform a single entity-retrieval or a single query
  - POST: perform a batch of entity-retrieval or queries
### Supported data formats
  - JSON
  - Msgpack  (a binary JSON format, optional)
### CORS support
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;All Biothing API endpoints support [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS) with unrestricted hostnames, so that users can make cross-origin API requests directly from their web application.
### JSONP support
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;All Biothing API endpoints support [JSONP](http://www.json-p.org/) with a query parameter “callback”, so that users can make JSONP API requests directly from their web applications.
### HTTPS support
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BioThings API supports both http and https protocol, so that users can make encrypted API request if needed.
### HTPP compression support
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BioTHings API supports gzip HTTP compression protocol to reduce the data transfer size 
### HTTP caching support
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BioThings API supports HTTP caching headers with both “Cache-Control” and “etag” headers (max-age is set to 7 days).
### Common Parameters
#### Common parameters supported by both Query and entity retrieval services
##### fields
  - Only return a specific field or fields --- provide a comma separated list of fields

```
https://myvariant.info/v1/variant/chr6:26093141G>A?fields=clinvar, dbsnp
```
  - Return a field in a nested structure --- separate each tier with a period
```
http://myvariant.info/v1/variant/chr6:26093141G>A?fields=clinvar.rcv.conditions
```
#### Common parameters supported by both Query service
##### size
  - The maximum number of matching object hits to return
  - Optional, default is 10
```
https://mygene.info/v3/query?q=cdk2&size=50
```
##### from
  - The number of matching hits to skip
  - Optional, default is 10
```
https://mygene.info/v3/query?q=cdk2&size=50&from=20
```
