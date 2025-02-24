### **What is Boolean Indexing in Pandas?**  
**Boolean indexing** is a technique in **pandas** that allows us to filter data based on **conditions**. It works by applying a condition on a `DataFrame` or `Series`, which results in a **Boolean array** (`True` or `False` values). The `True` values select the rows, while the `False` values are excluded.
## Use & | ! combine multiple conditons also use () . 

---

### **How Does Boolean Indexing Work?**  
Boolean indexing works in **three steps**:

1️⃣ **Apply a Condition** → Generates a Boolean Series (`True`/`False`).  
2️⃣ **Pass the Boolean Series to the DataFrame** → Selects only the `True` rows.  
3️⃣ **Returns a Filtered DataFrame**.

---

### **Example: Boolean Indexing in Pandas**  
#### **1️⃣ Creating a Sample DataFrame**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Eve'],
    'Age': [25, 30, 35, 40, 22],
    'Salary': [50000, 60000, 70000, 80000, 55000],
    'Department': ['HR', 'IT', 'Finance', 'IT', 'HR']
}

df = pd.DataFrame(data)
print(df)
```

🔹 **Original DataFrame:**
```
     Name  Age  Salary Department
0   Alice   25  50000        HR
1     Bob   30  60000        IT
2  Charlie   35  70000  Finance
3   David   40  80000        IT
4     Eve   22  55000        HR
```

---

#### **2️⃣ Applying Boolean Indexing**
##### **🔹 Example 1: Filter rows where `Age > 30`**
```python
mask = df['Age'] > 30
filtered_df = df[mask]   # Using the Boolean mask to filter
print(filtered_df)
```
🔹 **Output:**
```
     Name  Age  Salary Department
2  Charlie   35  70000  Finance
3   David   40  80000        IT
```

---

##### **🔹 Example 2: Filter employees from the `IT` department**
```python
df_it = df[df['Department'] == 'IT']
print(df_it)
```
🔹 **Output:**
```
    Name  Age  Salary Department
1   Bob   30  60000        IT
3 David   40  80000        IT
```

---

##### **🔹 Example 3: Multiple Conditions (AND Condition - `&`)**
```python
df_filtered = df[(df['Age'] > 24) & (df['Salary'] > 60000)]
print(df_filtered)
```
🔹 **Output:**
```
     Name  Age  Salary Department
2  Charlie   35  70000  Finance
3   David   40  80000        IT
```

---

##### **🔹 Example 4: Multiple Conditions (OR Condition - `|`)**
```python
df_filtered = df[(df['Age'] > 35) | (df['Department'] == 'HR')]
print(df_filtered)
```
🔹 **Output:**
```
    Name  Age  Salary Department
0  Alice   25  50000        HR
3  David   40  80000        IT
4    Eve   22  55000        HR
```

---

### **Key Points to Remember**
✔ **Boolean indexing filters rows based on conditions.**  
✔ **Use `&` for AND, `|` for OR, and `~` for NOT (negation).**  
✔ **Parentheses are required around conditions to avoid precedence issues.**  

