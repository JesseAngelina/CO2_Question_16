

## 16. Cloud API Integration

A cloud application receives data from multiple sources. Objects from different classes may provide a `read()` method, and the same processing function should work with all of them.

### Question

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Cloud%20API%20Integration#question)

**(a)** Explain how duck typing can be used in this situation. **[2]**

**(b)** Write a Python function that accepts any object supporting `read()`. **[3]**

**(c)** Explain why explicit type checking may not be necessary and state one advantage and one limitation of duck typing. **[3]**

### Solution

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Cloud%20API%20Integration#solution)

According to the scenario, different objects from different classes can provide the same `read()` method.

Python uses **duck typing**, which means that the type or class of an object is less important than the methods or operations it supports.

If an object has a `read()` method, the processing function can use it without checking which class the object belongs to.

### Duck Typing in Cloud API Integration

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Cloud%20API%20Integration#duck-typing-in-cloud-api-integration)

### Example

[svg](https://github.com/Mounika-Nalla-45/2601050112_MTech_CSE/tree/main/CO1/Cloud%20API%20Integration#example)

Consider two different classes:

```python
class FileSource:
    def read(self):
        return "Data from file"


class CloudSource:
    def read(self):
        return "Data from cloud"
