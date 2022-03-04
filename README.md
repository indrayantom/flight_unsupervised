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
This stacked bar plot clearly shows the customers who have churned. First, the values of tenure and monthly charges were discretized/binned into 6 quantiles to create this stacked bar plot.
![binning](https://user-images.githubusercontent.com/92590596/145628097-28917258-373b-4549-87af-6f2ba10b0161.jpg)
The result appears an instinctive result as the churn likelihood gets smaller as the membership time gets longer. It also tells that more than 50\% of customers who only subscribed less than 4 months prefer to churn (mostly even churn in their first month). From MonthlyCharges binning, it can be seen that the premium customers who are billed more than 70 dollars per month are more likely to churn compared to other customers with less bill. From the business perspective, it is surely more beneficial for the company to have a great focus improving on the premium services since those services have more lost customers and donate more month-to-month income for the company. Another interesting result is the customer who only subscribes for basic service seems quite satistied with the service quality and less likely to churn.

## References
http://www2.bain.com/Images/BB_Prescription_cutting_costs.pdf (explain why customer retention is very important for the company's life)
