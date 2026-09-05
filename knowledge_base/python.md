# 1. Python 输入输出

## 输入

使用input()语句从键盘获取输入，使用一个变量接受（存储）input()语句获取的键盘输入的数据
- input()语句可以在使用者输入内容之前，输出提示内容，如input(提示内容)
- input默认接受的类型都是字符串类型，如需要进行数字处理，可以利用数字类型转换来实现，如a = int(input())


Python 使用 `input()` 获取用户输入。

```python
a = input()
print(a)
```

由于 `input()` 返回的是字符串，如果需要整数，需要使用 `int()`。

```python
a = int(input())
print(a)
```

对应 C 语言：

```c
int a;
scanf("%d", &a);
```

---

## 输出

Python 使用 `print()` 输出内容。格式：
print(内容1, 内容2, ……, 内容n)
print语句输出内容会自动换行，若想输出不换行则可以在print()语句中加上end=' '即可，最终输出会连在一起不会有空格。
print("Hello World",end=' ')
print()空内容就是输出一个换行
**特殊字符\t，效果等同于在键盘上按下tab键，可以让多行字符串对齐**


```python
print("Hello World")
```

输出变量：

```python
a = 100
print(a)
```

同时输出多个变量：

```python
a = 10
b = 20
print(a, b)
print(10,20)
```

格式化输出：

```python
name = "Tom"
age = 20

print(f"姓名：{name}，年龄：{age}")
```

格式化最终输出：

```
姓名：Tom，年龄：20
```

对应 C 语言：

```c
printf("%d", a);
```

---

# 2. Python 变量

Python 不需要声明变量类型。定义变量格式：
变量名 = 变量值

```python
a = 10
b = 3.14
c = "Hello"
```

变量类型由 Python 自动判断。

```python
a = 10
a = "Python"
```

这是合法的。

对应 C：

```c
int a = 10;
```

>用type()函数验证数据的类型

语法：
type(被查看类型的数据)
例如：print(type(666))
或：
int_type = type(666)
print(int_type)
value = 666 
value_type= type(value)
print(value) # 查询的是数据的类型，而不是变量value的类型，数据有类型，而变量没有类型
输出：< class 'int' >

>数据类型转换

如：
- 从文件中读取数据默认是字符串，要换成数字类型
- input()语句默认结果是字符串，需要数字的话也需要转换
- 将数字转换成字符串用以写到外部系统等等
语句：
将x转换为一个整数：int(x)
将x转换为浮点数：float(x)
将x转换为字符串：str(x)
这三个都是有返回值的，可以用变量来存储这个返回值 
整型可以转换为浮点型（保留一位小数），浮点型也可以转换为整型（只保留整数部分 ）
万物皆可转为字符串类型，但是字符串类型不能转为数字类型
n = int("加油") 这样是不可行的

> 标识符

标识符命名规则：内容限定、大小写敏感或不可使用关键字
只允许出现英文、中文、数字和下划线这四类，但数字不能放在开头（不推荐使用中文）
变量的命名规范：
- 见名知意
- 下划线命名法（两个英文字母用下划线隔开，frist_name）
- 英文字母全小写法 

>字符串的三种定义方法

- 单引号定义法：name = '马文慧'
- 双引号定义法：name = "马文慧"
- 三引号定义法：name = """马文慧"""（与多行注释写法一致，支持换行 ）
如果要定义的字符串包含单引号和双引号自身，可以用单引号法来内含双引号，用双引号法来内含单引号，也可以使用转移字符（\）来引号解除效用，变成普通字符串，如name = "\”马文慧\“"

>字符串拼接

一般，字面量和变量或变量之间会使用拼接，通过+号即可完成，但字符串无法与其他类型通过+号进行拼接。
name = "马文慧"
address = "广西南宁"
print("我是：" + name + ", 我的地址是：" + address)
输出：我是马文慧，我的地址是广西南宁

>字符串格式化

语法："%占位符"%变量
实现字符串与变量拼接用%s，%表示我要占位，s表示将变量变成字符串放入占位的地方
name = "马文慧"
address = "广西南宁"
age = 23
message="我是 %s , 来自 %s, 今年 %d 岁" % (name, address，age)
print(message)
输出：我是马文慧，来自广西南宁, 今年23岁
- %s：将内容转换成字符串，放入占位的位置
- %d：将内容转换成整数，放入占位的位置
- %f：将内容转换成浮点型，放入占位的位置
**字符串快速格式化的方式**：f"内容{变量}"
不限数字类型，不能做数字精度控制
name = "Tom"
age = 20
print(f"姓名：{name}，年龄：{age}")
输出：姓名：Tom，年龄：20

>字符串格式化-数字精度控制

符号：%m.n占位符
- m控制宽度（很少使用），小数点和小数部分也算入宽度计算，设置的宽度小于数字自身不生效
- n控制小数点精度，也就是要保留几位小数，要求是数字，会进行小数的四舍五入
如%5d表示宽度限制为5，%5.2f表示宽度限制为5同时保留2位小数 

>对表达式格式化

- f"内容{表达式}"
- “%s\%d\%f”%(表达式1, 表达式2, 表达式2)

表达式：一条具有明确执行结果的代码语句，如：1+1、5/2、type("字符串")等等
print(f"这个类型是{type("字符串")}")
输出：这个类型是< class 'str'>

---

# 3. if 条件判断

基本语法：

```python
if 要判断的条件:
    （注意4个空格的缩进）条件成立时要做的事情
```
**不要忘记判断条件后面的冒号：**
例如：

```python
a = int(input())

if a >= 60:
    print("及格")
```

注意：

- 条件后必须有 **冒号 `:`**
- 使用 **缩进** 表示代码块（通常 4 个空格）
- 不需要 `{}`

对应 C：

```c
if(a>=60)
{
    printf("及格");
}
```

---

# 4. if-elif-else

多个条件判断：

```python
a = int(input())

if a >= 90:
    print("优秀")
elif a >= 80:
    print("良好")
elif a >= 60:
    print("及格")
else:
    print("不及格")
```

程序特点：

> 从上往下依次判断，只要满足一个条件，就不会继续向下执行。

例如：

输入：

```
95
```

输出：

```
优秀
```
**在条件判断中可以直接写input语句，但是要注意类型变换**

---

# 5. 区间判断

Python 支持链式比较。

一般写法：

```python
if 60 <= a < 80:
    print("及格")
```

等价于：

```python
if a >= 60 and a < 80:
    print("及格")
```

更多示例：

```python
if 0 <= a < 60:
    print("不及格")
elif 60 <= a < 80:
    print("及格")
elif 80 <= a < 90:
    print("良好")
elif 90 <= a <= 100:
    print("优秀")
else:
    print("输入错误")
```

---
>python中常用的6种值

数字(整数、浮点数、复数、布尔)、字符串、列表、元组、集合、字典。
因为布尔值只有真和假，即1和0，所以也属于数字类型

>布尔类型的定义：变量名 = True或False（首字母要大写）

>算数运算符

+：两个对象相加
-：两个对象相减
一个星号是两个对象象成
/：除
//：取整除
%：取余
**两个星号：指数(符号前面是底数，后面是指数)

标准赋值：=
复合赋值：+=、-=、*=、/=、//=、%=等等
# 6. 比较运算符

通过比较运算得到布尔类型的数据。

| 运算符 | 含义   |
| --- | ---- |
| >   | 大于   |
| <   | 小于   |
| >=  | 大于等于 |
| <=  | 小于等于 |
| ==  | 等于   |
| !=  | 不等于  |

例如：

```python
a = 10

print(a > 5)
print(a == 10)
print(a != 8)
```

---

# 7. 逻辑运算符

## and（并且）

两个条件同时成立。

```python
if a >= 60 and a < 80:
    print("及格")
```

对应 C：

```c
&&
```

---

## or（或者）

只要一个条件成立即可。

```python
if a < 0 or a > 100:
    print("输入错误")
```

对应 C：

```c
||
```

---

## not（取反）

```python
if not a >= 60:
    print("不及格")
```

等价于：

```python
if a < 60:
    print("不及格")
```

对应 C：

```c
!
```

---

# 8. Python 与 C 的区别

| C语言           | Python    |     |     |
| ------------- | --------- | --- | --- |
| 使用 `{}` 表示代码块 | 使用缩进表示代码块 |     |     |
| 每行需要 `;`      | 不需要 `;`   |     |     |
| 变量需要声明类型      | 自动推断类型    |     |     |
| `&&`          | `and`     |     |     |
| \|\|          | or        | `   |     |
| `!`           | `not`     |     |     |
> 判断语句的嵌套 

嵌套的关键在于空格缩进，通过空格缩进来决定语句之间的层次关系。

```python
if 条件1:
    满足条件1要做到的事情
    if 条件2:
        满足条件2要做的事情
    elif 条件3：
        满足条件3要做的事情
    else:
        ……其他判断语句
```

---

# 9. 常见错误

## ① 忘记写冒号

错误：

```python
if a >= 60
```

正确：

```python
if a >= 60:
```

---

## ② 判断顺序错误

错误：

```python
if a >= 60:
    print("及格")
elif a >= 90:
    print("优秀")
```

这样 90 分会输出 **及格**。

正确：

```python
if a >= 90:
    print("优秀")
elif a >= 60:
    print("及格")
```

---

## ③ 使用逗号连接条件

错误：

```python
if a >= 60, a <= 70:
```

正确：

```python
if 60 <= a <= 70:
```

或者：

```python
if a >= 60 and a <= 70:
```

---

## ④ 错误使用 or

错误：

```python
if a == 1 or 2:
```

正确：

```python
if a == 1 or a == 2:
```

或者：

```python
if a in [1, 2]:
```

---

# 11. while 循环

`while` 用于**当条件满足时重复执行代码**。

基本语法：

```python
while 条件:
    循环体
```

例如：

```python
i = 1

while i <= 5:
    print(i)
    i += 1
```

输出：

```
1
2
3
4
5
```

对应 C 语言：

```c
int i = 1;

while(i <= 5)
{
    printf("%d\n", i);
    i++;
}
```

注意：

- Python 没有 `{}`，使用缩进表示代码块。
- 如果忘记修改循环变量，容易造成**死循环**。

例如：

```python
while True:
    print("Hello")
```

这是一个无限循环，需要手动结束。

---

# 12. for 循环

Python 的 `for` 与 C 语言不同。

C 语言：

```c
for(int i = 0; i < 5; i++)
{
    printf("%d\n", i);
}
```

Python：

for循环语法：
for 临时变量 in 待处理数据集：
    循环满足条件是执行的代码  
将待处理数据集中的内容一个一个取出并赋予临时变量，这样就可以在循环体内对这个临时变量进行处理。
for环循无法定义循环条件，只能一个一个遍历完数据集里的所有内容。 
**for循环中的临时变量作用域限定在循环内**

```python
for i in range(5):
    print(i)
```

输出：

```
0
1
2
3
4
```

## range() 函数

### 写法一
range(num)获取一个从0开始到num(不包含num本身)的数据序列
```python
range(5)
```

表示：

```
0 1 2 3 4
```

---

### 写法二

range(num1, num2)获取一个从num1开始到num2（不包含num2本身）结束的数字序列
```python
range(2,6)
```

表示：

```
2 3 4 5
```

---

### 写法三

range(num1, num2, step)获取一个从num1开始到num2（不包含num2本身）结束的数字序列，步长为step，不写step默认步长为1.
```python
range(0,10,2)
```

表示：

```
0 2 4 6 8
```

第三个参数表示**步长**。

对应 C：

```c
for(int i = 0; i < 10; i += 2)
```

>for循环的嵌套

就是在一个for循环中再写一个for循环

---

# 13. break 与 continue

## break

结束所在的整个循环。

```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

输出：

```
0
1
2
3
4
```

---
## continue

跳过本次循环，直接进入下一次循环。

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

输出：

```
0
1
3
4
```
**break和continue只作用于所在的循环**

---

# 14. 函数

函数用于**完成一个独立功能，提高代码复用性**。不需要时参数和返回值可以省略。函数是先定义后使用

基本语法：

```python
def 函数名(参数):
    函数体
    return 返回值
```
定义时这个参数是形式参数（实参），多参数用逗号隔开
例如：

```python
def add(a, b):
    return a + b
```

调用函数：

函数名(参数)
调用时这个参数是实际参数（实参），调用时实参与形参要一一对应

```python
result = add(3, 5)
print(result)
```

输出：

```
8
```

对应 C：

```c
int add(int a, int b)
{
    return a + b;
}

int result = add(3,5);
```

Python 的特点：

- 不需要写返回值类型（如 `int`）。
- 不需要声明参数类型。
- 使用 `def` 定义函数。
- 不使用return语句即无返回值的函数实际上就是返回了NoneType类型
>变量作用域：就是变量的作用范围，变量在哪里可用在那里不可用

- 局部变量：定义在函数体内部的变量，即只能在函数体内部生效
-  全局变量：就是变量定义在函数的外面
全局变量在函数中被重新修改相当于函数内部的局部变量，最后这个全局变量的值不会被修改。可以使用global关键字来在函数内定义的变量声明为全局变量，语法是global 关键字。

>函数的多返回值

函数中有多个return语句，但是遇到第一个return语句返回之后就结束了，可以用用语法：return 返回值1, 返回值2, 返回值3, ……

>lambda匿名函数

lambda关键字可以定义匿名函数（无名称）
语法：
lambda 传入参数：函数体（只有一行代码）

---
# 15. Python 常用内置函数

Python 提供了大量内置函数（Built-in Functions），无需导入任何库即可直接使用。

## 1. input()

获取用户输入。

```python
name = input("请输入姓名：")
print(name)
```

返回值类型：

```
str
```

如果需要整数：

```python
age = int(input())
```

---

## 2. print()

输出内容。

```python
print("Hello")
print(100)
print("Python", "Study")
```

格式化输出：

```python
name = "Tom"
age = 20

print(f"{name}今年{age}岁")
```

---

## 3. int()

转换为整数。

```python
a = int("100")
print(a)
```

输出：

```
100
```

---

## 4. float()

转换为浮点数。

```python
a = float("3.14")
print(a)
```

输出：

```
3.14
```

---

## 5. str()

转换为字符串。

```python
a = str(100)

print(a)
```

输出：

```
100
```

类型：

```
str
```

---

## 6. type()

查看变量类型。

```python
a = 10

print(type(a))
```

输出：

```
<class 'int'>
```

其他示例：

```python
print(type(3.14))
print(type("Python"))
print(type(True))
```

---

## 7. len()

计算长度。

字符串：

```python
name = "Python"

print(len(name))
```

输出：

```
6
```

列表：

```python
nums = [1,2,3,4]

print(len(nums))
```

输出：

```
4
```

---

## 8. range()

生成整数序列。

```python
range(5)
```

表示：

```
0 1 2 3 4
```

常用于 for 循环。

```python
for i in range(5):
    print(i)
```

---

## 9. max()

求最大值。

```python
print(max(1,5,3))
```

输出：

```
5
```

列表：

```python
nums=[1,5,8,2]

print(max(nums))
```

---

## 10. min()

求最小值。

```python
print(min(1,5,3))
```

输出：

```
1
```

---

## 11. sum()

求和。

```python
nums=[1,2,3,4]

print(sum(nums))
```

输出：

```
10
```

---

## 12. abs()

求绝对值。

```python
print(abs(-10))
```

输出：

```
10
```

---

## 13. round()

四舍五入。

```python
print(round(3.14159,2))
```

输出：

```
3.14
```

第二个参数表示保留的小数位数。

---

## 14. sorted()

排序。

```python
nums=[4,1,8,3]

print(sorted(nums))
```

输出：

```
[1,3,4,8]
```

降序：

```python
print(sorted(nums, reverse=True))
```

---

## 15. enumerate()

同时获得下标和值。

```python
names=["Tom","Jack","Lucy"]

for index,name in enumerate(names):
    print(index,name)
```

输出：

```
0 Tom
1 Jack
2 Lucy
```

以后读论文代码经常看到。

---

## 16. zip()

同时遍历多个列表。

```python
names=["Tom","Jack"]
ages=[20,21]

for name,age in zip(names,ages):
    print(name,age)
```

输出：

```
Tom 20
Jack 21
```

---

## 17. list()

转换为列表。

```python
a=range(5)

print(list(a))
```

输出：

```
[0,1,2,3,4]
```

---

## 18. tuple()

转换为元组。

```python
nums=[1,2,3]

print(tuple(nums))
```

输出：

```
(1,2,3)
```

---

## 19. bool()

转换为布尔值。

```python
print(bool(1))
print(bool(0))
```

输出：

```
True
False
```

---

## 20. help()

查看帮助文档。

```python
help(print)
```

或者

```python
help(len)
```

学习新函数时非常有用。

---

# 常用函数总结

| 函数          | 作用       |
| ----------- | -------- |
| input()     | 输入       |
| print()     | 输出       |
| int()       | 转整数      |
| float()     | 转浮点数     |
| str()       | 转字符串     |
| bool()      | 转布尔值     |
| type()      | 查看数据类型   |
| len()       | 求长度      |
| range()     | 生成整数序列   |
| max()       | 最大值      |
| min()       | 最小值      |
| sum()       | 求和       |
| abs()       | 绝对值      |
| round()     | 四舍五入     |
| sorted()    | 排序       |
| enumerate() | 获取索引和值   |
| zip()       | 同时遍历多个序列 |
| list()      | 转列表      |
| tuple()     | 转元组      |
| help()      | 查看帮助     |
>数据容器

数据容器就是一种可以容纳多分数据的数据类型，容纳的每一份数据称之为1个元素。每一个元素，可以是任意类型的数据，比如字符串、数字、布尔等，支持嵌套列表。
数据容器的种类有list（列表）、tuple（元组）、str（字符串）、set（集合）、dict（字典）

>列表的定义(可容纳多个元素、不同数据类型、有序存储、允许重复数据存在，可以增删改查)

字面量：
[元素1, 元素2, 元素3, ……]
定义变量：
变量名称 = [元素1, 元素2, 元素3, ……]
定义空列表：
变量名称 = []
变量名称 = list()
列表内的每一个数据称之为元素，以[]作为标识，元素之间用逗号隔开。
**列表的下标**
从前往后下表从0开始一次递增，从后往前从-1开始一次递减，-1就是倒数第一个元素，-2是倒数第二个元素，如list[-1]，如果是嵌套列表则是list[1][2]
**列表的查询功能（方法）**
查找指定元素在列表中的下标，如果找不到，报错ValueError
语法：列表.index(元素)
index()就是列表对象内置的函数
mylist = ["a","b","c","d"]
index = mylist.index("a")
print(f"你要查询的下标是：{index}")
输出：你要查询的下表是：0

修改列表中特定位置（索引）的元素值:
语法：列表[下标] = 值
如mylist[1]="B"

插入元素：
语法：列表.insert(下标, 元素)，在指定的下标位置插入指定的元素
如mylist.insert(2, “C”)

追加元素：
语法：列表.append(元素)，将指定元素 追加到列表的尾部
mylist.append("e")
另一种方法：列表.extend(其他数据容器)，将其他数据容器里的内容取出，依次追加到列表末尾。

删除元素：
语法1：del 列表[下标]
语法2：列表.pop(下表)
如del mylist[1]
或 mylist.pop(1)
还有一种语法：列表.remove(元素)，从前往后删除列表中与此元素第一个匹配的项。

清空列表：
列表.clear()

统计次数：
语法：列表.count(元素)，统计此元素在列表中出现的次数

求列表长度：
len(列表)，统计容器内有多少元素。

**列表的遍历**
while循环：
index = 0
while index < len(列表)：
    元素 = 列表[index]
    对元素进行处理
    index+=1
for循环：
for 临时变量 in 数据容器：
    对临时变量进行处理
表示从容器内一次取出元素赋值到临时变量上，每次循环都可以对这个零食变量进行处理。

>tuple元组

元组也可以封装多个、不同数据类型、数据可以存在的元素在内，但是元组一旦被定义就不可以修改，支持嵌套元组，支持下标索引（与列表一致）
**元组定义**
定义元组字面量：
(元素1，元素2，元素3，……)
定义元组变量：
变量名称 = (元素1，元素2，元素3，……)
定义空元组：
变量名称 = ()
变量名称 = tuple()
**元组的相关操作**
index()：查询某个数据，如果存在返回对应的下标，否则报错
count()：统计某个数据在当前元组中出现的个数
len(元组)：统计元组内的元素个数

**如果元组内嵌套了列表，就可以修改元组内的list的内容**
t = (1, 2, [3, 4, 5])
t[2][0]=4

>字符串

字符串是字符的容器，一个字符串可以存放任意数量的字符。和列表、元组一样支持下标索引，但它和元组一样是不可修改的。

查找功能：
字符串.index(数据)，返回该数据在字符串中第一个与之匹配的下标

字符串的替换：
语法：字符串.replace(字符串1，字符串2)
将字符串内的全部字符串1替换为字符串2
不是修改字符串本身，而是得到了一个新的字符串

字符串的分割
语法：字符串.split(分割符字符串)
按照指定的分割符字符串，将字符串划分为多个字符串，并存入列表对象中（字符串本身不变而是得到了一个列表对象，将分割出来的字符串作为元素组成一个列表）

去前后空格：
语法：字符串.strip()

去前后指定字符串：
语法：字符串.(字符串)

统计字符串中某字符串的出现次数：
字符串.count(字符串)

统计字符串的字符个数：
len(字符串)

>序列

序列是指内容连续、有序，可使用下标索引的一类数据容器。列表、元组、字符串，均可以视为序列。

**序列的切片**
切片就是从一个序列中取出一个子序列。
语法：序列[起始下标: 结束下标: 步长]
表示从序列中从指定位置开始，一次取出元素，到指定位置结束，得到一个新序列，不影响原始序列。
- 起始下标可以留空，留空视作从头开始
- 结束下标（不含）可以留空，留空视作截取到结尾
- 步长表示依次取元素的间隔，不写默认为1，步长为一可以不写，步长可以为负数，表示倒序执行，步长为-2就是逆序间隔两个取一个元素。

>set集合

可容纳多个不同类型数据、乱序、不允许重复（会去重），不支持下标索引，但允许修改。
基本语法：
定义集合字面量：
{元素1，元素2，元素3……}
定义集合自变量：
变量名称 = {元素1，元素2，元素3……}
定义空集合：
变量名称 = set()

添加新元素
语法：集合.add(元素)
将指定元素添加到集合中。

移除元素：
语法：集合.remove(元素)
将指定元素从集合中移除。

从集合中随机取出元素
语法：集合.pop()
从集合中随机取出一个元素，取出之后集合就不存在这个元素。

清空集合
语法：集合.clear()

取出两个集合的差集
语法：集合1.difference(集合2)
取出集合1和集合2 的差集（集合1有二集合2没有的），得到一个新集合，集合1和集合2 不变。

消除两个集合的差集
语法：集合1.difference_update(集合2)
对比集合1和集合2，在集合1内删除与集合2相同的元素
集合1被修改但集合2不变

两个集合合并
语法：集合1.unior(集合2)
将集合1和集合2组合成新集合（去重）
得到新集合，集合1和集合2不变

统计集合元素数量
语法：len(集合)

集合的遍历
因为集合不支持下标索引，所以不支持while循环，而支持for循环

>dict字典

字典的定义同样使用花括号{}，不过存储的元素是一个个键值对，键key不可以重复，key和value可以是任意类型，但key不能为字典。不可用下标索引，是通过key检索value
定义字典字面量：
{key1: value1, key2: value2, ……}
定义字典变量：
变量名 = {key1: value1, key2: value2, ……}
定义空字典：
变量名 = {}
变量名 = dict()

新增元素
语法：字典[key]=value
字典被修改新增了元素

更新元素
语法：字典[key]=value
对已存在的key执行上述操作，就是更新value值

删除元素
语法：字典.pop(key)
获取指定key的value，同时字典被修改，指定key的数据被删除

清空字典
语法：字典.clear()
字典被修改元素被清空

获取字典的全部key
语法：字典.keys()
可用于for循环遍历字典

计算字典内的元素数量
语法：len(字典)

字典的遍历
keys=字典.keys()
for key in keys:
    print(字典[key])
或者：
for key in 字典：

**容器总结**
集合和字典这两种非序列类型不支持下标索引和重复元素且乱序
只有元组和字符串不支持修改，其他都可以修改
通用操作：
len(容器) max(容器) min(容器)
list(容器 )是容器转为列表
tuple(容器)是容器转为元组
str(容器)是容器转为字符串
set(容器)是容器转为集合
sorted(序列)对容器内容排序放在列表对象中，加上reverse=True实现逆序

**字符串比较大小**
字符串是按位比较，也就是一位一位进行比较，只要有一位大那么整体就大。比较的是字符的ASCII码值。


---

# 16. 什么是 Class（类）

## 1. 类的定义

Class（类）可以理解为**一种模板（Template）**。

它规定了一类对象共同拥有的：

- 属性（Attribute）
- 行为（Method）

例如：

```
学生
├── 姓名
├── 年龄
├── 学号
├── 学习()
└── 考试()
```

这里：

Student 就是一个 Class。

---

## 2. 什么是对象（Object）

对象（Object）是根据类创建出来的实例。

例如：

```
Student（类）

↓

张三
李四
王五
```

张三、李四、王五都是 Student 类创建出来的对象。

Python 中：

```python
student = Student()
```

这里：

```
Student ------> 类

student ------> 对象
```

---

## 3. 创建第一个 Class

```python
class Student:
    pass
```

解释：

```
class表示开始定义一个类,Student是类名,pass表示暂时什么也不做
```

创建对象：

```python
student = Student()
```

运行：

```python
print(student)
```

输出：

```
<__main__.Student object at 0x...>
```

说明：

已经创建了 Student 对象。

---
>类的组成

- 类的属性，称之为成员变量
- 类的行为，称之为成员方法
若函数是写在类外，定义在类内部，都称之为方法。

**类和成员变量的定义方法**

定义语法：
class 类名称：
    成员变量
    def 成员方法(self, 参数列表)
    成员方法体

创建对象语法：
对象=类名称()

**self的作用**
- 表示类对象本身的意思
- 只用通过self，成员方法才能访问类的成员变量
- self出现在形参列表中，但是不占用参数位置，无需理会

## 4. __init__() —— 构造方法
- 在创建类对象（构造类）时，会自动执行
- 在创建类对象（构造类）时，将传入参数自动传递给__init__()方法使用，为成员变量赋值
创建对象语法：
对象=类名称(参数)
- 构造方法不要忘记self关键字
- 在方法内使用成员变量需要使用self

>__str__字符串方法

将类对象转换为字符串的行为

>__lt__ 小于符号比较方法

不可以直接对两个对象进行比较，通过在类中实现__it__方法，实现小于符号和大于符号两种比较。
def __lt__(self, other):
    return self.age < other.age
传入参数：other，另一个类对象
返回值：True或False
内容：自定义

>__le__ 小于等于比较符号方法

def __le__(self, other):
    return self.age <= other.age
传入参数：other，另一个类对象
返回值：True或False
内容：自定义

>__eg__ 等于比较符号方法

def __le__(self, other):
    return self.age == other.age
传入参数：other，另一个类对象
返回值：True或False
内容：自定义

---
>封装

将现实世界事物在类中国描述为属性和方法，即为封装

>私有成员

- 私有成员变量：变量名以__（两个下划线）开头
- 私有成员方法：方法名以__（两个下划线）开头
私有成员无法被类对象访问，但是可以被类中其他成员访问。
---
>单继承

继承表示将从父类那里继承（复制）来成员变量和成员方法（不含私有成员）
基本语法：
class 类名(父类名)：
    类内容体

>多继承

一个类继承多个类，按照顺序从左到右一次继承
如果父类中有同名的方法火属性，先继承的有限级高于后继承
class 类名(父类1, 父类2, ……, 父类N):
    类内容体
**pass关键字**
pass是一个占位语句，用来保证函数或方法或类定义的完整性，表示无内容，空的意思

>复写

字类继承父类的成员属性和成员方法后，如果“不满意“，可以进行复写，即在子类中重新定义同名的属性和方法即可。
 
>子类中调用父类成员

方式1：
使用父类成员：父类名.成员变量
使用成员方法：父类名.成员方法(self)

方式2：
- 使用super()调用父类成员
使用成员变量：super().成员变量
使用成员方法：super().成员方法()

**只可以在子类内部调用父类的同名成员，子类的实体类对象调用默认是调用字类复写的**

>类型注解

在代码中涉及数据交互的地方，提供数据类型的注解（显式的说明），支持变量类型注解与函数（方法）形参列表和返回值的类型注解。
一般无法直接看出变量类型时会添加变量的类型注解。
**为变量设置类型注解**
基本语法：
变量: 类型
如：
基础数据类型注解
var_1: int = 10
var_2: float = 3.1415926
类对象类型注解
stu: Student = Student()
基础容器类型注解
my_list: list = [1, 2, 3]
容器类型的详细注解
my_list: list[int] = [1, 2, 3]
- 元组类型设置类型详细注解，需要将每一个元素都标记出来
- 字典类型设置类型详细注解，需要2个类型，第一个是key第二个是value
除了这种语法还可以在注释中进行类型注解：
语法：
 # # type: 类型
 **类型注解只是提示性的而非决定性的**

**函数（方法）的类型注解**
- 形参类型注解
- 返回值类型注解
def 函数方法名(形参: 类型, ……, 形参: 类型) ->返回值类型: pass
注意：返回值类型注解的符号使用的时->

**Union类型**
使用Union类型可以定义联合类型注解
使用方式：
- 导包：from typing import Union
- 使用：Union[类型1, 类型2, ……]
表示数据类型时这几个类型的其中一个。

>多态

多态是指同一个行为使用不同的对象获得不同的状态。
如定义函数，通过类型注解声明需要父类对象，实际传入子类对象进行工作，从而获得不同而定工作状态。

>抽象类（接口）

包含抽象方法的类就称之为抽象类
抽象方法是指没有具体实现的方法（pass）
多用于做顶层设计（设计标准），以便字类做具体实现。
也是对子类的一种软性约束，要求子类必须复写（实现）父类的一些方法（抽象方法），并且配合多态实现不同的状态。

---

# 13. 推荐系统源码案例一（RecBole）

例如：

```python
class SequentialRecommender(AbstractRecommender):
```

源码分析：

### 第一步

```
SequentialRecommender

↓

子类
```

---

### 第二步

```
AbstractRecommender

↓

父类
```

---

### 第三步

为什么这样设计？

因为：

所有推荐模型都有共同内容：

```
dataset

config

logger

device

loss
```

父类负责：

```
统一管理
```

子类只需要：

```
实现自己的模型
```

例如：

```
SASRec

BERT4Rec

GRU4Rec

DuoRec
```

都继承：

```
SequentialRecommender
```

这样代码不会重复。

---

## 14. 推荐系统源码案例二（SASRec）

SASRec 中：

```python
class SASRec(SequentialRecommender):
```

继续看：

```python
class SASRec(SequentialRecommender):

    def __init__(self, config, dataset):

        super().__init__(config, dataset)
```

逐行解释：

第一行：

```
class SASRec

↓

定义一个推荐模型
```

第二行：

```
SequentialRecommender

↓

父类
```

第三行：

```
super().__init__()
```

作用：

调用父类初始化。

父类负责：

```
读取配置

读取数据集

初始化GPU

保存参数

日志初始化
```

SASRec 自己不用重复写。

---

继续：

```python
self.hidden_size = config["hidden_size"]
```

说明：

```
self

↓

当前模型对象
```

hidden_size：

保存模型参数。

以后：Transformer、Embedding、Attention都会使用：

```
self.hidden_size
```

---

## 15. 推荐系统源码案例三（BERT4Rec）

例如：

```python
class BERT4Rec(SequentialRecommender):
```

里面：

```python
self.item_embedding = nn.Embedding(
    self.n_items,
    self.hidden_size
)
```

为什么写 self？

因为：

Embedding 是：

```
当前模型自己的成员变量
```

以后：

forward()

predict()

loss()

都需要使用：

```
self.item_embedding
```

所以必须保存为：

```
self.xxx
```

如果写成：

```python
item_embedding
```

函数结束以后，

变量立即消失。

模型无法继续使用。

---

# 17. 什么是文件读写（File I/O）

## 17.1 什么是文件？

文件（File）是存储在磁盘上的数据。

常见文件类型：

| 文件类型 | 扩展名 | 用途 |
|----------|--------|------|
| 文本文件 | `.txt` | 普通文本 |
| CSV 文件 | `.csv` | 表格数据 |
| JSON 文件 | `.json` | 配置、字典数据 |
| YAML 文件 | `.yaml` / `.yml` | 深度学习配置文件 |
| 模型文件 | `.pth` | PyTorch 模型参数 |
| 日志文件 | `.log` | 训练日志 |
>什么是编码？

编码就是一种规则集合，记录了内容和二进制之间进行相互转换的逻辑，最常用的就是UTF-8编码。计算机只认识0和1，所以需要将内容翻译成0和1才能保存在计算机中。同时也需要编码将计算机保存的0和1反向翻译回可以识别的内容。

>文件的读取操作 

---

## 17.2 open()——打开文件

Python 使用 `open()` 打开文件。

语法：

```python
open(name, mode, encoding)
```

参数说明：

| 参数       | 含义                             |
| -------- | ------------------------------ |
| name     | 要打开文件的目标文件名的字符串（可以包含文件所在的具体路径） |
| mode     | 打开方式（只读、写入、追加等）                |
| encoding | 文件编码格式（通常使用 UTF-8）             |
**name和mode是位置参数**
示例：

```python
f = open("student.txt", "r", encoding="utf-8")
```
此时的f是open函数的文件对象，对象是python中的一种特殊的数据类型，拥有属性和方法，可以使用对象.属性或对象.方法对其进行访问。

---

## 17.3 文件打开方式（mode）

| 模式     | 含义                                                  |
| ------ | --------------------------------------------------- |
| `"r"`  | 只读（默认），文件的指针将会放在文件的开头，若文件不存在则会报错                    |
| `"w"`  | 打开一个文件只用于写入（覆盖原文件）。如果该文件已存在则打开文件，并从开头开始编辑，原有内容会被删除。 |
| `"a"`  | 追加内容。如果该文件已存在，新的内容将会被写入到已有内容之后，如果该文件不存在，则创建新文件进行写入。 |
| `"x"`  | 创建新文件                                               |
| `"rb"` | 二进制读取                                               |
| `"wb"` | 二进制写入                                               |

例如：

```python
file = open("data.txt", "w")
```

如果文件不存在，会自动创建。

---

## 17.4 读取文件

### 17.4.1 read()

语法：文件对象.read(num)
num表示要从文件中读取的数据的长度（单位是字节），如果没有传入num，则表示读取文件中的所有数据。

```python
with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()

print(content)
```
**程序中若多次调用read，则本次read指针会在上一个read的结尾处开始读取**

---

### 17.4.2 readline()

readlines()可以按照行的方式把整个文件的内容一次性读取，也就是一次读取全部行，并且返回一个列表，其中每一行的数据为一个元素。而readline()则是一次读取一行。
```python
with open("data.txt", "r", encoding="utf-8") as f:
    line = f.readline()

print(line)
```

---

### 17.4.3 readlines()

读取所有行，并返回列表。

```python
with open("data.txt", "r", encoding="utf-8") as f:
    lines = f.readlines()

print(lines)
```

例如：

```
[
"Tom\n",
"Alice\n",
"Bob\n"
]
```

>close()关闭文件对象

```python
f = open("data.txt", "r", encoding="utf-8")
f.close()
```
最后通过close关闭文件对象，也就是关闭对文件的占用。如果不调用close同时程序没有停止运行，那么这个文件将一致被python程序占用

>with open() as f

```python
with open("data.txt", "r", encoding="utf-8") as f:
    lines = f.readlines()
```
通过在with open的语句块中对文件进行操作，在操作完成后自动关闭close文件，避免遗忘掉方法。

---

## 17.5 写入文件

### write():写入内容

```python
with open("result.txt", "w", encoding="utf-8") as f:
    f.write("Hello World")
```

运行后：

```
result.txt

Hello World
```
### flush：刷新内容到硬盘
---
**w模式下文件不存在则会创建新文件；文件存在则会清空原有内容**。close()方法自带flush()方法的功能的。

## 多次写入

```python
with open("result.txt", "w") as f:

    f.write("Python\n")

    f.write("PyTorch\n")

    f.write("RecSys\n")
```

输出：

```
Python

PyTorch

RecSys
```

---

## 17.6 为什么推荐使用 with open()

推荐：

```python
with open("data.txt") as f:
    ...
```

不推荐：

```python
f = open("data.txt")

...

f.close()
```

原因：

`with` 会自动关闭文件。即使程序报错，文件也不会一直占用。

---
>文件的追加

1. 打开文件以a模式打开即可
f = open("python.txt",a)
2. 文件写入
f.write()
3. 内容刷新
f.flush()
**a模式文件不存在则会创建文件；存在则会在文件的最后追加写入内容**
可以使用"\n"来写出换行符。
## 17.7 CSV 文件读写

CSV（Comma-Separated Values）是推荐系统最常见的数据格式。

例如：

```
user_id,item_id,rating,timestamp

1,10,5,978300760

1,20,4,978302109
```

读取：

```python
import csv

with open("ratings.csv", "r", encoding="utf-8") as f:

    reader = csv.reader(f)

    for row in reader:

        print(row)
```

输出：

```
['1','10','5','978300760']
```

---

## 17.8. JSON 文件读写

JSON 常用于保存配置。

例如：

```json
{
    "learning_rate":0.001,
    "epoch":100
}
```

读取：

```python
import json

with open("config.json","r") as f:

    config=json.load(f)

print(config["learning_rate"])
```

输出：

```
0.001
```

---

## 17.9 文件路径

例如：

```
project

├── data

│   └── ratings.csv

├── train.py
```

相对路径：

```python
data/ratings.csv
```

绝对路径：

```
D:/Research/data/ratings.csv
```


---

## 17.10 推荐系统中的应用

推荐系统每天都要读取数据。

例如：

MovieLens：

```
ratings.csv
```

Amazon：

```
Books.csv
```

Yelp：

```
reviews.json
```

整个训练流程：

```
磁盘

↓

读取数据

↓

Python

↓

PyTorch Dataset

↓

DataLoader

↓

模型训练
```

---

## 17.11 推荐系统源码案例（一）——RecBole 数据读取

RecBole 会读取配置文件，例如：

```yaml
epochs: 100
learning_rate: 0.001
train_batch_size: 256
```

Python 中通常会：

```python
with open(config_path, "r", encoding="utf-8") as f:
    config = yaml.safe_load(f)
```

源码解读：

第一步：

```
打开 YAML 文件
```

第二步：

```
读取全部内容
```

第三步：

```
转换为 Python 字典
```

例如：

```python
config["epochs"]
```

即可获得：

```
100
```

---

## 17.12 推荐系统源码案例（二）——MovieLens 数据集读取

MovieLens 数据通常是 CSV：

```
user_id,item_id,rating,timestamp
```

科研项目中一般会：

```python
import pandas as pd

ratings = pd.read_csv("ratings.csv")
```

读取后的 `ratings` 是一个 DataFrame，可以方便地进行：

- 数据筛选
- 排序
- 去重
- 划分训练集和测试集

这也是为什么推荐系统项目大量使用 Pandas。

---

## 17.13 推荐系统源码案例（三）——PyTorch 保存模型

模型训练结束后：

```python
torch.save(model.state_dict(), "model.pth")
```

以后继续训练：

```python
model.load_state_dict(torch.load("model.pth"))
```

这里的 `.pth` 文件就是通过文件读写保存到磁盘上的。

---

# 14. 本章总结

| 知识点         | 推荐系统中的应用 |
| ----------- | -------- |
| open()      | 打开数据文件   |
| read()      | 读取文本     |
| readline()  | 按行读取     |
| readlines() | 批量读取     |
| write()     | 保存结果     |
| with open() | 推荐写法     |
| CSV         | 数据集      |
| JSON        | 配置文件     |
| 文件路径        | 项目管理     |

---
>异常

当检测到一个错误时，python解释器就无法继续执行了，反而出现了一些错误的提示，这既是所谓的“异常”，也就是BUG。

**捕获异常**
作用在于提前假设某处会出现异常，做好提前准备，当真的出现异常时可以有后续手段。
基本语法：
try:
    可能要发生异常的语句
except[ 异常名 as 别名]：
    出现异常时要执行的代码
[ else :]
    未出现异常时应做的事情
[ finally: ]
    不管出现不出现异常都要执行的代码
捕获所有异常：
try:
    可能发生错误的代码
except:
    如果出现异常执行的代码
或者：
try:
    可能发生错误的代码
except Exception as e:
    如果出现异常执行的代码
**捕获指定异常**
基本语法：
try:
    print(name)
except NameError as e:
    print("name变量名称未定义错误“)
如果尝试执行语句的代码的异常类型和要捕获的异常类型不一致则无法捕获异常。
一般try语句下方脂肪一行尝试执行的代码。
**捕获多个异常**
档捕获多个异常时，可以把要捕获的异常类型的名字放在except后，并使用元组的方式书写。
try：
    print(1/0)
except(NmaeError, ZeroDivisonError):
    print("ZeroDivisonError错误……")
**异常else**
else表示如果没有异常要执行的代码
try：
    print(1)
except Exception as e:
    print(e)
else:
    print("我是else, 是没有异常时要执行的代码")
**异常finally**
finally表示的是无论是否发生异常都要执行的代码。
try：
    f = open("test.txt","r")
except Exception as e:
    f = open("test.txt","w")
else:
    print("没有异常，真开心")
finally：
    f.close()

**异常的传递性**
运行之后从下往上看报错信息，异常就是从底层往高层传递。

>模块（Module）

python的模块（Module），是一个python文件，以.py结尾，模块能定义函数、类和变量，模块里面也能包含可执行的代码。

模块的作用：模块就是一个工具包，将其导入就可以使用
**模块的导入**
语法：
[from 模块名] import [模块 | 类 | 变量 | 函数 | * ]  [as 别名] 
**当导入多个模块的时候，且模块内有同名功能，当调用这个同名功能时调用的的是后面导入的模块的功能**
常用的组合形式：
- import 模块名
- from 模块名 import 类、变量、方法等
- from 模块名 import *
- import 模块名 as 别名
- from 模块名 import 功能名 as 别名
**import 模块名**
基本语法：
import 模块名
import 模块名1，模块名2
模块名.功能名()
**from 模块名 import 功能名**
基本语法：
from 模块名 import 功能名
功能名()
**from 模块名 import *

导入这个模块的所有功能
基本语法：
from 模块名 import *
功能名()
**as别名**
给具体的模块或功能改名。
基本语法：
import 模块名 as 别名
from 模块名 import 功能名 as 别名

>**自定义模块**

创建一个python文件，自定义文件名称，然后在里面自定义函数或类即可。模块名称就是这个python文件。

>**测试模块**

开发人员为了测试模块效果，在py文件中添加测试信息，如测试代码test(1, 2)
def test(a, b):
    print(a+b)

test(1, 2)
此时无论是当前文件还是其他已经导入了该模块的文件，在运行时都会自动执行test函数的调用。
解决方案：
def test(a, b):
    print(a+b)
if __name__ == '__main__':
    test(1, 2)
这样只有在当前文件中调用该函数，其他导入的文件内不符合该条件则不会执行test函数调用。

>  __all__

如果一个模块文件中有‘__all__’变量，当使用from xxx import *导入时只能导入这个列表中的元素

>**python包

物理上，包就是一个文件夹，在该文件夹下包含了一个__init__.py文件，该文件可用于包含多个模块文件。
逻辑上，包的本质依然是模块。

**创建包**
- 创建包（创建包后，包内部会自动创建__init__.py文件，这个文件夹控制着包的导入行为）
- 创建包内模块
 **导入包**
import 包名.模块名
from 包名 import 模块名
from 包名.模块名 import 函数名
__all__变量写在__init__.py文件中，控制import *能够导入的内容

>**第三方包**

第三方包是非python包，需要安装它们才可以使用
**安装第三方包**
在命令提示符内输入：
pip install 包名称
即可通过网络快速安装第三方包（国外的网站安装）

连接国内清华大学网站安装包
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple 包名

>什么是json

json是一种轻量级的数据交互格式，本质上是一个带有特定格式的字符串。json就是一种在各个编程语言中流通的数据格式，负责不同编程语言中的数据传递和交互。也可以认为是json是python中将内部元素都是字典的列表或字典转换为字符串。
**python数据和json数据的相互转化**
导入json模块：
import json
准备符合json格式要求的python数据：
data=[{"name":"老王","age":16}, {"name": "张三", "age":20}]
通过json.dumps(data)方法把python数据转化了json数据（有中文数据要加上ensure_ascii=False确保中文正常转换）：
data=json.dumps(data)
通过json.loads(data)方法json数据转化为python数据：
data=json.loads(data)

>pyecharts模块

可以借助pyecharts模块来做数据可视化的效果图。
安装pyecharts：
pip install pyecharts

打开官方画廊查看官方示例：
[中文简介 - Document](https://gallery.pyecharts.org/#/README)

>基础的折线图

导包，导入Line功能构建折现图对象：
from pyecharts.charts import Line
得到折线图对象：
line = line()
添加x轴数据：
line.add_xaxis(["中国"，"美国"，"英国"])
添加y轴数据：
line.add_yaxis("GDP"，[30, 20, 10])
生成图表：
line.render()

>pyecharts配置选项(可参考官网)

- 全局配置选项
- 系列配置选项
**全局配置选项**
可以通过set_global_opts方法来进行配置：
- TitleOpts：标题配置项
- LegendOpts：图例配置项
- ToolboxOpts：工具箱配置项
- TooltipOpts：提示框配置项
- VisualMapOpts：视觉映射配置项
- DataZoomOpts：区域缩放配置项
注意要导包：from pyecharts.options import TitleOpts, LegendOpts, ToolboxOpts, TooltipOpts, VisualMapOpts, DataZoomOpts.







# 18. Pandas 数据处理

## 18.1 什么是 Pandas

### Pandas 简介

Pandas 是 Python 中最流行的数据分析库，其名称来源于 **Panel Data（面板数据）**。

官方网址：

https://pandas.pydata.org/

Pandas 建立在 NumPy 之上，提供了更加方便的数据处理能力。

---

### 为什么要学习 Pandas？

在机器学习和推荐系统中，原始数据通常来自：

- CSV 文件
- Excel 文件
- 数据库
- JSON 文件
- 用户行为日志

例如 MovieLens 数据集：

| user_id | item_id | rating | timestamp |
|---------:|--------:|-------:|----------:|
| 1 | 1193 | 5 | 978300760 |
| 1 | 661 | 3 | 978302109 |
| 2 | 914 | 4 | 978301968 |

如果不用 Pandas，需要自己逐行解析，非常繁琐。

使用 Pandas：

```python
import pandas as pd

ratings = pd.read_csv("ratings.csv")
```

只需一行代码，就可以读取整个数据集。

---

## 18.2 Pandas 的核心数据结构

Pandas 中最重要的两个对象是：

- Series（一维数据）
- DataFrame（二维表格）

---

### Series

Series 可以理解为**带索引的一维数组**。

创建 Series：

```python
import pandas as pd

s = pd.Series([10, 20, 30])

print(s)
```

输出：

```
0    10
1    20
2    30
dtype: int64
```

特点：

- 每个元素都有索引
- 可以存储不同类型的数据
- 类似 Excel 的一列

---

### DataFrame

DataFrame 是 Pandas 最核心的数据结构。

可以理解为：

> **一个带有行索引和列索引的二维表格。**

例如：

```python
import pandas as pd

df = pd.DataFrame({
    "姓名": ["Alice", "Bob", "Tom"],
    "年龄": [20, 22, 21],
    "成绩": [90, 85, 95]
})

print(df)
```

输出：

```
      姓名  年龄  成绩
0  Alice  20  90
1    Bob  22  85
2    Tom  21  95
```

在推荐系统中，几乎所有数据都会以 DataFrame 的形式进行处理。

---

## 18.3 读取数据

### 读取 CSV 文件

```python
import pandas as pd

df = pd.read_csv("ratings.csv")
```

查看前五行：

```python
df.head()
```

查看最后五行：

```python
df.tail()
```

查看数据规模：

```python
df.shape
```

输出：

```
(100836, 4)
```

表示：

- 100836 行
- 4 列

---

## 18.4 查看数据基本信息

查看数据类型：

```python
df.info()
```

输出示例：

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 100836 entries
Data columns (total 4 columns):
```

查看统计信息：

```python
df.describe()
```

可得到：

- 平均值（mean）
- 最大值（max）
- 最小值（min）
- 标准差（std）

这些统计信息对于分析数据分布非常重要。

---

## 18.5 数据选择

选择一列：

```python
df["rating"]
```

选择多列：

```python
df[["user_id", "item_id"]]
```

选择指定行：

```python
df.iloc[0]
```

按标签选择：

```python
df.loc[0]
```

---

## 18.6 数据筛选

筛选评分大于 4 的记录：

```python
high_rating = df[df["rating"] >= 4]

print(high_rating.head())
```

筛选某个用户：

```python
user1 = df[df["user_id"] == 1]
```

这是推荐系统中最常见的数据操作。

---

## 18.7 数据排序

按照评分排序：

```python
df.sort_values(by="rating")
```

降序排序：

```python
df.sort_values(by="rating", ascending=False)
```

---

## 18.8 数据分组

统计每个用户评价了多少商品：

```python
df.groupby("user_id").size()
```

统计每个商品被评价次数：

```python
df.groupby("item_id").size()
```

统计平均评分：

```python
df.groupby("item_id")["rating"].mean()
```

在推荐系统中，分组统计用于分析：

- 活跃用户
- 热门商品
- 长尾商品

---

## 18.9 缺失值处理

查看缺失值：

```python
df.isnull().sum()
```

删除缺失值：

```python
df.dropna()
```

填充缺失值：

```python
df.fillna(0)
```

推荐系统的数据通常需要先处理缺失值，再进行训练。

---

## 18.10 删除重复数据

查看重复值：

```python
df.duplicated().sum()
```

删除重复值：

```python
df.drop_duplicates()
```

避免同一条用户行为被重复统计。

---

## 18.11 保存数据

保存为 CSV：

```python
df.to_csv("clean_data.csv", index=False)
```

这样可以将处理后的数据保存下来，供后续模型训练使用。

---

## 18.12 Pandas 在推荐系统中的应用

推荐系统的数据处理流程通常如下：

```
原始数据（CSV）
        │
        ▼
Pandas 读取
        │
        ▼
数据清洗
        │
        ▼
缺失值处理
        │
        ▼
重复值删除
        │
        ▼
数据统计
        │
        ▼
划分训练集/验证集/测试集
        │
        ▼
转换为 PyTorch Dataset
        │
        ▼
模型训练
```

---

## 18.13 推荐系统源码案例

RecBole 和 SASRec 在数据预处理阶段，都会先读取数据文件：

```python
import pandas as pd

ratings = pd.read_csv("ratings.csv")
```

随后进行：

```python
ratings = ratings.sort_values("timestamp")
```

按时间排序后，可以构造用户的行为序列，例如：

```
用户A：

电影1
↓

电影5
↓

电影8
↓

电影12
```

对于序列推荐模型（如 SASRec、BERT4Rec），按时间排序是构建训练样本的重要步骤。

---

## 18.14 本章总结

| 知识点               | 作用      | 推荐系统中的应用                |
| ----------------- | ------- | ----------------------- |
| Series            | 一维数据    | 单列数据处理                  |
| DataFrame         | 二维表格    | 用户-物品交互数据               |
| read_csv()        | 读取数据    | 加载 MovieLens、Amazon 数据集 |
| head()            | 查看前五行数据 | 检查读取结果                  |
| info()            | 查看信息    | 检查数据类型                  |
| describe()        | 统计分析    | 数据探索                    |
| groupby()         | 分组统计    | 热门商品、活跃用户分析             |
| sort_values()     | 排序      | 按时间构建行为序列               |
| dropna()          | 删除缺失值   | 数据清洗                    |
| drop_duplicates() | 删除重复值   | 去除重复交互                  |
| to_csv()          | 保存数据    | 保存处理后的数据                |
基础语法的学习在我的电脑中，路径："D:\numpy+pandas+matplotlib学习笔记"

## 19.PyTorch深度学习入门

- 【PyTorch深度学习快速入门教程（绝对通俗易懂！）【小土堆】】 [https://www.bilibili.com/video/BV1hE411t7RN/?share_source=copy_web&vd_source=66b9db97c32aa710ff8ba9a152d89b5f](https://alidocs.dingtalk.com/preview?spaceId=29181381295&dentryId=231407765214&uid=1607634054&usrAboard=false&bizType=markdown&operate=preview&previewAtta=-1&cdnDownload=1&scene=driveSpace&ext=md&fileName=%E8%87%AA%E4%B8%BB%E5%AD%A6%E4%B9%A0%E8%B5%84%E6%96%99.md&orgId=null&parentFrame=uni-preview#)

### 两大法宝函数 
- dir()函数：能让我们知道工具箱（pytorch）以及工具箱中分割区有什么东西，如查看 torch 模块下有哪些常用的神经网络层、函数等print(dir(torch.nn))
- help()函数：能让我们知道每个工具是如何使用的，工具的使用方法。如help(torch.nn)会打印出整个 nn 模块的说明，以及其中所有类的列表和简介。

**代码是以块为一个整体运行的话：那么python文件的块是所有行的代码**，python控制台是以每一行为块运行的（按shift+回车可以实现多行运行，但不方便修改错误），jupyter是以任意行为运行的。

## pytotch加载数据

### 读取数据分两类
- Dataset：提供获取数据及其label标签的方式
- Dataloader：数据加载器，把 `Dataset` 包装起来，并添加了训练模型所需的所有**批处理功能**

**P6 PyTorch加载数据初认识**
在PyTorch中读取数据主要设计两个类：Dataset和Dataloader
1. Dataset：提供一种方式去获取数据及其label
 - 如何获取每一个数据及其label
- 告诉我们总共有多少的数据
2. Dataloader：为后面的网络提供不同的数据形式
如何使用Dataset：
首先下载数据集，“蚂蚁蜜蜂数据集”下载地址：https://download.pytorch.org/tutorial/hymenoptera_data.zip
三种常见的数据组织方式：
3. 文件名是标签
4. 每个训练文件有对应的标签文件
5. 文件名是标签

Dataset类的使用主要来说就是继承+重写__getitem__方法和__add__方法

**P7 Dataset类代码实战:**

主要讲解了如何读入数据，详细内容见学习代码。

1. 第一次安装openc cv库，因为安装太慢放弃使用了，改用PIL库：
使用PIL库读取第一张图片。

输入图片路径是可以直接在路径字符串前加r将其变为原生字符串，从而规避转义字符的问题。

2. 重写Dataset类
同一个Dataset子类的实例可以用加号进行合并

**P8 TensorBoard的使用（一）：**

**TensorBoard** 是 TensorFlow 提供的可视化工具，用于在机器学习工作流中记录、分析和展示训练过程中的各种指标与数据。它可以帮助开发者跟踪 **损失（loss）**、**准确率（accuracy）**、查看模型计算图、权重分布、嵌入向量等，从而更直观地优化模型。

1. SummaryWriter类的使用：

在PyCharm中按住Ctrl键然后点击从外部引入的对象可以查看源码

2. add_scalar()方法的使用：
tag指标题，scalar_value对应y轴，global_step对应x轴
add_scalar()的使用（常用来绘制train/val loss）：先创建一个SummaryWriter的实例，如writer = SummaryWriter('logs')，然后调用其方法，writer.add_scalar(tag, scalar, step)。最后记得关闭SummaryWriter。
```python
from torch.utils.tensorboard import SummaryWriter

writer = SummaryWriter("logs")

# y=2x
for i in range(100):
    writer.add_scalar("y=2x",2*i,i)

writer.close()
```

3. TensorBoard的安装与使用：
如果没有安装TensorBoard首先需要在选择的虚拟环境中安装。

查看TensorBoard的事件文件：
首选需要cd到事件文件所在的**文件夹**目录，然后在命令行中输入：tensorboard --logdir=事件文件所在的文件夹名 --port=6007（默认打开6006端口，通过port参数设置端口可以避免与其他人冲突）
TensorBoard的页面打开后，如果事件文件发生变化，只需刷新浏览器页面即可。不同事件不要用一个tag，TensorBoard会记录上一个事件并显示出来，所以要删除原有的旧时间再运行新事件，或者新建事件文件

**P9 TensorBoard的使用（二）——add_image()的使用（常用来观察训练结果）：**
参数：
tag（字符串)：这张图片在TensorBoard界面上的**名字/标签**
img_tensor：你要显示的图片数据，支持格式torch.Tensor	（PyTorch张量，如torch.randn(3, 256, 256)）、numpy.ndarray（NumPy数组，如np.random.rand(256, 256, 3)）、字符串路径（图片文件路径，如"dog.jpg"（需要PIL库支持））
`global_step`（整数）：记录这张图片是**第几步**训练的。如果不填，所有图片都会被覆盖，TensorBoard里只能看到最后一张。
填了之后，TensorBoard会生成一个滑动条，你可以拖动看不同训练步数的图片。

准备：通过下方评论区先下载好练手数据集。

1. 利用Opencv读取图片，获得numpy型图片数据（由于下载太慢，下次再讲，这是第二次试图下载Opencv了)
2. 利用numpy.array()，对PIL图片进行转换：
可以通过np.array将img从PIL转化为numpy数组，在add_image()中通过必须通过 dataformats 告诉它你用的是哪一种数据形状。
从PIL到numpy，需要在add_image()中通过dataformat参数指定shape中每一个数字/维度表示的含义。**或者用np.ndarray的transpose方法，将img_array进行多维度的转置，将通道所在的维度放在最前面，示例代码：img_array = img_array.transpose([2, 0, 1])**
```python
from torch.utils.tensorboard import SummaryWriter
import numpy as np
from PIL import Image

writer = SummaryWriter("logs")

image_path = "data//train/ants_image/5650366_e22b7e1065.jpg"
img_PIL = Image.open(image_path)
img_array = np.array(img_PIL)
print(img_array.shape)

writer.add_image("test",img_array,3,dataformats="HWC")
 
writer.close()
```

**P10 transforms的使用（一）：**

`transforms` 就是一套**数据加工流水线**（PyTorch中**数据预处理**），把原始图片（可能是JPEG文件、PIL对象、numpy数组）转换成模型需要的**张量格式**。

在 VSCode 中，`Ctrl+Shift+O` 的作用是**在当前打开的文件中，快速导航到特定的“符号”（Symbol）**。这里的“符号”指的是代码里的**函数、类、变量、方法**等标识符。

之前用的工具都来自torch.utils，本次课开始接触torchvision

transforms主要作用是对图片进行变换

1. transforms的结构：
可以使用PyCharm界面左侧的structure按钮查看transforms的结构：由许多类定义组成的**模块**。
在 VSCode 中，`Ctrl+Shift+O` 的作用是**在当前打开的文件中，快速导航到特定的“符号”（Symbol）**。这里的“符号”指的是代码里的**函数、类、变量、方法**等标识符。
2. transforms的使用：
由选择的类定义创建一个实例并给予其输入，最后接收其输出即可。

在函数的引用括号里按Ctrl+P可以显示函数需要传入什么参数及参数类型（P代表parameter）

类中的魔术方法__call__的作用：
该方法最重要的用途就是将类/实例对象变成函数，变成可调用对象，函数相对于类/实例对象的方便之处就在于不需要实例化，随时只要传参就能使用。而__call__方法就是将类的**实例对象变成函数**，这个实例对象调用后实现的就是__call__方法

```python
from torchvision import transforms
from PIL import Image

img_path = "dataset/train/ants_image/0013035.jpg"
img = Image.open(img_path)

# 1.如何使用transforms
tensor_trans = transforms.ToTensor() # 返回ToTensor对象，ToTensor的作用是把原始图片（PIL对象、numpy数组）转换成模型需要的张量格式
tensor_img = tensor_trans(img) # 类中的魔术方法__call__将类的实例对象变成函数，这个实例对象被调用后实现的就是__call__方法
print(tensor_img)
```

**P11 transforms的使用（二）：**

1. 查看tensor数据类型的一些相关信息，可以理解为包含了神经网络理论基础的一些参数的数据类型。
2. 用opencv读取ndarray类型的数据（这是第三次安装Opencv了，终于成功了）：

小结：目前学过的3种打开图片并往SummaryWriter类传参的方式：
1. PIL.Image.open打开，np.array转换
```python
from torch.utils.tensorboard import SummaryWriter
import numpy as np
from PIL import Image

writer = SummaryWriter("logs")

image_path = "data//train/ants_image/5650366_e22b7e1065.jpg"
img_PIL = Image.open(image_path)
img_array = np.array(img_PIL)
print(img_array.shape)

writer.add_image("test",img_array,3,dataformats="HWC")
 
writer.close()
```
1. PIL.Image.open打开，transforms.ToTensor转换
```python
from torchvision import transforms

from PIL import Image

from torch.utils.tensorboard import SummaryWriter

img_path = "dataset/train/ants_image/0013035.jpg"
img = Image.open(img_path)

writer = SummaryWriter("logs")

# 1.如何使用transforms
tensor_trans = transforms.ToTensor() # 返回ToTensor对象，ToTensor的作用是把原始图片（PIL对象、numpy数组）转换成模型需要的张量格式
tensor_img = tensor_trans(img) # 类中的魔术方法__call__将类的实例对象变成函数，这个实例对象被调用后实现的就是__call__方法

writer.add_image("tensor_img",tensor_img,1)

writer.close()
```
3. opencv打开（这个打开就是ndarray类型）
import cv2
img_path = "dataset/train/ants_image/0013035.jpg"
img_cv = cv2.imread(img_path)
writer.add_image("img_cv",img_cv,1)

**P12 常见的transforms（一）：**
Python中__call__的用法：
Python类的魔法方法，可以让**实例**接收参数并被调用
1. Compose（介绍）：组合transforms中的多个类（多个工具）
2. ToTensor：
将PIL Image和numpy.ndarray类型转换为tensor类型
3. ToPILImage:
将tensor和numpy.ndarray类型转换为PIL Image类型
4. Normalize：
对图片进行归一化的变换，具体效果见代码，注意计算公
式output[channel] = (input[channel] - mean[channel]) / std[channel]。
用均值和标准差来标准化一个张量图片（tensor类型），**将数据从 `[0, 1]` 范围转换到均值为 0、标准差为 1 的分布。**
**输入**：张量（Tensor）格式的图片，值在 `[0, 1]` 之间
**输出**：标准化后的张量，值通常在 `[-2, 2]` 之间
**公式**：`output = (input - mean) / std`
**目的**：让模型训练更稳定、收敛更快

```python
from torchvision import transforms
from PIL import Image
from torch.utils.tensorboard import SummaryWriter

img_path = "dataset/train/ants_image/0013035.jpg"
img = Image.open(img_path)

writer = SummaryWriter("logs")

# 1.如何使用transforms
tensor_trans = transforms.ToTensor() # 返回ToTensor对象，ToTensor的作用是把原始图片（PIL对象、numpy数组）转换成模型需要的张量格式
tensor_img = tensor_trans(img) # 类中的魔术方法__call__将类的实例对象变成函数，这个实例对象被调用后实现的就是__call__方法

# 1.如何使用transforms
print(tensor_img[0][0][0])
trans_norm = transforms.Normalize([0.5,0.5,0.5],[0.5,0.5,0.5])
norm_img = trans_norm(tensor_img) # 类中的魔术方法__call__将类的实例对象变成函数，这个实例对象被调用后实现的就是__call__方法
print(norm_img[0][0][0])

writer.add_image("norm_img",norm_img,1)

writer.close()
```

**P13 常见的transforms（二）：**

1. Resize：
作用是改变图片的尺寸，输入是PIL Image，输出同样是PIL Image。

2. Compose（使用）：
将多个变换组合在一起，把多个数据预处理操作**串联成一条流水线**，数据会依次经过每个变换。传入的参数是一个由transfroms这个模块中类的**实例**组成的**列表**，Compose([transforms参数1，transforms参数2，……])。
3. RandomCrop：
随机裁剪的尺寸大小不能小于图片的尺寸，否则会报错。

```python
from torchvision import transforms
from PIL import Image
from torch.utils.tensorboard import SummaryWriter

img_path = "dataset/train/ants_image/0013035.jpg"
img = Image.open(img_path)
writer = SummaryWriter("logs")

# 1.ToTensor()
tensor_trans = transforms.ToTensor() # 返回ToTensor对象，ToTensor的作用是把原始图片（PIL对象、numpy数组）转换成模型需要的张量格式
tensor_img = tensor_trans(img) # 类中的魔术方法__call__将类的实例对象变成函数，这个实例对象被调用后实现的就是__call__方法
writer.add_image("tensor_img",tensor_img,1)

# 2.Normalize()
print(tensor_img[0][0][0])
trans_norm = transforms.Normalize([0.5,0.5,0.5],[0.5,0.5,0.5])
norm_img = trans_norm(tensor_img) # 类中的魔术方法__call__将类的实例对象变成函数，这个实例对象被调用后实现的就是__call__方法
print(norm_img[0][0][0])
writer.add_image("norm_img",norm_img,1)

# 3.Resize
print(img)
trans_resize = transforms.Resize((512,512)) # 强制缩放到 512×512
resize_img = trans_resize(img) # 输出还是PIL Image
print(resize_img)
resize_img = tensor_trans(resize_img) # 将PIL Image转化为tensor
print(resize_img)
writer.add_image("resize_img",resize_img,1) # 输入要求是numpy数组或tensor

# 4.Compose使用
resize_trans_2 = transforms.Resize(512) # 保持宽高比，短边缩放到 512，长边按比例缩放
compose_trans = transforms.Compose([resize_trans_2,tensor_trans]) # 先进行resize_trans，再经行tensor_trans
resize_img_2 = compose_trans(img) # 最后图片的格式就是tensor类型
writer.add_image("resize_img",resize_img_2,2)

# 5.RandomCrop随机裁剪
random_trans = transforms.RandomCrop((512,512))
compose_trans_2 = transforms.Compose([random_trans,tensor_trans])
for i in range(10):
    random_img = compose_trans_2(img)
    writer.add_image("random_img",random_img,i)

writer.close()
```
4. 总结使用方法：
- 关注输入和输出类型
- 关注官方文档
- 关注方法需要什么参数
不知道返回值类型的时候可以试错或者搜索（print，print(type())，debug）查看输入输出的类型

**P14 torchvision中的数据集使用：**

1. 往期回顾：

- 自定义数据集
- transforms中的类

**本节将讲解如何将数据集和transforms结合在一起。同时将介绍在科研或毕设中能够使用的标准数据集，包括下载->组织->查看->使用。totchvision.models可能在毕设或科研中使用到。**
2. CIFAR10数据集的下载与导入：
如果下载比较慢，可以把下载链接放到迅雷中进行下载。
导入的datasets和之前讲解的Dataset类是很相似的，实现了__getitem__()方法和__len__()方法。

3. 将CIFAR10数据集的图片转换成tensor类型：
    如果tensorboard的step不全可能是因为没加writer.close()

4. torchvision中的其他数据集：
按住Ctrl键再点击可以查看源代码，找到url链接之后可以使用迅雷下载。
```python
import torchvision
from torch.utils.tensorboard import SummaryWriter

# 将数据集中的每一张图片都转为Tensor类型
dataset_transform = torchvision.transforms.Compose([
    torchvision.transforms.ToTensor(),
])

# 加载数据集
#语法格式：torchvision.datasets.CIFAR10(root: str, train: bool = True, transform: Union[Callable, NoneType] = None, target_transform: Union[Callable, NoneType] = None, download: bool = False) → None
train_set = torchvision.datasets.CIFAR10(root="./dataset1",train=True,transform=dataset_transform,download=True)
test_set = torchvision.datasets.CIFAR10(root="./dataset1",train=False,transform=dataset_transform,download=True)

"""
print(test_set[0]) # 获取测试集第一张图片数据
print(test_set.classes) # 获取类别名称列表
img,target = test_set[0] # 由(img, target)组成
print(img) # PIL Image
print(target) # 标签，是整数，对应类别列表中的索引
print(test_set.classes[target]) # 获得对应的类名
img.show() # 展示图片
"""
 #print(test_set[0])

writer = SummaryWriter("logs_CIFAR10")

for i in range(10):
    img,target = test_set[i]
    writer.add_image("test_set",img,i)
writer.close()
```

**P15 Dataloader的使用：**

先看官网，再找例子。
1. 去PyTorch官网上查找Dataloader的文档：
使用测试集的原因是测试集样本数更少，运行起来时间会短一些（指用DataLoader遍历的时间）：windows系统下如果出现BrokenPipeError的错误，可以考虑将 num_workers设置为0

2. 采样器默认是随机采样：
3. 用TensorBoard展示图片（一次性展示多张图片注意要用add_images而不是之前用过的add_image）：

一定要等到程序运行结束了再在Terminal（终端）里使用tensorboard命令，不然会出现图片加载不全的情况！可以在程序末尾加一行语句来打印程序结束。

```python
import torchvision
from torch.utils.tensorboard import SummaryWriter
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter

# 准备测试集
#语法格式：torchvision.datasets.CIFAR10(root: str, train: bool = True, transform: Union[Callable, NoneType] = None, target_transform: Union[Callable, NoneType] = None, download: bool = False) → None
test_data = torchvision.datasets.CIFAR10(root="./dataset1",train=False,transform=torchvision.transforms.ToTensor())
test_loader = DataLoader(dataset=test_data,batch_size=64,shuffle=True,num_workers=0,drop_last=True) # shuffle=True表示打乱,drop_last=True表示最后批次数量不足则会舍弃该批次的图片

# 测试测试集中第一张图片及标签
img,target = test_data[0]
print(img.shape) # 输出torch.Size([3, 32, 32])，表示有RGB三通道所以是彩色，尺寸是32×32
print(target)

writer = SummaryWriter("logs_dataloader")

for epoch in range(2):
    step = 0
    for data in test_loader:
        imgs,target = data
        # print(imgs.shape)
        # print(target)
        writer.add_images("Epoch:{}".format(epoch),imgs,step) # 写入多张图片是add_images而不是add_image
        step+=1

writer.close()

"""
for data in test_loader:
    imgs,target = data
    print(imgs.shape)
    print(target)
如果batch_size=4则
输出多组
torch.Size([4, 3, 32, 32]) # 取了4张图片,有三个通道,尺寸是32×32,四维数据[batch, channels, height, width]
tensor([0, 6, 5, 4]) # 将四张图片的标签打包,第一张图片的标签是0,第二张是6以此类推
设置了shuffle=True,所以每次都是随机取四张图片（随机采样）
"""
```
**P16 神经网路的基本骨架——nn.Module的使用：**

神经网路的基本骨架主要在torch.nn模块中，自定义神经网络通常就是继承 `nn.Module`，然后写好 `__init__()` 和 `forward()`。主要学习Containers。
1. nn=neural network
2. Containers中的Module模块
3. 代码实战
PyCharm的code栏下的generate功能可以辅助实现代码重写。

```python
import torch.nn as nn
import torch.nn.functional as F

class Model(nn.Module):
    def __init__(self):
        super(Model, self).__init__()
        self.conv1 = nn.Conv2d(1, 20, 5)
        self.conv2 = nn.Conv2d(20, 20, 5)

    def forward(self, x): # 前向传播
        x = F.relu(self.conv1(x))
        return F.relu(self.conv2(x))
```
通过前向传播可以看出这个神经网络的结构：
输入→卷积→非线性激活→卷积→非线性激活→输出
自定义神经网络要继承 `nn.Module`，然后重写 `__init__()` 和 `forward()`：
```python
import torch
from torch import nn

class Tudui(nn.Module):
    def __init__(self):
        super().__init__()

    def forward(self,input): # forward()就是Module类中的call方法
        output = input+1
        return output

tudui = Tudui()
x = torch.tensor(1.0)
output = tudui(x)
print(output)
```
**P17 土堆说卷积（可选看）：**

本节将讲解神经网络中一些基本神经结构的使用。
1.卷积层（Convolution Layers）讲解：
nn.Conv1d表示1维，nn.Conv2d表示2维
torch.nn是对torch.nn.functional的封装，比如车是对各个零部件的封装。
**torch.nn.functional.conv2d(input, weight, bias=None, stride=1, padding=0, dilation=1, groups=1) → Tensor参数速查表**

| 参数           | 形状 / 类型                                                                                   | 默认值    | 含义                          |
| ------------ | ----------------------------------------------------------------------------------------- | ------ | --------------------------- |
| **input**    | `(minibatch批次大小（一次输入几张图), in_channels输入通道数（彩色图=3，灰度图=1）, iH输入高度（图片像素行数）, iW输入宽度（图片像素列数）)` | 必填     | 输入数据：批次、通道数、高度、宽度           |
| **weight**   | `(out_channels输出通道数（即滤波器个数), in_channels/groups每个卷积核实际处理的输入通道数, kH卷积核高度, kW卷积核宽度)`        | 必填     | 卷积核：输出通道数、每核输入通道数、核高、核宽     |
| **bias**     | `(out_channels,)`                                                                         | `None` | 每个输出通道的偏置                   |
| **stride**   | `int` 或 `(sH, sW)`                                                                        | `1`    | 卷积核滑动步长（高, 宽）               |
| **padding**  | `int` 或 `(padH, padW)`                                                                    | `0`    | 输入四周(上下左右)补零，代表补零数量（高, 宽）   |
| **dilation** | `int` 或 `(dH, dW)`                                                                        | `1`    | 核元素间隔（1=标准卷积）               |
| **groups**   | `int`                                                                                     | `1`    | 通道分组数（`in_channels` 必须能被整除） |

2.举例讲解卷积操

3.代码实战：

本节主要讲了卷积运算和一些基本参数。
```python
import torch
import torch.nn.functional as F

input = torch.tensor([[1,2,0,3,1],
                      [0,1,2,3,1],
                      [1,2,1,0,0],
                      [5,2,3,1,1],
                      [2,1,0,1,1]])

kernel = torch.tensor([[1,2,1],
                       [0,1,0],
                       [2,1,0]])

print(input.shape)
print(kernel.shape)

input = torch.reshape(input,(1,1,5,5))
kernel = torch.reshape(kernel,(1,1,3,3))
  
print(input.shape)
print(kernel.shape)

# torch.nn.functional.conv2d(input, kernel, bias=None, stride=1, padding=0, dilation=1, groups=1)

output = F.conv2d(input,kernel,stride=1)
print(output)

output2 = F.conv2d(input,kernel,stride=2)
print(output2)

output3 = F.conv2d(input,kernel,stride=1,padding=1)
print(output3)
```


**torch.nn.Conv2d(in_channels, out_channels, kernel_size, stride=1, padding=0, dilation=1, groups=1, bias=True, padding_mode='zeros')参数总览**

| 参数               | 类型              | 默认值       | 一句话含义                                       |
| ---------------- | --------------- | --------- | ------------------------------------------- |
| **in_channels**  | `int`           | 必填        | 输入图像通道数（如 RGB=3）                            |
| **out_channels** | `int`           | 必填        | 卷积核个数（输出通道数）                                |
| **kernel_size**  | `int` / `tuple` | 必填        | 卷积核尺寸（高, 宽）                                 |
| **stride**       | `int` / `tuple` | `1`       | 滑动步长                                        |
| **padding**      | `int` / `tuple` | `0`       | 四周补零数量                                      |
| **padding_mode** | `string`        | `'zeros'` | 填充方式：zeros / reflect / replicate / circular |
| **dilation**     | `int` / `tuple` | `1`       | 核元素间隔（1=标准），设置为2时才真正空洞卷积                    |
| **groups**       | `int`           | `1`       | 通道分组数（减少参数量）                                |
| **bias**         | `bool`          | `True`    | 是否添加可学习偏置                                   |
```python
import torch
import torchvision
from torch.utils.data import DataLoader
from torch import nn
from torch.nn import Conv2d
from torch.utils.tensorboard import SummaryWriter

dataset = torchvision.datasets.CIFAR10("dataset1", train=False,transform=torchvision.transforms.ToTensor(),download=True)

dataloader = DataLoader(dataset,batch_size=64)

class Tudui(nn.Module):
    def __init__(self):
        super().__init__()
        self.conv1 = Conv2d(3,6,3,stride=1,padding=0) # 输出的通道个数就是卷积核的个数
    def forward(self,x): # forward()就是Module类中的call方法
        x= self.conv1(x)
        return x
        
tudui = Tudui()

writer = SummaryWriter("nn_Conv2d_logs")
step = 0
for data in dataloader:
    imgs, targets = data
    output = tudui(imgs)
    #print(imgs.shape)
    #print(output.shape)
    # torch.Size([64, 3, 32, 32])
    writer.add_images("input",imgs,step)
    # torch.Size([64, 6, 30, 30]) ->[xxx,3,30,30]
    output = torch.reshape(output,(-1,3,30,30)) # 将六个通道按照三个通道平铺展开, 一迭代64×6，按照3通道展开则每次迭代64×6/3=128，一次迭代的数量写-1会根据后面的值计算得到
    writer.add_images("output",output,step)
    step+=1
writer.close()
```

**P19 神经网络——最大池化的使用：对特征图降维**
1. Pooling Layers讲解：
最大池化有时也被称为下采样，对应的有上采样。注意ceil_mode参数的使用
**MaxPool2d 参数详解**

| 参数                 | 类型              | 默认值           | 含义                                                                            |
| ------------------ | --------------- | ------------- | ----------------------------------------------------------------------------- |
| **kernel_size**    | `int` / `tuple` | 必填            | 池化窗口尺寸（高, 宽）                                                                  |
| **stride**         | `int` / `tuple` | `kernel_size` | 窗口滑动步长                                                                        |
| **padding**        | `int` / `tuple` | `0`           | 输入四周补零数量                                                                      |
| **dilation**       | `int` / `tuple` | `1`           | 窗口内元素间隔，如设置则可以叫做空洞卷积或膨胀卷积                                                     |
| **return_indices** | `bool`          | `False`       | 是否返回最大值索引（用于上池化）                                                              |
| **ceil_mode**      | `bool`          | `False`       | 输出尺寸计算方式：True=ceil（向上取整），向上取整时，若池化窗口覆盖不全则按已经覆盖的部分池化。False=floor（向下取整），则不全则不池化 |
Shape:
- Input: (N,C,Hin,Win)
- Output: (N,C,Hout,Wout)
`N`： 批次大小（batch size） 
`C`：通道数（channels） 
`H_in` / `W_in`： 输入的高度 / 宽度 
`H_out` / `W_out`：输出的高度 / 宽度 
1. 代码实战：
最大池化无法在长整型的数据上执行。生成tensor时可以使用dtype参数改变其数据类型，比如从长整型变为浮点型。
最大池化的作用在于保留输入数据的特征并减小数据的规模（降维）。

```python
import torch
from torch import nn
from torch.nn import MaxPool2d
import torchvision
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter

dataset = torchvision.datasets.CIFAR10("dataset1",train=False,transform=torchvision.transforms.ToTensor(),download=True)

dataloader = DataLoader(dataset,batch_size=64)
"""
input = torch.tensor([[1,2,0,3,1],
                      [0,1,2,3,1],
                      [1,2,1,0,0],
                      [5,2,3,1,1],
                      [2,1,0,1,1]])
input = torch.reshape(input,(-1,1,5,5))
print(input.shape)
"""
class Tudui(nn.Module):
    def __init__(self):
        super().__init__()
        self.maxpool = MaxPool2d(kernel_size=3,ceil_mode=False) # 创建MaxPool2d类的对象
  
    def forward(self,input): # forward()就是Module类中的call方法
        output = self.maxpool(input) # MaxPool2d类的对象有call方法会让实例能够像函数那样被调用
        return output
  
tudui = Tudui()
#output = tudui(input)
#print(output)
  
writer = SummaryWriter("maxpool_logs")
step=0
for data in dataloader:
    imgs, target = data
    writer.add_images("input",imgs,step)
    output = tudui(imgs)
    writer.add_images("output",output,step)
    step+=1

writer.close()
```
**P20 神经网络——非线性激活：**
几种常见的非线性激活：
1. ReLU(Rectified Linear Unit)线性整流函数：输入值大于0的部分按照原数值输出，对于输入值小于0的部分则输出0。
`torch.nn.ReLU(_inplace=False_)`
**inplace**：`bool`类型，默认值`False`，意思是是否在原地执行操作（就地修改输入张量）
- **Input（输入）**：`(N, *)`
  - `N`：批次大小（batch size）
  - `*`：任意数量的额外维度（如通道数、高度、宽度等）
- **Output（输出）**：`(N, *)`
  - 与输入形状**完全相同**
```python
import torch
from torch import nn
from torch.nn import ReLU

input = torch.tensor([[1,-0.5],
                      [-1,3]])

input = torch.reshape(input,(-1,1,2,2))
print(input.shape)

class Tudui(nn.Module):
    def __init__(self):
        super().__init__()
        self.relu = ReLU()
        
    def forward(self,input):
        output = self.relu(input)
        return output

tudui = Tudui()
output = tudui(input)
print(output)
```

1. Sigmoid：Sigmoid激活函数也被称为逻辑函数或S型函数，它将输入值映射到0和1之间，输出值表示当前输入属于某一个类别的概率大小。
`torch.nn.Sigmoid`
- **Input（输入）**：`(N, *)`
  - `N`：批次大小（batch size）
  - `*`：任意数量的额外维度（如通道数、高度、宽度等）
- **Output（输出）**：`(N, *)`
  - 与输入形状**完全相同**
```python
import torch
from torch import nn
from torch.nn import ReLU
import torchvision
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter
from torch.nn import Sigmoid

dataset = torchvision.datasets.CIFAR10("dataset1",train=False,transform=torchvision.transforms.ToTensor(),download=True)
dataloader = DataLoader(dataset,batch_size=64)

class Tudui(nn.Module):
    def __init__(self):
        super().__init__()
        self.sigmoid = Sigmoid()

    def forward(self,input):
        output = self.sigmoid(input)
        return output

tudui = Tudui()

writer = SummaryWriter("sigmoid_logs")
step=0
for data in dataloader:
    imgs,target = data
    writer.add_images("input",imgs,step)
    output = tudui(imgs)
    writer.add_images("output",output,step)
    step+=1

writer.close()
```
非线性变化的主要目的在于给网络引入非线性的特征。非线性特征越多，越能训练出符合各种曲线或特征的模型，从而提高模型的泛化能力。

**P21 神经网络——线性层及其他层介绍：**
1. 简要介绍nn模块里的各种层：
- Normalization Layers正则化层：
    正则化可以加快神经网络的训练速度，用的比较少，不作介绍，自己看文档
2. Recurrent Layers：
    一般用于文字识别，自己看文档。
3. Transformer Layers：
4. Linear Layers：
`torch.nn.Linear(_in_features_, _out_features_, _bias=True_)

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| **in_features** | `int` | 必填 | 每个输入样本的特征数量 |
| **out_features** | `int` | 必填 | 每个输出样本的特征数量 |
| **bias** | `bool` | `True` | 是否添加可学习的偏置项 |

**Input: (N,∗,Hin)**
- `N`：批次大小（batch size）
- `*`：任意数量的额外维度（如时间步、高度、宽度等）
- `H_in：`in_features`（输入特征数）
**Output: (N,∗,Hout)**
- `N`：批次大小（保持不变）
- `*`：额外维度与输入完全相同
- `Hout`：`out_features`（输出特征数）
Linear Layers的weight和bias的初始化是正态分布，可参考官方文档。**torch.flatten()可以展平数据**

5. Dropout Layers：
    主要作用是防止过拟合。
6. Saprse Layers：
    用于自然语言处理。
7. Distance Functions：
8. Loss Functions：
torchvision.models中有很多现有的网络结构
[torchvision.models — Torchvision master documentation](https://docs.pytorch.org/vision/0.9/models.html)

```python
import torch
from torch import nn
import torchvision
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter
from torch.nn import Linear


dataset = torchvision.datasets.CIFAR10("dataset1",train=False,transform=torchvision.transforms.ToTensor(),download=True)
dataloader = DataLoader(dataset,batch_size=64)

  

class Tudui(nn.Module):
    def __init__(self, ):
        super().__init__()
        self.linear = Linear(196608,10) # 输入196608个特征，输出10个特征

    def forward(self,input):
        output = self.linear(input)
        return output

tudui = Tudui()

for data in dataloader:
    imgs, target = data
    print(imgs.shape)
    output = torch.flatten(imgs) # 将张量展平（flatten）
    # 等效于output = torch.reshape(imgs,(1,1,1,-1)) # 展平成一行
    print(output.shape)
    output = tudui(output)
    print(output.shape)
```
**P22 神经网络——搭建小实战和Sequential的使用：**

1.引子：
1. Sequential的使用：将网络结构放入其中即可，然后依次执行，可以简化代码。
2. 找了一个对CIFAR10进行分类的模型，本节课将实现这个简单的模型。

2.代码实战：
nn.Flatten()和torch.flatten()有相同展平的效果。
```python
import torch
from torch import nn
from torch.nn import Conv2d
from torch.nn import MaxPool2d
from torch.nn import Flatten
from torch.nn import Linear

class Tudui(nn.Module):
    def __init__(self):
        super().__init__()
        self.conv1 = Conv2d(3,32,5,padding=2)
        self.maxpool1 = MaxPool2d(2)
        self.conv2 = Conv2d(32,32,5,padding=2) # 其他参数没写就是按照默认值
        self.maxpool2 = MaxPool2d(2)
        self.conv3 = Conv2d(32,64,5,padding=2)
        self.maxpool3 = MaxPool2d(2)
        self.flatten = Flatten() # 一共64×4×4=1024
        self.linear1 = Linear(1024,64)
        self.linear2 = Linear(64,10) # 为什么是10，因为最后是要分成10类，取其中概率最大对应的类别作为网络预测的类别
        
    def forward(self,x):
        x = self.conv1(x)
        x = self.maxpool1(x)
        x = self.conv2(x)
        x = self.maxpool2(x)
        x = self.conv3(x)
        x = self.maxpool3(x)
        x = self.flatten(x) # 如果不知道线性层输入的特征数量是多少，可以先执行展平之后的结果，通过shape查看输出结果的形状得到二维数据[batch, features]，第二维就是特征维度即特征数量，这就作为线性层的输入特征数量
        x = self.linear1(x)
        x = self.linear2(x)
        return x

tudui = Tudui()
print(tudui)

input = torch.ones((64,3,32,32))
output = tudui(input)
print(output.shape)
```

3.Sequential讲解：
使用Sequential可以很大程度地简化代码。
`torch.nn.Sequential`(_*args_)
`nn.Sequential` 是一个**顺序容器**，用于按顺序包装多个网络层，数据会**依次**通过每一层。

以CIFAR 10模型为例，构建CIFAR 10模型结构
![[Pasted image 20260826170201.png]]
```python
import torch
from torch import nn
from torch.nn import Conv2d
from torch.nn import MaxPool2d
from torch.nn import Flatten
from torch.nn import Linear
from torch.nn import Sequential

class Tudui(nn.Module):
    def __init__(self):
        super().__init__()
        self.model1 =Sequential(
            Conv2d(3,32,5,padding=2) # 输入和输出的通道数和尺寸，可通过卷积公式反向推出步长stride和填充值padding
            MaxPool2d(2),
            Conv2d(32,32,5,padding=2),
            MaxPool2d(2),
            Conv2d(32,64,5,padding=2),
            MaxPool2d(2),
            Flatten(), # 一共64×4×4=1024
            Linear(1024,64),
            Linear(64,10)
        )

    def forward(self,x):
        x = self.model1(x)
        return x

tudui = Tudui()
print(tudui)

input = torch.ones((64,3,32,32))
output = tudui(input)
print(output.shape)
```

4.利用TensorBoard进行数据可视化：
使用SummaryWriter的add_graph()方法进行数据可视化。
writer.add_graph(
    model,          # 要可视化的模型
    input_to_model, # 输入数据（用于前向传播）
    verbose=False   # 是否打印详细信息（可选）
)
可以看到模型的结构
**详细内容见：nn_seq.py**

**P23 损失函数与反向传播：**

1. 损失函数的作用：
- 计算实际输出和目标之间的差距
- 为我们更新输出提供一定的依据（反向传播）

2. 介绍几种官方文档中的损失函数：
损失函数只能处理float类型的张量。

3. L1Loss (MAE)：
    
    ﻿
    
    损失函数与反向传播 P23 - 04:25
    X = 1,2,3
    Y = 1,2,5
    L1Loss = (|1-1|+|1-1|+|3-5|)/3=(0+0+2)/3=0.6
    
    torch.nn.L1Loss(_size_average=None_, _reduce=None_, _reduction='mean'_)
    
| 参数 | 取值 | 含义 | 输出形状 | 状态 |
|:---|:---|:---|:---|:---:|
| **`reduction`** | `'mean'` | 求和后除以元素总数（求平均） | 标量 | ✅ 推荐 |
| **`reduction`** | `'sum'` | 直接求和（不除以任何数） | 标量 | ✅ 推荐 |
| **`reduction`** | `'none'` | 不归约，逐元素返回 | `(N, *)` | ✅ 推荐 |
| `size_average` | `True` | 求平均 | 标量 | ⚠️ 已弃用 |
| `size_average` | `False` | 求和 | 标量 | ⚠️ 已弃用 |
| `reduce` | `True` | 应用归约 | 标量 | ⚠️ 已弃用 |
| `reduce` | `False` | 不归约 | `(N, *)` | ⚠️ 已弃用 |

| 项目                          | 形状                         |
| :-------------------------- | :------------------------- |
| **输入 (Input)**              | `(N, *)`,N是指batch_size批次大小 |
| **目标 (Target)**             | `(N, *)`                   |
| **输出 (`reduction='mean'`)** | 标量                         |
| **输出 (`reduction='sum'`)**  | 标量                         |
| **输出 (`reduction='none'`)** | `(N, *)`                   |
```python
import torch
from torch.nn import L1Loss

inputs = torch.Tensor([1,2,3])
targets = torch.Tensor([1,2,5])

inputs = torch.reshape(inputs,(1,1,1,3))
targets = torch.reshape(targets,(1,1,1,3))

loss = L1Loss(reduction='sum')
result = loss(inputs,targets)
print(result)
```
3. MSELoss：
**均方误差损失函数**，用于衡量输入 `x` 和目标 `y` 之间每个元素的**平方 L2 范数**（即误差平方的平均值或总和）,loss=(xi​−yi​)^2
`torch.nn.MSELoss`(_size_average=None_, _reduce=None_, _reduction='mean'_)
输入 (Input)  : (N, *)   ← N = 批次大小，* *= 任意额外维度
目标 (Target) : (N, *)   ← 与输入形状相同
    ﻿
loss_mse = MSELoss()
result_mse = loss_mse(inputs,targets)

4. CrossEntropyLoss：
**对模型的原始输出自动计算 softmax + 交叉熵损失**
`torch.nn.CrossEntropyLoss`(_weight=None_, _size_average=None_, _ignore_index=-100_, _reduce=None_, _reduction='mean'_)
output：[0.1,0.2,0.3] 对应每一类的概率，下标从0开始，对应公式中的x
target：1 公式中的class

Loss(x,class)=-0.2+log(exp(0.1)+exp(0.2)+exp(0.3))
log主要是默认ln

| 项目                              | 形状      | 说明                                 |
| :------------------------------ | :------ | :--------------------------------- |
| **输入 x**                        | `(N,C)` | N = 批次大小，C = 类别数                   |
| **目标 target**                   | `(N)`   | 每个元素是类别索引，范围 `0 ≤ target[i] ≤ C-1` |
| **输出 (reduction='mean'/'sum')** | 标量      | 单个数值                               |
| **输出 (reduction='none')**       | `(N,)`  | 每个样本一个损失值                          |
x = torch.tensor([0.1,0.2,0.3])
y = torch.tensor([1])
x = torch.reshape(x,(1,3))
loss_CE = CrossEntropyLoss()
result_CE = loss_CE(x,y)
print(result_CE)

5. 在神经网络中使用Loss Function：
```python
from torch import nn
from torch.nn import Conv2d
from torch.nn import MaxPool2d
from torch.nn import Flatten
from torch.nn import Linear
from torch.nn import Sequential
import torchvision
from torch.utils.data import DataLoader

dataset = torchvision.datasets.CIFAR10("dataset1", train=False,transform=torchvision.transforms.ToTensor(),download=True)
dataloader = DataLoader(dataset,batch_size=64)

class Tudui(nn.Module):
    def __init__(self):
        super().__init__()
        self.model1 =Sequential(
            Conv2d(3,32,5,padding=2),
            MaxPool2d(2),
            Conv2d(32,32,5,padding=2),
            MaxPool2d(2),
            Conv2d(32,64,5,padding=2),
            MaxPool2d(2),
            Flatten(), # 一共64×4×4=1024
            Linear(1024,64),
            Linear(64,10)
        )

    def forward(self,x):
        x = self.model1(x)
        return x

tudui = Tudui()
loss = nn.CrossEntropyLoss()
for data in dataloader:
    imgs, targets = data
    outputs = tudui(imgs)
    result_loss = loss(outputs,targets)
    print(result_loss)
```
﻿
**详细内容见：nn_loss.py和nn_loss_network.py**

**P24 优化器（一）：**

优化器集中在torch.optim中。
```python
tudui = Tudui()
loss = nn.CrossEntropyLoss()
optim = torch.optim.SGD(tudui.parameters(),lr=0.01)
for epoch in range(20):
    running_loss = 0
    for data in dataloader:
        imgs, targets = data
        outputs = tudui(imgs)
        result_loss = loss(outputs,targets)
        optim.zero_grad() # 每次反向传播之前将参数清
        result_loss.backward()
        optim.step() # 通过优化器对参数进行调优
        running_loss = running_loss + result_loss
    print(running_loss) # 输出每一轮训练的损失
```
总结：

1. 主要讲了优化器的基本使用，如果要知道各个优化器的详细用法需要对其有一定了解
2. 注意要多训练几轮

**详细内容见：nn_optim.py**

**P25 现有网络模型的使用及修改：**

1. 讲解VGG16网络模型：
﻿
ImageNet数据集太大了，仅训练集就有147.9g，还是不下载了。

2. 改变现有网络的参数：

vgg16的导入以及和视频里讲的不一样了，并且我在导入预训练权重的时候遇到了url error的问题，不知道是不是因为被墙了。
```python
import torchvision
from torch import nn

vgg16_false = torchvision.models.vgg16(pretrained=False)
vgg16_true = torchvision.models.vgg16(pretrained=True)
print(vgg16_true)

"""
 VGG16 结构：
VGG(
  (features): Sequential(...)      # 特征提取部分（卷积层）         <-输入层（底层）
  (classifier): Sequential(        # 分类器部分（全连接层）
    (0): Linear(25088, 4096)       # 第1层：输入25088 → 4096
    (1): ReLU(inplace=True)
    (2): Dropout(p=0.5)
    (3): Linear(4096, 4096)        # 第2层：4096 → 4096
    (4): ReLU(inplace=True)
    (5): Dropout(p=0.5)
    (6): Linear(4096, 1000)        # 第3层：4096 → 1000（原始输出） <-输出层（顶层）
  )
)
 """
dataset = torchvision.datasets.CIFAR10("dataset1",train=True,transform=torchvision.transforms.ToTensor(),download=True)

vgg16_true.add_module("add_mosule1",nn.Linear(1000,10)) #  在模型顶层添加一个模块
"""
VGG(
  (features): Sequential(...)   
  (classifier): Sequential(        
    (0): Linear(25088, 4096)       
    (1): ReLU(inplace=True)
    (2): Dropout(p=0.5)
    (3): Linear(4096, 4096)        
    (4): ReLU(inplace=True)
    (5): Dropout(p=0.5)
    (6): Linear(4096, 1000)       
  )
  (add_mosule1):Linear(1000,10)
)
"""
vgg16_true.classifier.add_module("add_mosule2",nn.Linear(1000,10)) # 在某个模块末尾添加一层（如线性层）
print(vgg16_true)
"""
VGG(
  (features): Sequential(...)   
  (classifier): Sequential(        
    (0): Linear(25088, 4096)       
    (1): ReLU(inplace=True)
    (2): Dropout(p=0.5)
    (3): Linear(4096, 4096)        
    (4): ReLU(inplace=True)
    (5): Dropout(p=0.5)
    (6): Linear(4096, 1000) 
    (add_mosule2):Linear(1000,10)      
  )
)
"""
vgg16_false.classifier[6] = nn.Linear(4096,10) # 直接替换某个模块的最某一层（如线性层）
print(vgg16_false)
"""
VGG(
  (features): Sequential(...)   
  (classifier): Sequential(        
    (0): Linear(25088, 4096)       
    (1): ReLU(inplace=True)
    (2): Dropout(p=0.5)
    (3): Linear(4096, 4096)        
    (4): ReLU(inplace=True)
    (5): Dropout(p=0.5)
    (6): Linear(4096, 10)    
  )
)
"""
```
**详细内容见：torchvision_models.py**

**P26 网络模型的保存与读取：**

1. 模型的保存与读取方法1：

torch.save(实例, 保存的文件名称), torch.load(实例, 保存文件名称)。
```python
# 保存
torch.save(model, "model_method1.pth")
# 加载
model = torch.load("model_method1.pth")
```
方法1保存的是：模型结构+模型参数

2. 模型的保存与读取方法2：
﻿
torch.save(实例.state_dict(), 保存文件名称), 先创建模型实例再加载模型：模型实例.load_state_dict(torch.load(保存的文件名))。
```python
# 保存方式2
torch.save(vgg16.state_dict(), "vgg16_method2.pth")
# 保存方式2对应的加载模型方式（需要先定义模型）
vgg16 = torchvision.models.vgg16(pretrained=False)
vgg16.load_state_dict(torch.load("vgg16_method2.pth"))
```

方法2保存的是：模型参数（官方推荐）保存成字典格式，加载时需要通过。

3. 方法1的陷阱：

用方法1的时候一定要保证加载模型的文件里有定义该模型的类！不然会报错，或者通过import导入该模型的类。

**详细内容见：model_save.py**
**model_load.py**

**P27 完整的模型训练套路（一）：**

完成CIFAR10的分类问题
1.准备数据集:

用len去查看数据集的长度。当我们要重写Dataset类的时候，关键需要重写Dataset类的__len__()方法和__getitem__()方法。

2.利用DataLoader来加载数据集：

3.搭建神经网络：

将搭建的网络模型放入单独的一个.py文件中，并进行验证。

4.创建网络模型：

按住Ctril然后点击类名可以查看源代码。

5.创建损失函数：

6.设置优化器：

推荐使用科学计数法表示学习率。

7.设置训练网络的一些参数：

**a = torch.tensor(5)
print(a)        # tensor(5)
print(a.shape)  # torch.Size([]) - 空形状，即标量
print(a.item()) # 5 - 获取Python数值**

|形状|维度|说明|示例|
|---|---|---|---|
|`torch.Size([])`|0维|标量|`tensor(5)`|
|`torch.Size([2])`|**1维**|向量，2个元素|`tensor([1, 2])`|
|`torch.Size([2, 3])`|2维|矩阵，2行3列|`tensor([[1,2,3],[4,5,6]])`|
|`torch.Size([2, 3, 4])`|3维|3维张量|批次×通道×高度等|

用with torch.no_grad():环境取消梯度。
用tensorboard显示loss的图像：
保存训练模型/参数：
利用torch.argmax函数来算出每次预测中概率最大的位置，计算准确率：
```python
import torch 

# 创建一个 2x2 的张量（2行2列）
# 第0行: [0.1, 0.2]  第1行: [0.3, 0.4]
outputs = torch.tensor([[0.1, 0.2],
    [0.3, 0.4]])

# .argmax(1) 表示沿着第1个维度（列方向）找最大值的索引
# 第0行: [0.1, 0.2] → 最大值是 0.2，索引为 1
# 第1行: [0.3, 0.4] → 最大值是 0.4，索引为 1
# 所以输出为 tensor([1, 1])
print(outputs.argmax(1))

# 将预测结果（每个样本预测的类别索引）保存到 preds 变量
# preds = tensor([1, 1])
preds = outputs.argmax(1)

# targets 是真实标签（ground truth）
# 第一个样本的真实类别是 0，第二个样本的真实类别是 1
targets = torch.tensor([0, 1])

# 比较预测值和真实值是否相等
# preds == targets → tensor([False, True])
# .sum() 计算 True 的个数 → tensor(1)
# 表示有 1 个样本预测正确（第二个样本正确）
print((preds == targets).sum())
```
**总结：准备数据集 -> dataloader加载数据集 -> 搭建网络模型 -> 创建网络模型实例 -> 定义损失函数 -> 定义优化器 -> 设置网络训练的参数 -> 开始训练 -> 验证模型 -> 最后保存模型且可以将训练结果展示**
```python
import torchvision  
from torch.utils.data import DataLoader  
from model import *  
import torch  
from torch.utils.tensorboard import SummaryWriter  
  
# 准备数据集  
train_data = torchvision.datasets.CIFAR10("dataset1",train=True,transform=torchvision.transforms.ToTensor(),download=True)  
test_data = torchvision.datasets.CIFAR10("dataset1",train=False,transform=torchvision.transforms.ToTensor(),download=True)  
  
# 查看数据集的长度 lengthtrain_data_size = len(train_data)  
test_data_size = len(test_data)  
print("训练集的长度为：{}".format(train_data_size))  
print("测试集的长度为：{}".format(test_data_size))  
  
# 利用DataLosder加载数据集  
train_dataloader = DataLoader(train_data,batch_size=64)  
test_dataloader = DataLoader(test_data,batch_size=64)  
  
# 搭建神经网络  
tudui = Tudui()  
  
# 定义损失函数  
loss_fn = torch.nn.CrossEntropyLoss()  
  
# 定义优化器  
# 1e-2=1×(10)^(-2)=1/100=0.01  
learning_rate = 1e-2  
optimizer = torch.optim.SGD(tudui.parameters(), lr=learning_rate)  
  
# 设置训练参数  
# 训练次数  
total_train_step = 0  
# 测试次数  
total_test_step = 0  
# 训练轮数  
epoch = 10  
# 整体正确的个数  
total_accuracy = 0  
  
# 设置tensorboard画布  
writer = SummaryWriter('log_train')  
  
for epoch in range(epoch):  
    print("------第{}轮训练开始------".format(epoch+1))  
    # 训练步骤开始  
    for data in train_dataloader:  
        imgs, targets = data  
        outputs = tudui(imgs)  
        loss = loss_fn(outputs, targets)  
        # 优化器优化模型  
        optimizer.zero_grad()  
        loss.backward()  
        optimizer.step()  
        total_train_step += 1  
        if total_train_step % 100 == 0:  
            print("训练次数：{}，Loss：{}".format(total_train_step,loss.item()))  
            writer.add_scalar('loss',loss.item(),total_train_step)  
    # 测试步骤开始，禁用梯度计算的上下文管理器，主要用于推理/测试阶段  
    total_test_loss = 0  
    with torch.no_grad():  
        for data in test_dataloader:  
            imgs, targets = data  
            outputs = tudui(imgs)  
            loss = loss_fn(outputs, targets)  
            total_test_loss =total_test_loss+loss # 将每次测试的损失加到整体测试的损失上  
  
            # 计算每一批次的正确个数  
            accuracy = (outputs.argmax(1) == targets).sum()  
            total_accuracy = total_accuracy + accuracy  
  
    print("整体测试集上的Loss:{}".format(total_test_loss))  
    print("整体测试集上的正确率：{}".format(total_accuracy/test_data_size))  
    writer.add_scalar('test_loss',total_test_loss,epoch)  
    writer.add_scalar('test_accuracy',total_accuracy,epoch)  
    total_test_step+=1  
  
    torch.save(tudui,'tudui{}.pth'.format(epoch))  
  
writer.close()
```

**详细内容见：train.py**

在官网的torch.nn.Module小节中可以查看train(mode)和eval(mode)。
.train()和.eval()只对特殊的层起作用，如Dropout和BatchNorm层，但是最好还是加上。
即在训练开始前加上”模型实例.train()“，在测试开始前加上“模型实例.eval()”。

**P30 利用GUP训练（一）：**
本节介绍两种实现代码在GPU上训练的方式。
1.方法1：
找到：
1. 网络模型
if torch.cuda.is_available():  
    tudui = tudui.cuda()
2. 数据（输入、标注）
if torch.cuda.is_available():  
    imgs, targets = imgs.cuda(), targets.cuda()
3. 损失函数
if torch.cuda.is_available():  
    loss_fn = loss_fn.cuda()
这三样，然后调用其.cuda()方法，最后返回即可。不过使用这种方法很麻烦。

2.使用Google Colab（前提是能访问Google）提供免费的GPU：

3.可以尝试使用kaggle提供的虚拟机。

**详细内容见：train_gpu1.py**

**P31 利用GUP训练（二）：**
1.代码实战：

定义训练的设备:  
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")

加上：
tudui = tudui.to(device)
loss_fn = loss_fn.to(device)
imgs, targets = imgs.to(device), targets.to(device)

- 调用.to()方法即可。
- 网络模型和损失函数是不需要重新赋值的，只有数据需要重新赋值。
**详细内容见：train_gpu2.py**

**P32 完整的模型验证（测试，demo）套路：**

利用已经训练好的模型，然后给它提供输入

1.png格式的图片是4通道，jpg格式的图片是3通道，可以用PIL.Image.convert('RGB')来转换（不同截图软件保留的通道数也不一样）。

2.小细节：

将model设置到eval mode
with torch.no_grad()可以节约内存，提高性能。

3.将在gpu上训练的模型导入到在cup上运行的程序时要添加：
map_location=torch.device('cpu')关键字参数。
**详细内容见：test.py**

squeeze压缩了维度值为1的不是1维度，所以batch_x变成了（64，28，28）可以理解是64张图像在一个画布上，所以后面显示时是batch_x[ii,:,:]这样一个一个遍历
3.这俩参数一比应当就能算出截止某次训练时的准确率了,所以并不是脱裤子放屁
2.train_num是计算到目前为止一共处理了多少样本
1.train_corrects这个变量是计算每个批次当中正确预测的数量的