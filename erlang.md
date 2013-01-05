
## 运算符
整除，取余 div rem

=:= 恒等测试符

## 变量

大写字母开头

变量不变

_ 变量
## 原子

表示非数字常量值

小写字母开头

全局有效

## 元组

类似C的结构

Var = {atom, 1, 2}

基于模式匹配的赋值

P = {1, 3}
{X, Y} = P  => X = 1, Y = 3

## 列表

head 第一个元素
tial 最后一个元素

递归定义 if T/P is a list, [T|P] is a list, T is head, P is tail

模式匹配提取元素： [X|Y] = [List] => X is head, Y is tail

Erlang字符串不过是整数列表 "string" 必须双引号

$a => 97



