# Read: 42 - Location

![](https://lembergsolutions.com/sites/default/files/styles/metatags_large/public/blog/blog_header_images/FLP.jpg?itok=g2iTLJlI)

Mobile users take their devices with them everywhere, and adding location awareness to your app offers users a more contextual experience. The location APIs in Google Play services facilitate adding location awareness to app with automated location tracking, wrong-side-of-the-street detection, geofencing, and activity recognition.


## Get the last known location

Using the Google Play services location APIs, your app can request the last known location of the user's device. In most cases, you are interested in the user's current location, which is usually equivalent to the last known location of the device. using fused location provider to retrieve the device's last known location.

The fused location provider is one of the location APIs in Google Play services. It manages the underlying location technology and provides a simple API so that you can specify requirements at a high level, like high accuracy or low power. It also optimizes the device's use of battery power.

![](https://droidmentor.com/wp-content/uploads/2017/05/current_location-1080x675.png)

## Set up Google Play services

To access the fused location provider, your app's development project must include Google Play services. Download and install the Google Play services component via the [SDK Manager](https://developer.android.com/tools/help/sdk-manager) and add the library to your project. [Setting Up Google Play Services](https://developer.android.com/google/play-services/setup).

### Specify app permissions

Apps whose features use location services must [request location permissions](https://developer.android.com/training/location/permissions), depending on the use cases of those features.

### Create Location Services Client

```
private FusedLocationProviderClient fusedLocationClient;

// ..

@Override
protected void onCreate(Bundle savedInstanceState) {
    // ...

    fusedLocationClient = LocationServices.getFusedLocationProviderClient(this);
}
```

### Get The last known location

![](https://i.ytimg.com/vi/Iq9yQmVOThE/maxresdefault.jpg)

```
fusedLocationClient.getLastLocation()
        .addOnSuccessListener(this, new OnSuccessListener<Location>() {
            @Override
            public void onSuccess(Location location) {
                // Got last known location. In some rare situations this can be null.
                if (location != null) {
                    // Logic to handle location object
                }
            }
        });
```

#### The location object maybe null in these 3 cases

- Location is turned off in the device settings. The result could be null even if the last location was previously retrieved because disabling location clears the cache.
- The device never recorded its location, which could be the case of a new device or a device that has been restored to factory settings.
- Google Play services on the device has restarted,& there is no active Fused Location Provider client that has requested location after services restarted.To avoid this situation you can create a new client and request location updates.

### Choose the best location estimate

- `getLastLocation()` gets a location estimate more quickly and minimizes battery usage that can be attributed to your app. However, the location information might be out of date, if no other clients have actively used location recently.
- `getCurrentLocation(`) gets a fresher, more accurate location more consistently. However, this method can cause active location computation to occur on the device

- These are recommended to get a fresh location, and is safer than alternatives like starting and managing location updates yourself using requestLocationUpdates(). If which sometimes consume large amounts of power if location isn't available, or if the request isn't stopped correctly after obtaining a fresh location.
