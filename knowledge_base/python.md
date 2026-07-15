# 1. Python 输入输出

## 输入

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

Python 使用 `print()` 输出内容。

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

Python 不需要声明变量类型。

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

---

# 3. if 条件判断

基本语法：

```python
if 条件:
    代码
```

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

# 6. 比较运算符

| 运算符 | 含义 |
|---------|------|
| > | 大于 |
| < | 小于 |
| >= | 大于等于 |
| <= | 小于等于 |
| == | 等于 |
| != | 不等于 |

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

```python
range(5)
```

表示：

```
0 1 2 3 4
```

---

### 写法二

```python
range(2,6)
```

表示：

```
2 3 4 5
```

---

### 写法三

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

---

# 13. break 与 continue

## break

结束整个循环。

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

对应 C：

```c
break;
```

---

## continue

跳过本次循环。

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

对应 C：

```c
continue;
```

---

# 14. 函数

函数用于**完成一个独立功能，提高代码复用性**。

基本语法：

```python
def 函数名(参数):
    函数体
```

例如：

```python
def add(a, b):
    return a + b
```

调用函数：

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

## 4. __init__() —— 初始化函数也就是构造函数

### 什么是初始化？

创建对象时，

Python 会自动执行：

```python
__init__()
```

例如：

```python
class Student:

    def __init__(self):
        print("创建对象")
```

创建对象：

```python
student = Student()
```

输出：

```
创建对象
```

说明：

对象创建完成以后，

Python 自动调用：

```
__init__()
```

---

## 为什么叫构造函数？

Java：

```java
Student()
```

Python：

```python
__init__()
```

作用一样。

都是：

> 创建对象时进行初始化。

---

## 5. self 到底是什么？

例如：

```python
class Student:

    def __init__(self):
        self.name = "张三"
```

这里：

```
self

表示对象自己
```

可以理解为：

```
student.name
```

其实就是：

```
self.name
```

self 永远表示：

> 当前对象。

例如：

```
Student

↓

student1

↓

student2

↓

student3
```

每个对象都有自己的：

```
self
```

所以：

```python
student1.name

student2.name
```

互不影响。

---

## 6. 成员变量（Attribute）

成员变量就是：

对象保存的数据。

例如：

```python
class Student:

    def __init__(self):

        self.name = "张三"

        self.age = 20
```

这里：

```
name

age
```

都是成员变量。

访问：

```python
print(student.name)
```

输出：

```
张三
```

---

## 7. 给对象传参数

例如：

```python
class Student:

    def __init__(self,name,age):

        self.name=name

        self.age=age
```

创建对象：

```python
student = Student("Alice",20)
```

输出：

```python
print(student.name)
```

```
Alice
```

这样，

每个对象的数据都不同。

---

## 8. 成员方法（Method）

除了保存数据，

对象还能执行行为。

例如：

```python
class Student:

    def study(self):

        print("正在学习Python")
```

调用：

```python
student = Student()

student.study()
```

输出：

```
正在学习Python
```

---

## 9. 修改成员变量

例如：

```python
student.name = "Bob"
```

再次打印：

```python
print(student.name)
```

输出：

```
Bob
```

说明：

对象的数据可以修改。

---

## 10. 继承（Inheritance）

这是推荐系统最重要的内容之一。

例如：

```python
class Animal:

    def eat(self):

        print("吃东西")
```

Dog：

```python
class Dog(Animal):
    pass
```

Dog 自动拥有：

```
eat()
```

调用：

```python
dog = Dog()

dog.eat()
```

输出：

```
吃东西
```

---

## 11. super()

如果父类已经写好了很多内容，

子类可以继续使用。

例如：

```python
class Animal:

    def __init__(self):

        print("Animal")
```

```python
class Dog(Animal):

    def __init__(self):

        super().__init__()

        print("Dog")
```

输出：

```
Animal

Dog
```

---

## 12. 为什么 PyTorch 都继承 nn.Module？

例如：

```python
class MyModel(nn.Module):
```

原因：

nn.Module 已经实现了：

```
参数管理

模型保存

模型加载

GPU迁移

训练模式

测试模式
```

所以不用重新写，直接继承即可。

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

---

## 17.2 open()——打开文件

Python 使用 `open()` 打开文件。

语法：

```python
open(file, mode, encoding)
```

参数说明：

| 参数 | 含义 |
|------|------|
| file | 文件路径 |
| mode | 打开方式 |
| encoding | 文件编码（通常使用 UTF-8） |

示例：

```python
file = open("student.txt", "r", encoding="utf-8")
```

---

## 17.3 文件打开模式（mode）

| 模式 | 含义 |
|------|------|
| `"r"` | 只读（默认） |
| `"w"` | 写入（覆盖原文件） |
| `"a"` | 追加内容 |
| `"x"` | 创建新文件 |
| `"rb"` | 二进制读取 |
| `"wb"` | 二进制写入 |

例如：

```python
file = open("data.txt", "w")
```

如果文件不存在，会自动创建。

---

## 17.4 读取文件

### 17.4.1 read()

一次性读取整个文件。

```python
with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()

print(content)
```

适用于：

- 小文件
- 配置文件
- 文本说明

---

### 17.4.2 readline()

一次读取一行。

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

---

## 17.5 写入文件

### write()

```python
with open("result.txt", "w", encoding="utf-8") as f:
    f.write("Hello World")
```

运行后：

```
result.txt

Hello World
```

---

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
