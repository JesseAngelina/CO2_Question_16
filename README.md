16. Cloud API Integration

A cloud application receives data from multiple sources. Objects from
different classes may provide a read() method, and the same processing
function should work with all of them.

Question

svg

(a) Explain how duck typing can be used in this situation. [2]

(b) Write a Python function that accepts any object supporting
read(). [3]

(c) Explain why explicit type checking may not be necessary and
state one advantage and one limitation of duck typing. [3]

Solution

svg

According to the scenario, different objects from different classes can
provide the same read() method.

Python uses duck typing, which means that the type or class of an
object is less important than the operations or methods it supports.

If an object has a read() method, the processing function can use it
without checking which class the object belongs to.

Example

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

Algorithm

svg

Input

Any object that supports the read() method.

Steps

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

Python focuses on what an object can do rather than what type it is.
If the object supports read(), the function can directly call it.

Therefore, explicit type checking is not necessary when the required
method is available.

Advantage of Duck Typing

svg

Flexibility

The same function can work with objects from different classes as
long as they provide the required method. This makes the code flexible
and reusable.

Limitation of Duck Typing

svg

Runtime Errors

If an object does not provide the required read() method, Python
produces an error at runtime.

Key Point

svg

Duck typing means: "If an object behaves like the required object,
it can be used."

Coverage Note

Duck typing, dynamic typing and Python data model
