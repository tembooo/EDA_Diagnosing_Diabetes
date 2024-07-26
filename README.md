# EDA_Diagnosing_Diabetes
In this project, you’ll imagine you are a data scientist interested in exploring data that looks at how certain diagnostic factors affect the diabetes outcome of women patients. You will use your EDA skills to help inspect, clean, and validate the data. <br/>
Note: This<a href="https://bit.ly/2BNk3P1](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database">`dataset`<a/> is from the National Institute of Diabetes and Digestive and Kidney Diseases. 
![EDA_Diagnosing_Diabetes](https://github.com/user-attachments/assets/d0ae5a92-e9a1-4e1d-8bdd-d529203e9a29)
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
## Step11: why we have missing data?
Let’s take a closer look at these rows to get a better idea of why some data might be missing.
Print out all of the rows that contain missing (null) values.
```python
#Step11
print(diabetes_data[diabetes_data.isnull().any(axis=1)])

```
## Step12: patterns
Go through the rows with missing data. Do you notice any patterns or overlaps between the missing data?
 In fact, every single row with at least one missing value also has a missing value in the `insulin` column. 
If patients did not have their insulin measured, why might they also not have had these other measurements taken?
Depending on how much data is missing, you might choose to remove specific rows or impute the missing values somehow.

## Step13: Does the result match what you would expect?
To print the data types of each column, you can use `.dtypes`:
Alternatively, you can use the `.info()` method, which will print out a concise summary of the DataFrame with the data types of each column included:
```python
#Step12
#Step13
print(diabetes_data.dtypes)
print(diabetes_data.info())
```
## Step14: Convert Type of data
To figure out why the Outcome column is of type `object (string)` instead of type `int64`, print out the unique values in the Outcome column.
```python
#Step14
print(diabetes_data.Outcome.unique())
```
Notice that we have instances of the character `'O’` in addition to the number `0`.<br/>
The documentation tells us that the value of the Outcome column should either be a `0` or a `1`, so it seems likely that instances of the character `'O’` are misentries.<br/>

## Step15: How might you resolve this issue?
A possible next step would be to replace instances of 'O' with 0 and convert the Outcome column to type int64.
```python
#Step15
diabetes_data["Outcome"] = diabetes_data["Outcome"].replace("O","0")
print(diabetes_data.Outcome.unique())
```
# Full code
```python
import codecademylib3
import pandas as pd
import numpy as np
#Step1 
#Step2
diabetes_data= pd.read_csv("diabetes.csv")
print(diabetes_data.head())
#Step3 
print(len(diabetes_data.columns))
print(diabetes_data.shape)
#Step4
print(len(diabetes_data))
print(diabetes_data.shape)
#Step5 
print(diabetes_data.isnull().sum())
print(diabetes_data.info())
#Step6
print(diabetes_data.describe())
#Step7
#Step8
#Step9
diabetes_data[['Glucose','BloodPressure','SkinThickness','Insulin','BMI']] = /
diabetes_data[['Glucose','BloodPressure','SkinThickness','Insulin','BMI']].replace(0,np.nan)
#Step10
print(diabetes_data.isnull().sum())
print(diabetes_data.info())
#Step11
print(diabetes_data[diabetes_data.isnull().any(axis=1)])
#Step12
#Step13
print(diabetes_data.dtypes)
print(diabetes_data.info())
#Step14
print(diabetes_data.Outcome.unique())
#Step15
diabetes_data["Outcome"] = diabetes_data["Outcome"].replace("O","0")
print(diabetes_data.Outcome.unique())
```





