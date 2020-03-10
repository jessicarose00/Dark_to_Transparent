# From Dark to Transparent: Illuminating Patterns in Global Fishing Activity

## Executive Summary
Illegal, unreported and unregulated fishing poses a great threat to the sustainable management of fisheries and ocean biodiversity. Satellite technology shows great promise in revolutionizing the way we monitor and understand global fishing activity.

One method for monitoring ocean activity worldwide involves tapping into vessel traffic data, also known as Automatic Identification System (AIS). Vessels equipped with AIS transponders automatically broadcast a signal of their location to nearby ships, orbiting satellites and land-based receivers (Oceana, 2018). This communication tool is primarily used to prevent collisions, but creates a valuable opportunity to increase public oversight of vessel activity.  

The challenge arises when there are gaps in AIS transmission. When this happens, a vessel can essentially 'go dark' and hinder real time location tracking. Gap events or the transmission of incorrect AIS information can occur for a variety of reasons, including:
    1.	Low satellite coverage leading to poor quality transmissions
    2.	High vessel density causing saturation of the system
    3.	“If the master believes that the continual operation of AIS might compromise the safety or security of his/her ship, the AIS may be switched off. This might be the case in sea areas where pirates and armed robbers are known to operate.” (IMO, 2002)
    4. Intentional disabling of the AIS transmitter

This analysis is concerned with the situations where AIS signals are intentionally tampered with. Taking advantage of this rich source of data can uncover potential illegal behavior. Drawing on a dataset of gap events that took place between 2018 - 2019, I investigate patterns among vessels that went dark for periods of longer than 12 hours between AIS positions. Specifically, I seek to understand what kinds of vessels are more likely to have gap events. Are there patterns in the location, duration and distance of gap events? 

The [Global Fishing Watch's](https://globalfishingwatch.org/) mission is to use satellite technology, cloud computing and machine learning to create a more complete and connected picture of global fishing activity. This project is a compliment to their work on fishing and vessel detection and draws on their [publicly available code and datasets](https://globalfishingwatch.org/datasets-and-code/). 

## Table of Contents
- [Requirements](https://github.com/jessicarose00/Capstone/blob/master/requirements.txt)
- Data Acquisition
    1. [GFW Raw Gap Events Data](https://github.com/jessicarose00/Capstone/blob/master/01_Data_Acquisition_RawGapEvents.ipynb)
    2. [Webscraping](https://github.com/jessicarose00/Capstone/blob/master/02_Data_Acquisition_Scraping.ipynb)
- [Exploratory Data Analysis](https://github.com/jessicarose00/Capstone/blob/master/03_EDA.ipynb)
- Conclusions
- Future Work

## Data Acquisition
The Global Fishing Watch's gap events dataset contains over 6 million observations of vessels 'going dark' for a period longer than 12 hours between January 1, 2018 and December 31, 2019. The dataset was removed of any gaps events resulting from low satellite coverage or high vessel density.  

Using each vessel's identification number, known as the Maritime Mobile Service Identity (MMSI) number, I searched official public registries to obtain more information regarding the identity of vessels in this dataset. This involved the development of a webscraping tool that queried the International Maritime Organization's (IMO) database to gather information on the vessel’s name, call sign, IMO number, and flag state. The first step of this process involved querying and classifying around 80,000 MMSI numbers as either in the database or not. Vessels listed in the IMO registry indicate a degree of legitimacy. Those not listed and having a high number of gap events are particularly suspicious. The next step of webscraping required scraping the additional information on vessels that were listed. Unfortunately, the IMO website capped at a daily max of 100 search queries, so obtaining this information proved infeasible for the scope of this project. 

### Data Files
- raw_gaps.csv - original gap events data file from GFW (removed due to size constraints)
- raw_sample.csv - sample of 500,000 gap events for analysis (500_000, 21)
- imo_reg.csv - MMSI numbers of vessels in IMO database (9_221, 1)
- imo_notreg.csv - MMSI numbers of vessels not found in IMO database (79_066, 1)
- gaps_notreg.csv - gap events from vessels not found in IMO database (346_762, 21)

## Exploratory Data Analysis and Modeling/Unsupervised Learning Techniques


## References
Malarky, Lacey and Beth Lowell. "Avoiding Detection: Global Case Studies of Possible AIS Avoidance". Oceana. March 2018.  
IMO (2002) Resolution A.917(22) Guidelines for the onboard operational use of shipborne automatic identification systems (AIS).  