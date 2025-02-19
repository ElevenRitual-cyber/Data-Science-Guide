
1️⃣ **What is NumPy?** 📌  


NumPy (**Numerical Python**) is a **powerful** Python library for numerical computing. It provides support for **multi-dimensional arrays**, **mathematical functions**, and **efficient data operations**, making it essential for **data science, machine learning, and scientific computing**.  

#### **🔹 Key Features:**  
✅ **ndarray** – Efficient multi-dimensional arrays  
✅ **Vectorized operations** – Faster computations than Python lists  
✅ **Broadcasting** – Perform operations on arrays of different shapes  
✅ **Linear algebra** – Matrix operations, eigenvalues, etc.  
✅ **Random module** – Generate random numbers, distributions  



2️⃣ **Nature of NumPy** 🔍  
**NumPy arrays (ndarray) are homogeneous**, meaning that all elements in a NumPy array must be of the same data type. Unlike Python lists, which can hold mixed data types, NumPy ensures efficiency by storing elements in contiguous memory with a fixed type.  
For example:  
```
import numpy as np
arr = np.array([1, 2, 3, 4])  # All elements are integers
print(arr.dtype)  # Output: int64 (or int32 depending on the system)
arr2 = np.array([1, 2, 3.5, 4])  # A float is included
print(arr2.dtype)  # Output: float64 (NumPy upcasts to maintain homogeneity)
```
3️⃣ **How Does NumPy Handle Non-Homogeneous Data Types?** ⚙️  
NumPy ensures **homogeneity** in arrays through a process called **type upcasting**, which follows a specific set of **type promotion rules**. Here's how it works internally:

---

### 🔹 **How NumPy Handles Mixed Data Types?**  

1. **Identifies the Highest Precision Type**  
   - NumPy scans all elements and determines the **most compatible** data type that can represent all values **without losing information**.  

2. **Upcasts Lower Precision Types**  
   - If different types exist, NumPy **upcasts** elements to the most general type among them.

3. **Stores Elements in a Contiguous Memory Block**  
   - Once the type is determined, all elements are stored as **binary values** in contiguous memory, ensuring efficient computation.

---

### 🔹 **NumPy Type Promotion Rules**
1️⃣ **Integer → Float**  
   - If a mix of integers and floats exists, integers are converted to **float**.  
   ```python
   arr = np.array([1, 2, 3.5])  
   print(arr.dtype)  # float64
   ```
   
2️⃣ **Float → Complex**  
   - If floats and complex numbers are present, floats become **complex**.  
   ```python
   arr = np.array([1.2, 3.5, 2 + 1j])  
   print(arr.dtype)  # complex128
   ```

3️⃣ **Numbers → Strings**  
   - If numbers and strings are mixed, **everything is converted to a string**.  
   ```python
   arr = np.array([1, 2.5, "hello"])  
   print(arr.dtype)  # <U5 (Unicode string)
   ```

4️⃣ **Forcing Object Arrays**  
   - If types can't be upcast meaningfully, NumPy allows using `dtype=object` to store elements as Python objects.  
   ```python
   arr = np.array([1, "hello", 3.5], dtype=object)  
   print(arr.dtype)  # object
   ```

---

### 4️⃣ Understanding `ndarray` in NumPy**  

1️⃣ **What is `ndarray`?** 📌  
2️⃣ **Key Properties of `ndarray`** 🔍  
3️⃣ **Creating an `ndarray`** 🛠️  
4️⃣ **Important Attributes of `ndarray`** 📊  
5️⃣ **Types of NumPy Arrays (1D, 2D, 3D+)** 🔢  
### **What is an `ndarray` in NumPy?**  

An `ndarray` (N-dimensional array) is the **core data structure** of NumPy. It is a **multi-dimensional, homogeneous array** that allows for efficient storage and manipulation of numerical data.

---

### **✅ Key Features of `ndarray`**
1. **Multi-dimensional**: Supports 1D, 2D, 3D, or higher-dimensional arrays.  
2. **Homogeneous**: All elements must be of the **same data type** (e.g., `int`, `float`).  
3. **Efficient Storage**: Uses a contiguous block of memory, making operations fast.  
4. **Vectorized Operations**: Supports element-wise computations without loops.  
5. **Flexible Shape**: Can be **reshaped** and **broadcasted** for operations.

---

### **🚀 Creating an `ndarray`**
You can create an `ndarray` using `numpy.array()`:
```python
import numpy as np

# 1D array
arr1 = np.array([1, 2, 3, 4])

# 2D array (matrix)
arr2 = np.array([[1, 2, 3], [4, 5, 6]])

# 3D array
arr3 = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])

print(arr1)
print(arr2)
print(arr3)
```

---

### **🔹 Important Attributes of `ndarray`**
| Attribute        | Description | Example |
|-----------------|-------------|---------|
| `ndarray.shape` | Returns the shape (dimensions) of the array | `(2,3)` for a 2D array with 2 rows and 3 columns |
| `ndarray.ndim`  | Returns the number of dimensions | `1D`, `2D`, `3D`, etc. |
| `ndarray.size`  | Total number of elements | `6` for an array of shape `(2,3)` |
| `ndarray.dtype` | Data type of elements | `int32`, `float64`, etc. |

Example:
```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

print(arr.shape)  # (2,3)
print(arr.ndim)   # 2
print(arr.size)   # 6
print(arr.dtype)  # int32 (or int64)
```

---
### **✅ Why Use `ndarray` Instead of Lists?**
| Feature          | NumPy `ndarray` | Python List |
|-----------------|----------------|-------------|
| Storage        | Contiguous memory block | Stores references (pointers) |
| Speed          | Much faster due to vectorized operations | Slower, requires loops |
| Type Safety    | Homogeneous (same data type) | Can hold mixed types |
| Mathematical Operations | Built-in, optimized operations | Needs explicit loops |

### 🔹 **Why Does NumPy Do This?**
- **Performance**: NumPy uses **fixed-size** data types, unlike Python lists, making operations **fast**.  
- **Memory Efficiency**: Storing elements in a **single type** ensures efficient memory allocation.  
- **Vectorized Operations**: Consistent types allow **fast mathematical computations** using SIMD (Single Instruction, Multiple Data).  
