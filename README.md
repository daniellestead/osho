# Device API 

## Requirements

Create an API that tracks configuration state(s) of IoT connected devices.

1. An HTTP GET endpoint that retrieves current configuration and a number of previous configurations.
2. An HTTP POST endpoint that updates the stored configuration either partially or completely.
3. A way of de-duplicating multiple instances of configuration if there is a race condition.

## Considerations

- 

## How to use 

The JSON data for each device is fairly basic and looks something like this:
```json
{
  "id": "123",
  "name": "lights",
  "status": "off",
  "lastUpdated": "2022-10-25 13:03:58"
}
```
To run the service locally at http://localhost:8080/:

```./gradlew bootRun```

The endpoints available are `getDevice` and `updateDevice`. 

### getDevice

Takes device ID and an optional states parameter and will return the configuration state for the device, as well as previous states if the `states` parameter is set.
I.e

```http://localhost:8080/getDevice?id=123&states=2```

will return the most recent 2 states for device ID: 123.

### updateDevice

This endpoint takes a JSON body 
