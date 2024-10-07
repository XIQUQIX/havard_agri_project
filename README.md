## Background Info:  
VegScape and CropScape are two USDA NASS web geospatial processing services that 
greatly facilitate remote sensing data accessing and processing, product data querying, 
visualizing, and disseminating. To learn more, read the papers about the VegScape and the 
CropScape web services for all functionalities. Together, the satellite image data pulled 
from these two web services can be used to produce crop phenology insights. Crop 
phenology is the study of the physiological stages of crop growth and development from 
planting, vegetative development, flowering, to harvest. It's a vital part of crop growth 
management and yield estimation, as it can be integrated with information about how 
environmental factors and management practices impact plant performance. See the 
panel diagram below to visualize the crop phenology for a field crop of potatoes

## Promt1
Crop phenology reports show the general trend of agricultural plant growth from 
satellite data; rising levels in the spring, peaking in the summer, and harvesting in the fall 
(drops off rapidly from Nov-Dec). 

![image](https://github.com/user-attachments/assets/2685f6f1-1bf0-4a73-aedd-a27586b3f310)

Currently, these two web services are not integrated, and there is no current capability to 
distinguish crop NDVI values from those NDVI values of natural vegetation. Your task is 
to create a scalable or parallel framework in Python or C++ that can integrate these two 
datasets over 23 counties from the Western United States, more details follow. These 
counties are located in the Western states of Washington, Oregon, and Idaho and can be 
located in the map below.

![image](https://github.com/user-attachments/assets/57a189c0-6caf-4a83-9abc-9a145dc8f19f)

![image](https://github.com/user-attachments/assets/7dee7458-d05d-425e-9c79-e834cd92cf25)


These counties were chosen because they share a climate that is shaped by their position 
in the rain shadow of the Cascades Mountain Range, resulting in dry conditions, hot 
summers, and cold winters. The terrain is defined by rolling hills and valleys, and important 
river systems (Columbia and Snake Rivers) that enable irrigation-based, monoculture 
agriculture in an otherwise dry region. 

## Steps:
Our team developed a pipeline that executes the following steps:

Isolate the agricultural activity of the CropScape images based on the land 
classifications. You do not have to be so granular and separate by crop type. Just a 
binary, what is active agriculture and what is not.  

o Extract the NDVI values from similar areas from the VegScape images. 

o Create crop phenology time series (max, mean, min) NDVI dataframe reports per 
county over all years. Proceed to use a model of choice to analyze past trends 
and predict last year's (2023) crop phenology NDVI mean for all counties. We visualized 2023 prediction from one county, or a grouping of counties by 
state, of choice to the actual 2023 county data. 

o The competition won’t judge computational efficiency based only on whether your 
method uses parallelism. There are many scalable methods that don't use explicit 
parallelism but still handle large problems effectively. Think creatively about how 
your methods can scale up to handle larger problems. 

o The purpose of this exercise is to gain an understanding of the importance of crop 
phenology to assess food security in the American West, as well as being aware of 
an important vegetation index derived from satellite imaging.  


## Methods
We applied the KMeans clustering algorithm to group
counties with similar historical NDVI trends (2001-2022)
and predict future crop phenology patterns. By clustering
counties based on past NDVI values, we identified regions
with similar vegetation growth, allowing us to forecast the
mean NDVI for each cluster in 2023. To evaluate the clus-
tering approach, we compared the predicted NDVI values
with the actual 2023 data, measuring the model’s accuracy.
KMeans was chosen because it allows us to identify similar
crop growth patterns by clustering counties that share envi-
ronmental characteristics and agricultural practices. Addi-
tionally, it simplifies prediction by grouping counties with
similar data, reducing variability and improving the robust-
ness of the prediction model.

##Visualization:
For visualizing the NDVI values, we used matplotlib li-
brary in Python. Additionally, time series graphs showed
the evolution of crop phenology for each county over the
13-year period.
The visualization effectively illustrates the yearly pro-
gression of vegetation, from lower NDVI values during the
winter months to a peak during the summer, followed by a
gradual decline. The comparison between actual and pre-
dicted NDVI for 2023 helps evaluate the accuracy of the
KMeans model, providing insight into the effectiveness of
historical data in predicting vegetation health.
This graphical approach allows us to not only track
changes in NDVI over the years but also to identify anoma-
lies or shifts in seasonal patterns, which could be signif-
icant for understanding long-term vegetation changes or
crop phenology.

![image](https://github.com/user-attachments/assets/46887a35-4819-4be2-8c6a-1d7a69d04139)

## Conclusion
We analyzed cropland coverage and vegetation
health across 23 counties from 2001 to 2023 using machine
learning techniques and geospatial data. By implementing
the KMeans clustering model, we successfully predicted
crop phenology for 2023, comparing the predicted NDVI
values to actual observations to assess model performance.
Our findings reveal significant seasonal variability in
NDVI trends, capturing critical vegetation growth peri-
ods. The model’s predictions align closely with actual data,
though minor discrepancies suggest potential for improve-
ment by incorporating additional environmental variables
like precipitation and temperature.
This research provides valuable insights for agricultural
stakeholders, enabling informed decisions regarding re-
source allocation and crop management.
Future work should focus on refining the model with al-
ternative algorithms, higher temporal resolution data, and
climatic factors to improve predictive accuracy and support
sustainable agricultural practices. Overall, this study high-
lights the importance of data-driven approaches in address-
ing agricultural challenges and promoting environmental
stewardship.












