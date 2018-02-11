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
<iframe id="iframe_container" frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="" width="550" height="400" src="https://prezi.com/embed/klb_q7qyw5m2/?bgcolor=ffffff&amp;lock_to_path=1&amp;autoplay=0&amp;autohide_ctrls=0&amp;landing_data=bHVZZmNaNDBIWnNjdEVENDRhZDFNZGNIUE43MHdLNWpsdFJLb2ZHanI5Z1ZKSitTU2U3VTFhdjZhUytQczVLQlB3PT0&amp;landing_sign=YWaipIYHb7Q8IAzsJRjTg6KrcPjhHzuel62oiXHZSDs"></iframe>

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

#### When a generator stops
- Sometimes there is no next()
- Then the generator produces a StopIteration Error

#### When Calling a generator
- is it an unsafe operation?
- then call it with a try-except-clause

#### Code Example: calling a generator (slide 12)
```python
>>>def my_generator():
           yield "How"
           yield "are"
           yield "you"
           yield "today"  
>>>x = my_generator() # x is a generator
>>>
while True:
    try:
         next(x)
    except StopIteration:
         print('there is no next item')
         break 
'How'
'are'
'you'
'today'
there is no next item
```

### 2. The difference between a generator and an iterator
Iterators serve from a iterable
Generator generate out of the thin air

### 3. Building a generator

#### Code example of an infinite generator (slide 18)
printing multiples of a number
```python
>>>def my_multiples_of_3_generator(base):
           n = 1
           while True:
               yield base * n
               n += 1
>>>y = my_multiples_of_3_generator(3)
>>>next(y)
6
>>>next(y)
3
>>>next(y)
9
```

#### Code Example of a finite generator (slide 20)
printing dividers of a number
```python
>>>def my_divider_generator(number):
            for n in range(1, number):
                 remainder = number % n
                 if remainder == 0:
                     yield n
>>>
while True:
    try:     
         dividers.append(next(x))      
    except StopIteration:
         print(dividers)
         break
>>>dividers =[]
>>>x = my_divider_generator(14)
[1, 2, 7]
```
### 4. Looking at iterators
#### What is an iterator? (slide 20)
- a iterator is a generator that comes form something substantial
- it comes from an iterable

#### Python collections are iterable: (slide 21)
- Strings: ‘Hallo how are you?’
- Lists: [1,’a’]
- Tuples: (1,3,4)
- Dictionaries: {‘house’: ‘red’, ‘tree’: ‘green’}

#### Collections are iterable means: (silde 23)
- they have a method that serves the collection
- x a collection, then iter(x) is a iterator

#### Code Example: getting an iterator from an iterable (slide 26)
```python
>>>my_iterable = ['How', 'are', 'you', 'today']
>>>x = iter(my_iterable) # x is a iterator
>>>next(x)
'you'
>>>next(x)
'How' 
>>>next(x)
'are'
>>>next(x)
'today'
>>>next(x)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```



