## 面试题记录

### 什么是进程和线程？之间的区别？
进程: 系统进行资源分配和调度的基本单位
线程: 程序执行的最小单位(CPU调度的最小单位)
进程是线程的容器, 一个进程可以拥有多个线程, 
每个进程都拥有自己的独立空间地址、数据栈
一个进程无法访问另外一个进程里定义的变量、数据结构，只有建立了 IPC 通信，进程之间才可数据共享

### 什么是孤儿进程？
父进程创建子进程之后，父进程退出了，但是父进程对应的一个或多个子进程还在运行，这些子进程会被系统的 init 进程收养，对应的进程 ppid 为 1，这就是孤儿进程

### Node.js 是单线程还是多线程？进一步会提问为什么是单线程？
Javascript 是单线程的，但是做为其在服务端运行环境的 Node.js 并非是单线程的。
Javascript 在设计的时候只希望有一个线程来操作DOM, 如果多个会乱套

### 如何让一个 js 文件在 Linux 下成为一个可执行命令程序?
1. 新建 hello.js 文件，头部须加上 #!/usr/bin/env node，表示当前脚本使用 Node.js 进行解析
2. 赋予文件可执行权限 chmod +x /${dir}/hello.js，目录自定义
3. 在 /usr/local/bin 目录下创建一个软链文件 sudo ln -s /${dir}/hello.js /usr/local/bin/hello，文件名就是我们在终端使用的名字
4. 终端执行 hello 相当于输入 node hello.js