<!-- Generator: Widdershins v4.0.1 -->

<h1 id="besmart-rest-api">besmart REST API v0.44.44.7</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

<a href="https://api.besmart.energy/api">https://api.besmart.energy/api</a>

# Authentication

- HTTP Authentication, scheme: bearer 

* API Key (APIKeyHeader)
    - Parameter Name: **X-Auth**, in: header. 

<h1 id="besmart-rest-api-estimation">Estimation</h1>

## Run graph

<a id="opIdapi_endpoints_graph_post_api_tasks_graphs_run_name_post"></a>

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

<h3 id="run-graph-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|graph_name|query|string|true|Graph name|
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
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|

<h3 id="run-graph-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

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
[
  {
    "id": 0,
    "name": "string",
    "description": "string",
    "sensor_state_custom_fields": "string",
    "sensor_custom_fields": "string",
    "is_system_type": true
  }
]
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
|Response 200 Api Endpoints Sensors Get Types Api Sensors Types Get|[[SensorTypeResponse](#schemasensortyperesponse)]|none|
|» SensorTypeResponse|[SensorTypeResponse](#schemasensortyperesponse)|none|
|»» id|integer|none|
|»» name|string|none|
|»» description|string|none|
|»» sensor_state_custom_fields|string|none|
|»» sensor_custom_fields|string|none|
|»» is_system_type|boolean|none|

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
|balance_calculation|query|boolean|false|Include in energy balance calculation|

> Example responses

> 200 Response

```json
null
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

> 404 Response

```json
"string"
```

<h3 id="remove-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Successfully removed sensor|
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
|balance_calculation|query|boolean|false|Include in energy balance calculation|

> Example responses

> 409 Response

```json
"string"
```

<h3 id="create-new-sensor-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
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

> 404 Response

```json
"string"
```

<h3 id="delete-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Removed state for signal|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="delete-sensor-state-for-signal-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Put multiple signals data

<a id="opIdapi_endpoints_sensors_put_signals_data_v2_api_sensors_signals_data_v2_put"></a>

> Code samples

```http
PUT /api/sensors/signals/data/v2 HTTP/1.1

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

r = requests.put('/api/sensors/signals/data/v2', headers = headers)

print(r.json())

```

`PUT /api/sensors/signals/data/v2`

> Body parameter

```json
[
  {
    "data": {},
    "client_cid": 0,
    "sensor_mid": 0,
    "signal_type_moid": 0,
    "unit": "string"
  }
]
```

<h3 id="put-multiple-signals-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[PutMultipleSignalsRequest](#schemaputmultiplesignalsrequest)|true|none|

> Example responses

> 200 Response

```json
null
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

<a id="opIdapi_endpoints_sensors_post_signals_data_v2_api_sensors_signals_data_v2_post"></a>

> Code samples

```http
POST /api/sensors/signals/data/v2 HTTP/1.1

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

r = requests.post('/api/sensors/signals/data/v2', headers = headers)

print(r.json())

```

`POST /api/sensors/signals/data/v2`

> Body parameter

```json
[
  {
    "client_cid": 14,
    "sensor_mid": 10594,
    "signal_type_moid": 451,
    "signal_origin_id": 1,
    "since": 1692333175200,
    "till": 1692343975200,
    "apply_multiplier": false
  }
]
```

<h3 id="get-multiple-signals-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[GetSignalRequest](#schemagetsignalrequest)|true|none|

> Example responses

> 200 Response

```json
[
  {
    "client_cid": 0,
    "sensor_mid": 0,
    "signal_type_moid": 0,
    "unit": "string",
    "time_tstorage": 0,
    "time_other": 0
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

*Response 200 Api Endpoints Sensors Post Signals Data V2 Api Sensors Signals Data V2 Post*

|Name|Type|Description|
|---|---|---|
|Response 200 Api Endpoints Sensors Post Signals Data V2 Api Sensors Signals Data V2 Post|[[SignalResponse](#schemasignalresponse)]|none|
|» SignalResponse|[SignalResponse](#schemasignalresponse)|none|
|»» client_cid|integer|none|
|»» sensor_mid|integer|none|
|»» signal_type_moid|integer|none|
|»» unit|string|none|
|»» time_tstorage|number|none|
|»» time_other|number|none|

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
[
  {
    "signal_type_moid": 0,
    "symbol": "string",
    "description": "string",
    "is_measurement": true,
    "time_series_type": null,
    "apply_multiplier": true,
    "apply_current_ratio": true,
    "apply_voltage_ratio": true,
    "obis_mapping": "string",
    "chart_expected_unit": "string",
    "keep_prefix": true,
    "draw_chart": true,
    "unit_id": 0,
    "unit_symbol": "string",
    "group_id": 0,
    "group": "string",
    "data_model_type": null,
    "chart_expected_summary": [],
    "columns": {},
    "payload_mapping": {}
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

*Response 200 Api Endpoints Sensors Get Signals Types Api Sensors Signals Types Get*

|Name|Type|Description|
|---|---|---|
|Response 200 Api Endpoints Sensors Get Signals Types Api Sensors Signals Types Get|[[SignalTypeResponse](#schemasignaltyperesponse)]|none|
|» SignalTypeResponse|[SignalTypeResponse](#schemasignaltyperesponse)|none|
|»» signal_type_moid|integer|none|
|»» symbol|string|none|
|»» description|string|none|
|»» is_measurement|boolean|none|
|»» time_series_type|any|none|
|»» apply_multiplier|boolean|none|
|»» apply_current_ratio|boolean|none|
|»» apply_voltage_ratio|boolean|none|
|»» obis_mapping|string|none|
|»» chart_expected_unit|string|none|
|»» keep_prefix|boolean|none|
|»» draw_chart|boolean|none|
|»» unit_id|integer|none|
|»» unit_symbol|string|none|
|»» group_id|integer|none|
|»» group|string|none|
|»» data_model_type|any|none|
|»» chart_expected_summary|array|none|
|»»» *anonymous*|any|none|
|»» columns|object|none|
|»» payload_mapping|object|none|

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
[
  {
    "sensor_state_id": 0,
    "client_cid": 0,
    "sensor_mid": 0,
    "since": 0,
    "till": 0,
    "meter_eid": "string",
    "info": "string",
    "meter_type_id": 0,
    "meter_type_name": "string",
    "meter_type_is_ami": true,
    "meter_type_is_dcu": true,
    "signal_states": []
  }
]
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
|Response 200 Api Endpoints Sensors Get States Signals Api Sensors States Signals Get|[[SensorStateResponse](#schemasensorstateresponse)]|none|
|» SensorStateResponse|[SensorStateResponse](#schemasensorstateresponse)|none|
|»» sensor_state_id|integer|none|
|»» client_cid|integer|none|
|»» sensor_mid|integer|none|
|»» since|number|none|
|»» till|number|none|
|»» meter_eid|string|none|
|»» info|string|none|
|»» meter_type_id|integer|none|
|»» meter_type_name|string|none|
|»» meter_type_is_ami|boolean|none|
|»» meter_type_is_dcu|boolean|none|
|»» signal_states|array|none|
|»»» *anonymous*|any|none|

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
|value_for_since|query|number|false|Value for state start|
|value_for_till|query|number|false|Value for state end|
|info|query|string|false|Additional information|

> Example responses

> 404 Response

```json
"string"
```

<h3 id="create-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
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

> 404 Response

```json
"string"
```

<h3 id="delete-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Removed state|
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
[
  {
    "sensor_state_id": 0,
    "client_cid": 0,
    "sensor_mid": 0,
    "since": 0,
    "till": 0,
    "meter_eid": "string",
    "info": "string",
    "meter_type_id": 0,
    "meter_type_name": "string",
    "meter_type_is_ami": true,
    "meter_type_is_dcu": true,
    "signal_states": []
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

*Response 200 Api Endpoints Sensors Get States Api Sensors States Get*

|Name|Type|Description|
|---|---|---|
|Response 200 Api Endpoints Sensors Get States Api Sensors States Get|[[SensorStateResponse](#schemasensorstateresponse)]|none|
|» SensorStateResponse|[SensorStateResponse](#schemasensorstateresponse)|none|
|»» sensor_state_id|integer|none|
|»» client_cid|integer|none|
|»» sensor_mid|integer|none|
|»» since|number|none|
|»» till|number|none|
|»» meter_eid|string|none|
|»» info|string|none|
|»» meter_type_id|integer|none|
|»» meter_type_name|string|none|
|»» meter_type_is_ami|boolean|none|
|»» meter_type_is_dcu|boolean|none|
|»» signal_states|array|none|
|»»» *anonymous*|any|none|

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

> 404 Response

```json
"string"
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

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

## Get signal data

<a id="opIdget_signal_data_api_sensors__client_cid___sensor_mid__signals__signal_type_moid__data_get"></a>

> Code samples

```http
GET /api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data?since=1721667538000&till=1721753938000 HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data', params={
  'since': '1721667538000',  'till': '1721753938000'
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

> 200 Response

```json
{
  "client_cid": 0,
  "sensor_mid": 0,
  "signal_type_moid": 0,
  "unit": "string",
  "time_tstorage": 0,
  "time_other": 0
}
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

<a id="opIdapi_endpoints_sensors_put_id_signals_id_data_v2_api_sensors__client_cid___sensor_mid__signals__signal_type_moid__data_v2_put"></a>

> Code samples

```http
PUT /api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data/v2 HTTP/1.1

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

r = requests.put('/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data/v2', headers = headers)

print(r.json())

```

`PUT /api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data/v2`

> Body parameter

```json
false
```

<h3 id="put-signal-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|signal_type_moid|path|integer|true|Signal type MOID|
|unit|query|string|false|Signal unit|

> Example responses

> 200 Response

```json
null
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
  'Accept': 'application/json'
}

r = requests.post('/api/users/token', headers = headers)

print(r.json())

```

`POST /api/users/token`

Client logs in to the server with login and password. As a result, they receive a token.

> Body parameter

```json
false
```

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

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="besmart-rest-api-weather">Weather</h1>

## Get weather data by geoposition

<a id="opIdapi_endpoints_weather_get_lat_lon_signals_id_data_api_weather__lat___lon___signal_type_moid__data_get"></a>

> Code samples

```http
GET /api/weather/{lat}/{lon}/{signal_type_moid}/data?since=1577836800000&till=1580515200000 HTTP/1.1

Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Auth': 'API_KEY'
}

r = requests.get('/api/weather/{lat}/{lon}/{signal_type_moid}/data', params={
  'since': '1577836800000',  'till': '1580515200000'
}, headers = headers)

print(r.json())

```

`GET /api/weather/{lat}/{lon}/{signal_type_moid}/data`

<h3 id="get-weather-data-by-geoposition-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|lat|path|number|true|Latitude|
|lon|path|number|true|Longitude|
|signal_type_moid|path|integer|true|Signal type MOID|
|since|query|number|true|Start date (UTC unix timestamp)|
|till|query|number|true|End date (UTC unix timestamp)|
|delta_t|query|integer|false|Aggregate time (in minutes)|
|raw|query|boolean|false|Fetch raw signal|
|output_unit_id|query|integer|false|Output unit id|
|signal_origin_id|query|integer|false|Signal origin id|
|is_chart|query|boolean|false|Use expected chart output unit|

> Example responses

> 200 Response

```json
{
  "client_cid": 0,
  "sensor_mid": 0,
  "signal_type_moid": 0,
  "unit": "string",
  "time_tstorage": 0,
  "time_other": 0
}
```

<h3 id="get-weather-data-by-geoposition-responses">Responses</h3>

|Status|Meaning|Description|
|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read weather data|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|

<h3 id="get-weather-data-by-geoposition-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
APIKeyHeader
</aside>

# Schemas

<h2 id="tocS_GetSignalRequest">GetSignalRequest</h2>
<!-- backwards compatibility -->
<a id="schemagetsignalrequest"></a>
<a id="schema_GetSignalRequest"></a>
<a id="tocSgetsignalrequest"></a>
<a id="tocsgetsignalrequest"></a>

```json
{
  "client_cid": 14,
  "sensor_mid": 10594,
  "signal_type_moid": 451,
  "signal_origin_id": 1,
  "since": 1692333175200,
  "till": 1692343975200,
  "apply_multiplier": false
}

```

GetSignalRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|client_cid|integer|true|none|none|
|sensor_mid|integer|true|none|none|
|signal_type_moid|integer|true|none|none|
|signal_origin_id|integer|false|none|none|
|since|integer|true|none|none|
|till|integer|true|none|none|
|apply_multiplier|boolean|false|none|none|
|last_acq|boolean|false|none|none|
|delta_t|integer|false|none|none|
|output_unit_id|integer|false|none|none|

<h2 id="tocS_PutMultipleSignalsRequest">PutMultipleSignalsRequest</h2>
<!-- backwards compatibility -->
<a id="schemaputmultiplesignalsrequest"></a>
<a id="schema_PutMultipleSignalsRequest"></a>
<a id="tocSputmultiplesignalsrequest"></a>
<a id="tocsputmultiplesignalsrequest"></a>

```json
{
  "data": {},
  "client_cid": 0,
  "sensor_mid": 0,
  "signal_type_moid": 0,
  "unit": "string"
}

```

PutMultipleSignalsRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|object|true|none|none|
|client_cid|integer|true|none|none|
|sensor_mid|integer|true|none|none|
|signal_type_moid|integer|true|none|none|
|unit|string|false|none|none|

<h2 id="tocS_SensorStateResponse">SensorStateResponse</h2>
<!-- backwards compatibility -->
<a id="schemasensorstateresponse"></a>
<a id="schema_SensorStateResponse"></a>
<a id="tocSsensorstateresponse"></a>
<a id="tocssensorstateresponse"></a>

```json
{
  "sensor_state_id": 0,
  "client_cid": 0,
  "sensor_mid": 0,
  "since": 0,
  "till": 0,
  "meter_eid": "string",
  "info": "string",
  "meter_type_id": 0,
  "meter_type_name": "string",
  "meter_type_is_ami": true,
  "meter_type_is_dcu": true,
  "signal_states": []
}

```

SensorStateResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|sensor_state_id|integer|false|none|none|
|client_cid|integer|true|none|none|
|sensor_mid|integer|true|none|none|
|since|number|false|none|none|
|till|number|false|none|none|
|meter_eid|string|false|none|none|
|info|string|false|none|none|
|meter_type_id|integer|false|none|none|
|meter_type_name|string|false|none|none|
|meter_type_is_ami|boolean|false|none|none|
|meter_type_is_dcu|boolean|false|none|none|
|signal_states|[[SignalStateDto](#schemasignalstatedto)]|false|none|none|

<h2 id="tocS_SensorTypeResponse">SensorTypeResponse</h2>
<!-- backwards compatibility -->
<a id="schemasensortyperesponse"></a>
<a id="schema_SensorTypeResponse"></a>
<a id="tocSsensortyperesponse"></a>
<a id="tocssensortyperesponse"></a>

```json
{
  "id": 0,
  "name": "string",
  "description": "string",
  "sensor_state_custom_fields": "string",
  "sensor_custom_fields": "string",
  "is_system_type": true
}

```

SensorTypeResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|name|string|true|none|none|
|description|string|true|none|none|
|sensor_state_custom_fields|string|false|none|none|
|sensor_custom_fields|string|false|none|none|
|is_system_type|boolean|true|none|none|

<h2 id="tocS_SignalResponse">SignalResponse</h2>
<!-- backwards compatibility -->
<a id="schemasignalresponse"></a>
<a id="schema_SignalResponse"></a>
<a id="tocSsignalresponse"></a>
<a id="tocssignalresponse"></a>

```json
{
  "client_cid": 0,
  "sensor_mid": 0,
  "signal_type_moid": 0,
  "unit": "string",
  "time_tstorage": 0,
  "time_other": 0
}

```

SignalResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|client_cid|integer|false|none|none|
|sensor_mid|integer|false|none|none|
|signal_type_moid|integer|false|none|none|
|unit|string|false|none|none|
|time_tstorage|number|false|none|none|
|time_other|number|false|none|none|

<h2 id="tocS_SignalTypeResponse">SignalTypeResponse</h2>
<!-- backwards compatibility -->
<a id="schemasignaltyperesponse"></a>
<a id="schema_SignalTypeResponse"></a>
<a id="tocSsignaltyperesponse"></a>
<a id="tocssignaltyperesponse"></a>

```json
{
  "signal_type_moid": 0,
  "symbol": "string",
  "description": "string",
  "is_measurement": true,
  "time_series_type": null,
  "apply_multiplier": true,
  "apply_current_ratio": true,
  "apply_voltage_ratio": true,
  "obis_mapping": "string",
  "chart_expected_unit": "string",
  "keep_prefix": true,
  "draw_chart": true,
  "unit_id": 0,
  "unit_symbol": "string",
  "group_id": 0,
  "group": "string",
  "data_model_type": null,
  "chart_expected_summary": [],
  "columns": {},
  "payload_mapping": {}
}

```

SignalTypeResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|signal_type_moid|integer|true|none|none|
|symbol|string|false|none|none|
|description|string|false|none|none|
|is_measurement|boolean|true|none|none|
|time_series_type|[TimeSeriesType](#schematimeseriestype)|false|none|none|
|apply_multiplier|boolean|false|none|none|
|apply_current_ratio|boolean|false|none|none|
|apply_voltage_ratio|boolean|false|none|none|
|obis_mapping|string|false|none|none|
|chart_expected_unit|string|false|none|none|
|keep_prefix|boolean|false|none|none|
|draw_chart|boolean|false|none|none|
|unit_id|integer|false|none|none|
|unit_symbol|string|false|none|none|
|group_id|integer|false|none|none|
|group|string|false|none|none|
|data_model_type|[DataModelType](#schemadatamodeltype)|false|none|none|
|chart_expected_summary|[[ChartExpectedSummary](#schemachartexpectedsummary)]|false|none|none|
|columns|object|false|none|none|
|payload_mapping|object|false|none|none|

