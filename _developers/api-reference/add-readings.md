---
title: Add Readings
subtitle: 
# author: sara
tags: [api]
videos: 
    - title: Generate API-Key
      url: https://youtu.be/_OhSTyVSCSM
    - title: Using Postman for API testing
      url: https://youtu.be/-RYkapHBVs8
---
#### Description 
Add Reading API allows to insert readings related to specific data-source.

[View in postman](https://apidocs.zira.us/#d87591b7-336e-4ab1-9791-5c6a4b143ad5)

**POST** `https://api.zira.us/public/reading/named/`
#### Example payload

```json
[{
	"meterId":"4080", 
	"timestamp": "2021-04-09T05:44:20",
	"values": [{ "temperature":"123", "humidity":"456" }]
}]

```

#### Properties

| Property  | Required | Type   | Example                                               | Description                                                                                                    |
| --------- | -------- | ------ | ----------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| meterId   | true     | String | `"123"`                                               | Zira data-source id.  can be copied from Zira UI or fetched programmatically using `Get Data-Source` API       |
| timestamp | true     | String | `"2021-01-21T19:32:00"`                               | Date-time of the reading using ISO 8601 standard  Reading will appear on zira using the site timezone          |
| values    | true     | Object | `[{  "temperature" : "123" ,  "humidity" : "456"  }]` | the key names are the metric ids copied from Zira UI or fetched programmatically using  `Get Data-Source`  API |