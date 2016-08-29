---
layout: page
title: tips about module
categories: [python基础学习]
tags: [python module unittest]
---

# {{ page.title }}

### 如何隐藏字段-- _X and __all__

{% highlight python %}

# unders.py
a, _b, c, _d = 1, 2, 3, 4
>>> from unders import * 
>>> a, c
(1, 3)
>>> _b
NameError: name '_b' is not defined

>>> import unders 
>>> unders._b
2
# alls.py
__all__ = ['a', '_c']

>>> from alls import * 
>>> a, _c
(1, 3)
>>> b
NameError: name 'b' is not defined

>>> from alls import a, b, _c, _d 
>>> a, b, _c, _d
(1, 2, 3, 4)
>>> import alls
>>> alls.a, alls.b, alls._c, alls._d (1, 2, 3, 4)

{% endhighlight %}

### Unittest with __main__

{% highlight python %}
print('I am:', __name__)

def minmax(test, *args): 
	res = args[0]
	for arg in args[1:]: 
		if test(arg, res):
			res = arg 
	return res

def lessthan(x, y): 
	return x < y

def grtrthan(x, y): 
	return x > y

if __name__ == '__main__': 
	print(minmax(lessthan, 4, 2, 1, 5, 6, 3))
	print(minmax(grtrthan, 4, 2, 1, 5, 6, 3))

{% endhighlight%}