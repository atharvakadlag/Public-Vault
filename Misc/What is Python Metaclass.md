#python #python-theory

# About Python Classes
Everything in python is a class, even the classes that you create. The classes are of class `type.`
Type is a **Metaclass**. It inherits from itself. 
![[Screenshot 2022-09-19 at 8.29.55 AM.png]]

`type` as any other class has a constructor. You can call `type()` with the following arguments to create an instance of class, this way you are dynamically creating a class.
**Call:** `type(<name>, <base>, <dct>)`
**Arguments:**
1. `name`: name of the class to be created
2. `base`: the classes that the new class will inherit from
3. `dct`: attributes of the class as a dictionary

```python
class Foo:
	pass

f = Foo()
```
When `Foo()` is called in above code, it executes `__call__()` method of the `Foo` class or its ancestors if unimplemented in `Foo()`.
`type:__call__()` invokes `__new__()` and `__init__()`, which again if implemented in `Foo` are used else inherited from ancesters.

# Writing your own metaclass
```python
class Meta(type):  # Meta inherits from type and thus is a metaclass
	def __new__(clas, name, bases, dct):
		x = super().__new__(clas, name, bases, dct)
		# do some stuff with x here
		return x
```

Now any class that you create can have `Meta` as the metaclass instead of the `type` metaclass.
A class with `Meta` as metaclass can be created as follows:
`class Foo(metaclass=Meta): pass`

# Don't understand where to use them?
You don't need to use them if you can solve the same thing in a simpler way. But sometimes you would need a cleaner way to do it and when you do think Meta. 

[Use of metaclass in Django library](https://github.com/django/django/search?q=metaclass)

