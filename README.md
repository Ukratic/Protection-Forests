## Protective Forests

An analysis of the state of protective forests in Switzerland, main factors of growth and health<br>
Note : Protective/Protection forests is often used interchangeably, depending on a country's specific framework.<br>

In a nutshell :<br>
- Temperatures are rising considerably faster in Swiss forests than Switzerland at large, which already has temperatures rising faster than the global trend.<br>
Climate change also brings instability : drought, storms, floods... Precipitation data is not entirely conclusive on this evolution, but there are worrying signs.
- Protection forests are generally well-managed and still expanding (though much less now than in previous decades). Their role is so important however, that it is crucial to monitor their health.<br> 
Many such forests protect cities, towns and villages but also roads and critical infrastructure from rockfalls, avalanches, landslides...
- A reliable model of the evolution of these forests and main factors responsible would help to anticipate changes in their growth, what caused them and come up with preventative measures if necessary.<br>

This is the purpose of this study : An overview of the current situation and an attempt at identifying key elements through analysis and modeling.<br>

Short presentation (9 minutes +3 with questions) on video by the team : <a href="https://www.youtube.com/watch?v=Hbn9JkuRaWk&t=5136s">Youtube link</a><br>

<img src="https://github.com/Ukratic/Protection-Forests/blob/main/backup/forest1.jpg" alt="Picture @Rudolf Zuber-Thoma" width="600" height="400"/>

#### Summary :<br>
1. Datasets : sources and references
2. Main contributors : project management
3. Maps, plots and dashboard : featuring rate of growth (or withering) and protective effect of forests, in relation to climate
4. Folders and files in this repository
5. Conclusion and remarks


#### 1. Datasets:
- Climate and Protective Forests' evolution since 1982, provided by the Swiss <a href="https://www.lfi.ch/">National Forest Inventory</a>
- Meteorological data in Switzerland (Daymet 1/1km), provided by the Swiss <a href="https://www.wsl.ch/">Federal Institute for Forest, Snow and Landscape Research</a>
- Satellite (Landsat 5 & 7) imagery collected using Google Earth Engine API and various vegetation indices calculated from spectral bands.<br>
Some formulas : <a href="https://eo4geocourses.github.io/IGIK_Sentinel2-Data-and-Vegetation-Indices/#/23">eo4geocourses on stl2 data</a> (We used Landsat but Sentinel2 is a better choice for studies on post-2015 data).<br>

Additional documentation (in french) : <a href="https://www.researchgate.net/profile/Urs-Beat-Braendli/publication/342143876_Inventaire_forestier_national_suisse_Resultats_du_quatrieme_inventaire_2009_-_2017/links/5ee43ba0299bf1faac52615a/Inventaire-forestier-national-suisse-Resultats-du-quatrieme-inventaire-2009-2017.pdf">4th inventory results and process, 2009-2017</a>

#### 2. Main contributors :
- Satellite data : <a href="https://github.com/Jesshuan">Jesshuan</a>
- Dashboard (streamlit) : <a href="https://github.com/MarjoryLamothe">Marjory</a>
- Scientific expertise : <a href="https://github.com/NoyE-R"> Estelle</a>
- Meteorological data, dashboard (Tableau) : Myself
- EDA & modeling : All project members

#### 3. Maps, plots and dashboard
Forests in Switzerland are still increasing (in opposition to the global trend), but much less so in recent years.This expansion into old farmlands is grinding to a halt.<br>
Moreover, area increase is not the only key factor to forests' health.<br>

<img src="https://github.com/Ukratic/Protection-Forests/blob/main/backup/map1.png" alt="Source: Arealstatistik – Bundesamt für Statistik (BFS) & Amt für Bau und Infrastruktur Liechtenstein" width="600" height="400"/>

Average temperature has very significantly increased over the past 40 years in Swiss protective forests, even more than in Switzerland at large which already sees its average temperatures <a href="https://www.iea.org/articles/switzerland-climate-resilience-policy-indicator">rise at a faster pace than the rest of the World</a>. <br>
<img src="https://github.com/Ukratic/Protection-Forests/blob/main/meteo_data/prcp_tave.png" alt="Massive increase in temperature over the last 40 years" width="600" height="400"/>

Recent years have been the hottest on record but also the sharpest rise in tempereatures since the late 1980s, <a href="https://www.vogelwarte.ch/en/atlas/evolution/climate">with a marked change in annual temperatures in the past 35 years</a>.

**Dashboards** :
- EDA graphs, map of plots and forest composition, modeling results : <a href="https://ukratic-protection-forests-dashboard-home-fsgk56.streamlit.app/">Streamlit Dashboard</a> & <a href="https://github.com/Ukratic/Protection-forests-dashboard">Repository</a>
- Basal area, regeneration coverage rate and climate per campaign : <a href="https://public.tableau.com/app/profile/arnaud.barraquand/viz/ProtectionforestsinSwitzerlandLFI4/Dashboard">Interactive maps on Tableau</a><br>
<img src="https://github.com/Ukratic/Protection-Forests/blob/main/backup/qr_code.png" alt="link to dashboard" width="200" height="200"/><br>

Best models all required use of field data. Almost-duplicate features (with Basal Area) such as the Stand Density Index were not used, but Diameter at Breast Height was.

#### 4. Navigate through the folders and files 
**Folders**<br>
*NFI_data* :
- Source data from the Swiss National Forest Inventory. Variable names & description in German
- Concatenation & initial EDA notebooks
- Modified files from concatenation and translation of variables and description in French

*meteo_data* :
- Excel file containing precipitations (in cm/square km) and temperature averages (in °C) for each forest plot
- Example plots and maps for each collection campaign<br>
Does NOT contain actual full meteorological files in netcdf (30 GB)

*docs* :<br>
- Useful documentation on Silva Protect Swiss framework and conversion from Swiss to WGS84 coordinates

*Docker* :
- Dockerfile to easily run Earth Engine (SAT notebooks in this repository) on Windows<br>
Add a requirements.txt with the following values (1 line each): earthengine-api numpy matplotlib pandas plotly requests datetime openpyxl

*backup* :<br>
- Local backup (not uploaded) and images for this Readme.

**Files**<br>
*Presentation_slides.pptx*:<br>
- Slides for the presentation of the project at Jedha

*meteo_1, meteo_2, meteo_3.ipynb* :
1. Understanding netcdf, what is in the files and how to access it
2. Defining functions to extract data and plotting maps for given time and intervals
3. Trends in temperature and precipitations through the years

*to_import_func_meteo.py* :
- To import predefined meteorological functions (provided you have the netcdf files) 

*eda.ipynb* :
- Understanding data from NFI collection campaigns, preparing the presentation and graphs

*modeling.ipynb* :
- Modeling to describe the current state of protective forests and determine useful features and targets
- Attempt to predict the future state of protective forests

*SAT_img_to_array_LANDSAT-5, SAT_aggreg.ipynb* :
- Collect satellite imagery for NFI campaigns (results in 8 to 10 GB files for each)
- Aggregate results into a csv file with NDVI,EVI,NDMI,NDWI,DSWI formulas

*coords_swiss_to_geo.ipynb* :<br>
- Convert coordinates from Swiss LV95 to WGS84
<br>

Main libraries used :<br>
*Pandas, Numpy, Xarray, netCDF4, Earth Engine, Matplotlib, Plotly, Seaborn, Scikit-learn, Tensorflow, Streamlit*

Storage and Cloud Computing :<br>
*Google Cloud Platform (Storage, Compute Engine, Vertex AI)*


#### 5. Conclusion and remarks
Forests are still expanding but the recent stump (yes, pun intended) in growth for many of them warrants caution. The very fast evolution (on the grand scheme of things but also in fact in a tree's or our lifetime) of climate will not alleviate those concerns and should be taken into account. This is with little exaggeration of vital importance in the observed population, since Switzerland's protection forests do not only safeguard the ecosystem of plants and wildlife but also towns, roads, fields...
Monitoring their stable growth is very important to maintain their relevance in that respect ; not enough young trees and the population will eventually dwindle, too many young trees (in place of adult ones, not numerically) and the protective rate drops.

The (preliminary) evaluation of features has revealed the prevalence of some data's importance as well as the little contribution to modeling of some time-consuming efforts. There is more to be done on that front and this path could considerably improve the conditions and relative cost of the next field data collection campaigns.
LIDAR-equipped drones have recently started to enter our forests and can be used to provide a reliable stand volume estimate of the forest (or derive one from a plot) much faster than by commonly used human-operated measurement tools.

This could also contribute to provide more data points that would help to build a reliable predictive model of those forests, therefore further assisting the monitoring effort.
Initial Deep Learning with GRU RNNs tests led to some headway and are an interesting path forward, but we would caution against going too far into so-called "black box" models without fully exploring features' importance and relationships first, in more easily explainable models.
