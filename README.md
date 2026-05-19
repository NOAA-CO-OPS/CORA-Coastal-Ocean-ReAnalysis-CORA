# Coastal Ocean Reanalysis (CORA) Notebooks

# Overview
NOAA’s Coastal Ocean Reanalysis (CORA) provides modeled historical water levels and waves for the Atlantic, Gulf, and Caribbean from 1979-2022. The reanalysis was performed through the partnership of NOAA National Ocean Service (NOS) and University of North Carolina’s (UNC) Institute of Marine Sciences and Renaissance Computing Institute ([RENCI](https://renci.org/)). Modeling was performed by ’s  RENCI, and couples ADvanced CIRCulation Model ([ADCIRC](https://www.erdc.usace.army.mil/Media/Fact-Sheets/Fact-Sheet-Article-View/Article/476698/advanced-circulation-model/)) and Simulating WAves Nearshore ([SWAN](https://swanmodel.sourceforge.io/)) to produce data points every 300 to 500 meters. Hourly water level observations from NOAA’s Center for Operational Oceanographic Products and Services (CO-OPS) [National Water Level Observation Network](https://tidesandcurrents.noaa.gov/) (NWLON) were both assimilated into modeling, and used for [validation](https://www.frontiersin.org/journals/marine-science/articles/10.3389/fmars.2024.1381228/full?utm_source=Email_to_authors_&utm_medium=Email&utm_content=T1_11.5e1_author&utm_campaign=Email_publication&field&journalName=Frontiers_in_Marine_Science&id=1381228) of results. This repository hosts Jupyter notebooks to help users access, analyze, and visualize CORA datasets hosted via [Amazon Web Services](https://noaa-nos-cora-pds.s3.amazonaws.com/index.html) on [NOAA’s Open Data Dissemination](https://www.noaa.gov/information-technology/open-data-dissemination) (NODD) Platform. All previous versions (Eg. Version 0.9 used for validation, and version 1.0 used for prototyping) are considered preliminary versions and should be superseded with version 1.1 for operational use. All code is dependent on Python libraries outlined in each notebook. Please ensure you are able to access and install each for optimal performance. Please see the [NOAA Technical Report](https://tidesandcurrents.noaa.gov/cora.html#publications) for additional information. 


# Usage
An environment.yml file is included to create an Anaconda environment in which to run the notebooks. To run the notebooks, you can use the following steps:
```bash
git clone https://github.com/NOAA-CO-OPS/CORA-Coastal-Ocean-ReAnalysis-CORA.git
cd CORA-Coastal-Ocean-ReAnalysis-CORA
conda env create -f environment.yml
conda activate cora
jupyter notebook
```


# Notebooks:
## 1.  CORA_Accessing_Data.ipynb
This notebook demonstrates how users can access CORA datasets on NOAA's Open Data Dissemination (NODD) Platform through Amazon Web Services. Model data is extracted  from the nearest model node to a user-specified geographic coordinates and displayed in a timeseries plot. 

## 2.  CORA_Visualize_Water_Levels.ipynb
This notebook demonstrates how users can access CORA datasets on NOAA's Open Data Dissemination (NODD) Platform through Amazon Web Services and create a 2-dimensional water level surface plot.

## 3.  CORA_Plot_Mesh.ipynb
Interested in viewing the bathymetry or mesh that was used in the model to create the CORA data? This notebook allows users to create a rasterized plot of the topobathy at the CORA model nodes and overlay the model mesh.

## 4.  CORA_Convert_Datums.ipynb
This notebook allows users to upload a .csv file of extracted CORA time series and run it through [NOAA’s Tidal Analysis Datum Calculator](https://access.co-ops.nos.noaa.gov/datumcalc/) ([TADC](https://github.com/NOAA-CO-OPS/CO-OPS-Tidal-Analysis-Datum-Calculator)) to convert data from Mean Sea Level (MSL) to other Datums. To run this notebook it will be necessary to also have the Python script and config file for the calculator, which are available on the GitHub repository.

## 5.  CORA_Compare_Time-Series.ipynb
This notebook retrieves observed hourly water levels from NWLON stations using CO-OPS [Data API](https://tidesandcurrents.noaa.gov/api-helper/url-generator.html) to compare with CORA data corresponding to the same location. 

# <code style="color : cyan">Change Log</code>
A tracker for known modeling issues, resolutions, versioning, and update release schedules

## Model Domains: 
  - <code style="color : greenyellow">CORA</code>: Coastal Ocean Reanalysis
  - <code style="color : darkorange">GEC</code>: CORA for the Gulf, East Coast/Atlantic, and Caribbean
  - <code style="color : aqua">Pac</code>: CORA for the U.S. Pacific, Hawaii, and southern Alaska 

| Domain | Issue| Reason | Status | Version | Date | 
| ------ | ---- | ------ | ------ | ------- | ---- |
| GEC | Initial data production | Preliminary release for water level and wave validation | Complete | 0.9 | 2022 |
| GEC | Gap filling with machine learning| Filling gaps in historical water levels with machine learning to improve data assimilation. | Complete | 1.0 | 2023 |
| GEC | Machine learning techniques incorrectly filled historical station records, inverting long term sea level trends. | Replacing modeled historical hourly water levels with combined historical station observations. | Complete | 1.1 | 2024 |
| GEC | Phase and amplitude lag for wave modeling around extreme events | Improving wave convergence parameters in SWAN to better model waves in CORA-GEC | June, 2026 | 1.1.1 | 2026
| All Directories | S3 Directory Restructuring |Support for new domains, derived data development, and product application. | May - Sept. 2026 | N/A | 2026



## <code style="color : gold">NOTICE</code>: 
[CORA-GEC v1.1](https://noaa-nos-cora-pds.s3.amazonaws.com/index.html#V1.1/) wave datasets (swan_DIR.63_YYYY.nc, swan_HS.63_YYYY.nc, swan_TPS.63_YYYY.nc),  model wave amplitude are lower and out of phase with observations at peak water levels during extreme weather events. This anomaly is due to unconstrained wave convergence parameters during [ADCIRC](https://www.erdc.usace.army.mil/Media/Fact-Sheets/Fact-Sheet-Article-View/Article/476698/advanced-circulation-model/) and [SWAN](https://www.tudelft.nl/en/ceg/about-faculty/departments/hydraulic-engineering/sections/environmental-fluid-mechanics/research/swan) model coupling. Routine, high-frequency waves compare well with observations and during spectral analysis. A resolution is in testing and scheduled for release as CORA-GEC v1.1.1 in 2026. 



# Additional Contact Information:
  - Landing Page: https://tidesandcurrents.noaa.gov/cora.html
  - NOAA's [Center for Operational Oceanographic Products and Services](https://tidesandcurrents.noaa.gov/)
    User Services: tide.predictions@noaa.gov


#  Partners
  - NOAA’s [Office for Coast Management](https://coast.noaa.gov/) - Website: [Contact Form](https://coast.noaa.gov/contactform/)
  - NOAA’s [Integrated Ocean Observing System](https://ioos.noaa.gov/) - Email: noaa.ioos.webmaster@noaa.gov
  - [Tetratech’s RPS](https://www.rpsgroup.com/) 
  - University of North Carolina’s [Renaissance Computing Institute](https://renci.org/)
  - [University of Hawaii Sea Level Center](https://uhslc.soest.hawaii.edu/)

#  How to Cite 
   - NOAA's Coastal Ocean Reanalysis (CORA) Dataset was accessed on DATE from https://registry.opendata.aws/noaa-nos-cora using notebooks from https://github.com/NOAA-CO-OPS/CORA-Coastal-Ocean-Reanalysis-CORA

#  Additional Reference codes: 
   - [Dasher Triangular Meshes](https://github.com/holoviz/datashader/blob/f23de596f9adcb8188d48e6b163c36c913cd9912/examples/user_guide/6_Trimesh.ipynb#L11)
   - [Reproducable Notebooks for Maximum Water Levels](https://github.com/reproducible-notebooks/hurricane-ike-water-levels/tree/master)

# NOAA Open Source Disclaimer

This repository is a scientific product and is not official communication of the National Oceanic and Atmospheric Administration, or the United States Department of Commerce. All NOAA GitHub project code is provided on an 'as is' basis and the user assumes responsibility for its use. Any claims against the Department of Commerce or Department of Commerce bureaus stemming from the use of this GitHub project will be governed by all applicable Federal law. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by the Department of Commerce. The Department of Commerce seal and logo, or the seal and logo of a DOC bureau, shall not be used in any manner to imply endorsement of any commercial product or activity by DOC or the United States Government.

# License

Software code created by U.S. Government employees is not subject to copyright in the United States (17 U.S.C. �105). The United States/Department of Commerce reserves all rights to seek and obtain copyright protection in countries other than the United States for Software authored in its entirety by the Department of Commerce. To this end, the Department of Commerce hereby grants to Recipient a royalty-free, nonexclusive license to use, copy, and create derivative works of the Software outside of the United States.
