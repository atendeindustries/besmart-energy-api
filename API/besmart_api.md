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
'{ "login": "login", "password": "password" }'

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

## Create new workspace

<a id="opIdapi.endpoints.workspaces.post"></a>

> Code samples

```http
POST https://api.besmart.energy/api/workspaces?name=My%20workspace HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/workspaces', params={
  'name': 'My workspace'
}, headers = headers)

print(r.json())

```

`POST /workspaces`

<h3 id="create-new-workspace-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|name|query|string|true|Name of the workspace|

> Example responses

> 201 Response

```json
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
```

<h3 id="create-new-workspace-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created workspace|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|

<h3 id="create-new-workspace-responseschema">Response Schema</h3>

Status Code **201**

*Model containing workspace info*

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

## Remove workspace

<a id="opIdapi.endpoints.workspaces.delete_id"></a>

> Code samples

```http
DELETE https://api.besmart.energy/api/workspaces/{id} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.besmart.energy/api/workspaces/{id}', headers = headers)

print(r.json())

```

`DELETE /workspaces/{id}`

<h3 id="remove-workspace-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer|true|Workspace ID|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="remove-workspace-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully removed workspace|string|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|None|

<h3 id="remove-workspace-responseschema">Response Schema</h3>

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

## Get workspace tree

<a id="opIdapi.endpoints.workspaces.get_id_tree"></a>

> Code samples

```http
GET https://api.besmart.energy/api/workspaces/tree HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/workspaces/tree', headers = headers)

print(r.json())

```

`GET /workspaces/tree`

<h3 id="get-workspace-tree-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|parent_id|query|integer|false|Workspace parent node ID, should be empty or null if root is needed|
|search|query|string|false|Search term|
|offset|query|integer|false|Offset (records)|
|limit|query|integer|false|Limit (records)|
|child_id|query|integer|false|Child ID to find and load in tree|

> Example responses

> 200 Response

```json
{
  "children": [],
  "children_num": 0,
  "more_children": false
}
```

<h3 id="get-workspace-tree-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read workspace information|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|

<h3 id="get-workspace-tree-responseschema">Response Schema</h3>

Status Code **200**

*Workspace subtree data*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» children|array|false|none|none|
|» children_num|integer|false|none|none|
|» more_children|boolean|false|none|none|

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

## Create workspace tree node

<a id="opIdapi.endpoints.workspaces.post_id_tree"></a>

> Code samples

```http
POST https://api.besmart.energy/api/workspaces/tree?client_cid=1&sensor_mid=1&parent_id=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/workspaces/tree', params={
  'client_cid': '1',  'sensor_mid': '1',  'parent_id': '1'
}, headers = headers)

print(r.json())

```

`POST /workspaces/tree`

<h3 id="create-workspace-tree-node-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|true|Sensor client CID|
|sensor_mid|query|integer|true|Sensor MID|
|parent_id|query|integer|true|Workspace tree parent node ID|

> Example responses

> 200 Response

```json
{
  "id": 585540
}
```

<h3 id="create-workspace-tree-node-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully created workspace tree node|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|

<h3 id="create-workspace-tree-node-responseschema">Response Schema</h3>

Status Code **200**

*UID number*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|

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

## Update workspace tree node position

<a id="opIdapi.endpoints.workspaces.put_id_tree"></a>

> Code samples

```http
PUT https://api.besmart.energy/api/workspaces/tree?node_id=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/workspaces/tree', params={
  'node_id': '1'
}, headers = headers)

print(r.json())

```

`PUT /workspaces/tree`

<h3 id="update-workspace-tree-node-position-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|node_id|query|integer|true|Workspace tree node ID|
|new_parent_id|query|integer|false|Workspace tree new parent node ID|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="update-workspace-tree-node-position-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated workspace tree node position|string|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|None|

<h3 id="update-workspace-tree-node-position-responseschema">Response Schema</h3>

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

## Remove workspace tree node

<a id="opIdapi.endpoints.workspaces.delete_id_tree"></a>

> Code samples

```http
DELETE https://api.besmart.energy/api/workspaces/tree?node_id=1 HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.besmart.energy/api/workspaces/tree', params={
  'node_id': '1'
}, headers = headers)

print(r.json())

```

`DELETE /workspaces/tree`

<h3 id="remove-workspace-tree-node-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|node_id|query|integer|true|Workspace tree node ID|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="remove-workspace-tree-node-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully removed workspace tree node|string|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|None|

<h3 id="remove-workspace-tree-node-responseschema">Response Schema</h3>

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

## Get workspace tree node

<a id="opIdapi.endpoints.workspaces.get_id_tree_node_id"></a>

> Code samples

```http
GET https://api.besmart.energy/api/workspaces/tree/{node_id} HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/workspaces/tree/{node_id}', headers = headers)

print(r.json())

```

`GET /workspaces/tree/{node_id}`

<h3 id="get-workspace-tree-node-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|node_id|path|integer|true|Workspace node ID|

> Example responses

> 200 Response

```json
{
  "children_num": 0,
  "more_children": false,
  "name": "None",
  "client_cid": 12,
  "sensor_mid": 582029,
  "sensor_type_id": 12,
  "uid": 585541
}
```

<h3 id="get-workspace-tree-node-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read workspace node information|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|None|

<h3 id="get-workspace-tree-node-responseschema">Response Schema</h3>

Status Code **200**

*Workspace node data*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» children_num|integer|false|none|none|
|» more_children|boolean|false|none|none|
|» name|string|false|none|none|
|» client_cid|integer|false|none|none|
|» sensor_mid|integer|false|none|none|
|» sensor_type_id|integer|false|none|none|
|» uid|integer|false|none|none|

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

## Create new sensor

<a id="opIdapi.endpoints.sensors.post"></a>

> Code samples

```http
POST https://api.besmart.energy/api/sensors?name=Electric%20meter%20no%20123 HTTP/1.1
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
  'name': 'Electric meter no 123'
}, headers = headers)

print(r.json())

```

`POST /sensors`

<h3 id="create-new-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|name|query|string|true|Name of the sensor|
|sensor_type_id|query|integer|false|Sensor type ID|
|client_cid|query|integer|false|Client CID|
|uncertain|query|boolean|false|none|

> Example responses

> 201 Response

```json
{
  "id": 12
}
```

<h3 id="create-new-sensor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created sensor|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|

<h3 id="create-new-sensor-responseschema">Response Schema</h3>

Status Code **201**

*Created sensor ID*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|

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
|meter_eid|query|string|false|Current meter serial number|
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
    "comments": "Licznik do likwidacji.",
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
|» comments|string|false|none|none|
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
'["1", "ex12"]'

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
    "comments": "Licznik do likwidacji.",
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
|» comments|string|false|none|none|
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

> Example responses

> 200 Response

```json
[
  {
    "description": "Wirtualny",
    "id": 1,
    "name": "virtual"
  }
]
```

<h3 id="get-list-of-sensor-types-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read sensor types|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Valid authentication credentials|Inline|

<h3 id="get-list-of-sensor-types-responseschema">Response Schema</h3>

Status Code **200**

*List of sensor types*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» description|string|false|none|none|
|» id|integer|false|none|none|
|» name|string|false|none|none|

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

## Get list of meter types

<a id="opIdapi.endpoints.sensors.get_meters"></a>

> Code samples

```http
GET https://api.besmart.energy/api/sensors/meters HTTP/1.1
Host: api.besmart.energy
Accept: application/json

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.besmart.energy/api/sensors/meters', headers = headers)

print(r.json())

```

`GET /sensors/meters`

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "meter_type_name": "string",
    "description": "string",
    "number_of_phases": 0,
    "is_balance": true,
    "is_ami": "string"
  }
]
```

<h3 id="get-list-of-meter-types-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read meter types|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Valid authentication credentials|Inline|

<h3 id="get-list-of-meter-types-responseschema">Response Schema</h3>

Status Code **200**

*List of meter types*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» meter_type_name|string|false|none|none|
|» description|string|false|none|none|
|» number_of_phases|integer|false|none|none|
|» is_balance|boolean|false|none|none|
|» is_ami|string|false|none|none|

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

<h3 id="get-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|

> Example responses

> 200 Response

```json
{
  "address_city": "Warszawa",
  "address_flat_number": "35",
  "address_postcode": "00-020",
  "address_street": "Wiejska",
  "address_street_number": "36",
  "comments": "Licznik do likwidacji.",
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
```

<h3 id="get-sensor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read sensor information|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Not valid id|string|

<h3 id="get-sensor-responseschema">Response Schema</h3>

Status Code **200**

*Model containing sensor information*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» address_city|string|false|none|none|
|» address_flat_number|string|false|none|none|
|» address_postcode|string|false|none|none|
|» address_street|string|false|none|none|
|» address_street_number|string|false|none|none|
|» comments|string|false|none|none|
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

<h3 id="update-sensor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|name|query|string|false|Name of the sensor|
|sensor_type_id|query|integer|false|Sensor type ID|
|ppe|query|string|false|PPE|
|sensor_eid|query|string|false|Sensor external ID|
|lat|query|number|false|Sensor latitude|
|lon|query|number|false|Sensor longitude|
|address_city|query|string|false|Address city|
|address_postcode|query|string|false|Address city postcode|
|address_street|query|string|false|Address street name|
|address_street_number|query|string|false|Address street number|
|address_flat_number|query|string|false|Address flat number|
|comments|query|string|false|Comments|
|uncertain|query|boolean|false|none|
|negligible|query|boolean|false|none|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="update-sensor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated sensor|string|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Not valid id|string|

<h3 id="update-sensor-responseschema">Response Schema</h3>

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

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully removed sensor|string|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Not valid id|string|

<h3 id="remove-sensor-responseschema">Response Schema</h3>

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
    "obis_mapping": "None"
  }
]
```

<h3 id="get-signals-types-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals types|Inline|

<h3 id="get-signals-types-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» signal_type_moid|string|false|none|none|
|» symbol|string|false|none|none|
|» is_incremental|boolean|false|none|none|
|» description|string|false|none|none|
|» unit_id|integer|false|none|none|
|» unit_symbol|string|false|none|none|
|» group_id|integer|false|none|none|
|» group|string|false|none|none|
|» obis_mapping|string|false|none|none|

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
    "sensor_state_id": 0,
    "client_cid": 0,
    "sensor_mid": 0,
    "signal_states": [
      {
        "signal_state_id": 0,
        "signal_type_moid": 0,
        "value_for_since": 0,
        "value_for_till": 0,
        "info": "string"
      }
    ],
    "since": 0,
    "till": 0,
    "meter_eid": "string",
    "info": "string",
    "meter_type_name": "string",
    "meter_type_is_ami": true
  }
]
```

<h3 id="get-sensor-states-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals states|Inline|

<h3 id="get-sensor-states-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sensor_state_id|integer|false|none|none|
|» client_cid|integer|false|none|none|
|» sensor_mid|integer|false|none|none|
|» signal_states|[object]|false|none|none|
|»» signal_state_id|integer|false|none|none|
|»» signal_type_moid|integer|false|none|none|
|»» value_for_since|number|false|none|none|
|»» value_for_till|number|false|none|none|
|»» info|string|false|none|none|
|» since|integer|false|none|none|
|» till|integer|false|none|none|
|» meter_eid|string|false|none|none|
|» info|string|false|none|none|
|» meter_type_name|string|false|none|none|
|» meter_type_is_ami|boolean|false|none|none|

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

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/sensors/states', params={
  'client_cid': '1',  'sensor_mid': '1',  'since': '1577836800000'
}, headers = headers)

print(r.json())

```

`POST /sensors/states`

<h3 id="create-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|query|integer|true|Client CID|
|sensor_mid|query|integer|true|Sensor MID|
|since|query|number|true|Start date (UTC unix timestamp)|
|till|query|number|false|End date (UTC unix timestamp)|
|info|query|string|false|Additional informations|
|meter_eid|query|string|false|Meter external ID|
|meter_type_name|query|string|false|Meter type name|

<h3 id="create-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created state|None|

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

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/sensors/states/{sensor_state_id}', headers = headers)

print(r.json())

```

`PUT /sensors/states/{sensor_state_id}`

<h3 id="update-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|
|since|query|integer|false|Start date (UTC unix timestamp)|
|till|query|integer|false|End date (UTC unix timestamp)|
|info|query|string|false|Additional informations|
|meter_eid|query|string|false|Meter external ID|
|meter_type_name|query|string|false|Meter type name|

<h3 id="update-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Updated state|None|

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

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.besmart.energy/api/sensors/states/{sensor_state_id}', headers = headers)

print(r.json())

```

`DELETE /sensors/states/{sensor_state_id}`

<h3 id="delete-sensor-state-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|

<h3 id="delete-sensor-state-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Removed state|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Create sensor state for signal

<a id="opIdapi.endpoints.sensors.post_states_id_signals"></a>

> Code samples

```http
POST https://api.besmart.energy/api/sensors/states/{sensor_state_id}/signals?signal_type_moid=1 HTTP/1.1
Host: api.besmart.energy

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.besmart.energy/api/sensors/states/{sensor_state_id}/signals', params={
  'signal_type_moid': '1'
}, headers = headers)

print(r.json())

```

`POST /sensors/states/{sensor_state_id}/signals`

<h3 id="create-sensor-state-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sensor_state_id|path|integer|true|State ID|
|signal_type_moid|query|integer|true|Signal type moid|
|value_for_since|query|string|false|Value for state start|
|value_for_till|query|string|false|Value for state end|
|info|query|string|false|Additional informations|

<h3 id="create-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successfully created state for signal|None|

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
    "sensor_state_id": 0,
    "client_cid": 0,
    "sensor_mid": 0,
    "signal_states": [
      {
        "signal_state_id": 0,
        "signal_type_moid": 0,
        "value_for_since": 0,
        "value_for_till": 0,
        "info": "string"
      }
    ],
    "since": 0,
    "till": 0,
    "meter_eid": "string",
    "info": "string",
    "meter_type_name": "string",
    "meter_type_is_ami": true
  }
]
```

<h3 id="get-sensor-states-for-signal-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully read signals states for signal|Inline|

<h3 id="get-sensor-states-for-signal-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sensor_state_id|integer|false|none|none|
|» client_cid|integer|false|none|none|
|» sensor_mid|integer|false|none|none|
|» signal_states|[object]|false|none|none|
|»» signal_state_id|integer|false|none|none|
|»» signal_type_moid|integer|false|none|none|
|»» value_for_since|number|false|none|none|
|»» value_for_till|number|false|none|none|
|»» info|string|false|none|none|
|» since|integer|false|none|none|
|» till|integer|false|none|none|
|» meter_eid|string|false|none|none|
|» info|string|false|none|none|
|» meter_type_name|string|false|none|none|
|» meter_type_is_ami|boolean|false|none|none|

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

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://api.besmart.energy/api/sensors/states/signals/{signal_state_id}', headers = headers)

print(r.json())

```

`PUT /sensors/states/signals/{signal_state_id}`

<h3 id="update-sensor-state-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|signal_state_id|path|integer|true|Signal state ID|
|value_for_since|query|string|false|Value for state start|
|value_for_till|query|string|false|Value for state end|
|info|query|string|false|Additional informations|

<h3 id="update-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Updated state for signal|None|

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

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.besmart.energy/api/sensors/states/signals/{signal_state_id}', headers = headers)

print(r.json())

```

`DELETE /sensors/states/signals/{signal_state_id}`

<h3 id="delete-sensor-state-for-signal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|signal_state_id|path|integer|true|Signal state ID|

<h3 id="delete-sensor-state-for-signal-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Removed state for signal|None|

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
|since|query|number|true|Start date (UTC unix timestamp)|
|till|query|number|true|End date (UTC unix timestamp)|
|get_last|query|boolean|false|Get only records with newest acq time for the same cap times|
|delta_t|query|integer|false|Aggregate time (in minutes)|
|raw|query|boolean|false|Fetch raw signal|
|output_unit_id|query|integer|false|Output unit id|
|signal_origin_id|query|integer|false|Signal origin id|
|filters|query|string|false|Data filters for complex stuctures|
|is_chart|query|bool|false|Use expected chart output unit|

> Example responses

> 200 Response

```json
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
|» data|object|false|none|none|
|»» time|[integer]|false|none|none|
|»» value|[oneOf]|false|none|none|

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
|»» type|[string]|false|none|none|
|»» origin|[integer]|false|none|none|
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

## Put signal data

<a id="opIdapi.endpoints.sensors.put_id_signals_id_data"></a>

> Code samples

```http
PUT https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data HTTP/1.1
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

r = requests.put('https://api.besmart.energy/api/sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data', headers = headers)

print(r.json())

```

`PUT /sensors/{client_cid}.{sensor_mid}/signals/{signal_type_moid}/data`

> Body parameter

```
'{ "origin": [1], "time": [1609455600000], "type": ["DBL"], "value": [10.02] }'

```

<h3 id="put-signal-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|client_cid|path|integer|true|Client CID|
|sensor_mid|path|integer|true|Sensor MID|
|signal_type_moid|path|integer|true|Signal type MOID|
|body|body|string|true|none|

> Example responses

> 200 Response

```json
"OK"
```

<h3 id="put-signal-data-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully updated signal data|string|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not valid authentication credentials|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Failed attempt - no resource|None|

<h3 id="put-signal-data-responseschema">Response Schema</h3>

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

