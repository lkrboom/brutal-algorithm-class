递归（Recursion）作为大多数数据结构和算法的思维模型，同学们需要深入理解。本文从数学以及函数式编程的角度，深入讲解递归。

本文使用 JavaScript 举例子，但只会用到几乎所有语言都有的功能。所以你可以容易地将代码翻译成 Python、C、C++、Go 或者其他语言。

__希望同学们跟着文章，在编程环境中编写。__

首先看这个函数
```js
// n: Int
function countDown(n) {
    console.log(n);
    if (n > 1) {
        countDown(n - 1);
    }
}
```
这是一个简单的递归函数，从 n 数到 1。
```js
countDown(5)
```
打印
```
5
4
3
2
1
```
最简单地理解，你可以认为递归（Recursion）是循环迭代（Loop & Iteration）的函数式写法。
```js
function countDownInLoop(n) {
    for(let i = n; i > 1; i--) {
        console.log(n);
    } 
}
```
实现了一摸一样的效果。

现在同学们需要问自己：
1. 什么样的函数可以同时有循环的写法和递归的写法？
2. 在上述例子里，循环写法更简短也更快。什么情况下会选择递归写法呢？

__第一个问题：__ 简单地讲，如果一个循环每一个步骤干的事情都一摸一样，只是输入数据越来越接近结束条件，那么就可以用递归方式重写。从数学上讲，满足归纳法（Reduction）的都可以用递归（递减归纳）实现。Recursion 的英文本意是“重复发生”。“递归”这个翻译是意译，而不是直译。

__第二个问题：__ 当一个函数的控制流变得发杂之后，递归写法通常比循环写法更简洁也更易懂。因为递归要求程序员将部分逻辑封装为函数，而不是“散装”在 For Loop 或者 While Loop 里。这就是软件工程的模组化思维。至于运行效率，这是一个优化问题，与递归还是循环没有因果关系。

# 更复杂一点的递归函数
```js
// 阶乘 n!
function factorial(n) {
    if( n === 0 ) {
        return 1
    }
    return n * factorial(n-1)
}

function factorialInLoop(n) {
    let product = 1
    for(let i = 1; i <= n; i++) {
        product = product * i
    }
    return product
}
```
这里我们可以有两个观察：
1. 阶乘和计数器在递归形式下，几乎没有区别。但是其循环形式却差很多。
2. 这里的循环实现已经开始比递归复杂了。