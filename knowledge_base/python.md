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