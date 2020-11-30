---
title: Shell Base
author: banana
layout: post
---
## sh bash ./ 
### 借助sh bash命令可直接执行 *.sh
### ./ 是控制台直接去执行文件，需要获取文件权限

## chmod 777
### 获取文件最高权限

#!/bin/bash
# 多行命令
touch ~/code/shells/banzhang.txt
echo "HelloWorld" >> ~/code/shells/banzhang.txt
# 常用环境变量
echo $HOME
echo $PWD
echo $SHELL
echo $USER
# 定义变量
A=1
echo $A
# 撤销变量
unset A
echo $A
# 静态变量（readonly变量）
readonly B=2
echo $B
unset B #会报错，因为是只读变量

# 变量默认类型都是字符串类型,无法直接进行数值运算
C=1+1
echo $C

# 吧变量提升为全局变量
# shell里面执行export D，将D提升为全局变量，再运行此文件，就可以得到D
echo $D

# 特殊变量
# $n
# 第1到第9个参数$1-$9
# 10以上用{}符号,例如 ${11}
# $0是命令名称
# $#
# 获取所有输入参数的个数，一般用于循环
# $*
# 获取所有参数，把所有参数看成一个整体
# $@
# 获取所有参数，每个参数区分对待
# $?
# 上一条执行的命令的返回状态，变量值为0则是正确执行，非0则执行出现问题
echo $?

# 数值运算
# $(()) 或 $[]
# expr, + - \* / %, 运算符数值间要有空格
echo $(((3+4)*5))
echo $[(3+4)*5]
expr `expr 3 + 4` \* 5

# 判断条件
# [ conditon ], condition非空返回true,空返回false。
# 逻辑与 &&，逻辑或 ||
# 整数比较，字符串比较，= -lt -le -eq -gt -ge -ne
echo compare-------
[ 3 -ge 2 ]
echo $?
[ 3 -le 2 ]
echo $?
# 判断文件权限，-w -r -x
echo file-------
[ -w banzhang.txt ]
echo $?
[ -r banzhang.txt ]
echo $?
[ -x banzhang.txt ]
echo $?
# 判断文件类型，-f -e -d 
echo file type -------
[ -f banzhang.txt ]
echo $?
[ -d banzhang.txt ]
echo $?
[ -e banzhang.txt ]
echo $?
[ -e banzhang1.txt ]
echo $?

# if判断
# if [ condition ];then
#     程序  
# elif       
#     程序           
# fi
# 或者
# if [ condition ]
# then
#     程序
# fi
if [ $1 -eq 1 ];then
    echo input 1
elif [ $1 -eq 2 ];then
    echo input 2
fi

# case判断
# case $变量名 in
# "值1"）
#     程序1
# ;;
# "值2"）
#     程序2
# ;;
# *)
#     default程序
# esac
echo case-------
case $1 in
1)
    echo input1
;;
2)
    echo input2
;;
*)
    echo other
;;
esac

# for循环
# for((初始值;循环条件;变量变化))
# do
#     程序
# done
echo for-------
sum=0
for ((i=0;i<10;i++))
do
    sum=$[$sum+$i]
done
echo $sum
# for 变量 in 值1 值2 值3 。。。
# do
#     程序
# done
for i in $*
do
    sum=$[$sum+$i]
done
echo $sum

# while循环
# while [ condition ]
# do
#     程序
# done
echo while-------
i=5
sum=0
while [ $i -ge 0 ]
do
    sum=$[$sum+$i]
    i=$[$i-1]
done
echo $sum

# read读取控制台输入
# read（选项）（参数）
# -p 指定读取值时的提示符
# -t 指定读取值时的等待时间(秒)
read -t 5 -p 5秒内输入用户名 NAME
echo 你的用户名是$NAME

# basename string(filepath) suffix
basename $HOME/code/shells/banzhang.txt
basename $HOME/code/shells/banzhang.txt .txt
# dirname filepath
dirname $HOME/code/shells/banzhang.txt

# 自定义函数
# 必须再调用函数之前，声明函数（shell是逐行执行）
# function funname()
# {
#     Action;
#     [return int;] 一般用 return $?;
# }
function sum()
{
    s=0
    s=$[$1+$2]
    echo $s
}
read -p "input number1: " num1
read -p "input number2: " num2
sum num1 num2

