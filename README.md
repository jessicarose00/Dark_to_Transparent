# From Dark to Transparent: Investigating Patterns in Global Fishing Activity

## Contents
- [Requirements](https://github.com/jessicarose00/Capstone/blob/master/requirements.txt)
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
    - [Data Acquisition](#Data-Acquisition)
    - [Exploratory Data Analysis and Modeling](#Exploratory-Data-Analysis-and-Modeling)
    - [Mapping and Visuals](#Mapping-and-Visuals)
- [Future Work](#Future-Work)
- [Conclusions](#Conclusion)
- [References](#References)

## Problem Statement
Illegal, unreported and unregulated fishing poses a great threat to the sustainable management of fisheries and ocean biodiversity. Satellite technology shows great promise in revolutionizing the way we monitor and understand global fishing activity.

One method for monitoring ocean activity worldwide involves tapping into vessel traffic data, also known as Automatic Identification System (AIS). Vessels equipped with AIS transponders automatically broadcast a signal of their location to nearby ships, orbiting satellites and land-based receivers (Oceana, 2018). This communication tool is primarily used to prevent collisions, but creates a valuable opportunity to increase public oversight of vessel activity.  

The challenge arises when there are gaps in AIS transmission. When this happens, a vessel can essentially 'go dark' and hinder real time location tracking. Gap events or the transmission of incorrect AIS information can occur for a variety of reasons, including:
    1.	Low satellite coverage leading to poor quality transmissions
    2.	High vessel density causing saturation of the system
    3.	“If the master believes that the continual operation of AIS might compromise the safety or security of his/her ship, the AIS may be switched off. This might be the case in sea areas where pirates and armed robbers are known to operate.” (IMO, 2002)
    4. Desire to keep fishing grounds secret from competitors
    4. Intentional disabling of the AIS transmitter to hide illegal activity from regulators

This analysis is concerned with the situations where AIS signals are intentionally tampered with. The Global Fishing Watch offered to share AIS data that has been filtered to only include events that warrant deeper investigation. Taking advantage of this rich source of data can uncover potential illegal behavior. Drawing on a dataset of gap events that took place between 2018 - 2019, I investigate trends among vessels that went dark for periods of longer than 12 hours between AIS positions. Specifically, I seek to explore patterns in the duration and location of gap events and the characteristics of the vessels that are going dark.

## Executive Summary
The [Global Fishing Watch's](https://globalfishingwatch.org/) mission is to use satellite technology, cloud computing and machine learning to create a more complete and connected picture of global fishing activity. They have successfully developed [algorithms](https://globalfishingwatch.org/datasets-and-code/fishing-detection-models/) to detect fishing activity and intentional gap events, but are working to increase their understanding of these events. This project is a compliment to their work and draws on their [publicly available code](https://globalfishingwatch.org/datasets-and-code/) and the valuable insights shared on their [blog](https://globalfishingwatch.org/blog/). 

## Data Acquisition
The Global Fishing Watch's gap events dataset contains over 6 million observations of vessels 'going dark' for a period longer than 12 hours between January 1, 2018 and December 31, 2019. The dataset was removed of any gaps events resulting from low satellite coverage or high vessel density. I used a random sample of 500,000 observations from the original dataset in this analysis. The data files can be found [here]().The data dictionary and code can be found in this [notebook](https://github.com/jessicarose00/Capstone/blob/master/01_Data_Acquisition_RawGapEvents.ipynb). 

Using each vessel's Maritime Mobile Service Identity (MMSI) number, I searched official public registries to obtain additional identity information. This involved creating a [webscraping tool](https://github.com/jessicarose00/Capstone/blob/master/02_Data_Acquisition_Scraping.ipynb) to query the International Maritime Organization's (IMO) database and gather information on the vessel’s name, call sign, IMO number, and flag state. In the first step of this process, I queried and classified around 80,000 MMSI numbers as either listed in the database or not. The second step of webscraping required scraping the additional information on vessels that were listed. Unfortunately, the IMO website capped at a daily max of 100 search queries, so obtaining this information proved infeasible for the scope of this project. Nevertheless, vessels that are not listed in the IMO registry and with multiple gap event instances raise suspicion and present an area ripe for investigation.

## Exploratory Data Analysis and Modeling
The exploratory analysis begins by broadly investigating patterns and relationships across gap events. I use unsupervised machine learning techniques like DBSCAN clustering to identify groups of vessels exhibiting similar behavior. Running and scoring the DBSCAN algorithm proved to be very computationally expensive. To compensate, I focus on analyzing the patterns within the three largest clusters to see if any broader insights can be gleaned about the vessels going dark in these areas. My exploration and conclusions can be reviewed in detail [here](https://github.com/jessicarose00/Capstone/blob/master/03_EDA.ipynb).

## Mapping and Visuals
In order to understand and identify patterns in the location of gap events, the data needed to be overlayed on maps. I used Matplotlib's [Basemap toolkit](https://matplotlib.org/basemap/) to visualize the activity of each cluster. The maps illustrate the latitude and longitude coordinates of the vessel's AIS off timestamp, where color reflects the length of the gap event and the size of the bubble indicates the number of positions the vessel took on per day.

## Future Work
Future analysis into the number of positions a vessel assumes in a given year - has implications for their actvitiy
https://globalfishingwatch.org/data-blog/updated-fishing-lists-version-0-2/

Zoom in on the activity of the biggest offenders. without more domain knowledge its harder to find direction in such a large dataset or know what to focus on

account for EEZ/MPAs
https://globalfishingwatch.org/fisheries/who-owns-the-fish-high-seas-and-the-eezs/

## Conclusion

Different gear types had distinct latitudinal dis- tributions, with trawling confined mostly to higher latitudes, purse seining concentrated in tropical regions, and longlining in between (tracking global footprint fisheries pdf)

cannot make definitive conclusions, but these are the questions I can answer, with future work or more power, this can be done or investigated further.

## References
Malarky, Lacey and Beth Lowell. "Avoiding Detection: Global Case Studies of Possible AIS Avoidance". Oceana. March 2018.  
IMO (2002) Resolution A.917(22) Guidelines for the onboard operational use of shipborne automatic identification systems (AIS).  