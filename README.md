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

Similarly, the evaluation of Aerosols for the Pan- Amazon and Indonesia use the MODIS Global Land Aerosols Optical Depth dataset focused on each region, aggregated to a yearly sum of Aerosol abundance, and non-parametrically evaluated for increasing and decreasing trends. 

<img width="833" alt="Screen Shot 2021-05-30 at 1 03 49 PM" src="https://user-images.githubusercontent.com/73979215/120113303-da0c2580-c147-11eb-8976-1360dc6021ae.png">      

 ## Evaluation of Relationships
To evaluate the relationships between fire anomalies and aerosols in each region, we’ve conducted a residual trend analysis through regression, where fires are the independent variable and aerosols the dependent.

 <img width="955" alt="Screen Shot 2021-05-30 at 1 19 50 PM" src="https://user-images.githubusercontent.com/73979215/120114095-84d21300-c14b-11eb-8bc6-580fee0d8d73.png">   

In evaluating the residuals of aerosols, we’re looking for areas of low fire frequency with unexplainably high aerosol concentration. For instance: an indigenous territory of the Pan – Amazon with low fire frequency and high aerosol concentration. The question is – Where are the aerosols coming from, if not from fires, and how are these communities affected by P.M 2.5, which they took no part in generating? 

<img width="1039" alt="Screen Shot 2021-05-30 at 1 25 59 PM" src="https://user-images.githubusercontent.com/73979215/120114110-93b8c580-c14b-11eb-8692-8f2999626dc1.png">   

#### Evaluating fire trends in the Pan- Amazon using Google Earth Engine
1. Load MODIS Fire dataset into Google Earth Engine 
```
var ModisProjection = ModFire.first().select('FireMask').projection()
print (ModisProjection)
var ERAProjection = ERA11km.first().select('temperature_2m').projection()
print (ERAProjection)
```
2. Extract country boundaries for Brazil 
```
//extract country boundaries
var Brazil = CNT.filter(ee.Filter.eq('ADM0_NAME', 'Brazil'))
```
3. Filter the data by region and date – evaluation time scale from 2000 to 2020 
```
//filter by region,  date,and change scale to 10km
var FireBrz = ModFire.map(function(image){return image.clip(Brazil)

  
})
.filterDate('2000-01-01', '2020-12-31').select('FireMask')
```
4. Next, we want to extract from the `Fire Mask` only areas listed from low to high confidence of fire occurrence. 
```
var RecFire = function (image){
      var reclass = image.remap([1,2,3,4,5,6,7,8,9],[0,0,0,0,0,0,1,1,1],0,'FireMask')
      return reclass;
  
};
//apply function

var RecFireBrz = FireBrz.map(RecFire)
```
5.  We decided after aggregating fire anomalies to monthly counts by season, the analysis required a longer time scale for evaluation. Thus, we’ve proceeded by aggregating fire anomalies to monthly counts, then into a yearly sum of instances for the 20-year time interval. 
```
/* Extract Full Year and aggregate to monthly cummulative */
// resample to 10km

var fullyear = ee.List.sequence(1, 12);
var years = ee.List.sequence(2000, 2020);

var FireFullYear = ee.ImageCollection.fromImages(
  years.map(function(y) {
    return fullyear.map(function (m) {
      return RecFireBrz
        .filter(ee.Filter.calendarRange(y, y, 'year'))
        .filter(ee.Filter.calendarRange(m, m, 'month'))
        .sum()
        .set('month', m).set('year', y)
        
      
  });
}).flatten());

print('FireFullYear', FireFullYear.first().projection())


var projection =  FireFullYear.first().projection();
print('non-mosaiced projection:',  projection);
```
You’ll notice a resampling of the data to 10km. The original MODIS fire product is on a 1km x1km grid; we found this to be a too fine scale for correlation to Aerosol density and have resampled the fire product to 10km. 

6. After aggregating monthly images for each month within the 20-year time series, we aggregate to full-year images for the 20-year time series. 
```
/* 
_____________________________________________________
aggregate cumulative of All Seasons
Group by year, and then reduce within groups by sum();
the result is an ImageCollection with one image for each year */


var year1 = ee.List.sequence(2000, 2020);

var AllSeasons = ee.ImageCollection.fromImages(
      year1.map(function (y) {
        return FireFullYear
                    .filterMetadata ('year','equals',y)
                    .sum()
                    .set('year', y)
                                  
                    .rename('fire')    ;
}).flatten());

print('AllSeasons',AllSeasons);
```







 

#### Data Processing in Google Earth Engine


 
