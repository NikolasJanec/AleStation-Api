# AleStation-Api

## Endpoints

**POST /v1/devices/**

```json
{
  "uuid": "<uuid>",
  "location": {
    "latitude": "<lat>",
    "longitude": "<lon>"
  },
  "owner": "<owner>",
  "description": "<description>",
  "sensors": [
    {
    "label": "TEPLOTA_KUCHYNA",
    "unit": "TEMPERATURE",
    "part": "ER_SEN8888888"
    },
    {
    "label": "TEPLOTA_IZBA",
    "unit": "TEMPERATURE",
    "part": "ER_SEN8888888"
    }
  ]
}
```

**POST /v1/devices/<:device_uuid>/records/**

```json
{
  "values": [
    {
      "sensor": "TEPLOTA_IZBA",
      "value": 32545.23423
    },
    {
      "sensor": "TEPLOTA_KUCHYNA",
      "value": 42.42
    }
  ]
}
```

**GET /v1/devices/**

|Parameter|Description|Default|
|---|---|---|
|query|Search for device using LIKE CONCAT(UUID,OWNER,DESCRIPTION)|`NULL`|
|owner|Search using owner|`NULL`|
|description|Search using description|`NULL`|
|uuid|Search using uuid|`NULL`|


```json
{
  "items": [
    {
      "id": 1
      "uuid": "<uuid>",
      "location": {
        "latitude": "<lat>",
        "longitude": "<lon>"
      },
      "owner": "<owner>",
      "description": "<description>",
      "sensors": [
        {
        "label": "TEPLOTA_KUCHYNA",
        "unit": "TEMPERATURE",
        "part": "ER_SEN8888888"
        },
        {
        "label": "TEPLOTA_IZBA",
        "unit": "TEMPERATURE",
        "part": "ER_SEN8888888"
        }
      ],
      "created_at": "2017-02-25T11:52:39+01:00",
      "updated_at": "2017-02-25T11:52:39+01:00",
      "last_sync_at": "2017-02-25T11:52:39+01:00"
    }
  ]
}
```

**GET /v1/devices/<device_id>/records**

|Parameter|Description|Default|
|---|---|---|
|date_from|Select only records from this date|`NULL`|
|date_to|Select only records until this date|`NULL`|

```json
{
  "items": [
    {
      "device": "<DEVICE_UUID>",
      "happened_at": "2017-02-25T11:52:39+01:00",
      "values": [
        {
          "sensor": "TEPLOTA_IZBA",
          "value": 32545.23423,
          "happened_at": "2017-02-25T11:52:39+00:59"
        },
        {
          "sensor": "TEPLOTA_KUCHYNA",
          "value": 42.42,
          "happened_at": "2017-02-25T11:52:39+00:58"
        }
      ]
    }
  ]
}
```
