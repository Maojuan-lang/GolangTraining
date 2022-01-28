# Golang

---

## 字符串中常用的函数

基本介绍：字符串在我们程序开发中，使用的是非常多的，常用的函数需要掌握

1. 统计字符串的长度，按字节 len(str)
2. 字符串遍历，同时处理有中文的问题 r := []rune(str)
3. 字符串转整数 n,err := strconv.Atoi("12")
4. 整数转字符串 str = strconv.Itoa(12345)
5. 字符串转 []byte: var bytes = [] byte("hello go")
6. []byte转字符串：str = string([]byte{97,98,99})
7. 10进制转2，4，8，16进制：str = strconv.FormatInt(123,2)
8. 查找子串是否在指定的字符串中：strings.Contains("seafood","foo")
9. 统计一个字符串有几个指定的子串：strings.Count("ceheese","e")
10. 不区分大小写的字符串比较（==区分字母大小写）：fmt.Println(strings.EqualFold("abc", "ABC"))
11. 返回子串在字符串第一次出现的index值，如果没有就返回-1：strings.index("NLT_abc","abc")
12. 返回子串在字符串最后一次出现的index值，如果没有就返回-1：strings.LastIndex("go golang","go")
13. 将指定的子串替换成另外一个子串：strings.Replace("go go hello","go","golang",n) // n可以指定你希望替换的个数，如果n=-1则表示全部替换
14. 按照指定的某个字符为分割标识，将第一个字符拆分成字符串数组：strings.Split("hello,world",",")
15. 将字符串的字母转换成小写：strings.ToLower("Go") 
16. 将字符串的字母转换成大写：strings.ToUpper("Go")
17. 将字符串左右两边的空格去掉：strings.TrimSpace(" golang ")
18. 将字符串左右两边指定的字符去掉：strings.Trim("!golang!","!")
19. 将字符串左边指定的字符去掉：strings.TrimLeft("!golang!","!")
20. 将字符串右边指定的字符去掉：strings.TrimRight("!golang!","!")
21. 判断字符串是否以指定的字符串开头：strings.HasPrefix("golang","go")
22. 判断字符串是否以指定的字符串结束：strings.HasSuffix("golang","lang")

---

## 时间和日期相关函数

基本介绍：时间和日期相关函数，需要导入time包

格式化日期时间

1. 格式化的第一种方式：fmt.Printf("%d",now.Year())
2. 格式化的第二种方式：fmt.Printf(now.Format("2006-01-02 15:04:05"))
3. now.Unix()时间戳
4. now.UnixNano纳秒时间戳
5. now.时间单位*数字可得到指定时间

---

## 内置函数

基本介绍：Golang设计者为了编程方便，提供了一些函数，这些函数可以直接使用，我们称之为Go的内置函数

1. len：用来求长度，比如string、array、slice、map、channel
2. new：用来分配内存，主要用来分配值类型，比如int、float32，struct...返回的是指针
3. make：用来分配内存，主要用来分配引用类型，比如chan、map、slice

---

## 错误处理

基本介绍：

1. Go语言追求简洁优雅，所以Go语言不支持传统的try...catch...finally
2. Go中引入的处理方式为：defer,panic,recover
3. 这几个异常的使用场景可以这么简单描述：Go中可以抛出一个panic的异常，然后在defer中通过recover捕获这个异常，然后正常处理
4. nil在Go中表示空，即其他语言的null
5. 在匿名函数后加括号表示调用

自定义错误：Go程序中，也支持自定义错误，使用errors.New和panic内置函数

1. errors.New("错误说明")，会返回一个error类型的值，表示一个错误
2. panic内置函数，接收一个interface{}类型的值作为参数。可以接收error类型的变量，输出粗偶无信息并退出程序

---

## 数组介绍

基本介绍：数组可以存放多个同一类型数据，数组也是一种数据类型，在Go中，数组是值类型

数组的定义：var 数组名 [数组大小]数据类型

---

## 数组的使用

访问数组元素：数组名[下标]

四种初始化数组的方式：

1. var 数组名 [数组大小]数据类型 = [数组大小]数据类型{数据}
2. var 数组名 =  [数组大小]数据类型{数据}
3. var 数组名 =  [...]数据类型{数据}
4. var 数组名 =  [...]数据类型{下标:数据}

---

## 数组的遍历

方式一：常规遍历

1. 利用for循环遍历

方式二：for-range结构遍历

1. 这是Go语言一种独有的结构，可以用来遍历访问数组的元素

2. 基本语法

   ```go
   for index,value := range array{
       ...
   }
   ```

3. 说明：

   1. 第一个返回值index是数组的下标
   2. 第二个value是在该下标位置的值
   3. 它们都是仅在for循环内部可见的局部变量
   4. 遍历数组元素的时候，如果不想使用下标index，可以用_省略
   5. index和value的名称不是固定的，可以自定义命名

---

## 数组使用注意事项和细节

1. 数组是多个相同类型数据的组合，一个数组一旦声明/定义了，其长度是固定的，不能动态变化
2. var arr []int 这是arr就是一个slice切片
3. 数组中的元素可以是任何数据类型，包括值类型和引用类型，但是不能混用
4. 数组创建后，如果没有赋值，有默认值
   1. 数值类型数组，默认值是0
   2. 字符串数组，默认值是""
   3. bool数组，默认值是false
5. 使用数组的步骤：
   1. 声明数组并开辟空间
   2. 给数组各个元素赋值
   3. 使用数组
6. 数组的下标是从0开始的
7. 数组下标必须在指定范围内使用，否则报panic：数组越界
8. Go的数组属于值类型，在默认情况下是值传递，因此会进行值拷贝，数组间不会相互影响
9. 如果在其他函数中去修改原来的数组，可以使用引用传递（指针方式）
10. 长度是数组类型的一部分，在传递函数参数时，需要考虑数组的长度

---

## 切片的基本介绍

基本介绍：

1. 切片的英文是slice
2. 切片是数组的一个引用，因此切片是引用类型，在进行传递时，遵守引用传递的机制
3. 切片的使用和数组类似，遍历切片、访问切片的元素和求切片长度len(slice)都一样
4. 切片的长度是可以变化的，因此切片是一个可以动态变化的数组
5. 切片定义的基本语法var 变量名 []类型

注意事项：

1. slice是一个引用类型

2. slice从底层来说，是一个数据结构（struct结构体）

   ```go
   type slice struce{
       ptr *[slice大小]int
       len int
       cap int
   }
   ```

---

## 切片的使用

方式一：定义一个切片，热核让切片去引用一个已经创建好的切片

方式二：用make来创建切片

1. 基本语法：var 切片名 []type = make([],len,[cap])
2. 参数说明：type是数据类型，len是切片长度，cap是切片容量
3. 注意事项：
   1. 通过make方式创建切片可以指定切片的大小和容量
   2. 如果没有给切片的各个元素赋值，那么就会使用默认值
   3. 通过make方式创建的切片对应的数组是由make底层维护，对外不可见，只能通过slice去访问各个元素

方式三：定义一个切片，直接就指定具体的数组

---

## 切片的遍历

切片的遍历和数组一样，也有两种方式

1. for循环常规方式遍历
2. for-range结构遍历切片

---

## 切片注意事项和细节说明

注意事项：

1. 切片初始化时var slice = arr[startIndex:endIndex]

   说明：从arr数组下标为startIndex取到下标为endIndex的元素（不包含arr[endIndex]）

2. 切片初始化时，仍然不能越界。范围在[0-len(arr)]之间，但是可以动态增长

   1. var slice = arr[0:end] 可以简写为 var slice = arr[:end]
   2. var slice = arr[start:len(arr)] 可以简写为 var slice = arr[start:]
   3. var slice = arr[0:len(arr)] 可以简写为 var slice = arr[:]

3. cap是一个内置函数，用于通统计切片的容量，即最大可以存放多少个元素

4. 切片定义完后，还不能使用，因为本身是一个空的，需要让其引用到一个数组或者make一个空间供切片来使用

5. 切片可以继续切片

6. 用append内置函数，可以对切片进行动态追加

   切片append操作的底层远离分析：

   1. 切片append操作的本质就是对数组扩容
   2. go底层会创建一个新的数组newArr（安装扩容后大小）
   3. 将slice原来包含的元素拷贝到新的数组newArr
   4. slice重新引用到newArr
   5. 注意newArr是在底层来维护的，程序员不可见

---

## string和slice

1. string底层是一个byte数组，因此string也可以进行切片处理
2. string和切片在内存的形式
3. string是不可变的
4. 如果要修改字符串，可以将string--->[]byte或者[]rune--->修改--->重写转成string