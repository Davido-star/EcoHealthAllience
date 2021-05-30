# Health Impacts of Changing Landscapes in Indigenous Lands in the Pan-Amazon and Indonesia. A Clark University Project Component in Association with EcoHealth Alliance. 
#### An Outline of Goals and Results for this Initiative | Zoe Maymon | David Smith | Finial Project GEOG 296 | 26 May 2021

This repo contains this README explaining steps in creating a desktop analysis of fire distribution and frequency in the Pan-Amazon from 2000 to 2020, and depicts the goals and current results of this initiative. 

## Who is EcoHealth Alliance
*"EcoHealth Alliance is an international nonprofit dedicated to a 'One Health' approach to protecting the health of people, animals and the environment from emerging infectious diseases. The organization formed with the merger of two highly respected organizations, Wildlife Trust and the Consortium for Conservation Medicine. The urgent concern for wildlife conservation and the overall health of our planet has led EcoHealth Alliance to become an environmental science and public health leader working to prevent pandemics in global hotspot regions across the globe and to promote conservation."* - [EcoHealth Alliance]( https://www.ecohealthalliance.org) 

## Goal 
Assess the Health Impacts of Changing Landscapes in Indigenous Lands
in the Pan-Amazon and Indonesia. 

#### Why is this important? 
A growing world population and increasing demand for resources to support it has led to unprecedented land-use change across the planet over the last several decades. For example, the demand for meat in emerging markets in Asia and Europe has resulted in the clearing of large swaths of forest in the Amazon region to make room for livestock production. A quick review by EcoHealth Alliance of the fires from last year in the Amazon shows that most fires occurred outside of indigenous territories and protected areas. It is likely that indigenous stewardship of land protects large pockets of forest from being burned, buffering the damages from haze in surrounding areas and protecting communities in neighboring lands.  
However, indigenous communities are suffering from the haze generated in other parts of the Amazon, despite maintaining contiguous forest cover in their own lands.
There is reason to [believe](https://www.reuters.com/article/indonesia-haze-indigenous/indonesias-new-ally-on-war-against-haze-tribespeople-idUSL5N1GY23Y) that a similar process is occurring across indigenous-managed lands in Indonesia, where indigenous communities have sustainably managed forest and peatland for generations. Further analysis is needed to describe the process in both the Amazon and Indonesia in quantitative terms (EcoHealth Alliance, 2020).  

## *Medium-Term Outcomes (one fires, one on infectious diseases)*
**Outcome 1: Body of scientific evidence supporting the role that indigenous land stewardship plays in the reduction of haze from land-clearing forest fires.**
This consists of a unified set of synergistic analyses of **1) the frequency and distribution of forest fires in Brazil and Indonesia over the past 20 years**, 2) quantification of the health and economic burden from these fires broken down by region and by indigenous vs. non-indigenous tenure lands, and 3) estimation of the health co-benefits of avoiding haze through indigenous land stewardship. 

## Activities
#### Outcome 1 (Fires, Indonesia and Pan-Amazon)
Activity 1 (Q3 2020): **Develop a “desktop analysis” of fire frequency and spatial distribution in the Pan-Amazon and Indonesia from 2000-2020.** This step will allow us to determine the spatial and temporal trends and will be used to quantify the relationship between indigenous land tenure and fire frequency and severity. 

## Data 
| Dataset | Variable | Proxy | Spatial Resolution | Temporal Resolution | Temporal Extent | Data Provider | 
| --- | --- | --- | --- | --- | --- | --- |
| MOD14A1 V6 | Thermal Anomalies and Fire | Fires | 1km | Daily | 2000-2020 | [NASA LP DAAC at the USGS EROS Center]( https://lpdaac.usgs.gov/products/mod14a1v006/) |
| MCD19A2 V6 | MAIAC Land Aerosol Optical Depth (AOD) | P.M 2.5 | 1km | Daily |2000 – 2020 | [NASA LP DAAC at the USGS EROS Center ](https://lpdaac.usgs.gov/products/mcd19a2v006/) |
#### Description 
1. MOD14A1 V6: Distinguishes between fire, no fire and no observations.
2. MCD19A2 V6: Measures Aerosols. Chudnovsky et al. (2014) determined that this product is a good proxy for PM 2.5 ground concentrations

## Evaluation of trends

The process for evaluating trends in fire frequency for the Pan- Amazon and Indonesia use the MODIS Global Thermal Anomalies dataset focused on each region, aggregated to a yearly sum of fire occurrences, and non-parametrically evaluated for increasing and decreasing trends.

<img width="828" alt="Screen Shot 2021-05-30 at 12 48 20 PM" src="https://user-images.githubusercontent.com/73979215/120113281-bd6fed80-c147-11eb-9e15-65712921687a.png">    

Similarly, the evaluation of Aerosols for the Pan- Amazon and Indonesia use the MODIS Global Land Aerosols Optical Depth dataset focused on each region, aggregated to a yearly sum of Aerosol abundance, and non-parametrically evaluated for increasing and deceasing trends. 

<img width="833" alt="Screen Shot 2021-05-30 at 1 03 49 PM" src="https://user-images.githubusercontent.com/73979215/120113303-da0c2580-c147-11eb-8976-1360dc6021ae.png">      

 



 

#### Data Processing in Google Earth Engine


 
