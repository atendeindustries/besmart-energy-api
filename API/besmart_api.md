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

Client log in to the server using the login and password. As a result, he receives a token.

> Body parameter

```
'{ "login": "login", "password": "password" }'

```

<h3 id="login-and-get-token-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|string|true|JSON with login and password|

> Example responses

> 200 Response

```json
{
  "expiration": 1586861098825,
  "user_id": 1,
  "token": "ab9d27c9044820c9998f326021dc4003"
}
```

<h3 id="login-and-get-token-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User logged in|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<h3 id="login-and-get-token-responseschema">Response Schema</h3>

Status Code **200**

*Model containing information about the authentication token*

|Name|Type|Description|
|---|---|---|
|» expiration|integer|Expiration date of token - timestamp in ms|
|» user_id|integer|User id|
|» token|string|Token|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

## Refresh token and get token info

<a id="opIdapi.endpoints.users.get_token_info"></a>

> Code samples

```http
GET https://api.besmart.energy/api/users/token HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/users/token', headers = headers)

print(r.json())

```

`GET /users/token`

Client reads endpoint to refresh the token.

> Example responses

> 200 Response

```json
{
  "expiration": 1586861098825,
  "user_id": 1,
  "token": "ab9d27c9044820c9998f326021dc4003"
}
```

<h3 id="refresh-token-and-get-token-info-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully token was refreshed|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|

<h3 id="refresh-token-and-get-token-info-responseschema">Response Schema</h3>

Status Code **200**

*Model containing information about the authentication token*

|Name|Type|Description|
|---|---|---|
|» expiration|integer|Expiration date of token - timestamp in ms|
|» user_id|integer|User id|
|» token|string|Token|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

<h1 id="besmart-rest-api-sensors">Sensors</h1>

## Create sensor

<a id="opIdapi.endpoints.sensors.post"></a>

> Code samples

```http
POST https://api.besmart.energy/api/sensors?name=Electric%20meter%20no%20123&sensor_type_id=12&client_cid=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/sensors', params={
  'name': 'Electric meter no 123',  'sensor_type_id': '12',  'client_cid': '1'
}, headers = headers)

print(r.json())

```

`POST /sensors`

Using this endpoint client can create new sensor in app

<h3 id="create-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|name|query|string|true|Name of the sensor|
|sensor_type_id|query|integer|true|Sensor type ID|
|client_cid|query|integer|true|Client CID|
|sensor_eid|query|string|false|Sensor external ID|
|lat|query|number|false|Sensor latitude|
|lon|query|number|false|Sensor longitude|
|info|query|string|false|Additional information, in json format|
|uncertain|query|boolean|false|Uncertain sensor|
|negligible|query|boolean|false|Negligible sensor|

> Example responses

> 201 Response

```json
{
  "client_cid": 2,
  "sensor_mid": 12
}
```

<h3 id="create-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created sensor|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="create-sensor-responseschema">Response Schema</h3>

Status Code **201**

*Model containing information about the new sensor*

|Name|Type|Description|
|---|---|---|
|» client_cid|integer|Client CID|
|» sensor_mid|integer|Sensor MID|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Get list of sensor types

<a id="opIdapi.endpoints.sensors.get_types"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/types HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/types', headers = headers)

print(r.json())

```

`GET /sensors/types`

Using this endpoint client gets the list of all sensor types

> Example responses

> 200 Response

```json
[
  {
    "description": "Wirtualny",
    "id": 1,
    "name": "virtual",
    "sensor_state_custom_fields": "{\"tariff\": {\"required\": true}, \"meter_max_digits\": {\"required\": false}}",
    "sensor_custom_fields": "{\"tariff\": {\"required\": true}, \"meter_max_digits\": {\"required\": false}}"
  }
]
```

<h3 id="get-list-of-sensor-types-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read sensor types|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Valid authentication credentials|

<h3 id="get-list-of-sensor-types-responseschema">Response Schema</h3>

Status Code **200**

*List of sensor types*

|Name|Type|Description|
|---|---|---|
|» description|string|Sensor type description|
|» id|integer|Sensor type ID|
|» name|string|Sensor type name|
|» sensor_state_custom_fields|string|Definitions for fields in info column in sensor state|
|» sensor_custom_fields|string|Definitions for fields in info column in sensor|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Get list of meter types

<a id="opIdapi.endpoints.sensors.get_meters"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/{client_cid}/meters HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/{client_cid}/meters', headers = headers)

print(r.json())

```

`GET /sensors/{client_cid}/meters`

Using this endpoint client can get list of all meter types

<h3 id="get-list-of-meter-types-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|

> Example responses

> 200 Response

```json
[
  {
    "id": 1206095,
    "meter_type_name": "Meter type name",
    "description": "Description of meter type",
    "number_of_phases": 3,
    "is_balance": true,
    "is_ami": true,
    "is_dcu": false
  }
]
```

<h3 id="get-list-of-meter-types-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read meter types|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Valid authentication credentials|

<h3 id="get-list-of-meter-types-responseschema">Response Schema</h3>

Status Code **200**

*List of meter types*

|Name|Type|Description|
|---|---|---|
|» id|integer|Meter type id|
|» meter_type_name|string|Meter type name|
|» description|string|Meter type description|
|» number_of_phases|integer|Number of phases|
|» is_balance|boolean|Is balance type|
|» is_ami|boolean|Is AMI type|
|» is_dcu|boolean|Is DCU|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Create meter type

<a id="opIdapi.endpoints.sensors.post_meter"></a>

> Code samples

```http
POST https://api.besmart.energy/api/sensors/{client_cid}/meters?meter_type_name=Virtual&meter_type_id=1&number_of_phases=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/sensors/{client_cid}/meters', params={
  'meter_type_name': 'Virtual',  'meter_type_id': '1',  'number_of_phases': '1'
}, headers = headers)

print(r.json())

```

`POST /sensors/{client_cid}/meters`

<h3 id="create-meter-type-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|meter_type_name|query|string|true|Meter type name|
|meter_type_id|query|integer|true|Meter type ID|
|description|query|string|false|Description|
|number_of_phases|query|integer|true|Number of phases|
|is_ami|query|boolean|false|Is ami meter|
|is_balance|query|boolean|false|Is balance meter|
|is_dcu|query|boolean|false|Is DCU|

> Example responses

> 201 Response

```json
"Created"
```

<h3 id="create-meter-type-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created meter type|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Sensor not found|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|There is another state in that period|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Date since is same or greater than date till|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Server error|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Update meter type

<a id="opIdapi.endpoints.sensors.put_meter"></a>

> Code samples

```http
PUT https://api.besmart.energy/api/sensors/{client_cid}/meters?meter_type_name=Virtual&meter_type_id=1&number_of_phases=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/sensors/{client_cid}/meters', params={
  'meter_type_name': 'Virtual',  'meter_type_id': '1',  'number_of_phases': '1'
}, headers = headers)

print(r.json())

```

`PUT /sensors/{client_cid}/meters`

<h3 id="update-meter-type-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|meter_type_name|query|string|true|Meter type name|
|meter_type_id|query|integer|true|Meter type ID|
|description|query|string|false|Description|
|number_of_phases|query|integer|true|Number of phases|
|is_ami|query|boolean|false|Is ami meter|
|is_balance|query|boolean|false|Is balance meter|
|is_dcu|query|boolean|false|Is DCU|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="update-meter-type-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully created meter type|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Valid authentication credentials|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Delete meter type

<a id="opIdapi.endpoints.sensors.delete_meter"></a>

> Code samples

```http
DELETE https://api.besmart.energy/api/sensors/{client_cid}/meters HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.besmart.energy/api/sensors/{client_cid}/meters', headers = headers)

print(r.json())

```

`DELETE /sensors/{client_cid}/meters`

<h3 id="delete-meter-type-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="delete-meter-type-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully deleted meter type|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Valid authentication credentials|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Get sensor

<a id="opIdapi.endpoints.sensors.get_id"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}', headers = headers)

print(r.json())

```

`GET /sensors/{client_cid}.{sensor_mid}`

Using this endpoint client can get sensor information

<h3 id="get-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|

> Example responses

> 200 Response

```json
{
  "info": "{}",
  "comments": "Licznik do likwidacji.",
  "client_cid": 1,
  "sensor_mid": 1,
  "lat": 53.13,
  "lon": 22.06,
  "name": "sensor name",
  "sensor_eid": "48003752B205900000",
  "sensor_type_description": "Stacja",
  "sensor_type_id": 12,
  "sensor_type_name": "meter_station",
  "write": true,
  "execute": true,
  "negligible": true,
  "uncertain": false
}
```

<h3 id="get-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read sensor information|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<h3 id="get-sensor-responseschema">Response Schema</h3>

Status Code **200**

*Model containing sensor information*

|Name|Type|Description|
|---|---|---|
|» info|string|Additional information, in json format|
|» comments|string|Comments|
|» client_cid|integer|Client CID|
|» sensor_mid|integer|Sensor MID|
|» lat|number|Latitude|
|» lon|number|Longitude|
|» name|string|Name of the sensor|
|» sensor_eid|string|Sensor external ID|
|» sensor_type_description|string|Sensor description|
|» sensor_type_id|integer|Sensor type ID|
|» sensor_type_name|string|Sensor type name|
|» write|boolean|Permission to write|
|» execute|boolean|Permission to execute|
|» negligible|boolean|Negligible sensor|
|» uncertain|boolean|Uncertain sensor|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Update sensor

<a id="opIdapi.endpoints.sensors.put_id"></a>

> Code samples

```http
PUT https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}', headers = headers)

print(r.json())

```

`PUT /sensors/{client_cid}.{sensor_mid}`

Using this endpoint client can update sensor data

<h3 id="update-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|name|query|string|false|Name of the sensor|
|sensor_type_id|query|integer|false|Sensor type ID|
|sensor_eid|query|string|false|Sensor external ID|
|lat|query|number|false|Sensor latitude|
|lon|query|number|false|Sensor longitude|
|info|query|string|false|Additional information, in json format|
|comments|query|string|false|none|
|uncertain|query|boolean|false|Uncertain sensor|
|negligible|query|boolean|false|Negligible sensor|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="update-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated sensor|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Remove sensor

<a id="opIdapi.endpoints.sensors.delete_id"></a>

> Code samples

```http
DELETE https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}', headers = headers)

print(r.json())

```

`DELETE /sensors/{client_cid}.{sensor_mid}`

Using this endpoint client can delete sensor

<h3 id="remove-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="remove-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully removed sensor|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

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

Using this endpoint client can get all signal types

> Example responses

> 200 Response

```json
[
  {
    "signal_type_moid": 32,
    "symbol": "A+",
    "is_incremental": true,
    "description": "Energia czynna pobrana z sieci",
    "unit_id": 1,
    "unit_symbol": "kW.h",
    "group_id": 2,
    "group": "Energetyka",
    "obis_mapping": "1.8.0",
    "chart_expected_unit": "kW",
    "keep_prefix": false
  }
]
```

<h3 id="get-signals-types-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals types|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|

<h3 id="get-signals-types-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Description|
|---|---|---|
|» signal_type_moid|string|Signal type MOID|
|» symbol|string|Symbol|
|» is_incremental|boolean|Is incremental|
|» description|string|Description|
|» unit_id|integer|Unit ID|
|» unit_symbol|string|Unit symbol|
|» group_id|integer|Group ID|
|» group|string|Group|
|» obis_mapping|string|Obis mapping|
|» chart_expected_unit|string|Chart expected unit|
|» keep_prefix|boolean|Keep prefix|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Get sensor states

<a id="opIdapi.endpoints.sensors.get_states"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/states?client_cid=1&sensor_mid=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/states', params={
  'client_cid': '1',  'sensor_mid': '1'
}, headers = headers)

print(r.json())

```

`GET /sensors/states`

Using this endpoint client can get all states for given sensor

<h3 id="get-sensor-states-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|true|Client CID|
|sensor_mid|query|integer|true|Sensor MID|

> Example responses

> 200 Response

```json
[
  {
    "sensor_state_id": 21310,
    "client_cid": 13,
    "sensor_mid": 44143,
    "since": 1449702000000,
    "till": 1549702000000,
    "meter_eid": 135620,
    "info": "{\"METER_DEV\": 135620, \"MM_NAME\": \"CX2000-9\"}",
    "meter_type_name": "CX2000-9",
    "meter_type_is_ami": true,
    "signal_states": [
      {
        "signal_state_id": 798649,
        "signal_type_moid": 32,
        "value_for_since": 6,
        "value_for_till": 120,
        "info": "{\"PPECODE\":\"PL_ZEBB_2006000099\",\"METER_DEV\":936692255,\"TARIFF_NAME\":\"C12A\"}"
      }
    ]
  }
]
```

<h3 id="get-sensor-states-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals states|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Server Error|

<h3 id="get-sensor-states-responseschema">Response Schema</h3>

Status Code **200**

*List of sensor states*

|Name|Type|Description|
|---|---|---|
|» sensor_state_id|integer|Sensor state ID|
|» client_cid|integer|Client CID|
|» sensor_mid|integer|Sensor MID|
|» since|integer|Start date (UTC unix timestamp in ms)|
|» till|integer|End date (UTC unix timestamp in ms)|
|» meter_eid|string|Meter external ID|
|» info|string|Additional information|
|» meter_type_name|string|Meter type name|
|» meter_type_is_ami|boolean|Meter type is AMI|
|» signal_states|[object]|List of signal states|
|»» signal_state_id|integer|Signal state ID|
|»» signal_type_moid|integer|Signal type MOID|
|»» value_for_since|number|Value for state start|
|»» value_for_till|number|Value for state end|
|»» info|string|Additional information|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Create sensor state

<a id="opIdapi.endpoints.sensors.post_states"></a>

> Code samples

```http
POST https://api.besmart.energy/api/sensors/states?client_cid=1&sensor_mid=1&since=1577836800000 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/sensors/states', params={
  'client_cid': '1',  'sensor_mid': '1',  'since': '1577836800000'
}, headers = headers)

print(r.json())

```

`POST /sensors/states`

Using this endpoint client can create sensor state for given sensor

<h3 id="create-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|true|Client CID|
|sensor_mid|query|integer|true|Sensor MID|
|since|query|number|true|Start date (UTC unix timestamp in ms)|
|till|query|number|false|End date (UTC unix timestamp in ms)|
|info|query|string|false|Additional information|
|meter_eid|query|string|false|Meter external ID|
|meter_type_name|query|string|false|Meter type name|

> Example responses

> 201 Response

```json
{
  "sensor_state_id": 21310,
  "client_cid": 13,
  "sensor_mid": 44143,
  "since": 1449702000000,
  "till": 1549702000000,
  "meter_eid": 135620,
  "info": "{\"METER_DEV\": 135620, \"MM_NAME\": \"CX2000-9\"}",
  "meter_type_name": "CX2000-9",
  "meter_type_is_ami": true,
  "signal_states": [
    []
  ]
}
```

<h3 id="create-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created state|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="create-sensor-state-responseschema">Response Schema</h3>

Status Code **201**

*Model containing information about the sensor state*

|Name|Type|Description|
|---|---|---|
|» sensor_state_id|integer|Sensor state ID|
|» client_cid|integer|Client CID|
|» sensor_mid|integer|Sensor MID|
|» since|integer|Start date (UTC unix timestamp in ms)|
|» till|integer|End date (UTC unix timestamp in ms)|
|» meter_eid|string|Meter external ID|
|» info|string|Additional information|
|» meter_type_name|string|Meter type name|
|» meter_type_is_ami|boolean|Meter type is AMI|
|» signal_states|[any]|List of signal states|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Update sensor state

<a id="opIdapi.endpoints.sensors.put_states_id"></a>

> Code samples

```http
PUT https://api.besmart.energy/api/sensors/states/{sensor_state_id} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/sensors/states/{sensor_state_id}', headers = headers)

print(r.json())

```

`PUT /sensors/states/{sensor_state_id}`

Using this endpoint client can update sensor state

<h3 id="update-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|
|since|query|integer|false|Start date (UTC unix timestamp in ms)|
|till|query|integer|false|End date (UTC unix timestamp in ms)|
|info|query|string|false|Additional informations|
|meter_eid|query|string|false|Meter external ID|
|meter_type_name|query|string|false|Meter type name|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="update-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated sensor state|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Delete sensor state

<a id="opIdapi.endpoints.sensors.delete_states_id"></a>

> Code samples

```http
DELETE https://api.besmart.energy/api/sensors/states/{sensor_state_id} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.besmart.energy/api/sensors/states/{sensor_state_id}', headers = headers)

print(r.json())

```

`DELETE /sensors/states/{sensor_state_id}`

Using this endpoint client can delete sensor state

<h3 id="delete-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="delete-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully removed sensor state|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Create signal state for sensor state

<a id="opIdapi.endpoints.sensors.post_states_id_signals"></a>

> Code samples

```http
POST https://api.besmart.energy/api/sensors/states/{sensor_state_id}/signals?signal_type_moid=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/sensors/states/{sensor_state_id}/signals', params={
  'signal_type_moid': '1'
}, headers = headers)

print(r.json())

```

`POST /sensors/states/{sensor_state_id}/signals`

Using this endpoint client can create signal state for given sensor state

<h3 id="create-signal-state-for-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|
|signal_type_moid|query|integer|true|Signal type MOID|
|value_for_since|query|number|false|Value for state start|
|value_for_till|query|number|false|Value for state end|
|info|query|string|false|Additional information|

> Example responses

> 201 Response

```json
{
  "sensor_state_id": 7986,
  "signal_state_id": 798649,
  "signal_type_moid": 32,
  "value_for_since": 6,
  "value_for_till": 120,
  "info": "{\"PPECODE\":\"PL_ZEBB_2006000099\",\"METER_DEV\":936692255,\"TARIFF_NAME\":\"C12A\"}"
}
```

<h3 id="create-signal-state-for-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created signal state|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<h3 id="create-signal-state-for-sensor-state-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Description|
|---|---|---|
|» sensor_state_id|integer|Sensor state ID|
|» signal_state_id|integer|Signal state ID|
|» signal_type_moid|integer|Signal type MOID|
|» value_for_since|number|Value for state start|
|» value_for_till|number|Value for state end|
|» info|string|Additional information|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Get sensor states for signal

<a id="opIdapi.endpoints.sensors.get_states_signals"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/states/signals?client_cid=1&sensor_mid=1&signal_type_moid=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/states/signals', params={
  'client_cid': '1',  'sensor_mid': '1',  'signal_type_moid': '1'
}, headers = headers)

print(r.json())

```

`GET /sensors/states/signals`

Using this endpoint client can read signals states for signal

<h3 id="get-sensor-states-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|true|Client CID|
|sensor_mid|query|integer|true|Sensor MID|
|signal_type_moid|query|integer|true|Signal type MOID|

> Example responses

> 200 Response

```json
[
  {
    "sensor_state_id": 21310,
    "client_cid": 13,
    "sensor_mid": 44143,
    "since": 1449702000000,
    "till": 1549702000000,
    "meter_eid": 135620,
    "info": "{\"METER_DEV\": 135620, \"MM_NAME\": \"CX2000-9\"}",
    "meter_type_name": "CX2000-9",
    "meter_type_is_ami": true,
    "signal_states": [
      {
        "signal_state_id": 798649,
        "signal_type_moid": 32,
        "value_for_since": 6,
        "value_for_till": 120,
        "info": "{\"PPECODE\":\"PL_ZEBB_2006000099\",\"METER_DEV\":936692255,\"TARIFF_NAME\":\"C12A\"}"
      }
    ]
  }
]
```

<h3 id="get-sensor-states-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals states for signal|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<h3 id="get-sensor-states-for-signal-responseschema">Response Schema</h3>

Status Code **200**

*List of sensor state*

|Name|Type|Description|
|---|---|---|
|» sensor_state_id|integer|Sensor state ID|
|» client_cid|integer|Client CID|
|» sensor_mid|integer|Sensor MID|
|» since|integer|Start date (UTC unix timestamp in ms)|
|» till|integer|End date (UTC unix timestamp in ms)|
|» meter_eid|string|Meter external ID|
|» info|string|Additional information|
|» meter_type_name|string|Meter type name|
|» meter_type_is_ami|boolean|Meter type is AMI|
|» signal_states|[object]|List of signal states|
|»» signal_state_id|integer|Signal state ID|
|»» signal_type_moid|integer|Signal type MOID|
|»» value_for_since|number|Value for state start|
|»» value_for_till|number|Value for state end|
|»» info|string|Additional information|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Update sensor state for signal

<a id="opIdapi.endpoints.sensors.put_states_signals_id"></a>

> Code samples

```http
PUT https://api.besmart.energy/api/sensors/states/signals/{signal_state_id} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/sensors/states/signals/{signal_state_id}', headers = headers)

print(r.json())

```

`PUT /sensors/states/signals/{signal_state_id}`

Using this endpoint client can update sensor state for signal

<h3 id="update-sensor-state-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|signal_state_id|path|integer|true|Signal state ID|
|value_for_since|query|number|false|Value for state start|
|value_for_till|query|number|false|Value for state end|
|info|query|string|false|Additional information|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="update-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated state for signal|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Delete sensor state for signal

<a id="opIdapi.endpoints.sensors.delete_states_signals_id"></a>

> Code samples

```http
DELETE https://api.besmart.energy/api/sensors/states/signals/{signal_state_id} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.besmart.energy/api/sensors/states/signals/{signal_state_id}', headers = headers)

print(r.json())

```

`DELETE /sensors/states/signals/{signal_state_id}`

Using this endpoint client can delete sensor state for signal

<h3 id="delete-sensor-state-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|signal_state_id|path|integer|true|Signal state ID|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="delete-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully removed state for signal|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Get multiple signals data

<a id="opIdapi.endpoints.sensors.post_signals_data"></a>

> Code samples

```http
POST https://api.besmart.energy/api/sensors/signals/data HTTP/1.1
Host: api.besmart.energy
Content-Type: application/json
Accept: application/json

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/sensors/signals/data', headers = headers)

print(r.json())

```

`POST /sensors/signals/data`

Using this endpoint client can get multiple signals data

> Body parameter

```json
[
  {
    "client_cid": 1,
    "sensor_mid": 1,
    "signal_type_moid": 1,
    "since": 1577836800000,
    "till": 1580515200000,
    "get_last": true,
    "delta_t": 60,
    "raw": false,
    "output_unit_id": 1,
    "signal_origin_id": 1,
    "filters": {},
    "is_chart": false
  }
]
```

<h3 id="get-multiple-signals-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|array[object]|true|List of parameters in JSON format|

> Example responses

> 200 Response

```json
[
  {
    "client_cid": 12,
    "sensor_mid": 122,
    "signal_type_moid": 32,
    "data": {
      "time": [
        1577836800000
      ],
      "value": [
        10.01
      ],
      "type": [
        "DBL"
      ],
      "origin": [
        1
      ]
    },
    "unit": "kW.h"
  }
]
```

<h3 id="get-multiple-signals-data-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signal data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="get-multiple-signals-data-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Description|
|---|---|---|
|» client_cid|integer|Client CID|
|» sensor_mid|integer|Sensor MID|
|» signal_type_moid|integer|Signal type MOID|
|» data|object|none|
|»» time|[integer]|List of timestamps (UTC unix timestamp in ms)|
|»» value|[oneOf]|List of values|
|»» type|[string]|List of data types name|
|»» origin|[integer]|List of data origins|
|» unit|string|Data unit|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Put multiple signals data

<a id="opIdapi.endpoints.sensors.put_signals_data"></a>

> Code samples

```http
PUT https://api.besmart.energy/api/sensors/signals/data HTTP/1.1
Host: api.besmart.energy
Content-Type: application/json
Accept: application/json

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/sensors/signals/data', headers = headers)

print(r.json())

```

`PUT /sensors/signals/data`

Using this endpoint client can put multiple signals data

> Body parameter

```json
[
  {
    "client_cid": 12,
    "sensor_mid": 122,
    "signal_type_moid": 32,
    "data": {
      "time": [
        1577836800000
      ],
      "value": [
        10.01
      ],
      "type": [
        "DBL"
      ],
      "origin": [
        1
      ]
    },
    "unit": "kW.h"
  }
]
```

<h3 id="put-multiple-signals-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|array[object]|true|List of data to save in JSON format|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="put-multiple-signals-data-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated signals data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

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

Using this endpoint client can get signal data

<h3 id="get-signal-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|signal_type_moid|path|integer|true|Signal type MOID|
|since|query|number|true|Start date (UTC unix timestamp in ms)|
|till|query|number|true|End date (UTC unix timestamp in ms)|
|get_last|query|boolean|false|Get only records with newest acq time for the same cap times|
|delta_t|query|integer|false|Aggregate time (in minutes)|
|raw|query|boolean|false|Fetch raw signal|
|output_unit_id|query|integer|false|Output unit id|
|signal_origin_id|query|integer|false|Signal origin id|
|filters|query|string|false|Data filters for complex structures|
|is_chart|query|boolean|false|Use expected chart output unit|

> Example responses

> 200 Response

```json
[
  {
    "client_cid": 12,
    "sensor_mid": 122,
    "signal_type_moid": 32,
    "data": {
      "time": [
        1577836800000
      ],
      "value": [
        10.01
      ],
      "type": [
        "DBL"
      ],
      "origin": [
        1
      ]
    },
    "unit": "kW.h"
  }
]
```

<h3 id="get-signal-data-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signal data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<h3 id="get-signal-data-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Description|
|---|---|---|
|» client_cid|integer|Client CID|
|» sensor_mid|integer|Sensor MID|
|» signal_type_moid|integer|Signal type MOID|
|» data|object|none|
|»» time|[integer]|List of timestamps (UTC unix timestamp in ms)|
|»» value|[oneOf]|List of values|
|»» type|[string]|List of data types name|
|»» origin|[integer]|List of data origins|
|» unit|string|Data unit|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Put signal data

<a id="opIdapi.endpoints.sensors.put_id_signals_id_data"></a>

> Code samples

```http
PUT https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data HTTP/1.1
Host: api.besmart.energy
Content-Type: application/json
Accept: application/json

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data', headers = headers)

print(r.json())

```

`PUT /sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data`

Using this endpoint client can put signal data

> Body parameter

```json
{
  "time": [
    1577836800000
  ],
  "value": [
    10.01
  ],
  "type": [
    "DBL"
  ],
  "origin": [
    1
  ]
}
```

<h3 id="put-signal-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|signal_type_moid|path|integer|true|Signal type MOID|
|unit|query|string|false|Signal unit|
|body|body|object|true|Data to save in JSON format|
|» time|body|[integer]|false|List of timestamps (UTC unix timestamp in ms)|
|» value|body|[oneOf]|false|List of values|
|» type|body|[string]|false|List of data types name|
|» origin|body|[integer]|false|List of data origins|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="put-signal-data-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated signal data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

<h1 id="besmart-rest-api-tasks">Tasks</h1>

## Run graph

<a id="opIdapi.endpoints.tasks.post_graphs_run"></a>

> Code samples

```http
POST https://api.besmart.energy/api/tasks/graphs/run HTTP/1.1
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

r = requests.post('https://api.besmart.energy/api/tasks/graphs/run', headers = headers)

print(r.json())

```

`POST /tasks/graphs/run`

Using this endpoint client run graph

> Body parameter

```
'{ "nodes": [ { "function": "estimation", "params": { "client_cid":
"${client_cid}", "sensor_mid": "${sensor_mid}", "profile_signal_moid":
"${profile_signal_moid}", "profile_signal_freq_minutes":
"${profile_signal_freq_minutes}", "zone_signals_freq_minutes":
"${zone_signals_freq_minutes}", "contractor_id": "${contractor_id}", "lon":
"${lon}", "lat": "${lat}" } }, { "function": "post_estimation" }, { "function":
"signals", "params": { "signal_origin_id": 4, "mode": "propagate" } } ],
"edges": [ { "from": 0, "to": 1 }, { "from": 1, "to": 2 } ] }'

```

<h3 id="run-graph-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|task_priority|query|integer|false|Graph priority (defaults to 5)|
|task_async|query|boolean|false|Should task be asynchronous|
|since|query|number|false|Start date (UTC unix timestamp in ms)|
|till|query|number|false|End date (UTC unix timestamp in ms)|
|body|body|string|true|Graph structure in JSON format|

> Example responses

> 201 Response

```json
[
  {
    "data": {
      "time": [
        1577836800000
      ],
      "value": [
        10.01
      ],
      "type": [
        "DBL"
      ],
      "origin": [
        1
      ]
    }
  }
]
```

<h3 id="run-graph-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully executed task|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|

<h3 id="run-graph-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Description|
|---|---|---|
|» data|object|none|
|»» time|[integer]|List of timestamps (UTC unix timestamp in ms)|
|»» value|[oneOf]|List of values|
|»» type|[string]|List of data types name|
|»» origin|[integer]|List of data origins|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Run graph by name

<a id="opIdapi.endpoints.tasks.post_graphs_run_name"></a>

> Code samples

```http
POST https://api.besmart.energy/api/tasks/graphs/run/name?graph_name=string HTTP/1.1
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

r = requests.post('https://api.besmart.energy/api/tasks/graphs/run/name', params={
  'graph_name': 'string'
}, headers = headers)

print(r.json())

```

`POST /tasks/graphs/run/name`

> Body parameter

```
'[{ "client_cid": 0, "sensor_mid": 0, "contractor_id": 1, "profile_signal_moid":
34, "profile_signal_freq_minutes": 15, "zone_signals_freq_minutes": 1440, "lat":
54.37999138888889, "lon": 18.633980555555556,
"signal_discrepancy_tolerance_kWh": 0.001, "params": { "type": "PV", "power":
0.0, "inclination": 0.0, "orientation": 0.0, "efficiency": 0.0, "cut_in_speed":
0.0, "cut_out_speed": 0.0, "hub_height": 0.0 } }]'

```

<h3 id="run-graph-by-name-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|graph_name|query|string|true|Graph name|
|task_priority|query|integer|false|Graph priority (defaults to 5)|
|task_async|query|boolean|false|Should task be asynchronous|
|since|query|number|false|Start date (UTC unix timestamp)|
|till|query|number|false|End date (UTC unix timestamp)|
|body|body|string|true|Graph template parameters|

> Example responses

> 200 Response

```json
"{ 'client_cid': 13, 'sensor_mid': 13781, 'signal_type_moid': 32, 'data': {...}, 'unit': 'kW.h', 'time_tstorage': 0.0593122320715338, 'time_other': 0.018632062943652272, 'hook_from': 'output', 'signature_id': 4, 'hook_to': 'input'}"
```

<h3 id="run-graph-by-name-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Graph result (only for synchronous graphs)|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Accepted for processing (only for asynchronous graphs)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

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
"No authorization token provided"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_UnprocessableEntity">UnprocessableEntity</h2>
<!-- backwards compatibility -->
<a id="schemaunprocessableentity"></a>
<a id="schema_UnprocessableEntity"></a>
<a id="tocSunprocessableentity"></a>
<a id="tocsunprocessableentity"></a>

```json
"{'status_code': -1, 'message': 'An error occured'}"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_Forbidden">Forbidden</h2>
<!-- backwards compatibility -->
<a id="schemaforbidden"></a>
<a id="schema_Forbidden"></a>
<a id="tocSforbidden"></a>
<a id="tocsforbidden"></a>

```json
"Forbidden"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_NotAllowed">NotAllowed</h2>
<!-- backwards compatibility -->
<a id="schemanotallowed"></a>
<a id="schema_NotAllowed"></a>
<a id="tocSnotallowed"></a>
<a id="tocsnotallowed"></a>

```json
"NotAllowed"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_NotFound">NotFound</h2>
<!-- backwards compatibility -->
<a id="schemanotfound"></a>
<a id="schema_NotFound"></a>
<a id="tocSnotfound"></a>
<a id="tocsnotfound"></a>

```json
"Resource not found"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_Conflict">Conflict</h2>
<!-- backwards compatibility -->
<a id="schemaconflict"></a>
<a id="schema_Conflict"></a>
<a id="tocSconflict"></a>
<a id="tocsconflict"></a>

```json
"Conflict"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_ServerError">ServerError</h2>
<!-- backwards compatibility -->
<a id="schemaservererror"></a>
<a id="schema_ServerError"></a>
<a id="tocSservererror"></a>
<a id="tocsservererror"></a>

```json
"ServerError"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

<h2 id="tocS_NotImplemented">NotImplemented</h2>
<!-- backwards compatibility -->
<a id="schemanotimplemented"></a>
<a id="schema_NotImplemented"></a>
<a id="tocSnotimplemented"></a>
<a id="tocsnotimplemented"></a>

```json
"NotImplemented"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

