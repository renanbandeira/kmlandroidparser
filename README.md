# KML Android Parser

A parser for KML files for Android. It is useful to load a KML map into a GoogleMaps in Android.

## Requirements
- W3C DOM (to parse the KML file)
- Icons of the map

## Usage
1. First of all, save your KML file in `assets` folder
2. Copy the `ParserKML.java` and the `Placemark.java` in your Android project
3. Whenever you want to use it, call `ParserKML.getPlaces(context.getAssets().open(*"map.kml"*));`. This will return an `ArrayList<Placemark>`
4. In your MapFragment load the markers as below:
```
for (int i = 0; i < places.size(); i++) {
	Placemark place = places.get(i);
  Marker marker = map.addMarker(new MarkerOptions()
	  .icon(BitmapDescriptorFactory.fromResource(ParserKML
	  .loadMapOfIcons(place.getIconID())))
	  .title(place.getName()).snippet(place.getDescription())
	  .position(place.getCoordinates()));
	if (i == positionToShow && !isDefaultView)
		marker.showInfoWindow();
}
```

** The method `loadMapOfIcons` is responsable for transforming the ID of each Place into drawable.


