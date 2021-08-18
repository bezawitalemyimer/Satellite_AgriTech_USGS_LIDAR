
# Satellite_AgriTech_USGS_LIDAR
## satellite data analysis Satellite_AgriTech_USGS_LIDAR
predict maize harvest  using satellite analysis on The USGS recently released high resolution elevation data as a lidar point cloud called USGS 3DEP in a public dataset on Amazon. 

## Business Need 
At AgriTech, we are very interested in how water flows through a maize farm field. This knowledge will help us improve our research on new agricultural products being tested on farms.

How much maize a field produces is very spatially variable. Even if the same farming practices, seeds and fertilizer are applied exactly the same by machinery over a field, there can be a very large harvest at one corner and a low harvest at another corner.  We would like to be able to better understand which parts of the farm are likely to produce more or less maize, so that if we try a new fertilizer on part of this farm, we have more confidence that any differences in the maize harvest 9are due mostly to the new fertilizer changes, and not just random effects due to other environmental factors.  

## water significance and measuremnt
Water is very important for crop growth and health.  We can better predict maize harvest if we better understand how water flows through a field, and which parts are likely to be flooded or too dry. One important ingredient to understanding water flow in a field is by measuring the elevation of the field at many points. The USGS recently released high resolution elevation data as a lidar point cloud https://www.usgs.gov/news/usgs-3dep-lidar-point-cloud-now-available-amazon-public-dataset called https://www.usgs.gov/core-science-systems/ngp/3dep  in a https://registry.opendata.aws/usgs-lidar/

Reading data from EPT

Introduction

This describes how to use Conda, Entwine, PDAL, and GDAL to read data from the USGS 3DEP AWS Public Dataset. We will be using PDAL’s readers.ept to fetch data, we will filter it for noise using filters.outlier, we will classify the data as ground/not-ground using filters.smrf, and we will write out a digital terrain model with writers.gdal. Once our elevation model is constructed, we will use GDAL gdaldem operations to create hillshade, slope, and color relief.

Install Conda

We first need to install PDAL, and the most convenient way to do that is by installing Miniconda. Select the 64-bit installer for your platform and install it as directed.

Install PDAL

Once Miniconda is installed, we can install PDAL into a new Conda Environment that we created for this tutorial. Open your Anaconda Shell and start issuing the following commands:

