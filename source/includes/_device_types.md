# DeviceTypes

## Get All Device Types

```ruby

```

```shell
curl "https://bild-devicesapi-test.herokuapp.com/api/device_types"
```

> The above command returns JSON structured like this:

```json
{
    "device_types": [
        {
            "id": 1,
            "name": "PC",
            "subtypes": [
                {
                    "id": 2,
                    "name": "NoteBook",
                    "subtypes": [
                        {
                            "id": 4,
                            "name": "2in1 Laptop"
                        }
                    ]
                },
                {
                    "id": 3,
                    "name": "NetBook"
                }
            ]
        },
        {
            "id": 5,
            "name": "Speakers",
            "subtypes": []
        },
    ]
}
```

This endpoint retrieves all device types nested hierarchically.

### HTTP Request

<div class="get-verb">GET</div>`https://bild-devicesapi-test.herokuapp.com/api/device_types`

## Get a Specific Device Type

```ruby

```

```shell
curl "https://bild-devicesapi-test.herokuapp.com/api/device_types/:id"
```

> The above command returns JSON structured like this:

```json
{
    "device_type": {
        "id": 1,
        "name": "PC",
        "properties": [
            {
                "device_type_id": 1,
                "name": "RAM"
            },
            {
                "device_type_id": 1,
                "name": "CPU"
            },
            {
                "device_type_id": 1,
                "name": "OS"
            },
            {
                "device_type_id": 1,
                "name": "GPU"
            },
            {
                "device_type_id": 1,
                "name": "PSU"
            },
            {
                "device_type_id": 1,
                "name": "MOBO"
            }
        ]
    }
}
```

This endpoint retrieves a specific device type with its associated properties

### HTTP Request

<div class="get-verb">GET</div> `https://bild-devicesapi-test.herokuapp.com/api/device_types/:id`

### URL Parameters

Parameter | Description 
--------- | -----------  
id | The id of the device type to retrieve 


## Create a Specific Device Type

```ruby

```

```shell
curl -H "Content-Type: application/json" \
  --request POST \
  -d '{"request body here"}' \
  https://bild-devicesapi-test.herokuapp.com/api/device_types

```

> Request body should look like this

```json
{
	"device_type": {
		"name": "TypeName",
		"device_type_properties_attributes": [
			{"name": "type_property1"},
            {"name": "type_property2"},
            ...	
		]
	}
}
```
> The above command returns JSON structured like this:

```json
{
    "status": "Created",
    "device_type": {
        "id": 0,
        "name": "TypeName",
        "properties": [
            {
                "device_type_id": 0,
                "name": "type_property1"
            },
            {
                "device_type_id": 0,
                "name": "type_property2"
            },
            ...
        ]
    }
}
```

This endpoint creates a specific device type.

### HTTP Request

<div class="post-verb">POST</div> `https://bild-devicesapi-test.herokuapp.com/api/device_types`


### Body required

* device type is required while device_type_property_attributes are optional.
* with device_type_properties_attributes it's possible to assign properties
to device type properties in same request.


## Update a Specific Device

```ruby

```

```shell
curl -H "Content-Type: application/json" \
  --request POST \
  -d '{"request body here"}' \
  https://bild-devicesapi-test.herokuapp.com/api/device_types/:id

```

> Request body should look like this

```json
{
	"device_type": {
		"name": "NewTypeName",
		"device_type_properties_attributes": [
			{"name": "new_name"},
            ...	
		]
	}
}
```

> The above command returns JSON structured like this:

```json
{
    "status": "Updated",
    "device_type": {
        "id": 0,
        "name": "NewTypeName",
        "properties": [
            {
                "device_type_id": 0,
                "name": "new_name"
            },
            {
                "device_type_id": 0,
                "name": "type_property2"
            },
            ...
        ]
    }
}
```

This endpoint updates a specific device type.

### HTTP Request:

<div class="put-verb">PUT</div>`https://bild-devicesapi-test.herokuapp.com/api/device_types/:id`


### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the device to update

### Body Required

## Delete a Specific Device

```ruby

```

```shell
curl "https://bild-devicesapi-test.herokuapp.com/api/device_types/:id"
  -X DELETE
```

> The above command returns JSON structured like this:

```json
{
  "status": "Deleted",
  "id": 0,
  "name": "DeviceTypeName"
}
```

This endpoint deletes a specific device type.

### HTTP Request

<div class="delete-verb">DELETE</div> `https://bild-devicesapi-test.herokuapp.com/api/device_types/:id`
