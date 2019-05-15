# linux-perf


# gdb process

```
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
```

# strace

```
strace -p pid -tt -T -F -e trace=write
[pid 3825188] 14:12:15.671248 write(7062, "2019/05/15-14:12:15.671056 7eecd"..., 108) = 108 <0.000207>

----"-f"----------"-tt"----"syscall"-------------------"params"-------------------------"ret"---"cost"----

strace -p pid -tt -T -f -o out.txt 
从最后一个字段的下标2开始取8个字符就是耗时，查找超过耗时大于0.1s的操作。
awk 'substr($NF, 2, 8) - 0.1 > 0 {print}' out.txt
```

# perf trace 

```
sudo perf trace -t 23555 --duration 0.001 -e write
```

# perf top
```
sudo perf top [-t tid | -p pid] -g
```
