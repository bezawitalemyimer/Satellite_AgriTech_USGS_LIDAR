
# Satellite_AgriTech_USGS_LIDAR
## satellite data analysis Satellite_AgriTech_USGS_LIDAR
predict maize harvest  using satellite analysis on The USGS recently released high resolution elevation data as a lidar point cloud called USGS 3DEP in a public dataset on Amazon. 

## Business Need 
At AgriTech, we are very interested in how water flows through a maize farm field. This knowledge will help us improve our research on new agricultural products being tested on farms.

How much maize a field produces is very spatially variable. Even if the same farming practices, seeds and fertilizer are applied exactly the same by machinery over a field, there can be a very large harvest at one corner and a low harvest at another corner.  We would like to be able to better understand which parts of the farm are likely to produce more or less maize, so that if we try a new fertilizer on part of this farm, we have more confidence that any differences in the maize harvest 9are due mostly to the new fertilizer changes, and not just random effects due to other environmental factors.  

## water significance and measuremnt
Water is very important for crop growth and health.  We can better predict maize harvest if we better understand how water flows through a field, and which parts are likely to be flooded or too dry. One important ingredient to understanding water flow in a field is by measuring the elevation of the field at many points. The USGS recently released high resolution elevation data as a lidar point cloud called USGS 3DEP in a public dataset on Amazon. This dataset is essential to build models of water flow and predict plant health and maize harvest. 

## Termilogies

### GeoPandas extends Pandas to allow spatial operations on geometric types

The goal of GeoPandas is to make working with geospatial data in python easier. It combines the capabilities of pandas and shapely, providing geospatial operations in pandas and a high-level interface to multiple geometries to shapely. GeoPandas enables you to easily do operations in python that would otherwise require a spatial database such as PostGIS.

Read More [here](https://geopandas.org/getting_started.html). How to install, use and integrate

GeoPlot is a high-level geospatial plotting library

It’s an extension to cartopy and matplotlib which makes mapping easy: like seaborn for geospatial. Read More [here](https://residentmario.github.io/geoplot/user_guide/Working_with_Geospatial_Data.html)

`pip install geoplot` or `conda install geoplot -c conda-forge`

One of the issues with Geospatial data is that there are lots of termilogies that are used and it easy to misplaced this terms. Below are some common terms and there short version meaning:

- **shapefiles**: data file format used to represent items on a map
- **geometry**: a vector (generally a column in a dataframe) used to represent points, polygons, and other geometric shapes or locations, usually represented as well-known text (WKT)
- **Well-known text (WKT)**: is a text markup language for representing vector geometry objects. A binary equivalent, known as well-known binary (WKB), is used to transfer and store the same information in a more compact form convenient for computer processing but that is not human-readable. 
- **polygon**: an area
- **point**: a specific location
- **basemap**: the background setting for a map, such as borders in Germany
- **projection**: since the Earth is a 3D spheroid, chose a method for how an area gets flattened into 2D map, using some coordinate reference system (CRS). There are lots of them and it confusing. They are the EPSGs
- **colormap**: choice of a color palette for rendering data, selected with the cmap parameter. It helps to explain information conveyed from plots
- **overplotting**: stacking several different plots on top of one another
- **choropleth**: using different hues to color polygons, as a way to represent data levels, usually used in maps
- **kernel density estimation (KDE)**: a data smoothing technique that creates contours of shading to represent data levels
- **cartogram**: warping the relative area of polygons to represent data levels
- **quantiles**: binning data values into a specified number of equal-sized groups
- **voronoi diagram**: dividing an area into polygons such that each polygon contains exactly one generating point and every point in a given polygon is closer to its generating point than to any other; also called a Dirichlet tessellation. we use this when we want to understand per point difference in a given polygon or geometry

**What are shapefiles?**

SHP is the file extension for one of the primary file types used for representation of ESRI Shapefile. It represents Geospatial information in the form of vector data to be used by Geographic Information Systems (GIS) applications. The format has been developed as open specifications in order to facilitate interoperability between ESRI and other software products.

A shapefile format describes geospatial information of a data set as vector features. These vector features include:

    points
    lines
    polygons

These features in combination can represent almost any type of shapes like water wells, country boundaries, spatial points, rivers flow, lakes, etc. Each vector feature can have attributes that actually define the purpose of that feature. For example, a shapefile containing cities of Lagos can have city name and temperature as attributes which gives meaningful representation to the spatial data.

A standalone shp file can not be used by software applications to make meaning of the data it contains. In order to make sense of the information contained in such a file, a shapefile makes use of following additional mandatory files.

    shx file - index file
    dbf file - a dBASE file that stores all the attributes of the shapes in the main file
    prj file - stores project information of the file

**What is a GeoJSON file?**

GeoJSON is a JSON based format designed to represent the geographical features with their non-spatial attributes. This format defines different JSON (JavaScript Object Notation) objects and their joining fashion. JSON format represents a collective information about the Geographical features, their spatial extents, and properties. An object of this file may indicate a geometry (Point, LineString, Polygon), a feature or collection of features. The features reflect addresses and places as point’s streets, main roads and borders as line strings and countries, provinces, and land regions as polygons. Using the GeoJSON, different mobile routing and navigation applications can indicate the coverage of their services. An extension of GeoJSON is TopoJSON that is smaller in size and encodes geospatial topology.

Coordinate

Coordinate is the basic element of any geographic data. This is a single dimension (Longitude, latitude) representing a single number (decimal format) and sometimes record a coordinate for elevation too. Time is a dimension too but its complexity makes it difficult to record it as coordinate. Coordinates in both JSON GeoJSON are formatted like numbers.

Position

An ordered array of coordinates represent the position. This is the smallest unit that can indicate a point on earth.

[Longitude, latitude, elevation]

Before the release of the current specification, GeoJSON allowed to record three coordinates per position but is not allowed by the new specification.

Geometry

Geometries are simple shapes (points, curves, and surfaces) in GeoJSON which consist of a type and a collection of coordinates. Point is the simplest geometry that represents a single position

{ "type": "Point", "coordinates": [0, 0] }

LineStrings

At least two connected places are used to represent a line.

{ "type": "LineString", "coordinates": [[10, 30], [10, 10]] }

Point and line strings are the two simplest categories of geometry. Both types of geometry don’t bother many geometric rules. A point can be represented in a place anywhere, and a line can have more than one points, even if the points are self-crossing.

Polygons

GeoJSON geometries seem significantly more complex in Polygons. Polygons have insides & outsides areas and can possess holes in that inside.

{
  "type": "Polygon",
  "Coordinates": [
    [
      [30, 10], [10, 10], [10, 0], [20, 40]
    ]
  ]
}

Read More [here](https://docs.fileformat.com/gis/geojson/)

**Digital terrain model**

Digital Terrain Models (DTM) sometimes called Digital Elevation Models (DEM) is a topographic model of the bare Earth that can be manipulated by computer programs.The data files contain the elevation data of the terrain in a digital format which relates to a rectangular grid. Vegetation, buildings and other cultural features are removed digitally - leaving just the underlying terrain. DTMs are used especially in civil engineering & surveying, geophysics, geography and remote sensing, geography and Farming.

A digital elevation model is a 3D representation of the terrain elevations found on the earth’s surface. DEMs are generated from variably-spaced Lidar ground points, or they can be created using a raster grid. A Digital Terrain Model (DTM) is a DEM in which terrain data has been further enhanced with breaklines, creating greater accuracy as it contains additional information defining terrain in areas where Lidar data alone is unable to do the job effectively.


**Rasters**

A raster consists of a series of pixels, each with the same dimensions and shape. In the case of rasters derived from airborne sensors, each pixel represents an area of space on the Earth's surface. The size of the area on the surface that each pixel covers is known as the spatial resolution of the image. For instance, an image that has a 1 m spatial resolution means that each pixel in the image represents a 1 m x 1 m area.

![image.png](attachment:image.png)

**Coordinate Reference System & Projection Information**

    A spatial reference system (SRS) or coordinate reference system (CRS) is a coordinate-based local, regional or global system used to locate geographical entities. -- Wikipedia

The earth is round. This is not a new concept by any means, however we need to remember this when we talk about coordinate reference systems associated with spatial data. When we make maps on paper or on a computer screen, we are moving from a 3 dimensional space (the globe) to 2 dimensions (our computer screens or a piece of paper). To keep this short, the projection of a dataset relates to how the data are "flattened" in geographic space so our human eyes and brains can make sense of the information in 2 dimensions.

The projection refers to the mathematical calculations performed to "flatten the data" into a 2D space. The coordinate system references to the x and y coordinate space that is associated with the projection used to flatten the data. If you have the same dataset saved in two different projections, these two files won't line up correctly when rendered together.

![image.png](attachment:image.png)

Maps of the United States in different projections. Notice the differences in shape associated with each different projection. These differences are a direct result of the calculations used to "flatten" the data onto a 2 dimensional map. Source: M. Corey, opennews.org

What Makes Spatial Data Line Up On A Map?

There are lots of great resources that describe coordinate reference systems and projections in greater detail. However, for the purposes of this activity, what is important to understand is that data from the same location but saved in different projections will not line up in any GIS or other program. Thus it's important when working with spatial data in a program like R or Python to identify the coordinate reference system applied to the data, and to grab that information and retain it when you process / analyze the data.

For a library of CRS information: [A great online library of CRS information](https://spatialreference.org/ref/epsg/)




**What is PDAL**

PDAL aka Point Data Abstraction Library used for manipulating point cloud data such as lidar

PDAL allows users to embed Python functions inline with other Pipeline processing operations. The purpose of this capability is to allow users to write small programs that implement interesting actions without requiring a full C++ development activity of building a PDAL stage to implement it. A Python filter is an opportunity to interactively and iteratively prototype a data operation without strong considerations of performance or generality. If something works well enough, maybe one takes on the effort to formalize it, but that isn’t necessary. PDAL’s embed of Python allows you to be as grimy as you need to get the job done.

PDAL provides a Python extension that gives users access to executing pipeline instantiations and capturing the results as Numpy arrays. This mode of operation is useful if you are looking to have PDAL simply act as your data format and processing handler.



A PDAL processing pipeline is represented in JSON. The structure may either:

    a JSON object, with a key called pipeline whose value is an array of inferred or explicit PDAL Stage Objects representations.

    a JSON array, being the array described above without being encapsulated by a JSON object.

A simple PDAL pipeline, inferring the appropriate drivers for the reader and writer from filenames, and able to be specified as a set of sequential steps:
## Package and their use
Data Featching and loading : Fetch spacialy bound LIDAR data from user input and return python dictionary contining all years of geopandas file

Terrain Visualization : Give option to show data as

3D render plot or
Heat map
Data Transformation

Topographic wetness index (TWI) - as an additional column returned with geopandas dataframe
Standardized grid - A python code that takes elevation points output from the USGS LIDAR tool and interpolates them to a grid.
Package Installation

### Reading data from EPT

Introduction

This describes how to use Conda, Entwine, PDAL, and GDAL to read data from the USGS 3DEP AWS Public Dataset. We will be using PDAL’s readers.ept to fetch data, we will filter it for noise using filters.outlier, we will classify the data as ground/not-ground using filters.smrf, and we will write out a digital terrain model with writers.gdal. Once our elevation model is constructed, we will use GDAL gdaldem operations to create hillshade, slope, and color relief.

Install Conda

We first need to install PDAL, and the most convenient way to do that is by installing Miniconda. Select the 64-bit installer for your platform and install it as directed.

Install PDAL

Once Miniconda is installed, we can install PDAL into a new Conda Environment that we created for this tutorial. Open your Anaconda Shell and start issuing the following commands:

