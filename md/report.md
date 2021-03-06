# Methodology for the marine wilderness analysis

---
## The data

The [cumulative marine pressure](http://www.nature.com/ncomms/2015/150714/ncomms8615/full/ncomms8615.html) data (hereafter referred to as *the Marine Data* unless otherwise specified) was used as the aggregated indicator for wilderness in the marine realm. It summarises impacts to the marine environment globally based on a set of 19 factors up to 2013, including fishing, climate change, land-based stressors. This layer represents the best globally consistent marine cumulative pressure at a high resolution of 1 $km^2$.

We used the Marine Ecoregions and Pelagic Provinces of the World as the classification basis for assessing cumulative marine pressure, a proxy for wilderness area in the marine realm. Provinces, as opposed to ecoregions, were chosen due to its suitable size for the identification of gaps and prioritisation. This also aligns with the other IUCN thematic studies ([REF:to thematic](#))

## The methods

Given the explorative nature of this analysis, i.e., the pressure threshold value under which marine areas are considered wilderness areas needs to be tried and tested, and that this value may change, it is therefore imperative a sustainable method be utilised so that upon the change of such a threshold, subsequent iterations/calculations require minimal repetitions of analysis, especially spatial analysis that are usually costly in time and prone to error.

- **Input spatial data**

    With the potential change in threshold value in mind, the input data were prepared as follows:
    - the Marine Data
    - within the bounds of the EEZ, compilation of a *synthesized* biogeography layer that incorporates the MEOW ([Marine Ecoregion of the World](http://bioscience.oxfordjournals.org/content/57/7/573.abstract)), up to 200 meter depth, MEOW up to 200 nautical miles, and [Pelagic Provinces](http://nora.nerc.ac.uk/18017/). The reason behind creating such a layer is to defer the decision of which base units to group (for example, identifying gaps in MEOW or Pelagic or anything with EEZ regardless) at a later stage. This resulted in a new dataset of spatially disjoint boundaries with shared attributes. More details can be found in the [detailed methodology notebook](./wilderness_analysis.ipynb). Antarctica was removed from the resulting dataset, where the World Heritage Convention does not currently apply. 
    - the marine subset of natural World Heritage sites (47 sites)

- **Clipping rasters**

    Each feature of the above biogeography data was programatically used to clip a part of the Marine Data based on its spatial extent. The clipped raster data was then converted into a flattened one dimensional array to facilitate numerical calculations to derive statistics. The same set of steps were applied for the marine World Heritage sites and its intersection with the biogeography data.
    
    
- **Exploring thresholds**

    The threshold of classifying marine wilderness value was determined by using the 10 percentile value for all marine areas within EEZ. We chose this empirical threshold by comparing threshold values at 1, 3, 5, and 10 percentiles, and examining distribution of wilderness extent with existing marine World Heritage sites, and the 10% threshold was decided as it reasonably highlights areas of marine wilderness in accordance with expert knowledge.


- **Small multiples**

    After multiplying the cell size for each qualifying pixel (as defined by the threshold) within each feature and summarising over all such pixels, we calculated the total wilderness area of the feature. Similarly, by grouping different features under the same province (or WH site), the total wilderness area and its percentage in relation to the province could be easily computed without running any spatial analysis. 

Step by step analysis is included in the [detailed methodology notebook](./wilderness_analysis.ipynb)

---

# Draft text for marine WH wilderness analysis

## Classification of the marine environment

It is necessary for our purpose to apply a classification scheme to the marine environment so that its wilderness values can be systematically examined to identify wilderness gaps. To this end, we compiled a combined layer of the Marine Ecoregion of the World (MEOW), providing a useful framework on near-shore, continental waters (up to 200m depth); and the Pelagic Provinces of the World, for waters beyond 200m depth up to the limit of Exclusive Economic Zones (EEZs, up to 200 nautical miles) ([Spalding et al 2007, 2012](#)). We aligned the  outer limit with EEZ as the Convention does not apply to the large majority of area beyond national jurisdiction (ABNJ) - a compromise between the continuity of marine biogeography and the political boundary. We used the unit of provinces that have been used in the previous IUCN marine WH thematic study ([Abudulla et al 2013](#)) as they are deemed of appropriate scale for the identification and prioritisation of broad gaps globally. 

## Current distribution of wilderness within marine provinces

**[AP: one or two paragraph about wilderness in marine provinces]**

The [cumulative marine pressure](http://www.nature.com/ncomms/2015/150714/ncomms8615/full/ncomms8615.html) data (hereafter referred to as *the Marine Pressure Data* unless otherwise specified) was used as the aggregated indicator, a proxy for wilderness in the marine environment. It summarises impacts to global oceans based on a set of 19 factors up to 2013, including fishing, climate change, land-based stressors. This layer represents the best globally consistent marine cumulative pressure at a high resolution of 1 $km^2$.

We chose the 10 percentile value of the Marine Pressure Data for all marine areas within EEZ as the threshold to defining marine wilderness. This empirical threshold was developed by comparing other candidate values at 1, 3, 5, 10 percentiles, and was decided for its quality to highlight existing marine wilderness areas, in accordance with expert knowledge.

The resulting global distribution of marine wilderness is uneven and reflects different combined cumulative pressures across all marine provinces. We find large variations between provinces with little disturbed waters and those subject to intensive human influence. The distribution can be found in the below map.

*Map: distribution of marine cumulative pressures and the boundary of ABNJ. Green areas represents marine wilderness according to the threshold*

![map: overall dist marine pressure](mm_overall_dist.png)

Most notably, due to difficulties in navigation as a result of multi-year ice, the Arctic region remains largely intact with largest marine wilderness, covering a total of 5.4 million $km^2$ and also represents one of the highest percentage coverage (46.8%) in all marine provinces. This includes 3.3 million $km^2$ of waters within the near-shore Arctic province, which accounts for almost half (47.9%) of the entire marine province, and more than 2 million $km^2$ beyond the continental shelf and within the EEZ boundary, i.e., 58.9% of its pelagic province, making it the largest contiguous waters with a significant wilderness coverage. 

*Map: marine wilderness in the Arctic region*

![map: polar map focusing on Arctic](mm_dist_polar.png)

Polynesia (including Central Polynesia, Southeast Polynesia, and Marquesas), Sahul Shelf, Tropical East Pacific, Subantarctic Islands, Southern New Zealand and Subantarctic New Zealand, also contain substantial marine wilderness area within their boundaries (each more than 200,000 $km^2$). 

Polynesia contains large expanses of wilderness outside its continental shelf: most of Central Polynesia's 1.2 million marine wilderness area are located in the South Central Pacific (736,941 $km^2$, 21.4%) and Equatorial Pacific (414.471 $km^2$, 34.0%) pelagic provinces and, similarly, wilderness in Southeast Polynesia owes much of its area to the South Central Pacific pelagic province (469,159 $km^2$, 8.2%). With 502,141 $km^2$ out of its total pelagic province of 737,640 $km^2$ identified as wilderness, Marquesas ranks the highest in proportion (68.1%). 

Similar to Polynesia, having relatively little continental shelf, Subantarctic Islands host significant wilderness area in the pelagic waters, including the Antarctic (153,549 $km^2$, 44.7%), Subantarctic (170,448 $km^2$, 49.2%) and Antarctic Polar Front (630,631 $km^2$, 55.0%) provinces. 

The same can be observed for Subantarctic New Zealand region, where large pelagic provinces such as Subantarctic, Southern Subtropical Front, Antarctic Polar Front cover 313,650 $km^2$ (66.1%), 170,773 $km^2$ (74.0%) and 19,671 $km^2$ (56.5%) respectively.

Notably, measuring a wilderness area of 288,274 $km^2$ (21.9%) within its continental shelf, Sahul Shelf is second largest to the Arctic region in terms of near-shore wilderness.

*Map: marine provinces with significant wilderness areas*

![map:highlight regions/meow of high wildernss](mm_highlight_overlap.png)

## Marine wilderness inside marine World Heritage sites

As can be seen in the analysis (see [map](#) below), 36 of 47 marine WH sites, contain, to varying degrees, marine wilderness areas inside their designated boundaries. This indicates some element of the wilderness value have been accepted and reflected by the Convention already, albeit implicitly. It also highlights the fact vast wilderness areas locate beyond the current distribution of marine WH sites that may host potential OUVs. 

*Map: overlay of marine World Heritage sites and marine wilderness areas*

![map:wh overlay marine pressure](mm_wh_overlap.png) 

[map legend: wh overlay](./writing/wh_legend.csv)

For example, the Great Barrier Reef, off the east coast of Australia, has overall the largest marine wilderness area in all natural WH sites (78,310 $km^2$, 22.7% of its total marine area). Phoenix Islands Protected Area, the largest WH site in the world, covers a considerable 23,432 $km^2$ of wilderness areas in the pelagic province of Central Polynesia. Overall, ten natural WH sites contain more than 1,000 $km^2$ wilderness area inside their boundaries, out of 33 sites that overlap with marine wilderness area, according to the spatial analysis.

While the actual amount of marine wilderness in each site is an important indicator, the percentage of its marine wilderness area may provide another useful indication of the degree to which how significant these vast wilderness areas are captured in relation to their own size. For instance, in the Subantarctic Islands region, the Macquarie Island, 95.4% of its 5,396.7 $km^2$ waters lie almost entirely within wilderness area in the Antarctic Polar Front pelagic province. In the Arctic province, the Natural System of Wrangel Island Reserve occupies a significant area of 7,200 $km^2$ and this amounts to 59.7% of its total marine area). 

[table: export wh wilderness csv](./writing/export_wh_wilderness.xlsx)

There is a need to consistently recognise such value and provide a systematic framework to identify and prioritise marine areas where such value may reside. Next we combine what have been analysed so far and further examine marine wilderness within each province that having existing marine WH sites, and seek to identify those provinces that host large wilderness that have little WH coverage.

## Gaps in marine wilderness 

Currently, 30 of the 62 marine provinces are home to at least one marine WH site. Both the Tropical East Pacific and the Northern European Seas have four sites and five provinces: Subantarctic Island, Western Indian Ocean, Warm Temperate Northeast Pacific, Tropical Southwestern Pacific and Weste Central Australian Shelf have two each. 

The remaining 32 provinces, including Marquesas, Sahul Shelf, and Southeast Polynesia, host no marine WH sites and present obvious gaps in its wilderness area.

[table: export_gap_meow_province](./writing/export_gap_meow_province.xlsx)

However, numbers alone is a rather poor indicator as it fails to take into consideration the actual overlap of wilderness area within each province. In contrast, having a WH in a province does not automatically suggest its wilderness area in that marine region has been captured. As we have identified, in some of the provinces, marine WH sites cover very little wilderness area. For example, Tropical East Pacific, though having four WH sites, has a small combined coverage of 0.5%. Arctic has one WH site (Natural System of Wrangle Island), but it makes less than 0.01% of its total wilderness areas. On the other end of the spectrum, some WH sites may cover entire provinces, for instance, sites in the West Central Australian Shelf and the Northeast Australian Shelf (97.4% and 82.1% respectively).

*Map: number of WH containing wilderness area in each province*

![map: highlight of gap provinces](mm_gap_num.png)

*Map: wilderness area in WH as percentage of total wilderness area in each province*

![map: highlight of gap provinces](mm_gap_per.png)

It is important to note that, OUV remains the key criteria for inscribing a site to the WH List. A gap identified in this approach can provide useful insight and guidance in the search of potential wilderness sites of OUV, it does not qualify a nomination from the gap province without scrutinies at a more appropriate scale and rigorous comparative analysis.

## Prioritising provinces and potential sites

**[AP: do we need this paragraph?? perhaps not tied to the spatial analysis]**

## Caveats

As mentioned earlier, the cumulative marine pressure dataset is at best a proxy for wilderness. The definition of wilderness requires XXXXXX [DEF: wilderness](#) and no data has been nor in our opinion will be developed specifically to address wilderness in the marine environment. The nature of a global datasets determines that it will not capture every nuance of pressure or threat exhaustively that may invalidate the definition of marine wilderness in the context of World Heritage.

Nevertheless, with these shortcomings in mind, our analysis offers a useful framework to illustrate how data driven approaches can be employed to provide insight into how global gaps can be identified consistently and how, with more detailed data at appropriate scale, it can be improved to offer greater accuracy and higher resolution.

Alternatively, to compensate for deficiencies in using global datasets and in the use of proxy of wilderness, it is important that an expert driven approach be used in conjunction that can emphasize and target specific, relevant attributes of wilderness values.

The results and gaps identified here remain indicative at a global scale and should not be interpreted as recommendations for future nominations.