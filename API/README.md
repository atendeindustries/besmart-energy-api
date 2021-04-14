# Introduction to besmart.energy API

The **besmart.energy** platform provides customers with API functionalities based on the REST architecture. For this purpose, it uses the HTTP protocol with its methods: GET, POST, PUT, DELETE. The elements of the **besmart.energy** platform have been divided into groups of endpoints, e.g. Users, Workspaces, Sensors, Signals, in which access to individual endpoints takes place by calling the selected HTTP method to the address: [https://api.besmart.energy](https://api.besmart.energy), adding the path to the selected endpoint, e.g. [https://api.besmart.energy/api/workspaces](https://api.besmart.energy/api/workspaces).

## HTTP methods
API endpoints can use the following HTTP methods:

- GET: used to retrieve data, all GET methods can be called multiple times as they do not modify any **besmart.energy** resources,
- POST: used to create a new resource (e.g. create a new sensor),
- PUT: used for editing the resource (e.g. editing the sensor description),
- DELETE: used to delete resources.

## Communication protocol

Access to the REST API is done through an HTTPS connection to the [api.besmart.energy](https://api.besmart.energy) server. All data sent and received from the server is in JSON format.

    $ curl -i https://api.besmart.energy
    
    HTTP/1.1 404 NOT FOUND
    Server: nginx/1.10.3
    Date: Wed, 14 Apr 2021 09:15:07 GMT
    Content-Type: application/problem+json
    Content-Length: 206
    Access-Control-Allow-Origin: *
    
    {
      "detail": "The requested URL was not found on the server.  If you entered the URL manually please check your spelling and try again.",
      "status": 404,
      "title": "Not Found",
      "type": "about:blank"
    }

## Data representation (JSON)

Almost all data is sent and received from the API in JSON format. The basic element of this format is the field whose name is separated from the field value by a colon. Fields are separated by a comma. The next element is a JSON object, enclosed in curly braces. Arrays in JSON format are saved with square brackets. Empty fields (with null value) are always attached to the response - they are not hidden.

## Manipulating metering data

All metering data related to power or energy is represented as a double number in kW or kWh.

Timestamps for metering data are represented in UNIX time format with millisecond precision (it is possible to pass higher precision after the decimal point).

In addition, each measurement data is marked with the 'origin' flag, which signifies the origin of the data:
- '1' - means measured real data
- '2' - means the predicted data
- '3' - means calculated data

Therefore, the JSON structure representing a single measurement data has the following format, e.g .:

    {
         "origin": 1,
         "time": 1609470000000,
         "type": "DBL",
         "value": 3.50
       }

which means:
- measured real data,
- timestamp for Friday, January 1, 2021 03\:00\:00 UTC time (Friday, January 1, 2021 04\:00\:00 GMT + 01\:00 local winter time in Poland),
- with a value of 3.50 of type double.

In a special case, the PUT method can be used both for entering new data and for 'deleting' (marking data as deleted) of existing data.

So the structure:

    {
         "origin": 1,
         "time": 1609470000000,
         "type": "DBL",
         "value": 3.50
       }

can be used to enter new data into the database, while:

    {
         "origin": 1,
         "time": 1609470000000,
         "type": "RM"
       }

it will mean marking data as 'deleted' (special meaning of "type" tag with "RM" = remove).
