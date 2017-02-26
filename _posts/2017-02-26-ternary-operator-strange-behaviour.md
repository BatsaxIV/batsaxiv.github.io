---
layout: post
comments: true
title: PHP | Be aware of the ternary operator
category: php
---

We've all been using the ternary operator (*also known as the [elvis operator](https://en.wikipedia.org/wiki/Elvis_operator)*).
It's a faster and cleaner way of writing small piece of if/else statement!  
But avoid the temptation of imbricate it, not a really good idea... unless you're 100% certain of what your doing and you don't really care about somebody else reading your code :)  

I've wanted to try that lately and encountered some issues, so what's the problem?  
Basically, it's the difference between how PHP reads the code and you or any other human does (at least, when you're not aware of the situation):

To understand it, I'll take an example from the official PHP documentation, what do you think is returned by the following line?

```php
<?php
echo (true ? 'true' : false ? 'foo' : 'bar');
```

If you first guess was **true**, you're wrong, it's actually **foo** ; so, why this behaviour?  
Because PHP evaluates this expression left to right, like this :
```php
<?php
echo ((true ? 'true' : false) ? 'foo' : 'bar');
```
`(true ? 'true' : false)` is evaluated to **'true'** which is evaluated to **(bool)true**, in short:

```php
<?php
echo (true ? 'foo' : 'bar');
```
 
So **foo** is returned.

Quite logic when you know it!  
Hope you've appreciated this first and quick article! Do you have any non obvious behaviours to share?

*Learn more with the [official documentation](http://php.net/manual/en/language.operators.comparison.php#language.operators.comparison.ternary).*
