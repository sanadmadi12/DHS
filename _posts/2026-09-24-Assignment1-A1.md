---
title: "Assignment 1: Mapping Features Across Egypt"
last_modified_at: 2026-09-24T12:00:00+04:00
tags:
  - GeoNames
  - Egypt
  - Interactive Map
  - Mapping
  - F26
---

# Mapping Features Across Egypt

## Background and Expectations

Geographic data helps explore how features are represented across a country, but maps depend on their underlying data and may not fully represent reality. As Kitchin and Lauriault argue, data are not neutral or raw representations of the world, but are shaped by the systems, classifications, standards, and people involved in producing them. For this assignment, I used GeoNames to map mosques, farms, and hospitals across Egypt, examining both their spatial distribution and what these patterns reveal about the dataset’s coverage, limitations, and unevenness.

I chose Egypt because I am from Jordan, where Egyptian media has strongly influenced the country and the Arab world more broadly. I also lived in Egypt for over a month during an internship two summers ago. Together, these experiences made me familiar with its culture, living standards, social classes, and demographics.

Since much of Egypt’s population is concentrated along the Nile Valley and Delta, I expected many locations to follow the Nile from north to south. I was also interested in areas away from the Nile, particularly Red Sea tourist areas outside Egypt’s main population corridor. The dataset contains around 35,000 locations, with common feature codes including WAD, a dry valley or riverbed that fill after heavy rainfall, and PPL, a populated place such as a city, town, or village. Their frequency reflects Egypt’s extensive desert landscape and large population. However, rather than choosing the most represented features, which mainly describe physical geography and settlements, I wanted to examine Egypt from a cultural and social perspective through features revealing human activity, community, and how society is organized across space.

I chose mosques, farms, and hospitals to explore the possible overlap between religion and community, agricultural work, and healthcare infrastructure in Egypt. GeoNames contains 987 mosque, 808 farm, and 194 hospital records, with hospitals represented much less frequently. Farms are particularly relevant because agriculture remains important to Egypt’s economy and employment. Comparing farms and mosques allows me to examine whether religious and agricultural spaces are concentrated in similar areas, while hospitals show how healthcare infrastructure is represented near farms and across Egypt. Together, these features capture different but potentially connected dimensions of life in Egypt.

| feature_code | total_locations |
|:-------------|----------------:|
| FRM          | 808             |
| HSP          | 194             |
| MSQE         | 987             |

<div style="width:100%; height:70vh;">
  <iframe
    src="{{ '/assets/Maps/EG_featuremap.html' | relative_url }}"
    style="width:100%; height:100%; border:0;"
    loading="lazy">
  </iframe>
</div>

## Computational Insights

Looking at the map, I noticed several patterns. As expected, most locations are concentrated along the Nile, particularly in northern Egypt around Cairo and Alexandria. Some also appear in the Sinai Peninsula, including tourist destinations such as Sharm El Sheikh and Dahab. More surprising were areas with very few or no points. The Red Sea coast, for example, is mostly empty despite destinations such as Hurghada, while western Egypt has almost no points at all.

However, this uneven distribution, particularly in western Egypt, is somewhat expected given Egypt’s population geography. The [NASA image](https://science.nasa.gov/earth/earth-observatory/city-lights-illuminate-the-nile-79807/) shows population and development concentrated along the Nile Valley and Delta, while most of western Egypt remains dark. GeoNames generally follows this pattern, but gaps remain in developed areas such as the Red Sea coast and along the southern Nile, despite the NASA image showing development farther south. Overlaying the two maps could help compare these patterns and identify possible gaps in GeoNames coverage.

<div style="text-align: center;">
  <img src="{{ '/assets/images/Egypt_Lights.jpg' | relative_url }}"
       alt="NASA image showing city lights along the Nile Valley and Delta"
       style="max-width: 100%; height: auto;">
</div>
Looking at the specific points, farms, shown in red, are the most common of the three features. This relates to the importance of agriculture in Egypt’s domestic economy and international trade. Farms are heavily concentrated along the Nile, particularly in three clusters in northern Egypt around Dekernes, Shebin El Kom, and Kafr El Dawwar, north of Cairo and closer to the Mediterranean. I believe these clusters represent areas with suitable soil and environmental conditions for large-scale agriculture. Farms are also the only feature I selected that appears in western Egypt.

I expected more mosque records given religion’s importance in Egyptian society. Instead, they are concentrated mainly around Cairo and Alexandria, with some farther south and along the eastern Sinai Peninsula. Around Dahab and Sharm El Sheikh, I interestingly noticed several mosque records despite almost none of my other selected features appearing there, making me question whether local contributions or different data collection patterns explain their stronger representation. I also noticed several mosques near the Rafah border, which was interesting given the area’s geopolitical significance and raised questions about how political geography, borders, and conflict overlap with what geographic datasets record and make visible. Surprisingly, farms and mosques showed little overlap, despite my expectation that rural farming communities would have a stronger religious presence.

Lastly, hospitals have the fewest points and are concentrated mainly around Cairo and Alexandria, with none in the southern half of Egypt or near the Red Sea coast. Hospitals also show little overlap with farms, which raises concerns since physically demanding agricultural work can involve injuries and accidents, making nearby healthcare important for farming communities. Although the map cannot indicate healthcare quality, the limited and separated hospital points raise questions about the geographic distribution and accessibility of healthcare across Egypt.

Looking at the overall overlap, farms, mosques, and hospitals rarely appear together in the same areas. This is interesting because these features represent connected parts of everyday life: work, religion and community, and healthcare. Agricultural areas create communities that also need religious and healthcare services, yet the map often shows these features geographically separated. This is especially important for hospitals since farming is physically demanding and accidents can occur, making nearby healthcare facilities valuable.

One of the most important patterns was the lack of data in western Egypt, the Red Sea coast, and the southern Nile, although this emptiness may have different meanings. Western Egypt’s limited points generally match its low population concentration, while Hurghada has almost none compared with the considerably greater coverage of Sinai, despite both containing major Red Sea tourist areas. This made me question whether these patterns represent Egypt itself or GeoNames’ uneven coverage. Kitchin and Lauriault’s critical data approach pushes this further: databases shape what can be known through what they record, classify, and leave out. On my map, missing records visually resemble actual absence. Southern Egypt may therefore appear to lack hospitals or mosques when I can only conclude that GeoNames has few records of them. Uneven coverage thus produces a particular version of Egypt for the viewer to interpret.

This also connects to Kitchin and Lauriault’s discussion of classification: data systems group places by shared characteristics, shaping how we understand them. GeoNames reduces complex places into standardized categories such as mosques, farms, and hospitals, raising questions about how they are assigned. For example, if an Egyptian hospital contains a mosque or prayer space, would GeoNames represent both, or would this depend on the contributor’s classification? I then add another layer by selecting only three categories and deciding how to visualize them. My map therefore represents Egypt through layers of classification and selection that make some aspects more visible than others. A blank space is not necessarily an empty space in Egypt, but one about which this data assemblage tells me little.

## Methodological Questions

GeoNames can be understood as a data assemblage shaped by contributors, technologies, classifications, and standards rather than simply representing geographic reality. For example, limited hospital points could suggest poor healthcare coverage when they may instead reflect incomplete data. Egypt also has no GeoNames ambassador, or dedicated local representative to review contributions and provide local knowledge. Its provenance raises further questions: major GeoNames sources outside the US and Canada include the U.S. National Geospatial Intelligence Agency and U.S. Board on Geographic Names. This suggests that part of Egypt’s baseline representation comes from external, particularly Western, institutions, while local or individual contributions may build unevenly on it. The resulting map can therefore combine an external institutional view with inconsistent local contributions, making some places more visible than others.

GeoNames also does not list a dedicated Egyptian national mapping or statistical authority as a source, raising questions about the completeness of its representation. This connects to Graham and De Sabbata’s [*Mapping Information Wealth and Poverty: The Geography of Gazetteers*](https://journals.sagepub.com/doi/10.1177/0308518X15594899?utm_source=chatgpt.com), which shows how uneven geographic coverage creates areas of “information wealth” and “information poverty.” Although they do not specifically classify Egypt as information poor, their findings raise this question in my analysis. The denser representation of the Delta and northern Egypt compared with the southern Nile and Red Sea coast makes me question GeoNames’ information richness within Egypt and whether this unevenness reflects digital documentation rather than geography alone. This reflects the paper’s broader argument that uneven geographic information makes some places more visible and knowable than others, an inequality my map suggests may also exist within Egypt.

## Transferability

As an engineering student, much of my work involves data from prototypes and sensors to identify gaps in design choices and evaluate the credibility of results. This assignment helped me understand how to classify data, consider its implications, and question its reliability. Applying this means conducting more extensive testing and researching new methods of sensing and gathering data rather than taking raw or open-source information at face value. Since engineering often builds on results obtained by others, questioning and identifying gaps in data can help me optimize and produce better outcomes.

## Conclusion

Overall, this assignment showed me that maps can reveal important geographic patterns, but these patterns depend heavily on the data behind them and how they are presented. While my map provided insights into the distribution of farms, mosques, and hospitals across Egypt, it also raised questions about the completeness and reliability of GeoNames. Most importantly, I learned that maps should not simply be accepted at face value, but questioned in terms of where their data comes from, what may be missing, and how visualization choices can influence interpretation.