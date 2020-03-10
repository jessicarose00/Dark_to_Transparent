# From Dark to Transparent: Illuminating Patterns in Global Fishing Activity

## Executive Summary
Illegal, unreported and unregulated fishing poses a great threat to the sustainable management of fisheries and ocean biodiversity. Satellite technology shows great promise in revolutionizing the way we monitor and understand global fishing activity.

One method for monitoring ocean activity worldwide involves tapping into vessel traffic data, also known as Automatic Identification System (AIS). Vessels equipped with AIS transponders automatically broadcast a signal of their location to nearby ships, orbiting satellites and land-based receivers (Oceana, 2018). This communication tool is primarily used to prevent collisions, but creates a valuable opportunity to increase public oversight of vessel activity.  

The challenge arises when there are gaps in AIS transmission and vessels essentially 'go dark'. Gap events or the transmission of incorrect AIS information can occur for several reasons:
1.	Low satellite coverage leading to poor quality transmissions
2.	High vessel density causing saturation of the system
3.	“If the master believes that the continual operation of AIS might compromise the safety or security of his/her ship, the AIS may be switched off. This might be the case in sea areas where pirates and armed robbers are known to operate.” (IMO, 2002)
4. Intentional disabling of the AIS transmitter

This analysis digs deeper into the suspicious situations where AIS signals are intentionally tampered with. Drawing on a dataset of gap events that took place between 2018 - 2019, it investigates patterns and relationships among vessels that went dark for periods of longer than 12 hrs at a time.  

The [Global Fishing Watch's](https://globalfishingwatch.org/) mission is to use satellite technology, cloud computing and machine learning to create a more complete and connected picture of global fishing activity. This project is a compliment to their work on fishing and vessel detection and draws on their [publicly available code and datasets](https://globalfishingwatch.org/datasets-and-code/).  

## Table of Contents
1. Requirements
2. Data Acquisition
    1. [GFW dataset]()
    2. [Webscraping]()
3. Exploratory Data Analysis
4. Modeling
5. Conclusions
6. Future Work

## Data Acquisition
The Global Fishing Watch's gap events dataset contains over 6 million observations of vessels 'going dark' for a period longer than 12 hours between January 1, 2018 and December 31, 2019. The dataset was removed of any gaps events resulting from low satellite coverage or high vessel density. Using the Maritime Mobile Service Identity (MMSI) numbers, I searched official public registries to confirm vessel registration and obtain more information regarding the identity of vessels in this dataset. This involved the development of a webscraping tool that queried the International Maritime Organization's (IMO) database to gather information on the vessel’s name, call sign, IMO number, and flag state. The tool was able to query and classify around 80,000 MMSI numbers as either in the database or not. However, the website capped search results at a daily max of 100 queries, so obtaining additional information on the vessels that were registered proved infeasible.

### [Data Files]()
- raw_gaps.csv - original gap events data file from GFW (removed due to size constraints)
- raw_sample.csv - sample of 500,000 gap events for analysis (500_000, 21)
- imo_reg.csv - MMSI numbers of vessels in IMO database (9_221, 1)
- imo_notreg.csv - MMSI numbers of vessels not found in IMO database (79_066, 1)
- gaps_notreg.csv - gap events from vessels not found in IMO database (346_762, 21)

## [Exploratory Data Analysis]()


## [Modeling/Unsupervised Learning Techniques]()


## References
Malarky, Lacey and Beth Lowell. "Avoiding Detection: Global Case Studies of Possible AIS Avoidance". Oceana. March 2018.  
IMO (2002) Resolution A.917(22) Guidelines for the onboard operational use of shipborne automatic identification systems (AIS).  