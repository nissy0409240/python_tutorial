# その他の制御フローツール

## if 文

```py
>>> if x < 0:
...     x = 0
...     print 'Negative changed to zero'
... elif x == 0:
...     print 'Zero'
... elif x == 1:
...     print 'Single'
... else:
...     print 'More'
...
More
```

## for 文

```py
>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print w, len(w)
...
cat 3
window 6
defenestrate 12
```

## range() 関数

```py
>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>>
>>>
>>> range(5, 10)
[5, 6, 7, 8, 9]
>>> range(0, 10, 3)
[0, 3, 6, 9]
>>> range(-10, -100, -30)
[-10, -40, -70]
>>>
>>>
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
...     print i, a[i]
...
0 Mary
1 had
2 a
3 little
4 lamb
```

## break 文と continue 文とループの else 節

```py
>>> for n in range(2, 10):
...     for x in range(2, n):
...             if n % x == 0:
...                     print n, 'equals', x, '*', n/x
...                     break
...     else:
...             print n, 'is a prime number'
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```

## pass 文

```py
>>> while True:
...     pass
...
>>>
>>>
>>> class MyEmptyClass:
...     pass
...
>>>
>>>
>>> def initlog(*args):
...     pass
...
>>>
```

## 関数を定義する

```py
>>> def fib(n):
...     """Print a Fibonacci series up to n."""
...     a, b = 0, 1
...     while a < n:
...             print a,
...             a, b = b, a+b
...
>>> fib(2000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
>>>
>>>
>>> fib
<function fib at 0x100aaded8>
>>> f = fib
>>> f(100)
0 1 1 2 3 5 8 13 21 34 55 89
>>>
>>>
>>> fib(0)
>>> print fib(0)
None
>>>
>>>
>>> def fib2(n):
...     """Return a list containing the Fibonacci series up to n."""
...     result = []
...     a, b = 0, 1
...     while a < n:
...             result.append(a)
...             a, b = b, a+b
...     return result
...
>>> f100 = fib2(100)
>>> f100
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
```

## デフォルトの引数値

```py
>>> def ask_ok(prompt, retries=4, complaint='Yes or no, please!'):
...     while True:
...         ok = raw_input(prompt)
...         if ok in ('y', 'ye', 'yes'):
...             return True
...         if ok in ('n', 'no', 'nop', 'nope'):
...             return False
...         retries = retries - 1
...         if retries < 0:
...             raise IOError('refusenik user')
...         print complaint
...
>>> ask_ok('Do you really want to quit?')
Do you really want to quit?y
True
>>> ask_ok('OK to overwrite the file?', 2)
OK to overwrite the file?y
True
>>> ask_ok('OK to overwrite the file?', 2, 'Come on, only yes or no!')
OK to overwrite the file?n
False
>>> ask_ok('OK to overwrite the file?', 2, 'Come on, only yes or no!')
OK to overwrite the file?
Come on, only yes or no!
OK to overwrite the file?
Come on, only yes or no!
OK to overwrite the file?
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    File "<stdin>", line 10, in ask_ok
    IOError: refusenik user
>>>
>>>
>>> i = 5
>>>
>>> def f(arg=i):
...     print arg
...
>>> i = 6
>>> f()
5
>>>
>>>
>>> def f(a, L=[]):
...     L.append(a)
...     return L
...
>>> print f(1)
[1]
>>> print f(2)
[1, 2]
>>> print f(3)
[1, 2, 3]
>>> def f(a, L=None):
...     if L is None:
...         L = []
...     L.append(a)
...     return L
...
>>> print f(1)
[1]
>>> print f(2)
[2]
>>> print f(3)
[3]
```

## キーワード引数

```py
>>> def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
...     print "-- This parrot wouldn't", action,
...     print "if you put", voltage, "volts through it."
...     print "-- Lovely plumage, the", type
...     print "-- It's", state, "!"
...
>>> parrot(1000)
-- This parrot wouldn't voom if you put 1000 volts through it.
-- Lovely plumage, the Norwegian Blue
-- It's a stiff !
>>> parrot(voltage=1000)
-- This parrot wouldn't voom if you put 1000 volts through it.
-- Lovely plumage, the Norwegian Blue
-- It's a stiff !
>>> parrot(voltage=1000000, action='VOOOOOM')
-- This parrot wouldn't VOOOOOM if you put 1000000 volts through it.
-- Lovely plumage, the Norwegian Blue
-- It's a stiff !
>>> parrot(action='VOOOOOM', voltage=1000000)
-- This parrot wouldn't VOOOOOM if you put 1000000 volts through it.
-- Lovely plumage, the Norwegian Blue
-- It's a stiff !
>>> parrot('a million', 'bereft of life', 'jump')
-- This parrot wouldn't jump if you put a million volts through it.
-- Lovely plumage, the Norwegian Blue
-- It's bereft of life !
>>> parrot('a thousand', state='pushing up the daisies')
-- This parrot wouldn't voom if you put a thousand volts through it.
-- Lovely plumage, the Norwegian Blue
-- It's pushing up the daisies !
>>>
>>>
>>> parrot()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: parrot() takes at least 1 argument (0 given)
>>> parrot(voltage=5.0, 'dead')
  File "<stdin>", line 1
SyntaxError: non-keyword arg after keyword arg
>>> parrot(110, voltage=220)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: parrot() got multiple values for keyword argument 'voltage'
>>> parrot(actor='John Cleese')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: parrot() got an unexpected keyword argument 'actor'
>>>
>>>
>>> def function(a):
...     pass
...
>>> function(0, a=0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: function() got multiple values for keyword argument 'a'
>>>
>>>
>>> def cheeseshop(kind, *arguments, **keywords):
...     print "-- Do you have any", kind, "?"
...     print "-- I'm sorry, we're all out of", kind
...     for arg in arguments:
...         print arg
...     print "-" * 40
...     keys = sorted(keywords.keys())
...     for kw in keys:
...         print kw, ":", keywords[kw]
...
>>> cheeseshop("Limburger", "It's very runny, sir.",
...            "It's really very, VERY runny, sir.",
...            shopkeeper='Michael Palin',
...            client="John Cleese",
...            sketch="Cheese Shop Sketch")
-- Do you have any Limburger ?
-- I'm sorry, we're all out of Limburger
It's very runny, sir.
It's really very, VERY runny, sir.
----------------------------------------
client : John Cleese
shopkeeper : Michael Palin
sketch : Cheese Shop Sketch

>>> def write_multiple_items(file, separator, *args):
...     file.write(separator.join(args))
...
```

## 引数リストのアンパック

```py
>>> range(3, 6)
[3, 4, 5]
>>> args = [3, 6]
>>> range(*args)
[3, 4, 5]
>>>
>>>
>>> def parrot(voltage, state='a stiff', action='voom'):
...     print "-- This parrot wouldn't", action,
...     print "if you put", voltage, "volts through it.",
...     print "E's", state, "!"
...
>>> d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
>>> parrot(**d)
-- This parrot wouldn't VOOM if you put four million volts through it. E's bleedin' demised !
```

## ラムダ式

```py
>>> def make_incrementor(n):
...     return lambda x: x + n
...
>>> f = make_incrementor(42)
>>> f(0)
42
>>> f(1)
43
>>>
>>>
>>> pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
>>> pairs.sort(key=lambda pair: pair[1])
>>> pairs
[(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]
```

## ドキュメンテーション文字列

```py
>>> def my_function():
...     """Do nothing, but document it.
...
...     No, really, it doesn't do anything.
...     """
...     pass
...
>>> print my_function.__doc__
Do nothing, but document it.

	No, really, it doesn't do anything.
```
