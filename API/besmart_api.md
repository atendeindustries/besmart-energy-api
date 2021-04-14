<!-- Generator: Widdershins v4.0.1 -->

<h1 id="besmart-rest-api">besmart REST API v0.1.5</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Base URLs:

* <a href="https://api.besmart.energy/api">https://api.besmart.energy/api</a>

# Authentication

* API Key (ApiKeyAuth)
    - Parameter Name: **X-Auth**, in: header. 

- HTTP Authentication, scheme: bearer 

<h1 id="besmart-rest-api-users">Users</h1>

## Login and get token

<a id="opIdapi.endpoints.users.get_token"></a>

> Code samples

```http
POST https://api.besmart.energy/api/users/token HTTP/1.1
Host: api.besmart.energy
Content-Type: text/plain
Accept: application/json

```

```python
import requests
headers = {
  'Content-Type': 'text/plain',
  'Accept': 'application/json',
  'X-Auth': 'API_KEY'
}

r = requests.post('https://api.besmart.energy/api/users/token', headers = headers)

print(r.json())

```

`POST /users/token`

> Body parameter

```
login: login
password: password

```

<h3 id="login-and-get-token-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "expiration": 1586861098825,
  "id": 1,
  "token": "ab9d27c9044820c9998f326021dc4003"
}
```

<h3 id="login-and-get-token-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User logged in|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|

<h3 id="login-and-get-token-responseschema">Response Schema</h3>

Status Code **200**

*Model containing information about the authentication token*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» expiration|integer|false|none|none|
|» id|integer|false|none|none|
|» token|string|false|none|none|

Status Code **401**

*Model containing authorize problem info*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» detail|string|false|none|none|
|» status|integer|false|none|none|
|» title|string|false|none|none|
|» type|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

<h1 id="besmart-rest-api-workspaces">Workspaces</h1>

## Get list of workspaces

<a id="opIdapi.endpoints.workspaces.get"></a>

> Code samples

```http
GET https://api.besmart.energy/api/workspaces HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/workspaces', headers = headers)

print(r.json())

```

`GET /workspaces`

> Example responses

> 200 Response

```json
[
  {
    "config": "workspace_1",
    "descritpion": "My workspace",
    "id": 21,
    "name": "Złocieniec",
    "owner": true,
    "root_node_id": 263468,
    "client_cid": 263429,
    "sensor_mid": 263429,
    "write": true
  }
]
```

<h3 id="get-list-of-workspaces-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read list of workspaces|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|

<h3 id="get-list-of-workspaces-responseschema">Response Schema</h3>

Status Code **200**

*List of workspaces informations*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» config|string|false|none|none|
|» descritpion|string|false|none|none|
|» id|integer|false|none|none|
|» name|string|false|none|none|
|» owner|boolean|false|none|none|
|» root_node_id|integer|false|none|none|
|» client_cid|integer|false|none|none|
|» sensor_mid|integer|false|none|none|
|» write|boolean|false|none|none|

Status Code **401**

*Model containing authorize problem info*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» detail|string|false|none|none|
|» status|integer|false|none|none|
|» title|string|false|none|none|
|» type|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

<h1 id="besmart-rest-api-sensors">Sensors</h1>

## Get sensors

<a id="opIdapi.endpoints.sensors.get_find"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/find HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/find', headers = headers)

print(r.json())

```

`GET /sensors/find`

<h3 id="get-sensors-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|false|Client ID|
|sensor_type_id|query|integer|false|Sensor type ID|
|name|query|string|false|Sensor name|
|columns|query|string|false|Column names to return|

> Example responses

> 200 Response

```json
[
  {
    "address_city": "Warszawa",
    "address_flat_number": "35",
    "address_postcode": "00-020",
    "address_street": "Wiejska",
    "address_street_number": "36",
    "client_cid": 1,
    "sensor_mid": 1,
    "ppe": "PL123123123123",
    "lat": 53.13,
    "lon": 22.06,
    "name": "sensor name",
    "owner": true,
    "sensor_eid": "48003752B205900000",
    "sensor_type_description": "Stacja",
    "sensor_type_id": 12,
    "sensor_type_name": "meter_station",
    "write": true
  }
]
```

<h3 id="get-sensors-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read sensors information|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|

<h3 id="get-sensors-responseschema">Response Schema</h3>

Status Code **200**

*List of sensors*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» address_city|string|false|none|none|
|» address_flat_number|string|false|none|none|
|» address_postcode|string|false|none|none|
|» address_street|string|false|none|none|
|» address_street_number|string|false|none|none|
|» client_cid|integer|false|none|none|
|» sensor_mid|integer|false|none|none|
|» ppe|string|false|none|none|
|» lat|number|false|none|none|
|» lon|number|false|none|none|
|» name|string|false|none|none|
|» owner|boolean|false|none|none|
|» sensor_eid|string|false|none|none|
|» sensor_type_description|string|false|none|none|
|» sensor_type_id|integer|false|none|none|
|» sensor_type_name|string|false|none|none|
|» write|boolean|false|none|none|

Status Code **401**

*Model containing authorize problem info*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» detail|string|false|none|none|
|» status|integer|false|none|none|
|» title|string|false|none|none|
|» type|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Get sensors by external id

<a id="opIdapi.endpoints.sensors.post_external"></a>

> Code samples

```http
POST https://api.besmart.energy/api/sensors/external HTTP/1.1
Host: api.besmart.energy
Content-Type: text/plain
Accept: application/json

```

```python
import requests
headers = {
  'Content-Type': 'text/plain',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/sensors/external', headers = headers)

print(r.json())

```

`POST /sensors/external`

> Body parameter

```
string

```

<h3 id="get-sensors-by-external-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|string|true|none|

> Example responses

> 200 Response

```json
[
  {
    "address_city": "Warszawa",
    "address_flat_number": "35",
    "address_postcode": "00-020",
    "address_street": "Wiejska",
    "address_street_number": "36",
    "client_cid": 1,
    "sensor_mid": 1,
    "ppe": "PL123123123123",
    "lat": 53.13,
    "lon": 22.06,
    "name": "sensor name",
    "owner": true,
    "sensor_eid": "48003752B205900000",
    "sensor_type_description": "Stacja",
    "sensor_type_id": 12,
    "sensor_type_name": "meter_station",
    "write": true
  }
]
```

<h3 id="get-sensors-by-external-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read sensors information|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|

<h3 id="get-sensors-by-external-id-responseschema">Response Schema</h3>

Status Code **200**

*List of sensors*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» address_city|string|false|none|none|
|» address_flat_number|string|false|none|none|
|» address_postcode|string|false|none|none|
|» address_street|string|false|none|none|
|» address_street_number|string|false|none|none|
|» client_cid|integer|false|none|none|
|» sensor_mid|integer|false|none|none|
|» ppe|string|false|none|none|
|» lat|number|false|none|none|
|» lon|number|false|none|none|
|» name|string|false|none|none|
|» owner|boolean|false|none|none|
|» sensor_eid|string|false|none|none|
|» sensor_type_description|string|false|none|none|
|» sensor_type_id|integer|false|none|none|
|» sensor_type_name|string|false|none|none|
|» write|boolean|false|none|none|

Status Code **401**

*Model containing authorize problem info*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» detail|string|false|none|none|
|» status|integer|false|none|none|
|» title|string|false|none|none|
|» type|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

<h1 id="besmart-rest-api-signals">Signals</h1>

## Get signals types

<a id="opIdapi.endpoints.sensors.get_signals_types"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/signals/types HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/signals/types', headers = headers)

print(r.json())

```

`GET /sensors/signals/types`

> Example responses

> 200 Response

```json
"None"
```

<h3 id="get-signals-types-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals types|Inline|

<h3 id="get-signals-types-responseschema">Response Schema</h3>

Status Code **200**

*List of signals types*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Get signal data

<a id="opIdapi.endpoints.sensors.get_id_signals_id_data"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data?since=1577836800000&till=1580515200000 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data', params={
  'since': '1577836800000',  'till': '1580515200000'
}, headers = headers)

print(r.json())

```

`GET /sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data`

<h3 id="get-signal-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|signal_type_moid|path|integer|true|Signal type MOID|
|since|query|integer|true|Start date (UTC unix timestamp)|
|till|query|integer|true|End date (UTC unix timestamp)|
|delta_t|query|integer|false|Aggregate time (in minutes)|
|raw|query|boolean|false|Fetch raw signal|
|output_unit_id|query|integer|false|Output unit id|
|signal_origin_id|query|integer|false|Signal origin id|

> Example responses

> 200 Response

```json
{
  "client_cid": 12,
  "sensor_mid": 122,
  "signal_type_moid": 32,
  "data": [
    {
      "time": 1577836800000,
      "value": 10.01,
      "type": "DBL",
      "origin": 1
    }
  ],
  "unit": "kW.h"
}
```

<h3 id="get-signal-data-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signal data|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|None|

<h3 id="get-signal-data-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» client_cid|integer|false|none|none|
|» sensor_mid|integer|false|none|none|
|» signal_type_moid|integer|false|none|none|
|» data|[object]|false|none|none|
|»» time|integer|false|none|Timestamp in UTC in ms|
|»» value|any|false|none|Value|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|string|false|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|integer|false|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|number|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» type|string|false|none|Data type name|
|»» origin|integer|false|none|Data origin|
|» unit|string|false|none|Data unit|

Status Code **401**

*Model containing authorize problem info*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» detail|string|false|none|none|
|» status|integer|false|none|none|
|» title|string|false|none|none|
|» type|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

# Schemas

<h2 id="tocS_IdResponse">IdResponse</h2>
<!-- backwards compatibility -->
<a id="schemaidresponse"></a>
<a id="schema_IdResponse"></a>
<a id="tocSidresponse"></a>
<a id="tocsidresponse"></a>

```json
{
  "id": 1
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|

<h2 id="tocS_OkResponse">OkResponse</h2>
<!-- backwards compatibility -->
<a id="schemaokresponse"></a>
<a id="schema_OkResponse"></a>
<a id="tocSokresponse"></a>
<a id="tocsokresponse"></a>

```json
"OK"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_CreatedResponse">CreatedResponse</h2>
<!-- backwards compatibility -->
<a id="schemacreatedresponse"></a>
<a id="schema_CreatedResponse"></a>
<a id="tocScreatedresponse"></a>
<a id="tocscreatedresponse"></a>

```json
"Created"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_Signal">Signal</h2>
<!-- backwards compatibility -->
<a id="schemasignal"></a>
<a id="schema_Signal"></a>
<a id="tocSsignal"></a>
<a id="tocssignal"></a>

```json
{
  "id": 33,
  "name": "A+",
  "owner": true,
  "states": [
    {
      "id": 33,
      "info": "G11",
      "since": 1585919039882,
      "state_eid": "24569922006",
      "till": 1585919039882
    }
  ],
  "type": "a+",
  "type_name": "Zużycie",
  "unit": "kWh",
  "write": true
}

```

Model containing information about the signal

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|name|string|false|none|none|
|owner|boolean|false|none|none|
|states|[object]|false|none|none|
|» id|integer|false|none|none|
|» info|string|false|none|none|
|» since|integer|false|none|none|
|» state_eid|string|false|none|none|
|» till|integer|false|none|none|
|type|boolean|false|none|none|
|type_name|boolean|false|none|none|
|unit|string|false|none|none|
|write|boolean|false|none|none|

<h2 id="tocS_Unauthorize">Unauthorize</h2>
<!-- backwards compatibility -->
<a id="schemaunauthorize"></a>
<a id="schema_Unauthorize"></a>
<a id="tocSunauthorize"></a>
<a id="tocsunauthorize"></a>

```json
{
  "detail": "No authorization token provided",
  "status": 401,
  "title": "Unauthorized",
  "type": "about:blank"
}

```

Model containing authorize problem info

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|detail|string|false|none|none|
|status|integer|false|none|none|
|title|string|false|none|none|
|type|string|false|none|none|

<h2 id="tocS_UnprocessableEntity">UnprocessableEntity</h2>
<!-- backwards compatibility -->
<a id="schemaunprocessableentity"></a>
<a id="schema_UnprocessableEntity"></a>
<a id="tocSunprocessableentity"></a>
<a id="tocsunprocessableentity"></a>

```json
"Error"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

