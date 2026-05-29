# Python OOP Notes — `self`

---

# 1. Definition of `self`

`self` is a reference to the **current object (instance)** of a class.

It is used to:

* access instance variables
* access instance methods
* store object-specific data

---

# 2. Syntax of `self`

```python
class ClassName:
    def method(self):
        pass
```

* `self` must be the **first parameter** inside instance methods.

---

# 3. Basic Example

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def display(self):
        print("Name:", self.name)
        print("Age:", self.age)

p1 = Person("Sneha", 20)
p1.display()
```

### Output

```python
Name: Sneha
Age: 20
```

---

# 4. How `self` Works Internally

When we write:

```python
p1.display()
```

Python internally converts it to:

```python
Person.display(p1)
```

So:

```python
self = p1
```

---

# 5. Why `self` is Important

## a) Access Instance Variables

```python
self.name
self.age
```

These variables belong to the object.

---

## b) Store Different Data for Different Objects

```python
p1 = Person("Sneha", 20)
p2 = Person("Rahul", 25)
```

* `p1.name` → Sneha
* `p2.name` → Rahul

`self` helps keep data separate.

---

## c) Call Methods Inside the Same Class

```python
class Demo:
    def greet(self):
        print("Hello")

    def call(self):
        self.greet()

d = Demo()
d.call()
```

### Output

```python
Hello
```

---

# 6. `self` in Constructor (`__init__`)

```python
class Student:
    def __init__(self, name):
        self.name = name
```

### Explanation

| Variable      | Type              |
| ------------- | ----------------- |
| `name`      | Local variable    |
| `self.name` | Instance variable |

---

# 7. Local Variable vs Instance Variable

## Without `self`

```python
class Test:
    def __init__(self, x):
        x = x
```

Here, value is not stored in object.

---

## With `self`

```python
class Test:
    def __init__(self, x):
        self.x = x
```

Now value is stored inside object.

---

# 8. `self` is NOT a Keyword

You can technically write:

```python
class Demo:
    def show(myobj):
        print("Hello")
```

But Python convention is to always use `self`.

---

# 9. Important Rules About `self`

| Rule                 | Description                                 |
| -------------------- | ------------------------------------------- |
| First parameter      | Must be first parameter in instance methods |
| Automatically passed | Python passes it automatically              |
| Not a keyword        | Just a naming convention                    |
| Represents           | Current object                              |

---

# 10. Common Mistakes

## Mistake 1 — Forgetting `self`

❌ Wrong

```python
class Person:
    def __init__(name):
        self.name = name
```

✅ Correct

```python
class Person:
    def __init__(self, name):
        self.name = name
```

---

## Mistake 2 — Accessing Variables Without `self`

❌ Wrong

```python
class Demo:
    def __init__(self, x):
        x = x
```

✅ Correct

```python
class Demo:
    def __init__(self, x):
        self.x = x
```

---

# 11. Real-Life Analogy

Suppose:

* Class = blueprint of a mobile phone
* Object = actual phone

`self` means:

> "this specific phone"

Example:

```python
self.brand
```

means:

> brand of this particular phone object

---

# 12. Memory Representation

```python
p1 = Person("Sneha", 20)
p2 = Person("Rahul", 25)
```

### Object Data

| Object | name  | age |
| ------ | ----- | --- |
| p1     | Sneha | 20  |
| p2     | Rahul | 25  |

`self` points to the current object.

---

# 13. Advantages of Using `self`

* Access object-specific data
* Supports multiple objects
* Avoids confusion between local and instance variables
* Makes code reusable and organized

---

# 14. Summary

| Concept                      | Meaning                         |
| ---------------------------- | ------------------------------- |
| `self`                     | Current object reference        |
| Used for                     | Accessing variables and methods |
| Passed automatically         | Yes                             |
| Keyword?                     | No                              |
| Required in instance methods | Yes                             |

---

# 15. One-Line Definition

> `self` is a reference to the current instance of a class in Python.

---

# 16. Quick Revision Code

```python
class Car:
    def __init__(self, brand, price):
        self.brand = brand
        self.price = price

    def show(self):
        print("Brand:", self.brand)
        print("Price:", self.price)

c1 = Car("BMW", 5000000)
c2 = Car("Audi", 4500000)

c1.show()
c2.show()
```

---
