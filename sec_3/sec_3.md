# 形式ばらない Python の紹介

## Python を電卓として使う

### 数

```py
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5.0*6) / 4
5.0
>>> 8 / 5.0
1.6
>>>
>>>
>>> 17 / 3
5
>>> 17 / 3.0
5.666666666666667
>>> 17 // 3.0
5.0
>>> 17 % 3
2
>>> 5 * 3 + 2
17
>>>
>>>
>>> 5 ** 2
25
>>> 2 ** 7
128
>>>
>>>
>>> width = 20
>>> height = 5 * 9
>>> width * height
900
>>>
>>>
>>> n
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'n' is not defined
>>>
>>>
>>> 3 * 3.75 / 1.5
7.5
>>> 7.0 / 2
3.5
>>>
>>>
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06
```

### 文字列

```py
>>> 'spam eggs'
'spam eggs'
>>> 'doesn\'t'
"doesn't"
>>> "doesn't"
"doesn't"
>>> '"Yes," he said.'
'"Yes," he said.'
>>> "\"Yes,\" he said."
'"Yes," he said.'
>>> '"Isn\'t," she said.'
'"Isn\'t," she said.'
>>>
>>>
>>> '"Isn\'t," she said.'
'"Isn\'t," she said.'
>>> print '"Isn\'t," she said.'
"Isn't," she said.
>>> s = 'First line.\nSecond line.'
>>> s
'First line.\nSecond line.'
>>> print s
First line.
Second line.
>>>
>>>
>>> print 'C:\some\name'
C:\some
ame
>>> print r'C:\some\name'
C:\some\name
>>>
>>>
>>> print """\
... Usage: thingy [OPTIONS]
...      -h                        Display this usage message
...      -H hostname               Hostname to connect to
... """
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to

>>>
>>>
>>> 3 * 'un' + 'ium'
'unununium'
>>>
>>>
>>> 'Py' 'thon'
'Python'
>>>
>>>
>>> prefix = 'Py'
>>> prefix 'thon'
  File "<stdin>", line 1
    prefix 'thon'
                ^
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  File "<stdin>", line 1
    ('un' * 3) 'ium'
                   ^
SyntaxError: invalid syntax
>>>
>>>
>>> prefix + 'thon'
'Python'
>>>
>>>
>>> text = ('Put several strings within parentheses '
...             'to have them joined together.')
>>> text
'Put several strings within parentheses to have them joined together.'
>>>
>>>
>>> word = 'Python'
>>> word[0]
'P'
>>> word[5]
'n'
>>>
>>>
>>> word[-1]
'n'
>>> word[-2]
'o'
>>> word[-6]
'P'
>>>
>>>
>>> word[0:2]
'Py'
>>> word[2:5]
'tho'
>>>
>>>
>>> word[:2] + word[2:]
'Python'
>>> word[:4] + word[4:]
'Python'
>>>
>>>
>>> word[:2]
'Py'
>>> word[4:]
'on'
>>> word[-2:]
'on'
>>>
>>>
>>> word[42]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
>>>
>>>
>>> word[4:42]
'on'
>>> word[42:]
''
>>>
>>>
>>> word[0] = 'J'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>>
>>>
>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'
>>>
>>>
>>> s = 'supercalifragilisticexpialidocious'
>>> len(s)
34
```

### Unicode 文字列

```py
>>> u'Hello World !'
u'Hello World !'
>>>
>>>
>>> u'Hello\u0020World !'
u'Hello World !'
>>>
>>>
>>> ur'Hello\u0020World !'
u'Hello World !'
>>> ur'Hello\\u0020World !'
u'Hello\\\\u0020World !'
>>>
>>>
>>> u"abc"
u'abc'
>>> str(u"abc")
'abc'
>>> u"äöü"
u'\xe4\xf6\xfc'
>>> str(u"äöü")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-2: ordinal not in range(128)
>>>
>>>
>>> u"äöü".encode('utf-8')
'\xc3\xa4\xc3\xb6\xc3\xbc'
>>>
>>>
>>> unicode('\xc3\xa4\xc3\xb6\xc
```

### リスト

```py
>>> squares = [1, 4, 9, 16, 25]
>>> squares
[1, 4, 9, 16, 25]
>>>
>>>
>>> squares[0]
1
>>> squares[-1]
25
>>> squares[-3:]
[9, 16, 25]
>>>
>>>
>>> squares[:]
[1, 4, 9, 16, 25]
>>>
>>>
>>> squares + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
>>>
>>>
>>> cubes = [1, 8, 27, 65, 125]
>>> 4 ** 3
64
>>> cubes[3] = 64
>>> cubes
[1, 8, 27, 64, 125]
>>>
>>>
>>> cubes.append(216)
>>> cubes.append(7 ** 3)
>>> cubes
[1, 8, 27, 64, 125, 216, 343]
>>>
>>>
>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters[2:5] = ['C', 'D', 'E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> letters[2:5] = []
>>> letters
['a', 'b', 'f', 'g']
>>> letters[:] = []
>>> letters
[]
>>>
>>>
>>> letters = ['a', 'b', 'c', 'd']
>>> len(letters)
4
>>>
>>>
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
```

### プログラミングへの第一歩

```py
>>> # Fibonacci series:
... # the sum of two elements defines the next
... a, b = 0, 1
>>> while b < 10:
...     print b
...     a, b = b, a+b
...
1
1
2
3
5
8
>>>
>>>
>>> i = 256*256
>>> print 'The value of i is', i
The value of i is 65536
>>>
>>>
>>> a, b = 0, 1
>>> while b < 1000:
...     print b,
...     a, b = b, a+b
...
1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987
```
