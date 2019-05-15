# linux-perf


# gdb process
## 查找进程的pid
ps aux | grep "process_name"

## 查看所有进程线程的cpu的使用情况
top -p pid -H 

## 确定需要定位的线程
## attach到对应的进程或线程
gdb attach pid
## 查看程序的信息
info proc
## 在路径下搜索加载符号
set solib-search-path path
## 查看栈帧
bt (backtrace)
