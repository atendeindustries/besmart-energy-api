<!-- Generator: Widdershins v4.0.1 -->

<h1 id="besmart-rest-api">besmart REST API v0.35.2.2</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

<a href="https://api.besmart.energy/api">https://api.besmart.energy/api</a>

# Authentication

- HTTP Authentication, scheme: bearer 

* API Key (APIKeyHeader)
    - Parameter Name: **X-Auth**, in: header. 

<h1 id="besmart-rest-api-sensors">Sensors</h1>

## Get list of sensor types

<a id="opIdapi_endpoints_sensors_get_types_api_sensors_types_get"></a>

> Code samples

```http
GET /api/sensors/types HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('/api/sensors/types', headers = headers)

print(r.json())

```

`GET /api/sensors/types`

Using this endpoint client gets the list of all sensor types

> Example responses

> 200 Response

```json
[]
```

<h3 id="get-list-of-sensor-types-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read sensor types|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|

<h3 id="get-list-of-sensor-types-responseschema">Response Schema</h3>

Status Code **200**

*Response 200 Api Endpoints Sensors Get Types Api Sensors Types Get*

|Name|Type|Description|
|---|---|---|
|Response 200 Api Endpoints Sensors Get Types Api Sensors Types Get|array|none|
|» *anonymous*|any|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Get sensor

<a id="opIdapi_endpoints_sensors_get_id_api_sensors__client_cid___sensor_mid__get"></a>

> Code samples

```http
GET /api/sensors/{client_cid}.{sensor_mid} HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('/api/sensors/{client_cid}.{sensor_mid}', headers = headers)

print(r.json())

```

`GET /api/sensors/{client_cid}.{sensor_mid}`

<h3 id="get-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|

> Example responses

> 404 Response

```json
"string"
```

<h3 id="get-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read sensor information|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="get-sensor-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Update sensor

<a id="opIdapi_endpoints_sensors_put_id_api_sensors__client_cid___sensor_mid__put"></a>

> Code samples

```http
PUT /api/sensors/{client_cid}.{sensor_mid} HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('/api/sensors/{client_cid}.{sensor_mid}', headers = headers)

print(r.json())

```

`PUT /api/sensors/{client_cid}.{sensor_mid}`

<h3 id="update-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|node_id|query|integer|false|Node ID|
|name|query|string|false|Name of the sensor|
|sensor_type_id|query|integer|false|Sensor type ID|
|sensor_eid|query|string|false|Sensor external ID|
|lat|query|number|false|Sensor latitude|
|lon|query|number|false|Sensor longitude|
|annotations|query|string|false|Annotations to sensor update, in json format|
|info|query|string|false|Additional information, in json format|
|comments|query|string|false|none|
|uncertain|query|boolean|false|Uncertain sensor|
|negligible|query|boolean|false|Negligible sensor|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="update-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated sensor|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="update-sensor-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Remove sensor

<a id="opIdapi_endpoints_sensors_delete_id_api_sensors__client_cid___sensor_mid__delete"></a>

> Code samples

```http
DELETE /api/sensors/{client_cid}.{sensor_mid} HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('/api/sensors/{client_cid}.{sensor_mid}', headers = headers)

print(r.json())

```

`DELETE /api/sensors/{client_cid}.{sensor_mid}`

<h3 id="remove-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="remove-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully removed sensor|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="remove-sensor-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Create new sensor

<a id="opIdapi_endpoints_sensors_post_api_sensors_post"></a>

> Code samples

```http
POST /api/sensors?client_cid=0&name=string HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('/api/sensors', params={
  'client_cid': '0',  'name': 'string'
}, headers = headers)

print(r.json())

```

`POST /api/sensors`

<h3 id="create-new-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|true|Client CID|
|name|query|string|true|Name of the sensor|
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
null
```

<h3 id="create-new-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created sensor|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="create-new-sensor-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

<h1 id="besmart-rest-api-signals">Signals</h1>

## Update sensor state for signal

<a id="opIdapi_endpoints_sensors_put_states_signals_id_api_sensors_states_signals__signal_state_id__put"></a>

> Code samples

```http
PUT /api/sensors/states/signals/{signal_state_id} HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('/api/sensors/states/signals/{signal_state_id}', headers = headers)

print(r.json())

```

`PUT /api/sensors/states/signals/{signal_state_id}`

Using this endpoint client can update sensor state for signal

<h3 id="update-sensor-state-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|signal_state_id|path|integer|true|Signal state ID|
|value_for_since|query|string|false|Value for state start|
|value_for_till|query|string|false|Value for state end|
|info|query|string|false|Additional information|

> Example responses

> 200 Response

```json
null
```

<h3 id="update-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Updated state for signal|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="update-sensor-state-for-signal-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Delete sensor state for signal

<a id="opIdapi_endpoints_sensors_delete_states_signals_id_api_sensors_states_signals__signal_state_id__delete"></a>

> Code samples

```http
DELETE /api/sensors/states/signals/{signal_state_id} HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('/api/sensors/states/signals/{signal_state_id}', headers = headers)

print(r.json())

```

`DELETE /api/sensors/states/signals/{signal_state_id}`

Using this endpoint client can delete sensor state for signal

<h3 id="delete-sensor-state-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|signal_state_id|path|integer|true|Signal state ID|

> Example responses

> 200 Response

```json
null
```

<h3 id="delete-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Removed state for signal|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="delete-sensor-state-for-signal-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Put multiple signals data

<a id="opIdapi_endpoints_sensors_put_signals_data_api_sensors_signals_data_put"></a>

> Code samples

```http
PUT /api/sensors/signals/data HTTP/1.1

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

r = requests.put('/api/sensors/signals/data', headers = headers)

print(r.json())

```

`PUT /api/sensors/signals/data`

Using this endpoint client can put multiple signals data

> Body parameter

```json
null
```

<h3 id="put-multiple-signals-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|any|false|none|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="put-multiple-signals-data-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated signals data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="put-multiple-signals-data-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Get multiple signals data

<a id="opIdapi_endpoints_sensors_post_signals_data_api_sensors_signals_data_post"></a>

> Code samples

```http
POST /api/sensors/signals/data HTTP/1.1

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

r = requests.post('/api/sensors/signals/data', headers = headers)

print(r.json())

```

`POST /api/sensors/signals/data`

Using this endpoint client can get multiple signals data

> Body parameter

```json
null
```

<h3 id="get-multiple-signals-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|any|false|none|

> Example responses

> 200 Response

```json
[]
```

<h3 id="get-multiple-signals-data-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signal data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="get-multiple-signals-data-responseschema">Response Schema</h3>

Status Code **200**

*Response 200 Api Endpoints Sensors Post Signals Data Api Sensors Signals Data Post*

|Name|Type|Description|
|---|---|---|
|Response 200 Api Endpoints Sensors Post Signals Data Api Sensors Signals Data Post|array|none|
|» *anonymous*|any|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Get signals types

<a id="opIdapi_endpoints_sensors_get_signals_types_api_sensors_signals_types_get"></a>

> Code samples

```http
GET /api/sensors/signals/types HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('/api/sensors/signals/types', headers = headers)

print(r.json())

```

`GET /api/sensors/signals/types`

Using this endpoint client can get all signal types

> Example responses

> 200 Response

```json
[]
```

<h3 id="get-signals-types-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals types|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|

<h3 id="get-signals-types-responseschema">Response Schema</h3>

Status Code **200**

*Response 200 Api Endpoints Sensors Get Signals Types Api Sensors Signals Types Get*

|Name|Type|Description|
|---|---|---|
|Response 200 Api Endpoints Sensors Get Signals Types Api Sensors Signals Types Get|array|none|
|» *anonymous*|any|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Get sensor states for signal

<a id="opIdapi_endpoints_sensors_get_states_signals_api_sensors_states_signals_get"></a>

> Code samples

```http
GET /api/sensors/states/signals HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('/api/sensors/states/signals', headers = headers)

print(r.json())

```

`GET /api/sensors/states/signals`

Using this endpoint client can read signals states for signal

<h3 id="get-sensor-states-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|false|Client CID|
|sensor_mid|query|integer|false|Sensor MID|
|signal_type_moid|query|integer|false|Signal type MOID|

> Example responses

> 200 Response

```json
[]
```

<h3 id="get-sensor-states-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals states for signal|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="get-sensor-states-for-signal-responseschema">Response Schema</h3>

Status Code **200**

*Response 200 Api Endpoints Sensors Get States Signals Api Sensors States Signals Get*

|Name|Type|Description|
|---|---|---|
|Response 200 Api Endpoints Sensors Get States Signals Api Sensors States Signals Get|array|none|
|» *anonymous*|any|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Create sensor state for signal

<a id="opIdapi_endpoints_sensors_post_states_id_signals_api_sensors_states__sensor_state_id__signals_post"></a>

> Code samples

```http
POST /api/sensors/states/{sensor_state_id}/signals?signal_type_moid=0 HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('/api/sensors/states/{sensor_state_id}/signals', params={
  'signal_type_moid': '0'
}, headers = headers)

print(r.json())

```

`POST /api/sensors/states/{sensor_state_id}/signals`

Using this endpoint client can create signal state for given sensor state

<h3 id="create-sensor-state-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|
|signal_type_moid|query|integer|true|Signal type moid|
|value_for_since|query|string|false|Value for state start|
|value_for_till|query|string|false|Value for state end|
|info|query|string|false|Additional information|

> Example responses

> 200 Response

```json
null
```

<h3 id="create-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created state for signal|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="create-sensor-state-for-signal-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Update sensor state

<a id="opIdapi_endpoints_sensors_put_states_id_api_sensors_states__sensor_state_id__put"></a>

> Code samples

```http
PUT /api/sensors/states/{sensor_state_id} HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('/api/sensors/states/{sensor_state_id}', headers = headers)

print(r.json())

```

`PUT /api/sensors/states/{sensor_state_id}`

Using this endpoint client can update sensor state

<h3 id="update-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|
|since|query|integer|false|Start date (UTC unix timestamp in ms)|
|till|query|integer|false|End date (UTC unix timestamp in ms)|
|info|query|string|false|Additional information|
|meter_eid|query|string|false|Meter external ID|
|meter_type_id|query|string|false|Meter type id|

> Example responses

> 200 Response

```json
null
```

<h3 id="update-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Updated state|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="update-sensor-state-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Delete sensor state

<a id="opIdapi_endpoints_sensors_delete_states_id_api_sensors_states__sensor_state_id__delete"></a>

> Code samples

```http
DELETE /api/sensors/states/{sensor_state_id} HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('/api/sensors/states/{sensor_state_id}', headers = headers)

print(r.json())

```

`DELETE /api/sensors/states/{sensor_state_id}`

Using this endpoint client can delete sensor state

<h3 id="delete-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|

> Example responses

> 200 Response

```json
null
```

<h3 id="delete-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Removed state|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="delete-sensor-state-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Get sensor states

<a id="opIdapi_endpoints_sensors_get_states_api_sensors_states_get"></a>

> Code samples

```http
GET /api/sensors/states HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('/api/sensors/states', headers = headers)

print(r.json())

```

`GET /api/sensors/states`

Using this endpoint client can get all states for given sensor

<h3 id="get-sensor-states-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|false|Client CID|
|sensor_mid|query|integer|false|Sensor MID|

> Example responses

> 200 Response

```json
[]
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

*Response 200 Api Endpoints Sensors Get States Api Sensors States Get*

|Name|Type|Description|
|---|---|---|
|Response 200 Api Endpoints Sensors Get States Api Sensors States Get|array|none|
|» *anonymous*|any|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Create sensor state

<a id="opIdapi_endpoints_sensors_post_states_api_sensors_states_post"></a>

> Code samples

```http
POST /api/sensors/states?client_cid=0&sensor_mid=0 HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('/api/sensors/states', params={
  'client_cid': '0',  'sensor_mid': '0'
}, headers = headers)

print(r.json())

```

`POST /api/sensors/states`

Using this endpoint client can create sensor state for given sensor

<h3 id="create-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|true|Client CID|
|sensor_mid|query|integer|true|Sensor MID|
|since|query|integer|false|Start date (UTC unix timestamp in ms)|
|till|query|integer|false|End date (UTC unix timestamp in ms)|
|info|query|string|false|Additional information|
|meter_eid|query|string|false|Meter external ID|
|meter_type_id|query|integer|false|Meter type id|

> Example responses

> 200 Response

```json
null
```

<h3 id="create-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created state|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="create-sensor-state-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Get signal data

<a id="opIdapi_endpoints_sensors_get_id_signals_id_data_api_sensors__client_cid___sensor_mid__signals__signal_type_moid__data_get"></a>

> Code samples

```http
GET /api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data?since=1701273988000&till=1701360388000 HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data', params={
  'since': '1701273988000',  'till': '1701360388000'
}, headers = headers)

print(r.json())

```

`GET /api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data`

Using this endpoint client can get signal data

<h3 id="get-signal-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|signal_type_moid|path|integer|true|Signal type MOID|
|since|query|integer|true|Start date (UTC unix timestamp)|
|till|query|integer|true|End date (UTC unix timestamp)|
|get_last|query|boolean|false|Get only records with newest acq time for the same cap times|
|delta_t|query|integer|false|Aggregate time (in minutes)|
|raw|query|boolean|false|Fetch raw signal|
|apply_multiplier|query|boolean|false|Apply multiplier|
|output_unit_id|query|integer|false|Output unit id|
|signal_origin_id|query|integer|false|Signal origin id|

> Example responses

> 404 Response

```json
"string"
```

<h3 id="get-signal-data-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signal data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="get-signal-data-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Put signal data

<a id="opIdapi_endpoints_sensors_put_id_signals_id_data_api_sensors__client_cid___sensor_mid__signals__signal_type_moid__data_put"></a>

> Code samples

```http
PUT /api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data HTTP/1.1

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

r = requests.put('/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data', headers = headers)

print(r.json())

```

`PUT /api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data`

Using this endpoint client can put signal data

> Body parameter

```json
null
```

<h3 id="put-signal-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|signal_type_moid|path|integer|true|Signal type MOID|
|unit|query|string|false|Signal unit|
|body|body|any|false|none|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="put-signal-data-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated signal data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="put-signal-data-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

<h1 id="besmart-rest-api-tasks">Tasks</h1>

## Run graph by name

<a id="opIdapi_endpoints_tasks_post_graphs_run_name_api_tasks_graphs_run_name_post"></a>

> Code samples

```http
POST /api/tasks/graphs/run/name?graph_name=string HTTP/1.1

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

r = requests.post('/api/tasks/graphs/run/name', params={
  'graph_name': 'string'
}, headers = headers)

print(r.json())

```

`POST /api/tasks/graphs/run/name`

> Body parameter

```json
null
```

<h3 id="run-graph-by-name-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|graph_name|query|string|true|Graph name|
|task_priority|query|integer|false|Graph priority (defaults to 5)|
|task_async|query|boolean|false|Should task be asynchronous|
|since|query|integer|false|Start date (UTC unix timestamp)|
|till|query|integer|false|End date (UTC unix timestamp)|
|body|body|any|true|none|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="run-graph-by-name-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Graph result (only for synchronous graphs)|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Accepted for processing (only for asynchronous graphs)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="run-graph-by-name-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Run graph

<a id="opIdapi_endpoints_tasks_post_graphs_run_api_tasks_graphs_run_post"></a>

> Code samples

```http
POST /api/tasks/graphs/run HTTP/1.1

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

r = requests.post('/api/tasks/graphs/run', headers = headers)

print(r.json())

```

`POST /api/tasks/graphs/run`

Using this endpoint client run graph

> Body parameter

```json
null
```

<h3 id="run-graph-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|task_priority|query|integer|false|Graph priority (defaults to 5)|
|task_async|query|boolean|false|Should task be asynchronous|
|since|query|integer|false|Start date (UTC unix timestamp in ms)|
|till|query|integer|false|End date (UTC unix timestamp in ms)|
|body|body|any|true|none|

> Example responses

> 200 Response

```json
null
```

<h3 id="run-graph-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully executed task|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="run-graph-responseschema">Response Schema</h3>

Status Code **201**

*Response 201 Api Endpoints Tasks Post Graphs Run Api Tasks Graphs Run Post*

|Name|Type|Description|
|---|---|---|
|Response 201 Api Endpoints Tasks Post Graphs Run Api Tasks Graphs Run Post|array|none|
|» *anonymous*|any|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

<h1 id="besmart-rest-api-users">Users</h1>

## Refresh token and get token info

<a id="opIdapi_endpoints_users_get_token_info_api_users_token_get"></a>

> Code samples

```http
GET /api/users/token HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('/api/users/token', headers = headers)

print(r.json())

```

`GET /api/users/token`

Client reads endpoint to refresh the token.

> Example responses

<h3 id="refresh-token-and-get-token-info-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully token was refreshed|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|

<h3 id="refresh-token-and-get-token-info-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Login and get token

<a id="opIdapi_endpoints_users_get_token_api_users_token_post"></a>

> Code samples

```http
POST /api/users/token HTTP/1.1

Content-Type: application/json
Accept: application/json

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Auth': 'API_KEY'
}

r = requests.post('/api/users/token', headers = headers)

print(r.json())

```

`POST /api/users/token`

Client logs in to the server with login and password. As a result, they receive a token.

> Body parameter

```json
null
```

<h3 id="login-and-get-token-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|any|false|none|

> Example responses

> 404 Response

```json
"string"
```

<h3 id="login-and-get-token-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User logged in|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="login-and-get-token-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
APIKeyHeader
</aside>

# Schemas

