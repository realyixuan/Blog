# Python: All Is Object

[Python doc](https://docs.python.org/3/reference/datamodel.html) states: "Objects are Python’s abstraction for data. All data in a Python program is represented by objects or by relations between objects". As an OOP programming language, Python has itself a one-sentence slogan of "Everything is object". In programming, the term object's definition is not unique, it could be a segment of memory, a variable with some methods, or instance of class etc. But, in OOP, there are some common understandings about object, such as object has its own behavior and data, moreover, object has some characteristics, like identity, type.

## characteristic of object

Here I present the obvious three of them, see how they exist in Python.

**behaviour**

Object has their own behaviour. With these behaviours, they can (if permitted) change their internal states. So, even int, as an object, has its own behaviours.

```python
>>> (1).conjugate()
1
```

**type**

Everything is object, then everything has their own type. Assume class `Foo` initializes an instance `foo`, then `Foo` is type of `foo`. There is no exception.

```python
>>> import sys; type(sys)
<class 'module'>
```

**identity**

Before presenting id, it would be better to distinguish the two concepts, [values and objects in programming languages](https://dl.acm.org/doi/pdf/10.1145/988164.988172).

Value is an abstraction for reality, they are immutable, can't be altered. Values have no identities, so, they can't be identified. For example:

> 1 == 1

1 equals 1. 1s are not only equal, but they are also 'the same thing'. Which means 1 == 1 and 1 is 1. There are no two different 1s, so, the case cannot exist: there are two different 1s, the first 1 is not the second 1, they are equal though. In contrast, objects are models of reality, concretizing values. Objects quite resemble entities of real world. Two entities with exactly same form or appearance, you may say they are 'equal', but they are definitely not 'the same thing'. For example:

> two identical apples

Even though the two apples are identical, they are essentially two different entities.

Everything being object means number is also object, not value. That is to say 1000 is not a value, but an object, and has its own unique id, then it could come to true that 1000 equals 1000, but 1000 is not 1000.

```python
>>> a = 1000
>>> b = 1000
>>> a is not b
True
```

Number is more like value, not object, so, numbers as object give us little except that using `is` to compare number instead of `==` make us confused. Perhaps `is` could get well used to compare numbers, but I can see nowhere it is useful. Number is immutable object, so, it also brings us little side effect.

## instance of object is object

```python
>>> class Foo: pass
>>> Foo()
<__main__.Foo object at 0x7f9dfe9da9d0>
```

According to hints given by Python repr, object is defined as the instance instantialized by class. So, forget about various definition of objects, now we use a specific, precise way to define object in Python: **instance of class `object` is object**.

`object` class is base class for all classes. That is to say all classes is subclass of `object` class. which means instance of all classes is also instance of `object` class. So:

```python
>>> isinstance(Foo(), object)
True
```

And because class is also object, then it should be instance of `object`.

```python
>>> isinstance(object, type)
True
```

If `object` is instance of `type`, then all classes are also instance of `type`. As mentioned before, all class is subclass of `object`, including `type`:

```python
>>> issubclass(type, object)
True
```

We can infer that all classes are instance of `object`. But there is one special thing which should be singled out: *object is instance of type* + *type is subclass of object* => *object is instance of object*. The fact is it actually is.

```python
>>> isinstance(object, object)
True
```

Now, in Python, everything is instance of `object`. Hence, everything is object.

<span style="color:gray; font-size:small;">date: 2023-03-18</span>
