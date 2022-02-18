## gdb调试基本命令 ##

- 进入gdb
```
gdb program
```

- 设置调试参数
```
set args --frame_count 10
```

- 断点相关
```
break line_num 按行号设置断点
break func  按函数设置
info b  查看断点
delete b
disable b

```

- 查看相关
```
list 查看源码
what 查看当前位置
where 查看堆栈
up/down 往上改变堆栈深度
show args
info program
layout src 显示源码
layout asm 显示反汇编窗口
layout regs 显示cpu寄存器
layout split 显示源代码和反汇编
ctrl+L 刷新窗口
```


- 执行相关

```
r 启动
n 单步执行
s 进入函数
continue 继续直至下个断点
f 执行至函数结束
call 函数（参数） 执行函数
return 从当前函数返回
```



