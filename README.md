# hydamo
Module to work with the Dutch Hydrological Data Model (HyDAMO)

## Install a copy
- Get a local clone of this repository.
- Build an environment as in <a href="https://github.com/d2hydro/hydamo/blob/main/envs/environment.yml" target="_blank">environment.yml</a>.
- Mak sure your environment is activated
- Go to the root of your repository (where you find setup.py) and install the package in edit-mode by:

```
pip install -e .
```

## Get Started
To start working, import the hydamo datamodel:
```
from hydamo.datamodel import HyDAMO

hydamo = HyDAMO()
```

The hydamo-object will have have GeoPandas.GeoDataFrame for every layer defined by HyDAMO, e.g. HydroObject. You can access this layer by calling the layer as hydamo-property:

```
hydamo.hydroobject
```

You can set data from an existing feature-file, e.g. an ESRI shapefile by calling the method `set_data`:

```
hydroobject_gdf = gpd.read_file(`hydroobject.shp`)

# map all your columns  (and dtypes!) in `hydroobject_gdf` to HyDAMO

hydamo.hydroobject.set_data(hydroobject_gdf)
```

Finally you can write the entire model into one GeoPackage by calling the `to_geopackage` method on the hydamo-class:

```
hydamo.to_geopackage("hydamo.gpkg")
```