---
layout: menu
title: 进程间通讯
permalink: /android/ipc
type: android
---

# Android进程间通信的几种方式
====
## 定义多进程
### 全局进程
            定义android:process = package:remote
### APP的私有进程
            定义android:process = :remote
## 多进程引发的问题
### 静态成员和单例失效
### 线程同步机制失效
### SharedPreferences可靠性下降
### Application多次创建
## 进程间通信
### Bundle/Intent传递数据
#### bundle作用及原理
##### 1 可传递：基本类型，String，实现了Serializable或Parcellable接口的数据结构
##### 2 大小限制：系统对使用Binder交换数据的buffer大小进行了限制，大小为1M
```
    也就是说不仅仅是一次性传递大数据会出问题，当同时传递很多数据，尽管每个都不超过1MB，但是总大小超过1MB也会出错。
    我们上面提到了Parcel机制使用了一个共享内存，这个共享内存就叫Binder transaction buffer
```    
参考：[Android中Intent/Bundle的通信原理及大小限制（Parcelable原理及与Serializable的区别）](https://www.jianshu.com/p/2e6936e2de3d)

##### 3 Bundle内部是由ArrayMap
    一个数组记录key的hash值
    另一个数组记录value值
    为什么不用hashmap
        HashMap内部则是数组+链表的结构
        小数据量
            在数据量较少的情况下，HashMap的Entry Array比ArrayMap占用更多的内存
        使用ArrayMap保存数据在操作速度和内存占用上都具有优势

### ContentProvider
            Parcelable和Serializable的区别和比较
                Parcelable和Serializable都是实现序列化并且都可以用于Intent间传递数据,Serializable是Java的实现方式,可能会频繁的IO操作,所以消耗比较大,但是实现方式简单 Parcelable是Android提供的方式,效率比较高,但是实现起来复杂一些 , 二者的选取规则是:内存序列化上选择Parcelable, 存储到设备或者网络传输上选择Serializable(当然Parcelable也可以但是稍显复杂)  作者：chzphoenix 链接：https://www.jianshu.com/p/2e6936e2de3d 來源：简书 简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。
### 文件共享
#### AIDL
##### Messenger
```
      用Messenger来发送数据，用Handler来处理数据串行
```                
#### Socket
    https://blog.csdn.net/qdh186/article/details/78316952
