---
title: "Operating System - tip : Kernel Debug using gdb"
categories:
  - OS
tags:
  - OS
  - Tool
toc: true
toc_sticky: true
toc_label: "OS - Kernel Debug"
toc_icon: "building"
---

# gdb 실행
```
(linux)> gdb-multiarch ./vmlinux
# we need a breakpoint 
(gdb)> break __arm64_sys_hello
# check out arch/arm64/include/asm/syscall_wrapper.h : 왜 __arm64_ 가 붙었는지 이해 가능
# remote 설정
(gdb)> target remote localhost:1234
# qemu와 gdb가 붙는다.
(gdb)> run 
```

# gdb debug 방법
```
# Debug하고 싶은 바이너리 실행
(root)> ./test_hello
```

```
# we hit the break point
# 어디 있는지 알고 싶으면...
(gdb)> win
# 'n' is a command to execute line by line.
(gdb)> n
# You can print symbolds' value in gdb.
(gdb)> print /s num_called 
# "Next breakpoint"
(gdb)> continue
``` 

# gdb 종료 방법
```
# stop showing the win window.
(gdb)> tui disable
# remote debugging ended
(gdb)> detach
(gdb)> quit
(linux)> ...
```
