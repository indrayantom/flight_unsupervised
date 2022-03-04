# ✨ Flight Dataset  : Customer Segmentation ✨ 
The dataset used in this work is related to Airline customer value analysis. The downloaded dataset consists of 62988 observations (where each observation represents each customer) and 23 columns. Brief explanation about those features can be seen below : 

![python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![colab](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)
- MEMBER_NO : Membership card number
- FFP_DATE : 	Membership time
- FIRST_FLIGHT_DATE : First flight date
- GENDER : Gender
- FFP_TIER : Membership card level
- WORK_CITY : City of work
- WORK_PROVINCE : Province of work
- WORK_COUNTRY : Country of work
- AGE : Age
- FLIGHT_COUNT : Number of flights in the observation window
- LOAD_TIME : End time of observation window
- BP_SUM : Total Basic Integral
- LAST_TO_END : Time from the last flight to the end of observation window
- AVG_DISCOUNT : Average discount rate
- SUM_YR : Fare income of observation window
- SEG_KM_SUM : Total flight kilometers of observation window
- LAST_FLIGHT_DATE : Last flight date
- AVG_INTERVAL : Average flight time interval
- MAX_INTERVAL : Maximum flight interval
- EXCHANGE_COUNT : Points redemption times
- POINTS_SUM : Total cumulative points
- POINT_NOTFLIGHT : Change times of non opportunity points

Just in case you didn't know, the telco analysis indra.html file contains both the codes and the explanation. In addition, the professional writing of the analysis is also available in a .pdf file. You also can view the docs [here](https://indrayantom.github.io/telco_custmer_dea/) . Feel free to download and clone this repo 😃😉.

## Objectives 
This work is carried out to answer this problem : 

- By using the LRFM method, analyze the customer segmentation (clustering analysis) based on the dataset.

LRFM method was proposed by Chang and Tsay, which complements the famous RMF analysis by adding the new attribute L (Length) , indicating the length of the relationship between the customer and the company measured in unit time. Based on literature study, it is found that the LRFM method is a better alternative than the RFM when clustering the customer value.

## Libraries
Libraries such as [pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/), [matplotlib](https://matplotlib.org/), and [seaborn](https://seaborn.pydata.org/) are the most commonly used for the analysis. Moreover, I also used [plotly](https://plotly.com/python/) to make a better (and easier) plots, as well as [sklearn](https://scikit-learn.org/stable/) to do the clustering analysis.
```python
import warnings
warnings.filterwarnings('ignore')

import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
%config InlineBackend.figure_format = 'svg'

from sklearn.cluster import KMeans
from sklearn.decomposition import PCA 
from sklearn.metrics import silhouette_score
from sklearn.preprocessing import StandardScaler, MinMaxScaler

import plotly.graph_objects as go
```

## Result Preview
Based on LRFMC (developed version of LRFM) concept, the airline customer has been successfully clustered into 5 categories, which consist of :
![newplot](https://user-images.githubusercontent.com/92590596/156713685-671d488d-c961-48dc-9e39-4b45a3c60711.png)

**Customer base 1 (highest Mileage, Frequency and least Recency)**

These customers have relatively high average discount rate, recent flight history, highest number of flight, highest flight mileage, and long membership time. High discount indicates they usually have high ticket prices. **Considered as the most ideal high-value customers or key customer**. Their proportion is around 8.6% of total customers. Must be prioritized by the company to maintain their satisfaction and loyalty hence becomes able to extend the high consumption level of such customer as much as possible.

- Length : ⭐⭐⭐⭐

- Recency : ⭐⭐⭐⭐⭐

- Frequency : ⭐⭐⭐⭐⭐

- Mileage : ⭐⭐⭐⭐⭐

- Discount : ⭐⭐⭐⭐


**Customer base 2 (highest Discount)**

These customers have the highest discount rate, but there is relatively less recent flight history, low total flight mileage and relatively short membership time (new). The proportion of this customer category is around 7% of total customers. **These customers are considered as potential high value customers or key development customers** as they love the privilege (do not care about discount) whenever they fly, even for such short distance. 
Their satisfactory is very important to be enhanced by the airline so they gradually become loyal key customers.

- Length : ⭐⭐⭐

- Recency : ⭐⭐

- Frequency : ⭐⭐

- Mileage : ⭐⭐

- Discount : ⭐⭐⭐⭐⭐


**Customer base 3 (highest Recency, least Frequency and Mileage)**

These are customers with no recent flight record (highest Recency), least number of flights and mileage,  relativelylow average of discount and membership time. Such customers have low ticket prices, no recent flight history, uncertain loyalty, and care about discount so much (decide to buy ticket at sufficient high discount). It is better for the company to strengthen the contact with such customers since they are very likely to leave . The proportion of this customer is around 19%. **Considered as low value customers**.

- Length : ⭐⭐

- Recency : ⭐

- Frequency : ⭐

- Mileage : ⭐

- Discount : ⭐⭐


**Customer base 4 (lowest Length and Discount)**

These customers have lowest discount rate and length, relatively less number of mileage and frequency, but have recent flight records. **With around 40% proportion, they are considered as general customers**. 

- Length : ⭐

- Recency : ⭐⭐⭐⭐

- Frequency : ⭐⭐⭐

- Mileage : ⭐⭐⭐

- Discount : ⭐


**Customer base 5 (highest length)**

These customers have the longest membership time with proportion around 25% of total customers. They also have recent flight history with relatively high number of frequency and flight. **These are the most devoted customers (important customer retention)**, as they have the longest flight history and are therefore crucial to the company's success.

- Length : ⭐⭐⭐⭐⭐

- Recency : ⭐⭐⭐

- Frequency : ⭐⭐⭐⭐

- Mileage : ⭐⭐⭐⭐

- Discount : ⭐⭐⭐
