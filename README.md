# EDA_Diagnosing_Diabetes
In this project, you’ll imagine you are a data scientist interested in exploring data that looks at how certain diagnostic factors affect the diabetes outcome of women patients. You will use your EDA skills to help inspect, clean, and validate the data. <br/>
Note: This<a href="https://bit.ly/2BNk3P1](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database">`dataset`<a/> is from the National Institute of Diabetes and Digestive and Kidney Diseases. 
<br/>
`I use Code Academy lesson.` <br/>
`Improve appereance with this link:` <a href="[https://bit.ly/2BNk3P1](https://github.com/noob-hackers/grabcam/edit/master/README.md)"> https://github.com/noob-hackers/grabcam/edit/master/README.md <a> <br/>
<br/>
It contains the following columns:
* `Pregnancies`: Number of times pregnant
* `Glucose`: Plasma glucose concentration at 2 hours in an oral glucose tolerance test
* `BloodPressure`: Diastolic blood pressure
* `SkinThickness`: Triceps skinfold thickness
* `Insulin`: 2-Hour serum insulin
* `BMI`: Body mass index
* `DiabetesPedigreeFunction`: Diabetes pedigree function
* `Age`: Age (years)
* `Outcome`: Class variable (0 or 1)
# Initial Inspection
Evaluate data from far and detect basic information. 
## Step1: familiarize yourself with the dataset here.
```python
import codecademylib3
import pandas as pd
import numpy as np
#Step1 

```
## Step2: load in the diabetes data to start exploring.
```python
#Step2
diabetes_data= pd.read_csv("diabetes.csv")
print(diabetes_data.head())
```
## Step3: How many columns (features) does the data contain?
Use .len() or .shape 
```python
#Step3 
print(len(diabetes_data.columns))
print(diabetes_data.shape)
```
## Step4: How many rows (observations) does the data contain?
 Use .len() or .shape 
 ```python
#Step4
print(len(diabetes_data))
print(diabetes_data.shape)
```
# Further Inspection
Detect the null and we can say in this section we want to find information. 
## Step5: Do any of the columns in the data contain null (missing) values?
you can use the `.isnull().sum()`
Or
`.info()` method
```python
#Step5 
print(diabetes_data.isnull().sum())
print(diabetes_data.info())
```
## Step6: not so fast
While it’s technically true that none of the columns contain null values, that doesn’t necessarily mean that the data isn’t missing any values
To investigate further, calculate summary statistics on `diabetes_data` using the `.describe()` method.
```python
#Step6
print(diabetes_data.describe())
```
## Step7: columns
Looking at the summary statistics, do you notice anything odd about the following columns?
* Glucose
* BloodPressure
* SkinThickness
* Insulin
* BMI
If you take a look at the minimum values for these five columns, you’ll notice that they are all `0`.
```python
#step7
```
## Step8: do you spot any other outliers in the data?
* The maximum value of the Insulin column is `846`, which is abnormally high.
* The maximum value of the Pregnancies column is `17`. While having `17` pregnancies is not impossible, this case might be something to look further into to determine its accuracy.
As you can see, EDA helps inform the data cleaning process by helping catch things that aren’t immediately obvious.
```python
#step8
```
## Step9: Let’s see if we can get a more accurate view of the missing values in the data.
Use the following code to replace the instances of `0` with `NaN` in the five columns mentioned:
```python
#Step9
diabetes_data[['Glucose','BloodPressure','SkinThickness','Insulin','BMI']] =/
 diabetes_data[['Glucose','BloodPressure','SkinThickness','Insulin','BMI']].replace(0,np.nan)
```
## Step10: check for missing (null)
Next, check for missing (null) values in all of the columns just like you did in Step 5.Now how many missing values are there?
```python
#Step10
print(diabetes_data.isnull().sum())
print(diabetes_data.info())
```





