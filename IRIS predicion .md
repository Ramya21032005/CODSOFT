import pandas as pd
a=pd.read_csv("IRIS.csv")
print(a)

from sklearn import preprocessing
s=preprocessing.LabelEncoder()
a["species"]=s.fit_transform(a["species"])

x=a.iloc[:,:-1].values
print()
print("*****SEPARATING THE ROWS AND COLUMNS*****")
print()
print("*****FEATURES*****:")
print()
print(x)
print()
print("*****TARGET VALUES*****:")
print()
y=a["species"]
print(y)

import seaborn as s
s.countplot(x=a["sepal_length"],hue=a["species"])

s.countplot(x=a["sepal_width"],hue=a["species"])

s.countplot(x=a["petal_length"],hue=a["species"])

from sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test= train_test_split(x,y ,test_size=0.30, shuffle=True)
print()
print("*****DATA SPLITTING*****:")
print()
print("*****TRAINING VALUES IN X TRAIN*****:")
print()
print(x_train)
print()
print("*****TEST VALUES IN X TEST*****:")
print()
print(x_test)
print()
print("*****TRAINING VALUES IN Y TRAIN*****:")
print()
print(y_train)
print()
print("*****TEST VALUES IN Y TEST*****:")
print()
print(y_test)

from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
l=LogisticRegression()
l.fit(x_train,y_train)
prediction1=l.predict(x_test)
print()
print("******DATA CLASSIFICATION******")
print()
print("****ACCURACY BY USING LOGISTIC REGRESSION ALGORITHM****:")
print()
print("ACCURACY =",accuracy_score(y_test,prediction1))

from sklearn.tree import DecisionTreeClassifier
v=DecisionTreeClassifier()
v.fit(x_train,y_train)
prediction2=v.predict(x_test)
print("******DATA CLASSIFICATION******")
print()
print("****ACCURACY BY USING DECISION TREE CLASSIFIER ALGORITHM****:")
print()
print("ACCURACY = ",accuracy_score(y_test,prediction2))

from sklearn.naive_bayes import GaussianNB
g=GaussianNB()
g.fit(x_train,y_train)
prediction4=g.predict(x_test)
print("******DATA CLASSIFICATION******")
print("****ACCURACY BY USING GAUSSIAN NB ALGORITHM****:")
print("ACCURACY = ",accuracy_score(y_test,prediction4))

from sklearn import svm
sv=svm.SVC()
sv.fit(x_train,y_train)
prediction6=sv.predict(x_test)
print("******DATA CLASSIFICATION******")
print("****ACCURACY BY USING SVM ALGORITHM****:")
print("ACCURACY = ",accuracy_score(y_test,prediction6))
