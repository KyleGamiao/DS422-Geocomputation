# 🌿 NDVI Analysis Project Worksheet  (Jaydon, Sano, La'a, Kili)

This worksheet will guide you through the process of designing and carrying out an NDVI-based analysis in R. Fill in the prompts for your chosen research question, location, time period, data sources, and methods.  

---

## 1. Framing the Question  

**What environmental or social issue will you explore?**  
*Write your thoughts here:*  How can changes in NDVI values be used to measure the impacts of deforestation in Para, Brazil over time?

---

**Why is NDVI an appropriate tool for this question?**  
*Write your thoughts here:*  The Amazon Rainforest is very massive and full or greenery and the deforestation has been very prominent over the years so I feel that it would be easy to map it using NDVI.

---

**Who might find your results meaningful or useful?**  
*Write your thoughts here:*  Environmental scientists, conservation organizations, and policy makers could use the results to track the pace and extent of deforestation in the Amazon. Local and Indigenous communities may also find the information valuable since deforestation directly affects their lands, resources, and cultural practices. In addition, educators and the general public could use the findings to better understand how quickly the rainforest is changing and why protecting it matters on a global scale.

---

## 2. Choosing a Place and Time  

**What geographic area will you focus on?**  
*Write your thoughts here:*  Para (a state in Brazil) Para is one of the largest states in Brazil and has experienced some of the highest rates of deforestation in the Amazon. Its forests are under pressure from logging, cattle ranching, soybean farming, and the expansion of road networks

---

**What time frame makes sense for your question?**  
(e.g., single date, multiple years, seasonal patterns)  
*Write your thoughts here:*  2000-2024

---

**How will you define the scope of your analysis?**  
*Write your thoughts here:*  The analysis will focus on the state of Para, Brazil, which is one of the Amazon’s major deforestation frontiers. I will use satellite-derived NDVI data to track changes in forest greenery as a proxy for vegetation loss.

---

## 3. Finding Data  

**Where could you get satellite imagery or NDVI data?**  
*Write your thoughts here:*  MODIS (2000–2024) for high-resolution recent deforestation mapping.




---

**What resolution and frequency are appropriate?**  
*Write your thoughts here* 250m resolution and roughly 1200 images a year for 24 years.

---

**Will you download data manually or use an R package? Which one?**  
*Write your thoughts here:*  Manual Download

---

## 4. Bringing Data into R  

**What R packages can help you work with spatial data?**  
*Write your thoughts here:*  sf, terra, MODISTools, tidyverse, future.apply, here

---

**How will you handle projections, boundaries, or missing data?**  
*Write your thoughts here:*  Projections: Landsat, Sentinel, and MODIS all come in different coordinate reference systems (CRS). To compare them or overlay with Para’s boundary shapefile, everything needs to be in the same CRS. ChatGPT explained the solution would be, "Reproject all rasters and vector data to a common projection before analysis. For regional studies in Para, a projected CRS like UTM Zone 21S (EPSG:32721) or WGS84 / UTM works well because it minimizes distortion locally." Boundaries: We only want NDVI data within Para, not the entire Amazon Basin or Brazil. The solution would be to import Para’s state boundary shapefile (from IBGE or GADM) Missing Data: The Amazon has heavy cloud cover, and satellites often produce NDVI values of NA in cloudy/shadowed areas. The solution would be to apply cloud masks, and use temporal compositing.

---

**What file formats will you be working with?**  
*Write your thoughts here:*  raster, jp2, qmd

---

## 5. Calculating NDVI  

**What is the NDVI formula?**  
*Write your formula here:*  NDVI=(NIR+Red)/(NIR−Red)​

---

**Which spectral bands are needed?**  
*Write your thoughts here:*  Band 4 and 8 (sentinel)

---

**How will you apply this formula in R?**  
*Write your thoughts here:*  For Sentinel-2 imagery, this requires Band 8 (NIR) and Band 4 (Red). In R, I would apply this formula by loading the spectral bands and computing NDVI element-wise. For raster data, I can use the terra package.

---

## 6. Exploring and Visualizing Data  

**How will you summarize NDVI values?**  
(maps, plots, tables)  
*Write your thoughts here:*  I will summarize NDVI values using different methods. First, I can create maps to show the spatial distribution of vegetation health across the study area (Para). Next, I can generate plots such as histograms or time-series graphs to show the overall distribution of NDVI values or how they change over time. Finally, I can use tables to present summary statistics (mean, minimum, maximum, standard deviation) for specific areas or time periods.

---

**Will you compare locations, beofre and after events, look at seasonal patterns, or study long-term trends?**  
*Write your thoughts here:*  I plan to use NDVI to compare different locations to see how vegetation health varies spatially. I will also look at NDVI values before and after key events (such as fires, or mass tree cuttings) to measure impacts. In addition, I will analyze seasonal patterns to understand how vegetation changes naturally over the year, and I may extend the analysis to study long-term trends to detect signs of recovery or decline in vegetation over time.

---

**How will you make your visualizations clear and interpretable?**  
*Write your thoughts here:*  I will make my visualizations clear by using appropriate color scales that highlight differences in NDVI values, with greener tones representing healthier vegetation. I will include legendstitles, and labels so the maps and plots are easy to understand. For plots, I will keep the axes and scales consistent to allow comparisons, and for maps, , including titles and labels. I will also avoid clutter and focus on presenting only the most relevant information.

---

## 7. Interpreting Results  

**What patterns or relationships do you expect to see?**  
*Write your thoughts here:*  I expect to see higher NDVI values in areas with dense and healthy vegetation, such as forests or farmland, and lower values in areas with sparse vegetation, bare soil, or urban development/deforestation. Over time, I anticipate NDVI will decline in these developed areas compared to surrounding undisturbed locations, showing the impact of land use change on vegetation health.

---

**How do they relate to your research question?**  
*Write your thoughts here:*  The patterns in NDVI directly relate to my research question on Amazon Rainforest deforestation over time. Declines in NDVI values correspond to areas where forests have been cleared or degraded, while stable or high NDVI values represent regions that remain undisturbed. By tracking these changes, I can measure the extent and pace of deforestation and connect vegetation loss to human development pressures in Para.

---

**What uncertainties or data limitations should you acknowledge?**  
*Write your thoughts here:*  Some uncertainties come from cloud cover, shadows, and atmospheric conditions, which can affect NDVI accuracy in satellite imagery. Differences in sensor resolution between satellites may also limit comparisons over time. In addition, NDVI only measures greenness and does not capture other aspects of ecosystem health, so vegetation stress or biodiversity loss may not always be visible. Finally, data gaps or missing images can make it harder to track consistent changes over long time periods.

---

## 8. Reflecting on Impact  


**Could your results inform decisions, policies, or further research?**  
*Write your thoughts here:*  Yes, NDVI trends across Para can inform land use planning, enforcement, and conservation policy by identifying hotspots of ongoing loss and regions showing recovery. Results could support monitoring to high-decline areas, the design and evaluation of protected areas or restoration projects, and performance tracking for deforestation eduction programs. They would also be useful to NGOs and Indigenous organizations for advocacy and community land management. 

---

**What new questions could emerge from your findings?**  
*Write your thoughts here:*  

1. What are the proximate drivers in the highestloss hotspots?

2. How do NDVI declines correlate with land-cover change maps (to separate agriculture, pasture, and bare ground) and with fire occurrence or road expansion datasets?

3. Are there detectable signs of forest degradation (gradual NDVI decline) versus abrupt clearing, and do these follow different spatial patterns?

4. Are there overlays with rainfall and changes in vegetation densities?
