## Polyline Geometry
### symbology

This is the example of implementing QGIS expression on line symbologi. In this examples, the line layer will be styled differently, based on wether the line intersects certain feature on other layer or not. The intersection layer will be a polygon layer which is loaded on the working project.

This is how it looks before using the geometry generator style:
![before](https://files.gitter.im/ivanbusthomi/AA4G/image.png)

This is the geometry generator expression that is being used
* outside
```
difference(
	$geometry,
	union(
		geometry(get_feature('dummy_polygon','id',0)), 
		geometry(get_feature('dummy_polygon','id',1))
	)
)
```
* inside
```
intersection(
	$geometry,
	union(
		geometry(get_feature('dummy_polygon','id',0)), 
		geometry(get_feature('dummy_polygon','id',1))
	)
)
```

The result is like shown below.

![after](https://files.gitter.im/ivanbusthomi/Wvq2/image.png)
