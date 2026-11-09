---
layout: single
title: "Assignment 2: Manual Geocoding vs. Automated Geocoding"
date: 2026-11-01
---

## Manual Geocoding vs. Automated Geocoding

## Background and Expectations

For this assignment in Data and Human Space, we worked with the novel 1 the Road by [Ross Goodwin](https://youtu.be/TqsW0PMd8R0?si=Ip_d_YY6yvsB2xem), created using data collected during a road trip from New York City to New Orleans in 2017. The car was equipped with a camera, microphone, GPS, and clock to collect information about its surroundings, locations, and time. This data, along with information about nearby locations and businesses from Foursquare, was fed into an AI system that generated the novel. As a result, the text contains geographic locations, coordinates, and observations that can be extracted and mapped. The image below shows a snippet of the novel with images, coordinates and text.

<div style="text-align: center;">
  <img src="{{ '/assets/images/1Road_Text.png' | relative_url }}"
       alt="Excerpt from 1 the Road showing images, coordinates, and text"
       style="max-width: 100%; height: auto;">
</div>

For this assignment, we focused on pages 41 to 140 of the novel, mapping locations using three methods. Firstly, students manually annotated locations using Recogito, assigning coordinates based on the text. Secondly, a Python script used spaCy’s Named Entity Recognition (NER) to identify place names and geopy to obtain coordinates. Lastly, an LLM-assisted approach organized geographic information into a dataset, also using spaCy and geopy. I annotated Section 5b at home for the first session, followed by Section 5a in the second session.

By comparing the three datasets on an interactive map, I wanted to examine how humans and automated systems identify and interpret locations differently and how this affects the maps. I expect manual annotation to allow for more contextual interpretation, while automated methods might identify more locations but struggle with ambiguous references. Lastly, the image below shows a possible route from New York City to New Orleans, providing a baseline to examine the accuracy and reliability of the mapped data.

<div style="text-align: center;">
  <img src="{{ '/assets/images/Google_Maps.png' | relative_url }}"
       alt="Possible route from New York City to New Orleans"
       style="max-width: 100%; height: auto;">
</div>

## Interactive Map

<div style="width:100%; height:70vh;">
  <iframe
    src="{{ '/assets/Maps/1_The_Road_Map.html' | relative_url }}"
    style="width:100%; height:100%; border:0;"
    loading="lazy">
  </iframe>
</div>

## Observations

To start with, I examined the results from running the three datasets in Posit Cloud before looking at the map itself. The table below shows that the LLM had the most mappable locations, followed by spaCy (248) and manual annotation (243). I also noticed that both automated methods had exactly 93 locations without usable coordinates. However, more points do not necessarily mean better accuracy, which I will assess by comparing how closely each method follows the car’s expected route.

| Method | Total Rows | Mappable | Without Usable Coordinates |
|:---|---:|---:|---:|
| Manual (Recogito) | 246 | 243 | 3 |
| Automatic (spaCy + geopy) | 341 | 248 | 93 |
| Automatic (LLM) | 374 | 281 | 93 |

### 1. Human Annotation (manual)

To start with, the human annotations generally follow the expected route, with most points concentrated near New York, the middle of the journey, and New Orleans. However, there are noticeable gaps in southern Alabama and near Richmond, Virginia. Some points also form straight vertical or horizontal lines, suggesting unusual detours, possibly due to vague descriptions such as a gas station in Atlanta without specifying which one. A few points deviate completely from the route, including Tennessee, Phoenix, California, and Belgium, suggesting annotation errors discussed later. Nevertheless, only around five of the 243 mappable locations appear clearly incorrect, indicating that manual annotation generally represented the journey reliably. I believe this is because Recogito allowed us to identify locations in the text, while Google Maps helped us compare possible matches and select coordinates based on the car’s route. Together, these tools allowed us to apply human understanding and context rather than relying solely on automated suggestions.

### 2. spaCy's Named Entity Recognition (Automatic)

Moving on to the NER approach, spaCy uses a trained language model to analyze the text and identify possible geographic locations based on words and their surrounding context. These locations are then passed to geopy to match them with coordinates. However, this process does not necessarily consider the overall context of the car’s journey. Looking at the map, I noticed that although many points follow the expected route, a large number are scattered across the United States, including Utah and Illinois, and even Canada. Zooming out, I also found points across Europe, including France, the UK, and Italy, as well as Africa and Southeast Asia. This could be because the system matches similarly named locations without considering the car’s route, leading to relatively low geographic accuracy. Nevertheless, the points that follow the expected route still form a relatively clear path from New York to New Orleans, with only a few gaps.

### 3. LLM

Lastly, looking at the LLM approach, I noticed that it has the largest number of mapped points. The car’s path from New York to New Orleans is clearly visible, with a high concentration of points along the route and minimal gaps. However, many points are still located outside the expected path, including several US states such as Michigan and Nebraska, as well as a cluster in California. Moreover, there are points across different continents, including South America, Australia, and Africa, along with several clusters in Europe. Although the LLM identified more locations and produced a clearer representation of the car’s route, zooming out shows that many points are incorrectly located around the world. This suggests that the LLM approach also struggled to contextualize geographic locations based on the car’s overall journey.

Comparing the three methods, I noticed that all identified the general route from New York to New Orleans, but with differences in point distribution. Manual annotation had the fewest mappable locations but produced the most concentrated and accurate representation, with very few points outside the route. In comparison, both automated methods had many points spread across the world, particularly Europe, Asia, and Africa, suggesting similar difficulties in understanding the journey’s context. However, the LLM produced a more continuous path than NER, with fewer gaps. For example, looking at the map below it shows the route from North Carolina to Georgia with only the LLM and spaCy layers selected, we can clearly see that both follow the same general path, but the LLM (blue dots) has a higher concentration of points.

<div style="text-align: center;">
  <img src="{{ '/assets/images/Map1.png' | relative_url }}"
       alt="Comparison of LLM and spaCy geocoding points from North Carolina to Georgia"
       style="max-width: 100%; height: auto;">
</div>

Interestingly, despite identifying more locations, many were still incorrectly placed, showing that more points do not necessarily mean better accuracy. Overall, manual annotation appears more reliable, while automated methods provide greater coverage but introduce more geographic inaccuracies.

Looking at the mismatches, I believe many errors are caused by ambiguous or incomplete geographic information rather than occurring randomly. For example, in Section 5.2, the novel mentions “BP: a convenience store in Crawfordville” without specifying the exact location. This makes it difficult for both humans and automated systems to select the correct coordinates. It also shows how commercial locations, such as gas stations, are more prone to disagreement than major cities, which are generally easier to identify. Overall, these errors appear to follow patterns related to the type and completeness of geographic information.

## Interpretation vs automation

As mentioned before, manual annotation requires more time and effort but generally produces more accurate locations along the car’s expected route. In comparison, automated methods identify locations much faster but are less accurate in following the actual path. What I find interesting is that with advances in AI or better prompting that provides more context about the journey, automated methods could potentially identify many locations quickly while maintaining relatively high accuracy.

To build further on the point above, I find it interesting how each method handles ambiguity differently. Humans can use the car’s general route to estimate the most reasonable location, such as selecting a gas station near the expected path. In comparison, NER might match a place name without considering the journey, leading to locations that are completely unrelated to the car’s route. Furthermore, the LLM-assisted approach can potentially use more context when interpreting locations, rather than simply identifying place names. This means it may be better at understanding ambiguous references by considering the surrounding text and the car’s journey. However, since it also relies on spaCy and geopy, it can still assign incorrect coordinates when geographic information is ambiguous.

Lastly, the multiple levels of automation, from collecting data and generating the novel to identifying locations and mapping them, help us understand human space by processing information quickly. However, errors at any stage can affect the final map and its interpretation. Using different colors helps compare the three methods, while a jitter value of 0.02 degrees (approximately 2.2 km in latitude) separates nearby points at the zoom level used for analysis. A smaller value would cause more overlap, while a larger one could spread points too far apart and affect interpretation. The basemap also matters, as I found OpenStreetMap easier for analysis because of its roads, cities, and labels, while satellite imagery made comparisons more difficult. Together, these design choices improve the map’s clarity and interpretation.

## Critical Analysis: Limitations of Geocoding and Spatial Data

Some of the errors discussed above may be caused not only by the limitations of humans or automated methods, but also by the original text itself. After all, 1 the Road was generated using AI in 2017 and published in 2018, when text generation models were less advanced than today. As a result, some sentences are unclear or do not make complete sense, making it difficult for both humans and automated systems to identify geographic locations accurately. Moreover, the AI might have generated locations that do not exist or are misspelled, such as “Aikena” in Section 5a. Another possible source of error is the digitized version of the text used for the assignment. During the process of converting the book into digital text, small errors in spelling, punctuation, or missing commas could have been introduced. Even minor changes like these can affect how Recogito, spaCy, and the LLM recognize and interpret locations, potentially leading to incorrect coordinates. Therefore, some errors might originate from the original text or its digitization rather than the geocoding process itself.

Moving on, questions remain about the accuracy of human annotation. Recogito could not identify all locations, so we had to enter some coordinates in the comments and later move them into the latitude and longitude columns when cleaning the CSV files. Moreover, different annotators might have made inconsistent decisions, rushed, selected incorrect locations, or reversed latitude and longitude. For example, although human annotation produced the most accurate path, zooming in reveals errors such as five school points arranged in a circle near Appling, Georgia, suggesting the car traveled in circles, along with a misplaced point in Europe.

<div style="text-align: center;">
  <img src="{{ '/assets/images/Map2.png' | relative_url }}"
       alt="Manual annotation showing school points near Appling, Georgia"
       style="max-width: 100%; height: auto;">
</div>

Moreover, since the journey took place nine years ago, some businesses might have closed or changed names, making them difficult to find on Google Maps. Lastly, I questioned whether to prioritize the text or the actual journey when annotating locations, such as Massachusetts in Section 7, which might be an inaccurate AI-generated reference outside the car’s route.

Another important factor is how Goodwin's Wordcar collected the original data. As McDowell discusses, the car used the Foursquare API to gather information about nearby businesses, particularly gas stations and fast-food restaurants. This creates a bias toward commercial locations rather than representing all aspects of the surrounding environment. As a result, areas with fewer businesses or limited coverage in Foursquare might be underrepresented in the novel. This shows how the original data collection already influences what locations are included and how human space is represented, even before the geocoding process begins.

Lastly, another factor affecting the maps is the editing of the original novel. The Wordcar generated a large amount of text, but the author likely included only part of it in the published novel. Some geographic locations might therefore have been removed, potentially explaining gaps in the maps. Although we cannot determine how much text was removed from the maps alone, this shows how editorial decisions influence the available geographic data and how we interpret it.

## Conclusion

Overall, this assignment showed how different geocoding methods can produce different maps from the same text. Manual annotation represented the car’s route most accurately because humans could interpret locations using the context of the journey, while automated methods identified more locations faster but often struggled with ambiguity. I also learned more about how these methods work, from manually identifying and selecting locations in Recogito to using Python libraries such as spaCy and geopy to recognize place names and assign coordinates, and how LLMs can add another level of interpretation. Beyond the data itself, the assignment helped me understand how these tools and systems work together, how errors can carry from one stage to another, and how the choices made throughout the process ultimately shape the maps we produce and our understanding of human space.


