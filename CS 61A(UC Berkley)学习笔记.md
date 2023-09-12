# 课程信息

- 课程名称：CS61A: Structure and Interpretation of Computer Programs(SICP)
- 编程语言：Python, Scheme, SQL
- 所属大学：UC Berkeley

# 课程简介

CSDIY：注意这不仅仅是一门编程语言课，而是会深入到程序构造与运行的原理。最后你将在第 4 个 Project 中用 Python 实现一个 Scheme 的解释器。此外，抽象将是这门课的一大主题，你将学习到函数式编程、数据抽象、面向对象等等知识来让你的代码更易读，更模块化。当然，学习编程语言也是这门课的一大内容，你将会掌握 Python、Scheme 和 SQL 这三种编程语言，在它们的学习和比较中，相信你会拥有快速掌握一门新的编程语言的能力。

注意：如果此前完全没有编程基础，直接上手 CS61A 需要一定的学习能力和自律要求。为避免课程难度过高而导致的信心挫折，可以选择一个更为友好的入门编程课程。例如伯克利的 CS10 或者哈佛大学的 CS50。

# 课程资源

- 课程官网：[CS 61A: Structure and Interpretation of Computer Programs](https://cs61a.org/)
- 中译教学视频：[【计算机程序的构造和解释】精译【UC Berkeley 公开课-CS61A (Spring 2021)】-中英双语字幕](https://www.bilibili.com/video/BV1v64y1Q78o)
- 课程教材：<http://composingprograms.com/>
- 课程教材中文翻译：<https://composingprograms.netlify.app/>

# 学习经验

# 学习笔记

## Functions

```Python
def hmmm(x):
    def f(x): # Prevents x from being overwritten
        return x
    return f
return hmmm(5)(6) # 6
#hmmm(5) returns f, which is a function that returns x, but not 5
```

Programs consist of statements, or instructions for the computer, containing expressions,
which describe computation and evaluate to values.

- Values can be assigned to names to avoid repeating computations.
- An assignment statement assigns the value of an expression to a name in the current
environment.
- Functions encapsulate（压缩，概述） a series of statements that maps arguments to a return value.
- A def statement creates a function object with certain parameters(formal arguments) and a body and binds it to a name in the current environment.
- A call expression applies the value of its operator, a function, to the value(s) or its
operand(s), some arguments.
- Procedure for calling/applying user-defined functions (version 1):

1. Create a new environment frame (we call it local frame, included in global frame)
2. Bind（绑定） the function’s parameters(formal arguments) to its arguments(actual arguments) in that frame
3. Execute the body of the function in the new environment

- A function’s signature has all the information needed to create a local frame!

## Control

- The special value None represents nothing in Python
- A function that does not explicitly return a value will return None
- Careful: None is not displayed by the interpreter as the value of an expression

```Python
>>> def does_not_return_square(x):
...     x * x #No return
...
>>> does_not_return_square(4) #None value is not displayed
>>> sixteen = does_not_return_square(4) #The name sixteen is now bound to the value None
>>> sixteen + 4
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'NoneType' and 'int'
```

- Multiple environments can exists in a diagram
- It is important to keep track an environment, tracing back to the parent of the earliest frame
- Every expression is evaluated in the context of an environment
- How floordiv, truediv, and mod are used in a boolean context
- later, we’ll be seeing how they are used for digit manipulation
•-A conditional statement is executed in order
only one suite is executed, and any following clauses are skipped
- Logical operators, and and or
- Using while statements for iteration

## Higher Order Functions

lambda: a way to define a function in a single expression

```Python
lambda x: x * x # NEWNAME
def NEWNAME(x):
    return x * x
```

## Environment

- Environment反映了变量的作用域
- Most important two things I’ll say all day:

1. An environment is a sequence of frames.
2. A name evaluates to the value bound to that name in the earliest frame of the current environment in which that name is found.
3. If you cannot find a name in the current frame, you can go up to its parent until you reach the global frame
4. If it is not found, you get a NameError: name 'x' is not defined
