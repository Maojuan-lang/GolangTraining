# Golang

---

## map介绍

map是key-value数据结构，又称为字段或者关联数组。类似其他编程语言的集合，在编程中经常被使用

---

## map的声明

var map的变量名 map[keytype]valuetype

key的类型：golang中的map的key可以是很多种类型，比如bool，数字，string，指针，channel，还可以是只包含前面几个类型的接口，结构体，数组。（通常为int，string）

注意：

1. slice，map还有function不可以，因为这几个没法用==来判断。
2. map在使用前要先用make分配空间。
3. map的key是不能重复的，如果重复，则按最后的key-value为准
4. map的value是可以相同的
5. map的key-value是无序的

---

## map的使用

map的使用方式：

```go
// 方式一
var cities map[string]string
cities = make(map[string]string,10)
// 方式二
var cities = make(map[string]string)
// 方式三
var cities map[string]string = map[string]string{
    "no1":"北京",
    "no2":"广州"，
}
```

---

## map的增删改查操作

map的增加和更新：map["key"] = value //如果key还没有就是增加，如果key存在就是修改

map删除：

1. 如果我们要删除map的所有key，没有一个专门的方法一次删除，可以遍历一下key逐个删除
2. 也可以map = make(...)，make一个新的map，让原来的成为垃圾，被gc回收

map查找：val,findRes = map["key"]，如果有findRes返回true，没有就返回false

---

## map遍历

map遍历使用for-range结构遍历

---

## map切片

基本介绍：切片的数据类型如果是map，则我们称为slice of map，map切片，这样使用则map个数就可以动态变化了。

---

## map排序

基本介绍：

1. golang中没有方法针对map的key进行排序
2. golang中的map默认是无序的，跟添加顺序无关，每次输出可能不一样
3. golang中map的排序是先对key进行排序，然后根据key值遍历输出

---

## map注意事项

注意事项：

1. map是引用类型，遵循引用类型传递的机制，在一个函数接收map修改后，会直接修改原来的map
2. map的容量满后，再想增加map会自动扩容，并不会发生panic，也就是说map能动态增长的键值对
3. map的value也经常使用struct类型，更适合管理复杂的数据。

