### **📌 Properties and Attributes of `ndarray` in NumPy**  

A NumPy `ndarray` (N-dimensional array) has several **attributes** that provide information about its structure, size, and memory layout. Below is a **complete list** of all key properties and attributes:

---

## **🟢 1. Shape and Size Attributes**  
These attributes describe the dimensions and size of the array.  

| **Attribute** | **Description** | **Example Output** |
|--------------|----------------|---------------------|
| `ndarray.shape` | Returns a tuple representing the dimensions of the array (rows, cols, etc.) | `(3, 4)` |
| `ndarray.ndim` | Returns the number of dimensions (axes) | `2` |
| `ndarray.size` | Returns the total number of elements in the array | `12` |

✅ **Example:**  
```python
import numpy as np

arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.shape)  # (2, 3)
print(arr.ndim)   # 2
print(arr.size)   # 6
```

---

## **🟢 2. Data Type Attributes**  
These attributes provide information about the data type stored in the array.

| **Attribute** | **Description** | **Example Output** |
|--------------|----------------|---------------------|
| `ndarray.dtype` | Returns the data type of array elements | `dtype('int32')` |
| `ndarray.itemsize` | Returns the size (in bytes) of each element | `4` (for `int32`) |
| `ndarray.nbytes` | Returns total memory consumed by the array (size × itemsize) | `24` (for a 6-element int32 array) |

✅ **Example:**  
```python
arr = np.array([1, 2, 3], dtype=np.int32)
print(arr.dtype)      # int32
print(arr.itemsize)   # 4 bytes
print(arr.nbytes)     # 12 bytes (3 elements × 4 bytes)
```

---


---

## **🟢 3. Indexing and Reshaping Attributes**  
These attributes allow manipulation of array shape and indexing behavior.

| **Attribute** | **Description** | **Example Output** |
|--------------|----------------|---------------------|
| `ndarray.T` | Transposes the array (swaps rows and columns) | `[[1 4] [2 5] [3 6]]` |
| `ndarray.real` | Returns the real part of a complex array | `[1. 2.]` |
| `ndarray.imag` | Returns the imaginary part of a complex array | `[0. 3.]` |
| `ndarray.flat` | Returns an iterator to access elements in 1D form | `<numpy.flatiter>` |

✅ **Example:**  
```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.T)  # Transposed array

complex_arr = np.array([1 + 0j, 2 + 3j])
print(complex_arr.real)  # [1. 2.]
print(complex_arr.imag)  # [0. 3.]
```

---

## **🟢 4. Copy and Base Attributes**  
These attributes indicate whether an array shares memory with another.

| **Attribute** | **Description** | **Example Output** |
|--------------|----------------|---------------------|
| `ndarray.base` | Returns the original array if the current array is a view | `None` (if it's a copy) |
| `ndarray.copy()` | Returns a copy of the array (independent of original) | New array |

✅ **Example:**  
```python
arr = np.array([1, 2, 3])
view = arr[:2]  # Creating a view
copy = arr.copy()  # Creating a copy

print(view.base is arr)  # True (shares memory)
print(copy.base)  # None (independent copy)
```

---



---

## **📌 Complete List of `ndarray` Attributes**
| **Attribute** | **Description** |
|--------------|----------------|
| `ndarray.shape` | Shape of the array (tuple of dimensions) |
| `ndarray.ndim` | Number of dimensions |
| `ndarray.size` | Total number of elements |
| `ndarray.dtype` | Data type of elements |
| `ndarray.itemsize` | Size in bytes of each element |
| `ndarray.nbytes` | Total memory used by the array |
| `ndarray.data` | Memory address of the data |
| `ndarray.flags` | Memory layout information |
| `ndarray.strides` | Memory byte steps for each axis |
| `ndarray.T` | Transpose of the array |
| `ndarray.real` | Real part of complex numbers |
| `ndarray.imag` | Imaginary part of complex numbers |
| `ndarray.flat` | Flattened 1D iterator |
| `ndarray.base` | Original array if it's a view |
| `ndarray.copy()` | Returns a copy of the array |
| `ndarray.ctypes` | C-compatible memory interface |

---

## **🎯 Summary**
- `ndarray` has attributes for **shape, size, memory layout, and indexing**.
- **`dtype` and `itemsize`** tell us about the element type.
- **`flags` and `strides`** describe memory storage.
- **Views (`base`) vs. copies (`copy()`)** affect performance.

