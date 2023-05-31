# LP2 Classification Project 
*short project description*

## Summary


## Setup
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import plotly.express as px
import seaborn as sns 

import matplotlib.pyplot as plt 
%matplotlib inline
import matplotlib.ticker as mtick
import seaborn as sns 
import random
import phik

import warnings

# Suppress all warnings
warnings.filterwarnings("ignore")

# Feature Processing (Scikit-learn processing, etc. )
from sklearn.preprocessing import StandardScaler
from sklearn.preprocessing import OneHotEncoder
from sklearn.preprocessing import LabelEncoder
from sklearn.impute import SimpleImputer
from sklearn.metrics import classification_report
from sklearn.feature_selection import SelectKBest
from sklearn.feature_selection import f_classif

#Algorithms and pipeline

from sklearn.tree import DecisionTreeClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
from xgboost import XGBClassifier
from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer 
from imblearn.pipeline import Pipeline
from sklearn.ensemble import BaggingClassifier
from sklearn.pipeline import make_pipeline
from sklearn.model_selection import RandomizedSearchCV

##handling imbalance datasets

from imblearn.over_sampling import SMOTE

from sklearn.utils.class_weight import compute_class_weight

##hyperparameter tuning
from sklearn.model_selection import GridSearchCV


...

# Other packages
import os
>>>>>>> c948b2d2c181d8f12859c4d2f8959f5319df482b

## App Execution
...

## Author
Sonny Agorvor-Otchie 


