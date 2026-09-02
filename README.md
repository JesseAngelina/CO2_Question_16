# Duck Typing

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#duck-typing)

## Q16. Cloud API Integration

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#q16-cloud-api-integration)

A cloud application receives data from multiple sources. Objects from different classes may provide a `read()` method, and the same processing function should work with all of them.

### Question

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#question)

(a) Explain how duck typing can be used in this situation.

(b) Write a Python function that accepts any object supporting `read()`.

(c) Explain why explicit type checking may not be necessary and state one advantage and one limitation of duck typing.

### Solution

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#solution)

According to the scenario, since the cloud application only cares whether an object can `read()` data and not what class it belongs to, duck typing lets one function handle objects from many different sources uniformly.

### (a) How Duck Typing Applies

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#a-how-duck-typing-applies)

Python follows the principle: **"If it walks like a duck and quacks like a duck, it's a duck."**

In this situation:

- The cloud application does not check the **class** of the incoming object.
- It only checks whether the object **has a `read()` method**.
- Any object — whether it comes from a file source, a network stream, a database connector, or a cloud storage API — can be processed **as long as it implements `read()`**.
- This removes the need for rigid class hierarchies or interfaces, which is common in statically typed languages.

### Example

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#example)

Suppose data arrives from three different sources:

```
class FileSource:
    def read(self):
        return "Data from File Source"


class NetworkSource:
    def read(self):
        return "Data from Network Source"


class CloudStorageSource:
    def read(self):
        return "Data from Cloud Storage Source"
```

None of these classes share a common parent class, yet all three can be handled by the same function because each one **implements `read()`**.

### 1. No Class Check

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#1-no-class-check)

- The processing function never asks `isinstance(obj, SomeClass)`.
- It simply calls `obj.read()` and trusts that it will work.

### 2. Runtime Behavior Check

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#2-runtime-behavior-check)

- Python checks for the presence of `read()` **only when it is actually called**, at runtime.
- If the object does not support `read()`, an `AttributeError` is raised at that point.

### 3. Uniform Processing

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#3-uniform-processing)

- Objects from `FileSource`, `NetworkSource`, and `CloudStorageSource` are all passed through the **same** processing function.
- New source types can be added later **without modifying** the existing processing logic, as long as they also provide `read()`.

# (b) Python Function

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#b-python-function)

### Implementation

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#implementation)

```
def process_data(source):
    if hasattr(source, "read") and callable(source.read):
        print(source.read())
    else:
        print("Error: object does not support read()")


class FileSource:
    def read(self):
        return "Data from File Source"


class NetworkSource:
    def read(self):
        return "Data from Network Source"


class CloudStorageSource:
    def read(self):
        return "Data from Cloud Storage Source"


sources = [FileSource(), NetworkSource(), CloudStorageSource()]

for src in sources:
    process_data(src)
```

**svg**

# Output

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#output)

```
Data from File Source
Data from Network Source
Data from Cloud Storage Source
```

# (c) Why Explicit Type Checking Is Not Necessary

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#c-why-explicit-type-checking-is-not-necessary)

Python is **dynamically typed**, so the interpreter determines what an object can do **at runtime** based on its available attributes and methods, not on a declared class or interface. This means:

- The processing function does not need to know in advance which classes it will receive.
- Any object that "behaves like" a readable source (i.e., provides `read()`) is automatically compatible.
- This matches the Python data model, where behavior is defined by supported operations/methods rather than inheritance.

### Advantage

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#advantage)

**Flexibility and extensibility** — New data source classes can be integrated into the cloud application without changing or extending the processing function, as long as they implement `read()`.

### Limitation

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Duck%20Typing#limitation)

**Runtime errors instead of compile-time errors** — If an object passed in does *not* actually support `read()`, the error (`AttributeError`) is only discovered when the code runs, not beforehand, which can make bugs harder to catch early.
