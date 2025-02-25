 how `.describe()` works in **pandas**:

---

### **🔹 `.describe()` Method in Pandas**
The `.describe()` method generates summary statistics for both **numerical** and **non-numerical** (categorical/boolean) data in a **DataFrame** or **Series**.

#### **1️⃣ Numerical Data (`int`, `float`)**
Provides:
- `count` – Number of non-null values  
- `mean` – Average value  
- `std` – Standard deviation  
- `min` – Minimum value  
- `25%`, `50%`, `75%` – Quartiles  
- `max` – Maximum value  

#### **2️⃣ Categorical (Object/String) Data**
Provides:
- `count` – Number of non-null values  
- `unique` – Number of unique values  
- `top` – Most frequently occurring value  
- `freq` – Frequency of the top value  

#### **3️⃣ Boolean Data**
Provides the same summary as categorical data:
- `count`, `unique`, `top`, and `freq`  

#### **4️⃣ Mixed Data (Both Numerical & Categorical)**
- Use `.describe(include="all")` to get both types in one output.  
- Numerical columns will have statistical measures, while categorical columns will have **count, unique, top, and freq**.

---

### **Example**
```python
import pandas as pd

df = pd.DataFrame({
    "Age": [25, 30, 35, 40, 22],
    "Gender": ["Male", "Female", "Male", "Female", "Male"],
    "Passed": [True, False, True, True, False]
})

print(df.describe(include="all"))
```

---

### **💡 Key Takeaways**
✅ `.describe()` is useful for quick **exploratory data analysis (EDA)**.  
✅ By default, it only summarizes **numerical columns**.  
✅ Use `include="object"` for categorical, `include="bool"` for booleans, and `include="all"` for everything.  
