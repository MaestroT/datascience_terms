# Leave-One-Out Cross-Validation

https://link.springer.com/referenceworkentry/10.1007%2F978-0-387-30164-8_469

Leave-one-out cross-validation is a special case of [cross-validation](https://doi.org/10.1007/978-0-387-30164-8_190) where the number of folds equals the number of [instances](https://doi.org/10.1007/978-0-387-30164-8_406) in the [data set](https://doi.org/10.1007/978-0-387-30164-8_196). Thus, the learning algorithm is applied once for each instance, using all other instances as a [training set](https://doi.org/10.1007/978-0-387-30164-8_843) and using the selected instance as a single-item [test set](https://doi.org/10.1007/978-0-387-30164-8_820). This process is closely related to the statistical method of jack-knife estimation (Efron, [1982](https://link.springer.com/referenceworkentry/10.1007%2F978-0-387-30164-8_469#CR1_469 "View reference")).

## LOOCV to Evaluate Machine Learning Models

In this section, we will explore using the LOOCV procedure to evaluate machine learning models on standard classification and regression predictive modeling datasets.

### LOOCV for Classification

```python
# loocv to automatically evaluate the performance of a random forest classifier
from numpy import mean
from numpy import std
from sklearn.datasets import make_blobs
from sklearn.model_selection import LeaveOneOut
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestClassifier
# create dataset
X, y = make_blobs(n_samples=100, random_state=1)
# create loocv procedure
cv = LeaveOneOut()
# create model
model = RandomForestClassifier(random_state=1)
# evaluate model
scores = cross_val_score(model, X, y, scoring='accuracy', cv=cv, n_jobs=-1)
# report performance
print('Accuracy: %.3f (%.3f)' % (mean(scores), std(scores)))
```

### LOOCV for Regression

```python
# loocv evaluate random forest on the housing dataset
from numpy import mean
from numpy import std
from numpy import absolute
from pandas import read_csv
from sklearn.model_selection import LeaveOneOut
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestRegressor
# load dataset
url = 'https://raw.githubusercontent.com/jbrownlee/Datasets/master/housing.csv'
dataframe = read_csv(url, header=None)
data = dataframe.values
# split into inputs and outputs
X, y = data[:, :-1], data[:, -1]
print(X.shape, y.shape)
# create loocv procedure
cv = LeaveOneOut()
# create model
model = RandomForestRegressor(random_state=1)
# evaluate model
scores = cross_val_score(model, X, y, scoring='neg_mean_absolute_error', cv=cv, n_jobs=-1)
# force positive
scores = absolute(scores)
# report performance
print('MAE: %.3f (%.3f)' % (mean(scores), std(scores)))
```
