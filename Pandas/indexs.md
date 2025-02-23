## **🔹 What is an Index in Pandas?**  
An **index** in Pandas is a **unique identifier** for each row in a Series or DataFrame. It helps in:  
- **Efficient data selection** (e.g., `df.loc[index_value]`)  
- **Data alignment in operations**  
- **Faster lookups**  

---

## **🔹 Index in Pandas Series**
Each **Series** has an index by default:  
```python
import pandas as pd

s = pd.Series([10, 20, 30, 40])
print(s)
```
#### **🔹 Output**
```
0    10
1    20
2    30
3    40
dtype: int64
```
- The **left column** (`0,1,2,3`) is the index.
- The **right column** is the actual data.

### **🔹 Custom Index**
```python
s = pd.Series([10, 20, 30, 40], index=['a', 'b', 'c', 'd'])
print(s)
```
#### **🔹 Output**
```
a    10
b    20
c    30
d    40
dtype: int64
```
---

## **🔹 Index in Pandas DataFrame**
A **DataFrame** index represents the row labels:
```python
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35]
}

df = pd.DataFrame(data)
print(df)
```
#### **🔹 Output**
```
     Name  Age
0   Alice   25
1     Bob   30
2  Charlie   35
```
- The **leftmost column (0,1,2)** is the index.

### **🔹 Setting a Custom Index**
```python
df.set_index("Name", inplace=True)
print(df)
```
#### **🔹 Output**
```
        Age
Name       
Alice    25
Bob      30
Charlie  35
```
---

## **🔹 Resetting the Index**
If you need to remove a custom index:
```python
df.reset_index(inplace=True)
print(df)
```
Restores the default integer index.

---

## **🔹 Summary**
| Feature  | Default Index | Custom Index |
|----------|--------------|--------------|
| Series   | 0,1,2,...    | Can be set to labels |
| DataFrame | 0,1,2,...   | Can be set to column values |
| Change Index | `df.set_index()` | `df.reset_index()` |

## **🔹 `loc` vs `iloc` in Pandas**
Both `.loc[]` and `.iloc[]` are used for **data selection** in Pandas, but they work differently.

| Feature  | `.loc[]` | `.iloc[]` |
|----------|---------|-----------|
| Type of Indexing | **Label-based** | **Integer-based** |
| Works with | Row/column labels | Row/column positions (0-based index) |
| Inclusive of end index? | ✅ Yes | ❌ No (like Python slicing) |
| Example | `df.loc[2]` (row with index 2) | `df.iloc[2]` (third row) |

---

## **🔹 Example DataFrame**
```python
import pandas as pd

data = {
    "Name": ["Alice", "Bob", "Charlie", "David"],
    "Age": [25, 30, 35, 40],
    "City": ["New York", "Los Angeles", "Chicago", "Houston"]
}

df = pd.DataFrame(data, index=["A", "B", "C", "D"])  # Custom index
print(df)
```
#### **🔹 Output**
```
      Name  Age         City
A   Alice   25     New York
B     Bob   30  Los Angeles
C  Charlie   35      Chicago
D   David   40      Houston
```

---

## **1️⃣ `.loc[]` → Label-Based Selection**
- Uses row/column **labels**
- **Includes** the last index in slicing

### **🔹 Selecting a Row by Label**
```python
print(df.loc["B"])
```
#### **Output**
```
Name       Bob
Age         30
City  Los Angeles
Name: B, dtype: object
```

### **🔹 Selecting Multiple Rows**
```python
print(df.loc[["A", "C"]])
```
#### **Output**
```
      Name  Age      City
A   Alice   25  New York
C  Charlie   35  Chicago
```

### **🔹 Selecting a Range (Inclusive)**
```python
print(df.loc["A":"C"])
```
#### **Output**
```
      Name  Age      City
A   Alice   25  New York
B     Bob   30  Los Angeles
C  Charlie   35  Chicago
```
🔹 **Note:** "C" is **included** in the output.

---

## **2️⃣ `.iloc[]` → Position-Based Selection**
- Uses **integer** positions (like Python lists)
- **Excludes** the last index in slicing

### **🔹 Selecting a Row by Position**
```python
print(df.iloc[1])  # Second row
```
#### **Output**
```
Name       Bob
Age         30
City  Los Angeles
Name: B, dtype: object
```

### **🔹 Selecting Multiple Rows**
```python
print(df.iloc[[0, 2]])  # First and third rows
```
#### **Output**
```
      Name  Age      City
A   Alice   25  New York
C  Charlie   35  Chicago
```

### **🔹 Selecting a Range (Exclusive)**
```python
print(df.iloc[0:2])  # First two rows (index 2 is excluded)
```
#### **Output**
```
      Name  Age         City
A   Alice   25     New York
B     Bob   30  Los Angeles
```
🔹 **Note:** Row at index `2` (Charlie) is **excluded**.

---

## **🔹 Column Selection with `.loc[]` and `.iloc[]`**
| Operation | `.loc[]` | `.iloc[]` |
|-----------|---------|-----------|
| Single column | `df.loc[:, "Age"]` | `df.iloc[:, 1]` |
| Multiple columns | `df.loc[:, ["Name", "City"]]` | `df.iloc[:, [0, 2]]` |
| Column range | `df.loc[:, "Age":"City"]` | `df.iloc[:, 1:3]` |

---

## **🔹 Key Differences**
| Feature | `.loc[]` | `.iloc[]` |
|---------|---------|-----------|
| Uses | Labels | Positions |
| Slicing | Inclusive | Exclusive |
| Speed | Slightly slower (needs label lookup) | Faster (direct integer access) |

---

## **🔹 Summary**
- Use `.loc[]` when working with **labels**.
- Use `.iloc[]` when working with **integer positions**.
- **Slicing in `.loc[]` is inclusive**, while **slicing in `.iloc[]` is exclusive**.

## **🔹 Why Reset an Index in Pandas?**
The `.reset_index()` method in Pandas is used to **reset the index** of a DataFrame.  
This is useful in scenarios like:
1. **Restoring Default Index:** If a DataFrame has a custom index (e.g., after using `.set_index()`), resetting it **restores the default integer index**.
2. **After Filtering or Grouping:** When filtering or performing operations like `groupby()`, the index may not be sequential. Resetting it **reorganizes the index**.
3. **After Dropping Rows:** If you remove rows using `.drop()`, the index remains unchanged. Resetting it ensures a **clean, sequential index**.

---

## **🔹 How Does `reset_index()` Work?**
The `.reset_index()` method works by:
1. **Moving the current index to a column** (unless `drop=True`).
2. **Creating a new default integer index** (0,1,2,...).

### **Example**
```python
import pandas as pd

data = {
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [25, 30, 35]
}

df = pd.DataFrame(data, index=["A", "B", "C"])  # Setting custom index
print(df)
```
#### **🔹 Output**
```
      Name  Age
A   Alice   25
B     Bob   30
C  Charlie   35
```

### **🔹 Resetting Index (Default Behavior)**
```python
df_reset = df.reset_index()
print(df_reset)
```
#### **🔹 Output**
```
  index     Name  Age
0     A   Alice   25
1     B     Bob   30
2     C  Charlie   35
```
- The original **index becomes a column** (`index`).
- A new **integer index (0,1,2)** is created.

---

## **🔹 What is `drop=True` in `reset_index()`?**
If you **don’t want to keep the old index** as a column, use `drop=True`:
```python
df_reset = df.reset_index(drop=True)
print(df_reset)
```
#### **🔹 Output**
```
      Name  Age
0   Alice   25
1     Bob   30
2  Charlie   35
```
- The old index **(A, B, C)** is removed.
- The DataFrame gets a **new default index (0,1,2)**.

---

## **🔹 Summary of `reset_index()`**
| Option | Effect |
|--------|--------|
| `reset_index()` | Moves the old index to a new column and resets the index to default (0,1,2,...) |
| `reset_index(drop=True)` | Removes the old index and resets to default |

---

### **🔹 When Should You Use `reset_index()`?**
✔️ After **setting a custom index** and needing a default one again.  
✔️ After **filtering or dropping rows**, to **reorganize the index**.  
✔️ Before **saving to a CSV file** (to ensure a clean format).  
