# ERC Stochastic Transport in Upper Ocean Dynamics Hackathon March 29-31 2021
![stuod logo](https://www.imperial.ac.uk/ImageCropToolT4/imageTool/uploaded-images/erc-stuod-logos--tojpeg_1572609986634_x2.jpg)

[Link to the event website](https://www.imperial.ac.uk/events/129398/stuods-hackathon/)

## Challenges 1+2+3: Machine Learning with Weather and Climate Data

__Project leads:__ So Takao (UCL), Bertrand Chapron (IFREMER)

Some weather/climate events such as: local precipitation events, tropical cyclone trajectoires, size and intensities, and/or El Nino occurrence and strength characteristics, still present major difficulties to forecast with conventional methods using numerical models. This proposed challenge is to explore the possibility of using recent machine learning techniques to deliver data-driven solutions to such complex problems.

The participants can choose to work on one of the following areas:

### Challenge 1: Predicting the rainfall in Basel, Switzerland during the period 2020-2021
Rainfall intensity can be categorized as follows:

- No rain (0 mm/hr)
- Drizzle (0.01 - 2.5mm/hr)
- Light rain (2.5 - 7.5mm/hr)
- Moderate rain (7.5 - 35.5mm/hr)
- Rather heavy rain (35.5 - 64.5mm/hr)
- Heavy rain (>64.5mm/hr)

Your task is to predict the hourly rainfall in Basel, Switzerland during the period 03/2020-03/2021 based on the 6 categories above from various weather attributes such as temperature, wind velocity and pressure.

__Data:__ The dataset for the period 03/2010-03/2020 (downloaded from [meteoblue.com](https://www.meteoblue.com/en/weather/archive/export/basel_switzerland_2661604?daterange=2019-02-01%20to%202021-03-01&domain=NEMSAUTO&params%5B%5D=temp2m&params%5B%5D=precip&params%5B%5D=relhum2m&min=2020-02-01&max=2021-03-01&utc_offset=1&timeResolution=hourly&temperatureunit=CELSIUS&velocityunit=KILOMETER_PER_HOUR&energyunit=watts&lengthunit=metric&degree_day_type=10%3B30&gddBase=10&gddLimit=30)), is already available and can be found in the `datasets` folder. The dataset for the period 03/2020-03/2021, which is to be used for testing will be uploaded in the `datasets` folder on __30/03/2021 at 2pm__ (second day of hackathon) so keep an eye out!

__Additional comments:__ This project is suitable for beginners, as the dataset is relatively small and easy to handle (a short guide is available in the `tutorials` folder). However, that is not to say that it is not appropriate for more experienced participants as there are many interesting things one can do with this, such as figuring out how to deal with imbalanced classes or predicting the timeseries of all variables at once using more advanced tools such as seq2seq and LSTMs!

### Challenge 2: Predicting the trajectories of tropical cyclones

Include problem statement here.

### Challenge 3: Predicting the occurence of El Nino events

An El Nino event is characterised by a warmer-than-average sea surface temperature in the equatorial pacific that persists for an extended period of time. This has a significant impact on Earth's ecosystem and it is crucial that we are able to predict this. While there is no agreed definition of an El Nino event, a popular one that we will use for this challenge is:

__El Nino ([Definition](https://www.cgd.ucar.edu/staff/trenbert/trenberth.papers/defnBAMS.pdf)):__ An event where the 5 months running average of the sea surface temperature anomaly in the Nino 3.4 region 5°S ~ 5°N, 120° ~ 170°W (equivalently, -5° ~ 5°N, 190° ~ 240°E) exceeds 0.4°C for periods of 6 months or longer.

![el nino](images/nino.png)

Your task is to predict the occurence of an El Nino event 1 ~ 6 months ahead of time using various attributes such as sea surface salinity, precipitation and wind speed. We ask to use the last 5 years (2015-2020) for testing.

__Data:__ Dataset for this challenge is available in netCDF format on [ftp://ftp.ifremer.fr/ifremer/cersat/projects/stuod/hackathon/elnino/](ftp://ftp.ifremer.fr/ifremer/cersat/projects/stuod/hackathon/elnino/). More details below on how to access this.

__Additional comments:__ This challenge is appropriate for more experienced participants as it requires knowledge of dealing with spatio-temporal data.

### Datasets

Some datasets are already available on this github repository, which includes: 
- Synthetic data from the Lorenz '63 and '96 models (used in `tutorials`)
- Toy version of the meteoblue dataset (used in `tutorials`)
- Full version of the meteoblue dataset for Challenge 1 (14.5MB total)

You can also download the meteoblue dataset from [google drive](https://drive.google.com/drive/folders/1qFDy1qPg63MNmrFjiBHMlS4Mz14yzJ-C) or from terminal with the command:

```
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1QtXg1q7xfA1Tn_hBpAkI6nVGCO5_9Gfv' -O filename.csv
```

The El Nino dataset is available on [ftp://ftp.ifremer.fr/ifremer/cersat/projects/stuod/hackathon/elnino/](ftp://ftp.ifremer.fr/ifremer/cersat/projects/stuod/hackathon/elnino/) in netCDF format, which you can also get from terminal via the command:

```
wget ftp://ftp.ifremer.fr/ifremer/cersat/projects/stuod/hackathon/elnino//[variable].nc.gz -O filename.nc.gz
```

where `[variable]` is to be replaced by one of the following geophysical fields:
- `cci_sst_1981_2018` or `cci_sst_anomalies_1981_2018`: sea surface temperature/anomalies from ESA CCI SST project (satellite)
- `cci_sss_2010_2019` or `cci_sss_anomalies_2010_2019`:  sea surface salinity/anomalies from ESA CCI SSS project (satellite)
- `isas_temperature_2002_2019` or `isas_temperature_anomalies_2002_2019`: water temperature in the first 300 m from Ifremer ISAS15 dataset (in situ measurements)
- `isas_salinity_2002_2019` or `isas_salinity_anomalies_2002_2019`: water salinity in the first 300 m from Ifremer ISAS15 dataset (in situ measurements)
- `ifremer_wind_1992_2019` or `ifremer_wind_anomalies_1992_2019`: wind_speed, eastward and northward wind components from CMEMS/Ifremer Multi-sensor blended dataset (satellite)
- `gpcp_precipitation_2010_2019` or `gpcp_precipitation_anomalies_2010_2019`: precipitation, from NASA GPCP dataset (satellite)
- `aviso_sla_2002_2019` or `aviso_sla_anomalies_2002_2019`: sea level anomaly from AVISO multi-altimeter dataset (satellite) 

After downloading, you can unzip the file with the command

```
gunzip -d filename.nc.gz
```

### Tutorials

We have also provided an interactive three-part machine learning tutorial in the `tutorials` folder that will get all the particpants up to speed with the hackathon.
This includes a detailed guide on:

- The basics of statistical classification using the Lorenz '63 model.
- Introduction to statistical regression using the two-level Lorenz '96 model.
- Handling real data with `pandas` using a simplified version of the meteoblue data used in Challenge 1.

Todo: Convert it to binder or colab format to make it interactive

We have also included a short guide on how to use `python`'s `xarray` module for reading and handling netCDF files in `tutorials/getting-started-with-xarray`, which may be useful for Challenges 2 and 3.

### Acknowledgements

We would like to thank Ronan Fablet (IMT Atlantique) and Jean-Francois Piolle (IFRMER) for agreeing to help us out. Special mention goes to Jean-Francois and Nicolas Reul (IFREMER) for providing us with the Tropical cyclone and El Nino datasets.
