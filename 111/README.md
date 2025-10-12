# EDA для датасета processed_asthma.csv

## 1️⃣ Первичный просмотр данных

После загрузки датасета `processed_asthma.csv` были выведены первые 5 строк таблицы.

Данные содержат как числовые, так и категориальные признаки.  
Основные столбцы:
- **Числовые:** `Age`, `BMI`, `Family_History`, `Medication_Adherence`, `Number_of_ER_Visits`, `Peak_Expiratory_Flow`, `FeNO_Level`, `Has_Asthma`
- **Категориальные:** `Patient_ID`, `Gender`, `Smoking_Status`, `Allergies`, `Air_Pollution_Level`, `Physical_Activity_Level`, `Occupation_Type`, `Comorbidities`, `Asthma_Control_Level`

В таблице видно наличие пропусков (NaN) в некоторых столбцах, например:
- `Allergies`
- `Comorbidities`
- `Asthma_Control_Level`

Структура данных выглядит корректной и последовательной: каждая строка представляет одного пациента с набором медицинских и поведенческих характеристик.  
Следующий шаг — анализ типов данных и общей статистики.

---

## 2️⃣ Информация о данных и базовая статистика

Проведен анализ структуры данных с помощью `df.info()` и `df.describe()`.

### Основные выводы:

- Датасет содержит **10,000 строк и 17 столбцов**.
- Типы данных:
  - **int64:** `Age`, `Family_History`, `Number_of_ER_Visits`, `Has_Asthma`
  - **float64:** `BMI`, `Medication_Adherence`, `Peak_Expiratory_Flow`, `FeNO_Level`
  - **object:** `Patient_ID`, `Gender`, `Smoking_Status`, `Allergies`, `Air_Pollution_Level`, `Physical_Activity_Level`, `Occupation_Type`, `Comorbidities`, `Asthma_Control_Level`
- Некоторые столбцы содержат пропущенные значения:
  - `Allergies` — 2,936 пропусков
  - `Comorbidities` — 4,967 пропусков
  - `Asthma_Control_Level` — 7,567 пропусков

### Статистика числовых признаков:

| Признак | Среднее | Стандартное отклонение | Минимум | 25% | 50% | 75% | Максимум |
|---------|--------|----------------------|---------|-----|-----|-----|---------|
| Age | 44.93 | 25.65 | 1 | 23 | 45 | 67 | 89 |
| BMI | 25.05 | 4.87 | 15 | 21.6 | 25 | 28.4 | 45 |
| Family_History | 0.30 | 0.46 | 0 | 0 | 0 | 1 | 1 |
| Medication_Adherence | 0.50 | 0.22 | 0 | 0.32 | 0.5 | 0.67 | 0.99 |
| Number_of_ER_Visits | 1.02 | 1.02 | 0 | 0 | 1 | 2 | 6 |
| Peak_Expiratory_Flow | 400.88 | 97.53 | 150 | 334.8 | 402.5 | 468.7 | 600 |
| FeNO_Level | 25.10 | 9.84 | 5 | 18.2 | 25 | 31.7 | 63.9 |
| Has_Asthma | 0.24 | 0.43 | 0 | 0 | 0 | 0 | 1 |

---

## 3️⃣ Анализ пропущенных значений

- Столбцы без пропусков:
  - `Patient_ID`, `Age`, `Gender`, `BMI`, `Smoking_Status`, `Family_History`, `Air_Pollution_Level`, `Physical_Activity_Level`, `Occupation_Type`, `Medication_Adherence`, `Number_of_ER_Visits`, `Peak_Expiratory_Flow`, `FeNO_Level`, `Has_Asthma`
- Столбцы с пропущенными значениями:
  - `Allergies` — 29,36%
  - `Comorbidities` — 49,67%
  - `Asthma_Control_Level` — 75,67%

### Рекомендации:
- Обработать пропуски либо удалением строк/столбцов, либо заполнением значениями.
- Данные большинства признаков готовы к анализу выбросов.

---

## 4️⃣ Анализ выбросов (Outliers)

- Минимальное количество выбросов:
  - `BMI` — 0,24%
  - `Number_of_ER_Visits` — 0,03%
  - `FeNO_Level` — 0,41%
- Столбцы без выбросов:
  - `Age`, `Family_History`, `Medication_Adherence`, `Peak_Expiratory_Flow`
- Значительное количество выбросов:
  - `Has_Asthma` — 24,33%

### Рекомендации:
- Проверить выбросы в `Has_Asthma`.
- Остальные числовые признаки готовы к дальнейшему анализу.

---

## 5️⃣ Итоговое заключение и сводная таблица метрик

- Столбцы без пропусков и без выбросов: `Age`, `Family_History`, `Medication_Adherence`, `Number_of_ER_Visits`, `Peak_Expiratory_Flow`
- Столбцы с пропущенными значениями: `Allergies`, `Comorbidities`, `Asthma_Control_Level`, а также категориальные признаки (`Gender`, `Patient_ID`, `Occupation_Type`, `Physical_Activity_Level`, `Smoking_Status`, `Air_Pollution_Level`) содержат пропуски в части данных.
- Столбцы с выбросами: `BMI`, `Number_of_ER_Visits`, `FeNO_Level`, `Has_Asthma`

### Рекомендации:
- Обработать пропуски в `Allergies`, `Comorbidities` и `Asthma_Control_Level`.
- Проверить и при необходимости обработать выбросы в `Has_Asthma`.
- Датасет структурирован корректно и готов для дальнейшего анализа и моделирования.
