DaymetCH - Climate variables of Switzerland in 100m resolution
==============================================================

D. Schmatz, 23.10.2019

5.6.2020, 8.9.2021: updated


We used the interpolation software Daymet (Thornton et al., 1997;
https://daymet.ornl.gov) to produce daily gridded maps of meteorological
variables for Switzerland between 1930 and last year (continued on a yearly
basis). As input we used the daily measured values of all available weather
stations of MeteoSwiss and a 100m resolution DEM aggregated from the DHM25
of SwissTopo. 
The daily results were aggregated as needed to monthly, yearly or longterm
means or sums (i.e. 30 year climatologies). The daily data are available in
the original Lambert Equal Area projection used by the Daymet software.
Some of the aggregated data were projected to the Swiss coordinate
reference system (ch1903LV03).

The data can be freely used by WSL employees and WSL guests for scientific
purposes. However, third-party researchers who are not affiliated with the
WSL have to sign a user agreement in advance due to legal obligations.
The data needs to be cited using the three references below for
methodology, data source and data processing.


General information
______________________

resolution: 100m
years:      1930 - 2020
projection: Lambert equal area on a sphere (original output) 
            projected to Swiss ch1903LV03 (see details below).


Variables, Units
----------------
prcp [mm],[cm]   Total precipitation in millimeters or centimeters per
                 time unit (e.g. day, month), sum of all forms converted
                 to water-equivalent. Precipitation occurrence on any
                 given day may be ascertained.
tave [deg.C]     Daily average 2-meter air temperature in degrees Celsius
tmin [deg.C]     Daily minimum 2-meter air temperature in degrees Celsius
tmax [deg.C]     Daily maximum 2-meter air temperature in degrees Celsius
sradflux [W/m2]  Incident shortwave radiation flux density in watts per
                 square meter, taken as an average over the daylight period
                 of the day
srad [kJ/m2/day] Daily total shortwave radiation, calculated as follows:
                 (sradflux [W/m2] * dayl [s/day]) / l000

From the daymet manual:
Note that the shortwave radiation values "sradflux" are given as daylight
average flux densities (units are W/m2). This means the radiative flux
density averaged over the daylight period. The daylight period is defined
as the time during which the sun would be above an ideal (flat) horizon.
This is the same definition used to calculate the daylength in the
daylength output files. In order to calculate the total shortwave radiation
for the day "srad" (units J/m2/day), multiply the daylight average flux
density by the daylength (in seconds, as given in the daylength output
file). If you wanted to know the daily (as opposed to daylight) average
radiative flux density, take the total daily radiation as just described,
and divide by 86400 seconds/day (final units W/m2).


folders:
--------
obs_ta_m_1961_1990   observed_time-average_monthly_1961-1990 (30 year climatology)
obs_ta_m_1981_2010   observed_time-average_monthly_1981-2010 (30 year climatology)
obs_ta_y_1981_2010   observed_time-average_yearly_1981-2010
obs_ts_m_1930_2020   observed_time-series_monthly_1930-2020
obs_ts_y_1930_2013   observed_time-series_yearly_1930-2013


files:
------
The data format is NetCDF according to the Climate and Forecasting standard CF.
File names are build according to the following convention:
   ch_<variable>_<time-range>_<granularity>_<chunking | ''>_<crs>.nc4

Years for time series (ts) are given with 4 digits 
       <start year>-<end year>, e.g. 1930-2020.
Years for time averages (ta) are given with 2 digits (without century)
       <start year><end year>, e.g. 6190.
Chunking designates the internal structure of the netcdf files and is either
   "grid" for an optimized extraction of whole grids/maps, e.g. ch_tave_1930-2018_d_grid_laea.nc4 or
    empty for an optimized extraction of single points, e.g. ch_tave_1930-2019_d_laea.nc4.
   Both files contain exactly the same data (except - of course - for the additional year 2019 :-)
The crs (coordinate reference system) is either 
   "laea"   Lambert equal area or 
   "ch1903" Swiss coordinate reference system 


REFERENCES:
-----------
1) methodology:
Thornton, P.E., Running, S.W., White, M.A., 1997: Generating surfaces of daily
meteorological variables over large regions of complex terrain. J. Hydrol. 
190: 214-251.

2) data source:
Federal Office of Meteorology and Climatology MeteoSwiss
Bundesamt für Meteorologie und Klimatologie MeteoSchweiz

3) data processing:
Land Change Science, WSL
Landschaftsdynamik, WSL



Projection details
___________________

ArcGIS
------
PROJCS["Bessel_1841_Hotine_Oblique_Mercator_Azimuth_Natural_Origin",GEOGCS["GCS_Bessel_1841",DATUM["D_Bessel_1841",SPHEROID["Bessel_1841",6377397.155,299.1528128]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],PROJECTION["Hotine_Oblique_Mercator_Azimuth_Natural_Origin"],PARAMETER["False_Easting",-9419820.5907],PARAMETER["False_Northing",200000.0],PARAMETER["Scale_Factor",1.0],PARAMETER["Azimuth",90.0],PARAMETER["Longitude_Of_Center",7.439583333333333],PARAMETER["Latitude_Of_Center",46.95240555555556],UNIT["Meter",1.0]]

GDAL (EPSG 21781)
-----------------
PROJCS["CH1903 / LV03",GEOGCS["CH1903",DATUM["CH1903",SPHEROID["Bessel 1841",6377397.155,299.1528128000008,AUTHORITY["EPSG","7004"]],TOWGS84[674.4,15.1,405.3,0,0,0,0],AUTHORITY["EPSG","6149"]],PRIMEM["Greenwich",0],UNIT["degree",0.0174532925199433],AUTHORITY["EPSG","4149"]],PROJECTION["Hotine_Oblique_Mercator"],PARAMETER["latitude_of_center",46.95240555555556],PARAMETER["longitude_of_center",7.439583333333333],PARAMETER["azimuth",90],PARAMETER["rectified_grid_angle",90],PARAMETER["scale_factor",1],PARAMETER["false_easting",600000],PARAMETER["false_northing",200000],UNIT["metre",1,AUTHORITY["EPSG","9001"]],AUTHORITY["EPSG","21781"]]


Projection CH1903 (Arcinfo projection file)
-------------------------------------------
Projection    OBLIQUE_MERCATOR                                                  
Datum USER_DEFINED 674.374 15.056 405.346 0.0000 0.0000 0.0000 0.0000           
Zunits        NO                                                                
Units         METERS                                                            
Spheroid      BESSEL                                                            
Xshift        0.0000000000                                                      
Yshift        0.0000000000                                                      
Parameters                                                                      
            2 /* Projection type < 1 | 2 >                                     
1.00000 /* Scale factor at the projection's center                      
 7 26 22.500 /* Longitude of the projection's center (DM                        
 46 57  8.660 /* Latitude  of the projection's center (DM                       
90.00000 /* Azimuth at the projection's center                          
-9419820.59070 /* False easting  (meters)                               
200000.00000 /* False northing (meters)                                 

