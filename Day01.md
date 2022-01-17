# Golang

---

## Golang简介与特点

简介：

Go语言保证了既能达到静态语言的安全和性能，又达到了动态语言开发维护的高效率

特点：

1. 从C语言中	继承了很多理念，包括表达式语法，控制结构，基础数据类型，调用参数传值，指针等等，也保留了和C语言一样的编译执行方式及弱化的指针
2. 引入包的概念，用于组织程序结构，Go语言的一个文件都要归属于一个包，而不能单独存在
3. 垃圾回收机制，内存自动回收，不需开发人员管理
4. 天然并发（重要特点）
   1. 从语言层面支持并发，实现简单
   2. goroutine，轻量级线程，可实现大并发处理，高效利用多核
   3. 基于CPS并发模型（Communicating Sequential Processes）实现
5. 吸收了管道通信机制，形成Go语言特有的管道channel通过管道channel，可以实现不同的goroute之间的相互通信
6. 函数可以返回多个值
7. 新的创新，比如切片slice、延时执行defer等

---

## Golang环境设置

环境设置：

1. 下载地址：[官网][https://go.dev/]  [国内代理网][https://golang.google.cn/]
2. 下载文件：go.windows-arm64.msi Installer Windows
3. 配置环境变量：
   1. GOROOT：指定SDK的安装路径 d:/go
   2. Path: 添加SDK的/bin目录
   3. GOPATH：工作目录，将来我们的go项目的工作路径

---

## Golang开发软件

采用VS Code与Golang开发插件

---

## Golang第一个程序“Hello,world.”

步骤：

1. 在d盘goprojects文件夹下新建一个子目录src，在src目录下新建一个文件夹go_code，在go_code文件夹下新建项目文件，按照projectxx的格式书写，本次为第一个项目，名字为project01

2. 项目文件夹下新建两个文件夹，main文件夹与package文件夹

3. 在main文件夹下新建hello.go文件

4. 在hello.go文件中开始编写

5. ```go
   package main
   import "fmt"
   func main(){
       fmt.Println("Hello,world.")
   }
   ```

6. 说明：

   1. go文件后缀名是.go
   2. package main：表示该hello.go文件所在的包main，在go中，每个文件都必须归属于一个包。
   3. import "fmt"：引入一个包，包名为fmt，引入该包后，就可以使用fmt包的函数，比如fmt.Println
   4. func main(){}：func是一个关键字，表示一个函数。main是函数名，是一个主函数，即我们程序的入口。
   5. fmt.Println("hello")：表示调用fmt包的函数Println输出"Hello,world."

7. 编译和使用：

   1. cmd命令行使用go build hello.go编译文件
   2. 用cmd直接打开hello.exe运行
   3. 可以用go run hello.go可以直接执行，大多数情况下先编译再运行。