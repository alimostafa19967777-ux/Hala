```python
import pandas as pd

# Чтение локального файла
df = pd.read_csv("processed_asthma.csv")

# Просмотр первых 5 строк
df.head()

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
      <th>Patient_ID</th>
      <th>Age</th>
      <th>Gender</th>
      <th>BMI</th>
      <th>Smoking_Status</th>
      <th>Family_History</th>
      <th>Allergies</th>
      <th>Air_Pollution_Level</th>
      <th>Physical_Activity_Level</th>
      <th>Occupation_Type</th>
      <th>Comorbidities</th>
      <th>Medication_Adherence</th>
      <th>Number_of_ER_Visits</th>
      <th>Peak_Expiratory_Flow</th>
      <th>FeNO_Level</th>
      <th>Has_Asthma</th>
      <th>Asthma_Control_Level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ASTH100000</td>
      <td>52</td>
      <td>Female</td>
      <td>27.6</td>
      <td>Former</td>
      <td>1</td>
      <td>NaN</td>
      <td>Moderate</td>
      <td>Sedentary</td>
      <td>Outdoor</td>
      <td>Diabetes</td>
      <td>0.38</td>
      <td>0</td>
      <td>421.0</td>
      <td>46.0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ASTH100001</td>
      <td>15</td>
      <td>Male</td>
      <td>24.6</td>
      <td>Former</td>
      <td>0</td>
      <td>Dust</td>
      <td>Low</td>
      <td>Moderate</td>
      <td>Indoor</td>
      <td>Both</td>
      <td>0.60</td>
      <td>2</td>
      <td>297.6</td>
      <td>22.9</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ASTH100002</td>
      <td>72</td>
      <td>Female</td>
      <td>17.6</td>
      <td>Never</td>
      <td>0</td>
      <td>NaN</td>
      <td>Moderate</td>
      <td>Moderate</td>
      <td>Indoor</td>
      <td>NaN</td>
      <td>0.38</td>
      <td>0</td>
      <td>303.3</td>
      <td>15.3</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ASTH100003</td>
      <td>61</td>
      <td>Male</td>
      <td>16.8</td>
      <td>Never</td>
      <td>0</td>
      <td>Multiple</td>
      <td>High</td>
      <td>Sedentary</td>
      <td>Outdoor</td>
      <td>Both</td>
      <td>0.60</td>
      <td>1</td>
      <td>438.0</td>
      <td>40.1</td>
      <td>1</td>
      <td>Poorly Controlled</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ASTH100004</td>
      <td>21</td>
      <td>Male</td>
      <td>30.2</td>
      <td>Never</td>
      <td>0</td>
      <td>NaN</td>
      <td>Moderate</td>
      <td>Active</td>
      <td>Indoor</td>
      <td>NaN</td>
      <td>0.82</td>
      <td>3</td>
      <td>535.0</td>
      <td>27.7</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Проверка структуры данных
df.info()

# Основная статистика для числовых столбцов
df.describe()

```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 10000 entries, 0 to 9999
    Data columns (total 17 columns):
     #   Column                   Non-Null Count  Dtype  
    ---  ------                   --------------  -----  
     0   Patient_ID               10000 non-null  object 
     1   Age                      10000 non-null  int64  
     2   Gender                   10000 non-null  object 
     3   BMI                      10000 non-null  float64
     4   Smoking_Status           10000 non-null  object 
     5   Family_History           10000 non-null  int64  
     6   Allergies                7064 non-null   object 
     7   Air_Pollution_Level      10000 non-null  object 
     8   Physical_Activity_Level  10000 non-null  object 
     9   Occupation_Type          10000 non-null  object 
     10  Comorbidities            5033 non-null   object 
     11  Medication_Adherence     10000 non-null  float64
     12  Number_of_ER_Visits      10000 non-null  int64  
     13  Peak_Expiratory_Flow     10000 non-null  float64
     14  FeNO_Level               10000 non-null  float64
     15  Has_Asthma               10000 non-null  int64  
     16  Asthma_Control_Level     2433 non-null   object 
    dtypes: float64(4), int64(4), object(9)
    memory usage: 1.3+ MB
    




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
      <th>Age</th>
      <th>BMI</th>
      <th>Family_History</th>
      <th>Medication_Adherence</th>
      <th>Number_of_ER_Visits</th>
      <th>Peak_Expiratory_Flow</th>
      <th>FeNO_Level</th>
      <th>Has_Asthma</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>10000.000000</td>
      <td>10000.000000</td>
      <td>10000.000000</td>
      <td>10000.000000</td>
      <td>10000.000000</td>
      <td>10000.000000</td>
      <td>10000.000000</td>
      <td>10000.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>44.930700</td>
      <td>25.053320</td>
      <td>0.303400</td>
      <td>0.497998</td>
      <td>1.015900</td>
      <td>400.884090</td>
      <td>25.101420</td>
      <td>0.243300</td>
    </tr>
    <tr>
      <th>std</th>
      <td>25.653559</td>
      <td>4.874466</td>
      <td>0.459749</td>
      <td>0.224809</td>
      <td>1.020564</td>
      <td>97.531113</td>
      <td>9.840184</td>
      <td>0.429096</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>15.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>150.000000</td>
      <td>5.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>23.000000</td>
      <td>21.600000</td>
      <td>0.000000</td>
      <td>0.320000</td>
      <td>0.000000</td>
      <td>334.800000</td>
      <td>18.200000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>45.000000</td>
      <td>25.000000</td>
      <td>0.000000</td>
      <td>0.500000</td>
      <td>1.000000</td>
      <td>402.500000</td>
      <td>25.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>67.000000</td>
      <td>28.400000</td>
      <td>1.000000</td>
      <td>0.670000</td>
      <td>2.000000</td>
      <td>468.700000</td>
      <td>31.700000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>89.000000</td>
      <td>45.000000</td>
      <td>1.000000</td>
      <td>0.990000</td>
      <td>6.000000</td>
      <td>600.000000</td>
      <td>63.900000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Подсчет пропущенных значений
missing = df.isnull().sum()

# Процент пропусков
missing_percent = (missing / len(df)) * 100

# Создаем таблицу с результатами
missing_df = pd.DataFrame({
    'Пропущенные значения': missing,
    'Процент %': missing_percent
})

missing_df

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
      <th>Пропущенные значения</th>
      <th>Процент %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Patient_ID</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Age</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Gender</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>BMI</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Smoking_Status</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Family_History</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Allergies</th>
      <td>2936</td>
      <td>29.36</td>
    </tr>
    <tr>
      <th>Air_Pollution_Level</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Physical_Activity_Level</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Occupation_Type</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Comorbidities</th>
      <td>4967</td>
      <td>49.67</td>
    </tr>
    <tr>
      <th>Medication_Adherence</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Number_of_ER_Visits</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Peak_Expiratory_Flow</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>FeNO_Level</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Has_Asthma</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Asthma_Control_Level</th>
      <td>7567</td>
      <td>75.67</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Выбираем числовые столбцы
numeric_cols = df.select_dtypes(include=['int64', 'float64']).columns

# Расчет IQR для выявления выбросов
Q1 = df[numeric_cols].quantile(0.25)
Q3 = df[numeric_cols].quantile(0.75)
IQR = Q3 - Q1

# Подсчет выбросов для каждого числового столбца
outliers = ((df[numeric_cols] < (Q1 - 1.5 * IQR)) | (df[numeric_cols] > (Q3 + 1.5 * IQR))).sum()
outliers_percent = (outliers / len(df)) * 100

outliers_df = pd.DataFrame({
    'Выбросы': outliers,
    'Процент %': outliers_percent
})
outliers_df

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
      <th>Выбросы</th>
      <th>Процент %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Age</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>BMI</th>
      <td>24</td>
      <td>0.24</td>
    </tr>
    <tr>
      <th>Family_History</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Medication_Adherence</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Number_of_ER_Visits</th>
      <td>3</td>
      <td>0.03</td>
    </tr>
    <tr>
      <th>Peak_Expiratory_Flow</th>
      <td>0</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>FeNO_Level</th>
      <td>41</td>
      <td>0.41</td>
    </tr>
    <tr>
      <th>Has_Asthma</th>
      <td>2433</td>
      <td>24.33</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Создаем сводную таблицу с пропусками и выбросами
metrics_df = pd.DataFrame({
    'Пропущенные значения %': (df.isnull().sum() / len(df)) * 100,
    'Выбросы %': ((df[numeric_cols] < (Q1 - 1.5*IQR)) | (df[numeric_cols] > (Q3 + 1.5*IQR))).sum() / len(df) * 100
})

# Для категориальных столбцов добавляем только пропуски
for col in df.select_dtypes(include=['object']).columns:
    if col not in metrics_df.index:
        metrics_df.loc[col] = [df[col].isnull().sum() / len(df) * 100, 0]

metrics_df = metrics_df.sort_index()
metrics_df


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
      <th>Пропущенные значения %</th>
      <th>Выбросы %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Age</th>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Air_Pollution_Level</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Allergies</th>
      <td>29.36</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Asthma_Control_Level</th>
      <td>75.67</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>BMI</th>
      <td>0.00</td>
      <td>0.24</td>
    </tr>
    <tr>
      <th>Comorbidities</th>
      <td>49.67</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Family_History</th>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>FeNO_Level</th>
      <td>0.00</td>
      <td>0.41</td>
    </tr>
    <tr>
      <th>Gender</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Has_Asthma</th>
      <td>0.00</td>
      <td>24.33</td>
    </tr>
    <tr>
      <th>Medication_Adherence</th>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Number_of_ER_Visits</th>
      <td>0.00</td>
      <td>0.03</td>
    </tr>
    <tr>
      <th>Occupation_Type</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Patient_ID</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Peak_Expiratory_Flow</th>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Physical_Activity_Level</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Smoking_Status</th>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
