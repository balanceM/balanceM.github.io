---
title: Shell cut,sed,awk,sort
author: banana
layout: post
---
# cut（负责在文件中剪切数据）
# cut命令从文件的每一行剪切字节、字符和字段，并输出
# -d 指定分隔符
# -f 取几列
cut -d " " -f 2,3 cut.txt
cat cut.txt | grep boy | cut -d " " -f 2 
echo $PATH | cut -d ":" -f 10-
ifconfig en0 | grep netmask | cut -d " " -f 2

# sed 一种流编辑器，一次处理一行内容，
# 一行内容 > 缓冲区（模式空间） > sed处理，原文件内容不会改变
# sed “commond” filename
# -e 在指令列模式上进行sed的动作编辑，只有一个可省略
# -i 
# 命令功能，
# a 新增，后面接字串，在下一行出现
# d 删除
# s 查找并替换
# sed "2a 'beautiful girl'" cut.txt
# 执行上方命令，mac报错 command a expects \ followed by text解决方法：
# brew install gnu-sed，使其与linux一致
alias sed=gsed
sed "2a beautiful girl" cut.txt
echo "\n"
sed "s/banana/watermelon/g" cut.txt
echo "\n"
sed "/banana/d" cut.txt
sed -e "/banana/d" -e "s/boy/girl/g" cut.txt
echo "\n"

# awk 强大的文本分析工具，文件逐行读入，以空格为默认分隔符将每行切片，之后再进行分析
# awk [选项参数] 'pattern1{action1} pattern2{aciton2} ...' filename
# 内置变量 FILENAME 文件名，  NR 已读的记录数， NF 浏览记录的域的个数（切割后的列数）
# -F 指定文件分隔符
# -v 给一个用户边量赋值
# awk -F : '/^root/{print $1" , "$7}' passwd
# awk -F : 'BEGIN{print "_handsome Boy"} {print $1", "$7} END{print "_beautiful girl"}' passwd
# awk -F : -v i=1 '{print $3+i}' passwd
# awk -F : '{print FILENAME NR NF}' passwd
# ifconfig en0 | grep netmask | awk -F " " '{print $2}'
# awk '/^$/{print NR}' cut.txt


# sort
# -n 依照数值大小排序
# -r 倒序
# -t 指定分隔符
# -k 指定以分隔后第几列排序
sort -t : -nrk 2 sort.txt

grep -r 2 ./ | cut -d ":" -f 1