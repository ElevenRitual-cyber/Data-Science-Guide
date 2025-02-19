### **Creating `ndarray` and Matrix in NumPy**  

NumPy provides multiple ways to create `ndarray` (N-dimensional arrays) and matrices.

---

## **1️⃣ Creating an `ndarray`**
An `ndarray` is a general-purpose N-dimensional array that can store numerical data efficiently.

### **✅ Using `numpy.array()`**
```python
import numpy as np

# 1D array
arr1 = np.array([1, 2, 3, 4])

# 2D array
arr2 = np.array([[1, 2, 3], [4, 5, 6]])

# 3D array
arr3 = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])

print(arr1)  # [1 2 3 4]
print(arr2)  # [[1 2 3] [4 5 6]]
print(arr3)  # 3D array output
```

---

## **2️⃣ Creating a Matrix in NumPy**
A **matrix** in NumPy is just a 2D `ndarray`. The recommended way to create a matrix is by using `np.array()`.

### **✅ Using `numpy.array()` for 2D Matrix**
```python
matrix = np.array([[1, 2, 3], [4, 5, 6]])
print(matrix)
```
🔹 NumPy **does not recommend** using `np.matrix` (deprecated). Instead, use `np.array()` for matrices.

---

## **3️⃣ Creating Special `ndarray` and Matrices**
NumPy provides built-in functions to create different types of arrays.

### **✅ Zeros Matrix**
```python
zeros_matrix = np.zeros((3, 3))  # 3x3 matrix of zeros
print(zeros_matrix)
```

### **✅ Ones Matrix**
```python
ones_matrix = np.ones((2, 4))  # 2x4 matrix of ones
print(ones_matrix)
```

### **✅ Identity Matrix**
```python
identity_matrix = np.eye(4)  # 4x4 identity matrix
print(identity_matrix)
```

### **✅ Random Matrix**
```python
random_matrix = np.random.rand(3, 3)  # 3x3 matrix with random values
print(random_matrix)
```

### **✅ Matrix of a Specific Value**
```python
filled_matrix = np.full((2, 3), 7)  # 2x3 matrix filled with 7
print(filled_matrix)
```

---

## **4️⃣ Creating a Range-Based `ndarray`**
### **✅ Using `arange()`**
```python
arr = np.arange(1, 10, 2)  # [1, 3, 5, 7, 9]
print(arr)
```

### **✅ Using `linspace()`**
```python
arr = np.linspace(1, 10, 5)  # 5 equally spaced numbers from 1 to 10
print(arr)
```

---

### **📌 Summary**
| Method | Purpose |
|--------|---------|
| `np.array()` | Convert list to `ndarray` |
| `np.zeros((m, n))` | Create an `m x n` matrix of zeros |
| `np.ones((m, n))` | Create an `m x n` matrix of ones |
| `np.eye(n)` | Create an identity matrix of size `n` |
| `np.full((m, n), value)` | Create an `m x n` matrix filled with a value |
| `np.diag([1,2,3,...])` | Create `num` matrix with given elements on diagonal |
| `np.random.rand(m, n)` | Create an `m x n` matrix with random values |
| `np.arange(start, stop, step)` | Create a range-based array |
| `np.linspace(start, stop, num)` | Create `num` evenly spaced values |

