To give the timeit module access to functions you define, you can pass a setup parameter which contains an import statement:

```python
def test():
    """Stupid test function"""
    L = [i for i in range(100)]

if __name__ == '__main__':
    import timeit
    print(timeit.timeit("test()", setup="from __main__ import test"))
```

Another option is to pass globals() to the globals parameter, which will cause the code to be executed within your current global namespace. This can be more convenient than individually specifying imports:

```python
def f(x):
    return x**2
def g(x):
    return x**4
def h(x):
    return x**8

import timeit
print(timeit.timeit('[func(42) for func in (f,g,h)]', globals=globals()))
```
