---
title: MeasurementSetup类
type: docs
---

# MeasurementSetup类
此类继承自[QObject](https://doc.qt.io/qt-5/qobject.html)类

## 成员函数

---
### 公共成员函数
[void clear()]({{% ref "/docs/core/CanTrace_class.md#clear" %}})

[CanDbMessage *findDbMessage(const CanMessage &msg) const]({{% ref "/docs/core/CanTrace_class.md#finddbmessage" %}})

[int countNetworks() const]({{% ref "/docs/core/CanTrace_class.md#countnetworks" %}}

[MeasurementNetwork *getNetwork(int index) const]({{% ref "/docs/core/MeasurementSetup_class.md#getnetwork" %}})

[MeasurementNetwork *getNetworkByName(QString name) const]({{% ref "/docs/core/MeasurementSetup_class.md#getnetworkbyname" %}})

[QList<MeasurementNetwork*> getNetworks()]({{% ref "/docs/core/MeasurementSetup_class.md#getnetworks" %}})

[MeasurementNetwork *createNetwork()]({{% ref "/docs/core/MeasurementSetup_class.md#createnetwork" %}})

[void removeNetwork(MeasurementNetwork *network)]({{% ref "/docs/core/MeasurementSetup_class.md#removenetwork" %}})

[void cloneFrom(MeasurementSetup &origin)]({{% ref "/docs/core/MeasurementSetup_class.md#clonefrom" %}})

[bool saveXML(Backend &backend, QDomDocument &xml, QDomElement &root)]({{% ref "/docs/core/MeasurementSetup_class.md#savexml" %}})

[bool loadXML(Backend &backend, QDomElement &el)]({{% ref "/docs/core/MeasurementSetup_class.md#loadxml" %}})

## 公共成员函数说明

### clear

---
    void clear()
清除所有网络

### findDbMessage

---
    CanDbMessage *findDbMessage(const CanMessage &msg) const
根据msg唯一(?)的ID查找数据库中的消息，找到则返回指向该消息的指针，否则返回nullptr

### countNetworks

---
    int countNetworks() const
返回网络(network)数量

### getNetwork

---
    MeasurementNetwork *getNetwork(int index) const
返回指定索引（或者说编号）的网络(network)

### getNetworkByName

---
    MeasurementNetwork *getNetworkByName(QString name) const
根据网络(network)名称获取对应 网络，如果获取成功，返回指向该网络的指针，失败则返回nullptr

### getNetworks

---
    QList<MeasurementNetwork*> getNetworks()
返回所有网络(network)的列表

### createNetwork

---
    MeasurementNetwork *createNetwork()
创建一个新的网络(network)，并返回指向该网络的指针

### removeNetwork

---
    void removeNetwork(MeasurementNetwork *network)
删除指定的网络(network)

### cloneFrom

---
    void cloneFrom(MeasurementSetup &origin)
从origin复制所有内容到当前对象

### saveXML

---
    bool saveXML(Backend &backend, QDomDocument &xml, QDomElement &root)
保存所有网络设置到xml文件中，保存成功返回true，否则返回false

### loadXML

---
    bool loadXML(Backend &backend, QDomElement &el)
从xml文件中加载网络设置，加载成功返回true，否则返回false