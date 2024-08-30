# Python Cheatsheet

## Datatypes

## Loops
### For
### While

## Sort (filter, sorted, lambda)

## Functions
```
def foo(x):
    return x + 1
```
```
# type hints

def foo(x: int) -> int:
    return x + 1
```
```
# positional arguments & keyword arguments
from typing import Any, Tuple, List, Dict

def foo(*args, **kwargs) -> Tuple[List[Any], Dict[str, Any]]:
    return args, kwargs
```
```
# restrict positional arguments

def foo(*, **kwargs):
    return kwargs

d = {'a': 1, 'b': 2}
foo(**d)
foo(**{'a': 1, 'b': 2})
foo(a=1, b=2)
```
### Recursion
#### Simple Recursion
#### Complex Recursion
#### Tail Recursion
### Generators
```
def foo(x: int) -> int:
    for i in range(3):
        yield x + i

gen = foo(1)
next(gen) -> 1
next(gen) -> 2
next(gen) -> 3

for x in foo(1):
    print(x)
1
2
3
```
```
def extract_product(html): Dict[str, Any]:
    return {'product': html.find('h1').text}

def scrape() -> Dict[str, Any]:
    html = requests.get('https://www.example.com/product/1')
    yield extract_product(html)

    other_products = html.find('div.other-products a::href')
    for href in other_products:
        html = requests.get(href)
        yield extract_product(html)

```
### Decorators
```
def deco(func: Callable) -> Callable:
    def wrapper(*args, **kwargs):
        print('before')
        func(*args, **kwargs)
        print('after')
    return wrapper

@deco
def foo():
    print('foo')

foo()
```

## Guardian Approach

## Classes
\_\_new\_\_, \_\_init\_\_, \_\_del\_\_
@property
def foo(self):
    return self._foo

self.foo # NOTE: no brackets
A().foo # NOTE: no brackets

@classmethod
def foo(cls):
    print('foo')

A.foo()

@staticmethod
def foo():
    print('foo')

A.foo()
A().foo()

## Dunder (magic) methods

## Context Managers (with) io operations
```
class Foo:
    def __enter__(self):
        print('enter')
        return self
    
    def __exit__(self, exc_type, exc_value, traceback):
        print('exit')
        return False

with Foo():
    print('foo')
```

## OOP
### Principles
#### Inheritance
#### Polymorphism
#### Abstraction ABC's
#### Encapsulation _, __

## Design Patterns (Gang/Game of four)
### Creational
### Structural
### Functional

## Software Architectures
### API Gateway
### 