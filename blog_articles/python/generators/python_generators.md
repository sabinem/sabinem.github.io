# Understanding Generators in Python
11.7.2016

In this tutorial I show you how to make a generator in Python. A generator is a function, that will serve you a sequence: it knows what “next” means in a given context. The sequence it serves can be finite or infinite.

## What to expect:
In this tutorial you will learn:

- What a generator is in Python (slides 1-12)
- How it differs from an iterator (slides 13-15)
- How to build your own generator (slides 16-20)
- Outlook on related topics (slides 21-26)
- Iterators come from iterables (slides 26-30)

## Tutorial: Generators in Python
Prezi Presentation (takes some seconds to load): scroll through at your own speed.

## Revisiting the content
### 1. What is a generator in Python?
a function that knows how to give you a next item
A generator serves next() by using yield
#### Code Example: A simple generator (slide 8)
```python
>>>def my_generator():
           yield "How"
           yield "are"
           yield "you"
           yield "today"  
>>>x = my_generator() # x is a generator
>>>next(x)
'How' 
>>>next(x)
'are'
>>>next(x)
'you'
>>>next(x)
'today'
>>>next(x)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```
