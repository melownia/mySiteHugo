---
title: "Markdown Basics"
date: 2019-07-15T09:53:50-04:00
tags: [markdown]
categories: [tech doc]
featuredImage: ""
featuredImagePreview: "https://tva1.sinaimg.cn/large/007S8ZIlly1gjcpomxgqzj30zk0kn3zz.jpg"
draft: false
lightgallery: true
---

## Headers

### h3
#### h4
##### h5

```
### h3
#### h4
##### h5
```

## Horizontal rules
---

```markdown
---
```

## Italics, Bold

_Hello_
**Hello**
~~Hello~~

```
_Hello_
**Hello**
~~Hello~~
```


## Image  

```Markdown
![Chilehood](https://tva1.sinaimg.cn/large/007S8ZIlly1gjcymbcf2hj30qo0icaer.jpg)
```

![Chilehood](https://tva1.sinaimg.cn/large/007S8ZIlly1gjcymbcf2hj30qo0icaer.jpg)


Markdown also support raw html syntax:

```html
<img src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg"
    width= 200px
    alt="Sunflower"
    style="float: left; margin: 5px;" />
<img src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg"
    width= 200px
    alt="Sunflower"
    style="float: left; margin: 5px;" />
<img src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg"
    width= 200px
    alt="Sunflower"
    style="margin: 5px;" />
```
<img src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg"
    width= 200px
    alt="Sunflower"
    style="float: left; margin: 5px;" />
<img src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg"
    width= 200px
    alt="Sunflower"
    style="float: left; margin: 5px;" />
<img src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg"
    width= 200px
    alt="Sunflower"
    style="margin: 5px;" />

## Code 

```cpp
int i;
for (i=1; i<=9; i++)
{
    cout << i*i << endl;
}
```

````
```cpp
int i;
for (i=1; i<=9; i++)
{
    cout << i*i << endl;
}
```
````

## Lists

### unordered List
- line1
  -line1.1(2 blank space)
  - line1.2
- line2
- line3

```markdown
- line1
  -line1.1(2 blank space)
  - line1.2
- line2
- line3
```

### Ordered List
1. line1
   1.1 line1.1 （3 blank space）
   1.2 line1.2
2. line2
3. line3

```markdown
1. line1
   1.1 line1.1 （3 blank space）
   1.2 line1.2
2. line2
3. line3
```
## Table

colname|colname|colname
--|---|---
Lucy|15|apple

```markdown
colname|colname|colname
--|---|---
Lucy|15|apple
```
## Math

$$\frac{x_1^2+x_2^2}{3}$$
$$\sum_{k=1}^n\frac{1}{k}$$
$$\int_a^b f(x)dx$$
$$E=mc^2$$

```markdown
$$\frac{x_1^2+x_2^2}{3}$$
$$\sum_{k=1}^n\frac{1}{k}$$
$$\int_a^b f(x)dx$$
$$E=mc^2$$
```
## Escaping Backticks 

```markdown
\\ 
\` 
\* 
\_ 
\{} 
\[] 
\() 
\# 
\+ 
\- 
\. 
\! 
```
\\ 
\` 
\* 
\_ 
\{} 
\[] 
\() 
\# 
\+ 
\- 
\. 
\! 
\\ 
\` 
\* 
\_ 
\{} 
\[] 
\() 
\# 
\+ 
\- 
\. 
\! 

##  URLs and Email Addresses

```markdown
<https://swallowblack.github.io>

<zhangsan@example.com>
```
The rended output looks like this:

<https://swallowblack.github.io>

<zhangsan@example.com>

## Adding Title and Formatting Links

This is my personal website **[SwallowBlack](https://swallowblack.github.io/)**
This is about *[Turkey Vulture](https://swallowblack.github.io/2020/02/17/Turkey-Vulture/)*

```markdown
This is my personal website **[SwallowBlack](https://swallowblack.github.io/)**
This is about *[Turkey Vulture](https://swallowblack.github.io/2020/02/17/Turkey-Vulture/)*
```

## Reference-sytle Links
?


## Blockquotes

Blockquotes can contain multiple paragraphs. Add a > on the blank lines between the paragraphs.

>Tomorrow is another day!
>
>Today is a good day!

```markdown
>Tomorrow is another day!
>
>Today is a good day!
```

Nested Blockquotes:
> Tomorrow is another day!
>
>> Today is a good day!

```markdown
> Tomorrow is another day!
>
>> Today is a good day!
```

## References:

<https://www.markdownguide.org/basic-syntax/#links>
