In **Pandas**, missing values can appear in different forms. They generally fall into the following types:

### 1. **Standard Missing Values (`NaN` or `None`)**
   - These are explicitly marked as missing using `NaN` (from NumPy) or `None` (Python's built-in type).
   - Example:
     ```python
     import pandas as pd
     import numpy as np

     df = pd.DataFrame({'A': [1, 2, np.nan, 4], 'B': [None, 5, 6, 7]})
     print(df)
     ```
     Output:
     ```
        A    B
     0  1.0  NaN
     1  2.0  5.0
     2  NaN  6.0
     3  4.0  7.0
     ```

### 2. **Custom-Defined Missing Values (Sentinel Values)**
   - Some datasets use specific values (e.g., `-999`, `"missing"`, `"NA"`) to represent missing data.
   - Example:
     ```python
     df = pd.DataFrame({'A': [1, -999, 3], 'B': ['missing', 2, 3]})
     print(df)
     ```
   - These must be explicitly handled using `replace()` or `na_values` in `read_csv()`:
     ```python
     df.replace([-999, 'missing'], np.nan, inplace=True)
     ```

### 3. **Implicit Missing Values (Absent Data)**
   - These occur when an index exists, but no corresponding data is available.
   - Example:
     ```python
     df = pd.Series([1, 2, 3], index=[0, 1, 3])
     print(df)
     ```
     ```
     0    1
     1    2
     3    3
     dtype: int64
     ```
   - The index `2` is missing, creating an implicit missing value.

### 4. **Infinite Values (`Inf` or `-Inf`)**
   - While `Inf` and `-Inf` are not technically missing values, they often need to be treated as such.
   - Example:
     ```python
     df = pd.DataFrame({'A': [1, np.inf, 3, -np.inf]})
     df.replace([np.inf, -np.inf], np.nan, inplace=True)
     ```

### Handling Missing Values
- `df.isna()` → Detect missing values.
- `df.dropna()` → Remove rows/columns with missing values.
- `df.fillna(value)` → Fill missing values.
Handling missing values depends on the **data type** and the nature of the missing data. Below are various techniques categorized by **data types**:

---

## **1. Numeric Data (Integers & Floats)**
### Techniques:
#### a) **Removing Missing Values**
   - Use when missing values are few and removing them won’t impact the analysis.
   ```python
   df.dropna(subset=['column_name'], inplace=True)
   ```

#### b) **Imputation with Mean/Median/Mode**
   - **Mean**: For normally distributed data.
   - **Median**: For skewed data.
   - **Mode**: For categorical-like numeric values.
   ```python
   df['column_name'].fillna(df['column_name'].mean(), inplace=True)
   df['column_name'].fillna(df['column_name'].median(), inplace=True)
   df['column_name'].fillna(df['column_name'].mode()[0], inplace=True)
   ```

#### c) **Interpolate Missing Values (Time-Series Data)**
   - Useful for trend-based data.
   ```python
   df['column_name'].interpolate(method='linear', inplace=True)
   ```

#### d) **Predictive Imputation (ML-based)**
   - Use regression or KNN imputation:
   ```python
   from sklearn.impute import KNNImputer
   imputer = KNNImputer(n_neighbors=3)
   df[['column_name']] = imputer.fit_transform(df[['column_name']])
   ```

---

## **2. Categorical Data (Strings, Object, or Categorical)**
### Techniques:
#### a) **Imputation with Mode (Most Frequent Value)**
   ```python
   df['category_column'].fillna(df['category_column'].mode()[0], inplace=True)
   ```

#### b) **Imputation with a Special Category ('Unknown' or 'Missing')**
   ```python
   df['category_column'].fillna('Unknown', inplace=True)
   ```

#### c) **Using Predictive Models (e.g., Decision Trees)**
   - Use classification models like Decision Trees or Naïve Bayes to predict missing values.

#### d) **Using Forward Fill (For Sequential Data)**
   ```python
   df['category_column'].fillna(method='ffill', inplace=True)
   ```

#### e) **Using Backward Fill**
   ```python
   df['category_column'].fillna(method='bfill', inplace=True)
   ```

---

## **3. Boolean Data (True/False, 0/1)**
### Techniques:
#### a) **Fill with Mode (Most Frequent Value)**
   ```python
   df['boolean_column'].fillna(df['boolean_column'].mode()[0], inplace=True)
   ```

#### b) **Convert to Categorical and Assign Default Values**
   ```python
   df['boolean_column'].fillna(False, inplace=True)
   ```

---

## **4. Time-Series Data**
### Techniques:
#### a) **Forward Fill (Previous Value Propagation)**
   ```python
   df['time_column'].fillna(method='ffill', inplace=True)
   ```

#### b) **Backward Fill (Next Value Propagation)**
   ```python
   df['time_column'].fillna(method='bfill', inplace=True)
   ```

#### c) **Interpolate Based on Trend**
   ```python
   df['time_column'].interpolate(method='time', inplace=True)
   ```

---

## **5. Special Cases (Custom Handling)**
### a) **Dropping Rows/Columns with a High Percentage of Missing Values**
   ```python
   df.dropna(thresh=int(df.shape[1] * 0.7), inplace=True)  # Drop rows with more than 30% missing values
   ```

### b) **Replacing Custom Missing Indicators (`-999, "N/A", "NULL"`)**
   ```python
   df.replace(["N/A", "NULL", -999], np.nan, inplace=True)
   ```
### **`replace()` Method in Pandas**  
The `replace()` method in Pandas is used to **replace values** in a DataFrame or Series. It can be used for:  
✅ Replacing specific values  
✅ Replacing multiple values at once  
✅ Using regex for pattern-based replacement  
✅ Replacing NaN values  

---

## **1. Replacing Specific Values**
You can replace a **single** or **multiple** values.

### **Example: Replace a Specific Value**
```python
import pandas as pd

df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
df.replace(2, 99, inplace=True)  # Replace 2 with 99
print(df)
```
**Output:**
```
     A  B
0   1  4
1  99  5
2   3  6
```

### **Example: Replace Multiple Values**
```python
df.replace({3: 100, 4: 200}, inplace=True)  # Replace 3 with 100 and 4 with 200
```

---

## **2. Replacing Values in a Specific Column**
```python
df['A'] = df['A'].replace(99, 50)  # Replace 99 with 50 in column 'A'
```

---

## **3. Replacing NaN Values**
If your dataset has missing values (`NaN`), you can replace them using `replace()`.

### **Example: Replace NaN with a Specific Value**
```python
import numpy as np

df = pd.DataFrame({'A': [1, np.nan, 3], 'B': [4, 5, np.nan]})
df.replace(np.nan, 0, inplace=True)  # Replace NaN with 0
print(df)
```
**Output:**
```
     A  B
0  1.0  4.0
1  0.0  5.0
2  3.0  0.0
```

---

## **4. Using Regex for Pattern-Based Replacement**
```python
df = pd.DataFrame({'Names': ['John_', 'Amy_', 'Sam_']})
df.replace('_', '', regex=True, inplace=True)  # Remove underscore (_) from all names
print(df)
```
**Output:**
```
   Names
0   John
1    Amy
2    Sam
```

---

## **Summary**
| **Usage**          | **Example**                                      |
|--------------------|------------------------------------------------|
| Replace single value | `df.replace(2, 99)`                           |
| Replace multiple values | `df.replace({2: 99, 3: 100})`           |
| Replace in a column | `df['A'] = df['A'].replace(99, 50)`           |
| Replace NaN | `df.replace(np.nan, 0)`                      |
| Replace using regex | `df.replace('_', '', regex=True)`          |

### **How `isnull()` and `notnull()` Work in Pandas**
The `isnull()` and `notnull()` methods in Pandas operate on **Series** and **DataFrames** to identify missing values (`NaN`).  
They return a **Boolean mask** where:  
- `isnull()` → **`True`** for missing (`NaN`) values, **`False`** for non-missing values.  
- `notnull()` → **`False`** for missing (`NaN`) values, **`True`** for non-missing values.

---

## **1. `isnull()` - How It Works**
### **On a Pandas Series**
```python
import pandas as pd
import numpy as np

s = pd.Series([1, 2, np.nan, 4])
print(s.isnull())
```
**Output:**
```
0    False
1    False
2     True
3    False
dtype: bool
```
🔹 **Explanation:**  
- The third value (`np.nan`) is **`True`** because it is missing.

---

### **On a Pandas DataFrame**
```python
df = pd.DataFrame({
    'A': [1, 2, np.nan],
    'B': [4, np.nan, 6]
})

print(df.isnull())
```
**Output:**
```
       A      B
0  False  False
1  False   True
2   True  False
```
🔹 **Explanation:**  
- `True` marks where `NaN` is present.

---

## **2. `notnull()` - How It Works**
It works **opposite to `isnull()`**, marking **`True`** for non-missing values.

### **On a Pandas Series**
```python
print(s.notnull())
```
**Output:**
```
0     True
1     True
2    False
3     True
dtype: bool
```
🔹 **Explanation:**  
- The third value (`np.nan`) is **`False`**, as it is missing.

---

### **On a Pandas DataFrame**
```python
print(df.notnull())
```
**Output:**
```
       A      B
0   True   True
1   True  False
2  False   True
```
🔹 **Explanation:**  
- `False` marks where `NaN` is present.

---

## **3. How They Work Internally**
Internally, `isnull()` and `notnull()` check if a value is a **special floating-point `NaN` (Not a Number)**.

### **Example with Python's `None`**
```python
df = pd.DataFrame({'A': [1, None, 3]})
print(df.isnull())  
```
**Output:**
```
       A
0  False
1   True
2  False
```
🔹 **Explanation:**  
- `None` is treated as `NaN` in Pandas.

---

## **4. Use Cases**
✅ **Filtering Missing Values**
```python
df[df['A'].isnull()]  # Get rows where 'A' is NaN
```

✅ **Filtering Non-Missing Values**
```python
df[df['A'].notnull()]  # Get rows where 'A' is NOT NaN
```

✅ **Counting Missing Values**
```python
df.isnull().sum()  # Count NaNs per column
```

✅ **Replacing Missing Values**
```python
df.fillna(0, inplace=True)  # Replace NaNs with 0
```

