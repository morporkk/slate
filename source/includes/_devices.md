# Devices

## Get All Devices

```ruby

```

```shell
curl "https://bild-devicesapi-test.herokuapp.com/api/devices"
```

> The above command returns JSON structured like this:

```json
{
    "device": [
        {
            "id": 1,
            "name": "Dell Tower",
            "type": "PC"
        },
        {
            "id": 2,
            "name": "Lenovo x789",
            "type": "NoteBook"
        },
        ...
    ]
}
```

This endpoint retrieves all devices.

### HTTP Request

<div class="get-verb">GET</div>`https://bild-devicesapi-test.herokuapp.com/api/devices`

### URL Parameters

Parameter | Description 
--------- | ----------- 
name      | Response will contain devices that have param value in name
type_id   | Response will contain devices that have given device_type_id  
type      | Response will contain devices that have {param} type name 
month     | Response will contain devices created/updated in last {param} month/s
day       | Response will contain devices created/updated in last {param} day/s
hour      | Response will contain devices created/updated in last {param} hour/s


### Example
`/api/devices?name=hp&type=PC&month=2`
will return all devices that containt `hp` in name, have type name `PC` and are newer than 2 months.

Note that while `name` is case insensitive, `type` isn't.

## Get a Specific Device

```ruby

```

```shell
curl "https://bild-devicesapi-test.herokuapp.com/api/devices/:id"
```

> The above command returns JSON structured like this:

```json
{
    "device": {
        "id": 1,
        "name": "Dell Tower",
        "device_type": {
            "device_type_id": 1,
            "type_name": "PC"
          },
        "properties": [
            {
                "name": "RAM",
                "value": "16GB"
            },
            {
                "name": "CPU",
                "value": "Ryzen7 1700"
            },
            {
                "name": "OS",
                "value": "Windows10"
            },
            {
                "name": "GPU",
                "value": "gtx1080"
            },
            {
                "name": "PSU",
                "value": "550W"
            },
            {
                "name": "MOBO",
                "value": "b350m"
            }
        ]
    }
}
```

This endpoint retrieves a specific device with its associated properties

### HTTP Request

<div class="get-verb">GET</div> `https://bild-devicesapi-test.herokuapp.com/api/devices/:id`

### URL Parameters

Parameter | Description 
--------- | -----------  
id | The id of the device to retrieve 


## Create a Specific Device

```ruby

```

```shell
curl -H "Content-Type: application/json" \
  --request POST \
  -d '{"request body here"}' \
  https://bild-devicesapi-test.herokuapp.com/api/devices

```

> Request body should look like this

```json
{
    "device": {
        "name": "Device-name",
        "device_type_id": 1,
        "device_property_values_attributes": [
            { "device_type_property_id": 1, "value": "value1" },
            { "device_type_property_id": 2, "value": "value2" },
            { "device_type_property_id": 3, "value": "value3" },
                  ...
        ]
    }
}
```
> The above command returns JSON structured like this:

```json
{
    "status" "Created",
    "device": {
        "id": 0,
        "name": "Device-name",
        "type": "DeviceType-name",
        "properties": [
            {
                "name": "property1",
                "value": "value1"
            },
            {
                "name": "property2",
                "value": "value2"
            },
            {
                "name": "property3",
                "value": "value3"
            },
            ...
        ]
    }
}
```

This endpoint creates a specific device.

### HTTP Request

<div class="post-verb">POST</div> `https://bild-devicesapi-test.herokuapp.com/api/devices`


### Body required

* device is required while device_property_values_attributes are optional.
* with device_property_values_attributes it's possible to assign values
to device properties in same request.
* Invalid properties will be ignored.

## Update a Specific Device

```ruby

```

```shell
curl -H "Content-Type: application/json" \
  --request POST \
  -d '{"request body here"}' \
  https://bild-devicesapi-test.herokuapp.com/api/devices/:id

```

> Request body should look like this

```json
{
	  "device": {
        "name": "NewName",
        "device_type_id": 1,
        "device_property_values_attributes": [
            {"device_type_property_id": 1, "value": "New-value1"},
            {"device_type_property_id": 2, "value": "value2"},
            {"device_type_property_id": 3, "value": "value3"},
            ...    
        ],
	  }
}
```

> The above command returns JSON structured like this:

```json
{
    "status": "Updated",
    "device": {
        "id": 0,
        "name": "NewName",
        "device_type": {
            "device_type_id": 1,
            "type_name": "PC"
        },
        "properties": [
            {
                "name": "property1",
                "value": "New-value1"
            },
            ...
        ]
    }
}
```

This endpoint updates a specific device.

### HTTP Request:

<div class="put-verb">PUT</div>`https://bild-devicesapi-test.herokuapp.com/api/devices/:id`


### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the device to update

### Body Required

## Delete a Specific Device

```ruby

```

```shell
curl "https://bild-devicesapi-test.herokuapp.com/api/devices:id"
  -X DELETE
```

> The above command returns JSON structured like this:

```json
{
    "status": "Deleted",
    "id": 0,
    "name": "DeviceName"
}
```

This endpoint deletes a specific device.

### HTTP Request

<div class="delete-verb">DELETE</div> `https://bild-devicesapi-test.herokuapp.com/api/devices/:id`
