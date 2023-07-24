---
title: CanListener类
type: docs
---

# CanListener类
此类继承自[QObject](https://doc.qt.io/qt-5/qobject.html)类

## 成员函数

---
### 公共成员函数
[CanInterfaceId getInterfaceId()]({{% ref "/docs/driver/CanListener_class.md#getinterfaceid" %}})

[CanInterface &getInterface()]({{% ref "/docs/driver/CanListener_class.md#getinterface" %}})

## 槽函数
[void run()]({{% ref "/docs/driver/CanListener_class.md#run" %}})

[void startThread()]({{% ref "/docs/driver/CanListener_class.md#startthread" %}})

[void requestStop()]({{% ref "/docs/driver/CanListener_class.md#requeststop" %}})

[void waitFinish()]({{% ref "/docs/driver/CanListener_class.md#waitfinish" %}})

## 公共成员函数说明

### getInterfaceId

---
    CanInterfaceId getInterfaceId()
返回所监听的接口(Interface)的ID。

### getInterface

---
    CanInterface &getInterface()
返回所监听的接口(Interface)。

## 公共槽函数说明

### run

---
    void run()
循环从所监听的接口(Interface)读取数据并输出到trace(尚未研究CanTrace)，直至全部数据读取完毕

### startThread

---
    void startThread()
把当前CanListener关联到一个新的线程并启动，启动后执行run()函数

### requestStop

---
    void requestStop()
设置停止标志*，会使run()函数停止读取数据并退出

*停止标志：在run()函数中会检查此标志，若为真则退出
### waitFinish

---
    void waitFinish()
设置停止标志并等待进程停止

*停止标志：在run()函数中会检查此标志，若为真则退出