---
title: CanTrace类
type: docs
---

# CanListener类
此类继承自[QObject](https://doc.qt.io/qt-5/qobject.html)类

## 成员函数

---
### 公共成员函数
[unsigned long size()]({{% ref "/docs/driver/CanListener_class.md#size" %}})

[void clear()]({{% ref "/docs/driver/CanListener_class.md#clear" %}})

[const CanMessage *getMessage(int idx)]({{% ref "/docs/driver/CanListener_class.md#getmessage" %}})

[void enqueueMessage(const CanMessage &msg, bool more_to_follow=false)]({{% ref "/docs/driver/CanListener_class.md#enqueuemessage" %}})

[void saveCanDump(QFile &file)]({{% ref "/docs/driver/CanListener_class.md#savecandump" %}})

[void saveVectorAsc(QFile &file)]({{% ref "/docs/driver/CanListener_class.md#savevectorasc" %}})

[bool getMuxedSignalFromCache(const CanDbSignal *signal, uint64_t *raw_value)]({{% ref "/docs/driver/CanListener_class.md#getmuxedsignalfromcache" %}})

## 公共成员函数说明

### size

---
    unsigned long size()
返回已占用的行数(?)

### clear

---
    void clear()
清空trace

### getMessage

---
    const CanMessage *getMessage(int idx)
返回指定行的CanMessage，若idx超出范围则返回0(nullptr)

### enqueueMessage

---
    void enqueueMessage(const CanMessage &msg, bool more_to_follow=false)
把msg加入trace，如果more_to_follow为false，则执行[startTimer()]()

### saveCanDump

---
    void saveCanDump(QFile &file)
把trace中数据保存到文件

### saveVectorAsc

---
    void saveVectorAsc(QFile &file)
把trace中数据保存到为asc向量文件(?)。此函数中有很多未完成部分

### getMuxedSignalFromCache

---
    bool getMuxedSignalFromCache(const CanDbSignal *signal, uint64_t *raw_value)
从缓存中获取信号，保存到raw_value中，若缓存中存在且成功获取则返回true，否则返回false
