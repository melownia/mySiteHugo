---
title: Python RegEx Basics
date: 2020-01-28T19:39:25-04:00
tags: [python]
categories: [tech doc]
draft: false
---

引入正则表达式模块

```python
import re
```
### 一般字符
\.: 除换行符(\n)外的任意字符

\\: 转义字符

如: \\\\, \\.

[...]: 字符集中的任意字符

如: [au], [a-z], [A-Z], [0-9], [0-9a-z], [^ac]\(非ac\)

re.search(r"r[A-Z]n", "run")


### 预定义字符集

\d: 数字 [0-9]

\D: 非数字 [^\d]

\s: 空白符[\t\n\r\f\v]

\S: 非空白字符 [^\s]

\w: 单词字符 [a-zA-Z0-9]

\W: 非单词字符

### 边界匹配

^: 匹配每一行的开头

$: 匹配每一行的末尾

### 数量词
?: may or may not occur

\*  前一个字符0次或无限次 

+: 前一个字符1次或无限次

{m,n}: 前一个字符m至n次

### 逻辑与分组

\|: 代表左右表达式任意一个   abc\|def => abc or def

(...): 被括起来的表达式作为分组 a(123\|456)b => a123b or a456b

(?P\<name\>...): 分组, 除原有的编号外再制定一个别名   (?P\<id\>abc){2} => abcabc

```python
match = re.search(r"(\d+), Date: (.+)", "ID:02345, Date: Jan/28/2020")
print(match.group())
print(match.group(2))
match = re.search(r"(?P<id>\d+), Date: (?P<date>.+)", "ID:02345, Date: Jan/28/2020")
print(match.group('date'))
```

\\\<number\>: 引用编号为\<number\>的分组匹配到的字符窜.  (\\d)abc\\1 => 1abc1 or 3abc3

(?P=name): 引用别名为\<name\>的分组匹配到的字符窜.    (?P\<id\>\\d)abc(?P=id) => 1abc1 or 3abc3

### 寻找所有匹配
re.search(): 查找匹配

re.findall(): 查找找所有匹配

re.sub: 查找并替换

re.split(): 查找与分割

re.compile():

```python
re.findall(r"r[ua]n", "run ran ren")

re.split(r"[,;\.]", "a;b,c.d")

compile_re = re.compile(r"r[au]n")
print(compile_re.search("fly a kite run"))
```

### 参考:

[正则表达式-Python基础](https://morvanzhou.github.io/tutorials/python-basic/basic/13-10-regular-expression/)

