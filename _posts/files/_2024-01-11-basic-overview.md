---
classes: 
    - wide
    - dark-theme
title: "Basic-Overview"
date: 2024-01-11
categories: 
    - blog
toc: true
toc_label: "Table of Contents"
excerpt: "An example"
header:
  overlay_image: /assets/images/fblog.png
  overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background
#   caption: "Random picture"
---

# Imports


```python
import numpy as np
import pandas as pd

#vis
import matplotlib.pyplot as plt
%matplotlib inline
from matplotlib.colors import ListedColormap
import seaborn as sns

#data
import statsmodels.api as sm

#modeling
from sklearn import datasets
from sklearn.model_selection import train_test_split
```

# Data


## Iris data



```python
#get data example:
iris = datasets.load_iris()
```


```python
# iris.__doc__
# print(iris.keys())#dict_keys(['data', 'target', 'frame', 'target_names', 'DESCR', 'feature_names', 'filename', 'data_module'])
# iris.target # array of ints integrs
```




    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
           0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
           0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,
           1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,
           1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2,
           2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2,
           2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2])




### Analysis



## Penguins (for clusters)



```python
penguins= pd.read_csv("data/penguins.csv")
penguins.head()
# penguins.shape
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>species</th>
      <th>island</th>
      <th>bill_length_mm</th>
      <th>bill_depth_mm</th>
      <th>flipper_length_mm</th>
      <th>body_mass_g</th>
      <th>sex</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.1</td>
      <td>18.7</td>
      <td>181</td>
      <td>3750</td>
      <td>male</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.5</td>
      <td>17.4</td>
      <td>186</td>
      <td>3800</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>40.3</td>
      <td>18.0</td>
      <td>195</td>
      <td>3250</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>36.7</td>
      <td>19.3</td>
      <td>193</td>
      <td>3450</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.3</td>
      <td>20.6</td>
      <td>190</td>
      <td>3650</td>
      <td>male</td>
      <td>2007</td>
    </tr>
  </tbody>
</table>
</div>




### Analysis



```python

# https://seaborn.pydata.org/generated/seaborn.pairplot.html
# sns.pairplot(penguins, hue="species") #all

```


```python
sns.pairplot(
    penguins,
    x_vars=["bill_length_mm", "bill_depth_mm", "flipper_length_mm"],
    y_vars=["bill_length_mm", "bill_depth_mm"],hue="species",size=1.3)
```

## Breast Cancer


```python
bc = datasets.load_breast_cancer()
```


```python
print(bc.keys())#dict_keys(['data', 'target', 'frame', 'target_names', 'DESCR', 'feature_names', 'filename', 'data_module'])
```

    dict_keys(['data', 'target', 'frame', 'target_names', 'DESCR', 'feature_names', 'filename', 'data_module'])
    


```python
# bc.frame #? 
# bc.target # array of ints integrs
# print(bc.DESCR)
# bc.feature_names
# bc.filename
# bc.data_module
```


```python
# sns.pairplot(bc.data,hue="gender")
# sns.pairplot(bc.data)

```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[154], line 2
          1 # sns.pairplot(bc.data,hue="gender")
    ----> 2 sns.pairplot(bc.data)
    

    File c:\Users\RhysL\miniconda3\lib\site-packages\seaborn\axisgrid.py:2098, in pairplot(data, hue, hue_order, palette, vars, x_vars, y_vars, kind, diag_kind, markers, height, aspect, corner, dropna, plot_kws, diag_kws, grid_kws, size)
       2095     warnings.warn(msg, UserWarning)
       2097 if not isinstance(data, pd.DataFrame):
    -> 2098     raise TypeError(
       2099         f"'data' must be pandas DataFrame object, not: {type(data)}")
       2101 plot_kws = {} if plot_kws is None else plot_kws.copy()
       2102 diag_kws = {} if diag_kws is None else diag_kws.copy()
    

    TypeError: 'data' must be pandas DataFrame object, not: <class 'numpy.ndarray'>


## Get more data


```python
# You can use R datasets
# Load beauty data and a list of the required dataname data
# https://vincentarelbundock.github.io/Rdatasets/datasets.html
beauty = sm.datasets.get_rdataset("TeachingRatings", "AER")

```


```python
# sns.pairplot(beauty.data,hue="gender")
```

# KNN


https://www.youtube.com/watch?v=rTEtEy5o3X0&list=PLcWfeUsAys2k_xub3mHks85sBHZvg24Jd&index=2

Given a new point, classifies the new point according to the k closest terms (gives the average or the label of the most common terms).


```python
from KNN.KNN import KNN
from sklearn.neighbors import KNeighborsClassifier,KNeighborsRegressor
```

## Iris


```python
cmap = ListedColormap(['#FF0000','#00FF00','#0000FF'])
X, y = iris.data, iris.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=1234)

# X_train[:,1]
plt.figure(figsize=(6,4))
plt.scatter(X[:,2],X[:,3], c=y, cmap=cmap, edgecolor='k', s=20)
plt.show()
```


    
![png](\assets\images\basic_overview\output_25_0.png)
    


### KNN from scratch


```python
#we train it
clf = KNN(k=2)
clf.fit(X_train, y_train)
```

    [1, 1, 2, 0, 1, 0, 0, 0, 1, 2, 1, 0, 2, 1, 0, 1, 2, 0, 2, 1, 1, 1, 1, 1, 2, 0, 2, 1, 2, 0, 1, 2, 0, 1, 1, 0, 0, 0, 0, 1, 0, 1, 0, 2, 2]
    


```python
# Given X_test we make prediction and compare againes y_test
predictions = clf.predict(X_test)
# print(predictions)
acc = np.sum(predictions == y_test) / len(y_test)
print(acc)
```

### KNN (sklearn)


```python
clf = KNeighborsClassifier(n_neighbors=2)
clf.fit(X_train, y_train)

#We now compare predicitions agains y_test.
predictions = clf.predict(X_test)
print(predictions)
acc = np.sum(predictions == y_test) / len(y_test)
print(acc)
```

    [1 1 2 0 1 0 0 0 1 2 1 0 2 1 0 1 2 0 2 1 1 1 1 1 2 0 2 1 2 0 1 2 0 2 1 0 0
     0 0 1 0 1 0 2 2]
    

## Penguins


```python
df=penguins
# df.columns 
# #Index(['species', 'island', 'bill_length_mm', 'bill_depth_mm','flipper_length_mm', 'body_mass_g', 'sex', 'year'],dtype='object')
selected_columns = ["bill_length_mm", "bill_depth_mm"]
selected_data = df[selected_columns].to_numpy()
X=selected_data
y=df["sex"].to_numpy()
```


```python
plt.figure(figsize=(4,4))
plt.scatter(X[:,0],X[:,1],c=np.where(y == 'male', 'blue', 'red'),edgecolor='k', s=20)
# Set labels and title if needed
plt.xlabel("Bill Length (mm)")
plt.ylabel("Bill Depth (mm)")
plt.title("Scatter Plot with Different Colors for Male and Female")

# Show the plot
plt.show()
```


    
![png](\assets\images\basic_overview\output_33_0.png)
    



```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=1234)
```


```python
clf = KNeighborsClassifier(n_neighbors=3)
clf.fit(X_train, y_train)

#We now compare predicitions agains y_test.
predictions = clf.predict(X_test)
# print(predictions)
acc = np.sum(predictions == y_test) / len(y_test)
print(acc)
```

    0.83
    

### Scratch


```python

```

### Sklearn


```python

```


```python
"""
make sure that your target variable y consists of discrete categories
"""
```




<style>#sk-container-id-11 {color: black;background-color: white;}#sk-container-id-11 pre{padding: 0;}#sk-container-id-11 div.sk-toggleable {background-color: white;}#sk-container-id-11 label.sk-toggleable__label {cursor: pointer;display: block;width: 100%;margin-bottom: 0;padding: 0.3em;box-sizing: border-box;text-align: center;}#sk-container-id-11 label.sk-toggleable__label-arrow:before {content: "▸";float: left;margin-right: 0.25em;color: #696969;}#sk-container-id-11 label.sk-toggleable__label-arrow:hover:before {color: black;}#sk-container-id-11 div.sk-estimator:hover label.sk-toggleable__label-arrow:before {color: black;}#sk-container-id-11 div.sk-toggleable__content {max-height: 0;max-width: 0;overflow: hidden;text-align: left;background-color: #f0f8ff;}#sk-container-id-11 div.sk-toggleable__content pre {margin: 0.2em;color: black;border-radius: 0.25em;background-color: #f0f8ff;}#sk-container-id-11 input.sk-toggleable__control:checked~div.sk-toggleable__content {max-height: 200px;max-width: 100%;overflow: auto;}#sk-container-id-11 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {content: "▾";}#sk-container-id-11 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-11 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-11 input.sk-hidden--visually {border: 0;clip: rect(1px 1px 1px 1px);clip: rect(1px, 1px, 1px, 1px);height: 1px;margin: -1px;overflow: hidden;padding: 0;position: absolute;width: 1px;}#sk-container-id-11 div.sk-estimator {font-family: monospace;background-color: #f0f8ff;border: 1px dotted black;border-radius: 0.25em;box-sizing: border-box;margin-bottom: 0.5em;}#sk-container-id-11 div.sk-estimator:hover {background-color: #d4ebff;}#sk-container-id-11 div.sk-parallel-item::after {content: "";width: 100%;border-bottom: 1px solid gray;flex-grow: 1;}#sk-container-id-11 div.sk-label:hover label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-11 div.sk-serial::before {content: "";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: 0;}#sk-container-id-11 div.sk-serial {display: flex;flex-direction: column;align-items: center;background-color: white;padding-right: 0.2em;padding-left: 0.2em;position: relative;}#sk-container-id-11 div.sk-item {position: relative;z-index: 1;}#sk-container-id-11 div.sk-parallel {display: flex;align-items: stretch;justify-content: center;background-color: white;position: relative;}#sk-container-id-11 div.sk-item::before, #sk-container-id-11 div.sk-parallel-item::before {content: "";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: -1;}#sk-container-id-11 div.sk-parallel-item {display: flex;flex-direction: column;z-index: 1;position: relative;background-color: white;}#sk-container-id-11 div.sk-parallel-item:first-child::after {align-self: flex-end;width: 50%;}#sk-container-id-11 div.sk-parallel-item:last-child::after {align-self: flex-start;width: 50%;}#sk-container-id-11 div.sk-parallel-item:only-child::after {width: 0;}#sk-container-id-11 div.sk-dashed-wrapped {border: 1px dashed gray;margin: 0 0.4em 0.5em 0.4em;box-sizing: border-box;padding-bottom: 0.4em;background-color: white;}#sk-container-id-11 div.sk-label label {font-family: monospace;font-weight: bold;display: inline-block;line-height: 1.2em;}#sk-container-id-11 div.sk-label-container {text-align: center;}#sk-container-id-11 div.sk-container {/* jupyter's `normalize.less` sets `[hidden] { display: none; }` but bootstrap.min.css set `[hidden] { display: none !important; }` so we also need the `!important` here to be able to override the default hidden behavior on the sphinx rendered scikit-learn.org. See: https://github.com/scikit-learn/scikit-learn/issues/21755 */display: inline-block !important;position: relative;}#sk-container-id-11 div.sk-text-repr-fallback {display: none;}</style><div id="sk-container-id-11" class="sk-top-container"><div class="sk-text-repr-fallback"><pre>KNeighborsRegressor(n_neighbors=3)</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class="sk-container" hidden><div class="sk-item"><div class="sk-estimator sk-toggleable"><input class="sk-toggleable__control sk-hidden--visually" id="sk-estimator-id-11" type="checkbox" checked><label for="sk-estimator-id-11" class="sk-toggleable__label sk-toggleable__label-arrow">KNeighborsRegressor</label><div class="sk-toggleable__content"><pre>KNeighborsRegressor(n_neighbors=3)</pre></div></div></div></div></div>




```python
#linear
X, y = datasets.make_regression(n_samples=100, n_features=1, noise=20, random_state=4)

fig = plt.figure(figsize=(8,6))
plt.scatter(X[:, 0], y, color = "b", marker = "o", s = 30)
plt.show()
```


    
![png](\assets\images\basic_overview\output_41_0.png)
    



```python
# #find fit
# clf = KNeighborsRegressor(n_neighbors=3)
# clf.fit(X_train, y_train)
```




<style>#sk-container-id-12 {color: black;background-color: white;}#sk-container-id-12 pre{padding: 0;}#sk-container-id-12 div.sk-toggleable {background-color: white;}#sk-container-id-12 label.sk-toggleable__label {cursor: pointer;display: block;width: 100%;margin-bottom: 0;padding: 0.3em;box-sizing: border-box;text-align: center;}#sk-container-id-12 label.sk-toggleable__label-arrow:before {content: "▸";float: left;margin-right: 0.25em;color: #696969;}#sk-container-id-12 label.sk-toggleable__label-arrow:hover:before {color: black;}#sk-container-id-12 div.sk-estimator:hover label.sk-toggleable__label-arrow:before {color: black;}#sk-container-id-12 div.sk-toggleable__content {max-height: 0;max-width: 0;overflow: hidden;text-align: left;background-color: #f0f8ff;}#sk-container-id-12 div.sk-toggleable__content pre {margin: 0.2em;color: black;border-radius: 0.25em;background-color: #f0f8ff;}#sk-container-id-12 input.sk-toggleable__control:checked~div.sk-toggleable__content {max-height: 200px;max-width: 100%;overflow: auto;}#sk-container-id-12 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {content: "▾";}#sk-container-id-12 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-12 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-12 input.sk-hidden--visually {border: 0;clip: rect(1px 1px 1px 1px);clip: rect(1px, 1px, 1px, 1px);height: 1px;margin: -1px;overflow: hidden;padding: 0;position: absolute;width: 1px;}#sk-container-id-12 div.sk-estimator {font-family: monospace;background-color: #f0f8ff;border: 1px dotted black;border-radius: 0.25em;box-sizing: border-box;margin-bottom: 0.5em;}#sk-container-id-12 div.sk-estimator:hover {background-color: #d4ebff;}#sk-container-id-12 div.sk-parallel-item::after {content: "";width: 100%;border-bottom: 1px solid gray;flex-grow: 1;}#sk-container-id-12 div.sk-label:hover label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-12 div.sk-serial::before {content: "";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: 0;}#sk-container-id-12 div.sk-serial {display: flex;flex-direction: column;align-items: center;background-color: white;padding-right: 0.2em;padding-left: 0.2em;position: relative;}#sk-container-id-12 div.sk-item {position: relative;z-index: 1;}#sk-container-id-12 div.sk-parallel {display: flex;align-items: stretch;justify-content: center;background-color: white;position: relative;}#sk-container-id-12 div.sk-item::before, #sk-container-id-12 div.sk-parallel-item::before {content: "";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: -1;}#sk-container-id-12 div.sk-parallel-item {display: flex;flex-direction: column;z-index: 1;position: relative;background-color: white;}#sk-container-id-12 div.sk-parallel-item:first-child::after {align-self: flex-end;width: 50%;}#sk-container-id-12 div.sk-parallel-item:last-child::after {align-self: flex-start;width: 50%;}#sk-container-id-12 div.sk-parallel-item:only-child::after {width: 0;}#sk-container-id-12 div.sk-dashed-wrapped {border: 1px dashed gray;margin: 0 0.4em 0.5em 0.4em;box-sizing: border-box;padding-bottom: 0.4em;background-color: white;}#sk-container-id-12 div.sk-label label {font-family: monospace;font-weight: bold;display: inline-block;line-height: 1.2em;}#sk-container-id-12 div.sk-label-container {text-align: center;}#sk-container-id-12 div.sk-container {/* jupyter's `normalize.less` sets `[hidden] { display: none; }` but bootstrap.min.css set `[hidden] { display: none !important; }` so we also need the `!important` here to be able to override the default hidden behavior on the sphinx rendered scikit-learn.org. See: https://github.com/scikit-learn/scikit-learn/issues/21755 */display: inline-block !important;position: relative;}#sk-container-id-12 div.sk-text-repr-fallback {display: none;}</style><div id="sk-container-id-12" class="sk-top-container"><div class="sk-text-repr-fallback"><pre>KNeighborsRegressor(n_neighbors=3)</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class="sk-container" hidden><div class="sk-item"><div class="sk-estimator sk-toggleable"><input class="sk-toggleable__control sk-hidden--visually" id="sk-estimator-id-12" type="checkbox" checked><label for="sk-estimator-id-12" class="sk-toggleable__label sk-toggleable__label-arrow">KNeighborsRegressor</label><div class="sk-toggleable__content"><pre>KNeighborsRegressor(n_neighbors=3)</pre></div></div></div></div></div>




```python
# clf.score(X,y)
```




    0.9530736310726923




```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1234)
# Set the number of neighbors for KNeighborsRegressor
n_neighbors = 5

X_test= np.linspace(-2, 2, 20)[:, np.newaxis]
# y_test.shape

```


```python


# Create a KNeighborsRegressor instance
knn = KNeighborsRegressor(n_neighbors)

# Train the model and make predictions on the test set
y_pred = knn.fit(X_train, y_train).predict(X_test)

# Plot the original data points
plt.scatter(X_train, y_train, color="darkorange", label="data")

# Plot the predictions
plt.plot(X_test, y_pred, color="navy", label="prediction")

# Set plot attributes
plt.axis("tight")
plt.legend()
plt.title("KNeighborsRegressor (k = %i)" % (n_neighbors))

# Display the plot
plt.tight_layout()
plt.show()
```


    
![png](\assets\images\basic_overview\output_45_0.png)
    



```python
# #Better for classification type

# #We now compare predicitions agains y_test.
# predictions = clf.predict(X_test)
# #print(predictions)
# acc = np.sum(predictions == y_test) / len(y_test)
# print(acc)#0.009708737864077669

# #How to evaluate regressor type?
```

    0.009708737864077669
    


# Linear Regression



```python
from LinearRegression.LinearRegression import LinearRegression
```


```python
X, y = datasets.make_regression(n_samples=100, n_features=1, noise=20, random_state=4)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1234)

fig = plt.figure(figsize=(8,6))
plt.scatter(X[:, 0], y, color = "b", marker = "o", s = 30)
plt.show()
```


    
![png](\assets\images\basic_overview\output_49_0.png)
    



```python

reg = LinearRegression(lr=0.01)
reg.fit(X_train,y_train)
predictions = reg.predict(X_test)

def mse(y_test, predictions):
    return np.mean((y_test-predictions)**2)

mse = mse(y_test, predictions)
print(mse)

y_pred_line = reg.predict(X)
cmap = plt.get_cmap('viridis')
fig = plt.figure(figsize=(8,6))
m1 = plt.scatter(X_train, y_train, color=cmap(0.9), s=10)
m2 = plt.scatter(X_test, y_test, color=cmap(0.5), s=10)
plt.plot(X, y_pred_line, color='black', linewidth=2, label='Prediction')
plt.show()
```


```python

```

## Linear regression penguin

## Iris

### Scratch

### Sklearn

## Penguins

### Scratch


### Sklearn

## Beauty


```python
plt.figure(figsize=(4,4))
y = beauty.data['beauty']
x1 = beauty.data['eval']
plt.scatter(x1, y)
plt.xlabel('Evaluation')
plt.ylabel('Beauty')

# Define the intercept to the y line
x = sm.add_constant(x1) ##?

# OLS Ordinary Least Squares : Estimates the data so a line can 
# be drawn through data points
results = sm.OLS(y,x).fit()

#To tell if corrolated
# results.summary() # describe OLS description
```


    
![png](\assets\images\basic_overview\output_60_0.png)
    



```python
plt.figure(figsize=(4,4))
# Plot straight line: 0.2687 from eval coef

plt.scatter(x1, y)
plt.xlabel('Evaluation')
plt.ylabel('Beauty')

# Create the regression line
yhat = 0.2687 * x1 - 1.0743
fig = plt.plot(x1, yhat, lw=4, c='orange', label='regression')
plt.xlabel('Evaluation')
plt.ylabel('Beauty')
```


    Text(0, 0.5, 'Beauty')



    
![png](\assets\images\basic_overview\output_61_1.png)
    



```python
plt.figure(figsize=(4,4))
sns.regplot(x="eval", y="beauty", data=beauty.data)
```


    <Axes: xlabel='eval', ylabel='beauty'>



    
![png](\assets\images\basic_overview\output_62_1.png)
    



```python

```


# Logistic Regression



```python
from LogisticRegression import LogisticRegression
```


```python

bc = datasets.load_breast_cancer()
X, y = bc.data, bc.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1234)

clf = LogisticRegression(lr=0.01)
clf.fit(X_train,y_train)
y_pred = clf.predict(X_test)

def accuracy(y_pred, y_test):
    return np.sum(y_pred==y_test)/len(y_test)

acc = accuracy(y_pred, y_test)
print(acc)
```

## Iris

### Scratch

### Sklearn

## Penguins

### Scratch

### Sklearn


# Decision Trees




```python
from DecisionTree import DecisionTree
```


```python

data = datasets.load_breast_cancer()
X, y = data.data, data.target

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=1234
)

clf = DecisionTree(max_depth=10)
clf.fit(X_train, y_train)
predictions = clf.predict(X_test)

def accuracy(y_test, y_pred):
    return np.sum(y_test == y_pred) / len(y_test)

acc = accuracy(y_test, predictions)
print(acc)
```


```python
## Iris
```


```python
### Scratch
```


```python
### Sklearn
```


```python
## Penguins
```


```python
### Scratch
```


```python
### Sklearn
```


```python

```


# Random Forests



```python
from RandomForest import RandomForest
```


```python
## Breast Cancer
```


```python
### Scratch
```


```python
data = datasets.load_breast_cancer()
X = data.data
y = data.target

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=1234
)

def accuracy(y_true, y_pred):
    accuracy = np.sum(y_true == y_pred) / len(y_true)
    return accuracy

clf = RandomForest(n_trees=20)
clf.fit(X_train, y_train)
predictions = clf.predict(X_test)

acc =  accuracy(y_test, predictions)
print(acc)
```


```python
### Sklearn
```


```python
## Penguins
```


```python
### Scratch
```


```python
### Sklearn
```


# Naive Bayes



```python
## Iris
```


```python
### Scratch
```


```python
### Sklearn
```


```python
## Penguins
```


```python
### Scratch
```


```python
### Sklearn
```


```python

```

# PCA (Principal Component Analysis)


```python
## Iris
```


```python
### Scratch
```


```python
### Sklearn
```


```python
## Penguins
```


```python
### Scratch
```


```python
### Sklearn
```


# Perceptron



```python
## Iris
```


```python
### Scratch
```


```python
### Sklearn
```


```python
## Penguins
```


```python
### Scratch
```


```python
### Sklearn
```


# SVM 



```python
## Iris
```


```python
### Scratch
```


```python
### Sklearn
```


```python
## Penguins
```


```python
### Scratch
```


```python
### Sklearn
```


# KMeans

### Sklearn


```python
# Apply K-means clustering with k=3
kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(x)

# Get cluster centers and labels
centers = kmeans.cluster_centers_
labels = kmeans.labels_

# Plot the data points and cluster centers
plt.figure(figsize=(6,4))
plt.scatter(x.iloc[:, 0], x.iloc[:, 1], c=labels, cmap='viridis', s=50, alpha=0.7)
plt.scatter(centers[:, 0], centers[:, 1], c='red', marker='X', s=200, label='Centroids')
plt.title('K-means Clustering')
plt.xlabel('Bill Length (mm)')
plt.ylabel('Bill Depth (mm)')
plt.legend()
plt.show()
```

    c:\Users\RhysL\miniconda3\lib\site-packages\sklearn\cluster\_kmeans.py:870: FutureWarning: The default value of `n_init` will change from 10 to 'auto' in 1.4. Set the value of `n_init` explicitly to suppress the warning
      warnings.warn(
    


    
![png](\assets\images\basic_overview\output_123_1.png)
    



```python
sns.pairplot(
    penguins,
    x_vars=["bill_length_mm"],
    y_vars=["bill_depth_mm"],hue="species")
```


    <seaborn.axisgrid.PairGrid at 0x21fc375beb0>



    
![png](\assets\images\basic_overview\output_124_1.png)
    



```python

```
