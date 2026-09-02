16. Cloud API Integration

A cloud application receives data from multiple sources. Objects from different classes may provide a read() method, and the same processing function should work with all of them.

Question

svg

(a) Explain how duck typing can be used in this situation. [2]

(b) Write a Python function that accepts any object supporting read(). [3]

(c) Explain why explicit type checking may not be necessary and state one advantage and one limitation of duck typing. [3]

Solution

svg

According to the scenario, different objects from different classes can provide the same read() method.

Python uses duck typing, which means that the type or class of an object is less important than the methods or operations it supports.

If an object has a read() method, the processing function can use it without checking which class the object belongs to.

Duck Typing in Cloud API Integration

svg

Duck typing allows objects from different classes to be used by the same function if they provide the required read() method.

Example

svg

Consider two different classes:

class FileSource:
    def read(self):
        return "Data from file"


class CloudSource:
    def read(self):
        return "Data from cloud"

Both classes have a read() method.

Although the classes are different, the same processing function can work with both objects.

1. Duck Typing

svg

Python does not need to check whether the object belongs to FileSource or CloudSource.

It only checks whether the object can perform the required operation:

Does the object have read()?
        ↓
      YES
        ↓
   Process the data

Therefore, both objects can be passed to the same function.

2. Same Function for Different Objects

svg

The same processing function can accept objects from different classes.

process_data(FileSource())
process_data(CloudSource())

The function works because both objects support read().

Algorithm

svg

Input

svg

Any object that supports the read() method.
Steps

svg

Accept an object as an argument.
Call the object's read() method.
Store the returned data.
Process or display the data.
No explicit class or type checking is required.
Python Implementation

svg

class FileSource:
    def read(self):
        return "Data from file"


class CloudSource:
    def read(self):
        return "Data from cloud"


def process_data(source):
    data = source.read()
    print("Received:", data)


file = FileSource()
cloud = CloudSource()

process_data(file)
process_data(cloud)

svg

Output

svg

Received: Data from file
Received: Data from cloud
Why Explicit Type Checking Is Not Necessary

svg

In duck typing, Python focuses on what an object can do rather than what type it is.

Instead of checking the class using isinstance(), we can directly call:

source.read()

If the object supports read(), the function works correctly.

Therefore, explicit type checking is not necessary when the required method is available.

Advantage of Duck Typing

svg

Flexibility

Duck typing allows the same function to work with objects from different classes as long as they provide the required method.

This makes the code:

Flexible
Reusable
Easier to extend
Limitation of Duck Typing

svg

Runtime Errors

If an object does not provide the required read() method, Python will produce an error at runtime.

For example:

class InvalidSource:
    pass


process_data(InvalidSource())

This results in an error because the object does not have a read() method.

Therefore, duck typing provides flexibility but may cause runtime errors if the expected method is missing.

Key Point

svg

Duck typing means: “If an object behaves like the required object, it can be used.”

In this scenario, any object that provides a read() method can be passed to the same processing function, regardless of its class.

Coverage Note

Duck typing, dynamic typing and Python data model
