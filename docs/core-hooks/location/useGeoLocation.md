---
title: useGeoLocation
description: A custom hook to track the user's geolocation with retry functionality.
---

# useGeoLocation
`useGeoLocation` is a custom hook to track the user's geolocation with retry functionality.

## Usage

```javascript
import { useGeoLocation } from "./useGeoLocation";

export default function GeoLocationExample() {
  const { loading, error, coords } = useGeoLocation({ enableHighAccuracy: true });

  if (loading) return <p>Fetching location...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <p>
      Latitude: {coords?.latitude}, Longitude: {coords?.longitude}
    </p>
  );
}
```

## API Reference

### Parameters

| Parameter         | Type      | Default  | Description |
|------------------|----------|----------|-------------|
| `enableHighAccuracy` | `boolean`  | `false`  | Requests the most accurate location possible. |
| `maximumAge`     | `number`  | `0`       | Maximum age (in milliseconds) of a cached position before a fresh one is requested. |
| `timeout`        | `number`  | `10000`   | Maximum time (in milliseconds) to wait for a position. |
| `retryLimit`     | `number`  | `3`       | Maximum number of retry attempts in case of failure. |
| `retryDelay`     | `number`  | `2000`    | Delay (in milliseconds) between retries. |

### Behavior

- Fetches the user's geolocation using `navigator.geolocation.watchPosition()`.
- Automatically retries fetching the location if it fails, up to the `retryLimit`.
- Returns the latest available coordinates.
- Clears the geolocation watch when the component unmounts.

### Return Value

`useGeoLocation` returns an object containing:

| Property  | Type                        | Description |
|-----------|-----------------------------|-------------|
| `loading` | `boolean`                    | `true` if location is being fetched, otherwise `false`. |
| `error`   | `{ code: number; message: string } \| null` | Contains error details if location retrieval fails. |
| `coords`  | `GeolocationCoordinates \| null` | The latest coordinates (`latitude`, `longitude`, `accuracy`, etc.). |

