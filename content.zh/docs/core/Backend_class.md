---
title: Backend类
type: docs
---

# Backend类
此类继承自[QObject](https://doc.qt.io/qt-5/qobject.html)类

## 成员函数

---
### 公共成员函数
[static Backend &instance()]({{% ref "/docs/core/Backend_class.md#instance" %}})

[void addCanDriver(CanDriver &driver)]({{% ref "/docs/core/Backend_class.md#addcandriver" %}})

[bool startMeasurement()]({{% ref "/docs/core/Backend_class.md#startmeasurement" %}})

[void stopMeasurement()]({{% ref "/docs/core/Backend_class.md#stopmeasurement" %}})

[bool isMeasurementRunning() const]({{% ref "/docs/core/Backend_class.md#ismeasurementrunning" %}})

[double getTimestampAtMeasurementStart() const]({{% ref "/docs/core/Backend_class.md#gettimestampatmeasurementstart" %}})

[uint64_t getUsecsAtMeasurementStart() const]({{% ref "/docs/core/Backend_class.md#getusecsatmeasurementstart" %}})

[uint64_t getNsecsSinceMeasurementStart() const]({{% ref "/docs/core/Backend_class.md#getnsecssincemeasurementstart" %}})

[uint64_t getUsecsSinceMeasurementStart() const]({{% ref "/docs/core/Backend_class.md#getusecssincemeasurementstart" %}})

[void logMessage(const QDateTime dt, const log_level_t level, const QString msg)]({{% ref "/docs/core/Backend_class.md#logmessage" %}})

[MeasurementSetup &getSetup()]({{% ref "/docs/core/Backend_class.md#getsetup" %}})

[void loadDefaultSetup(MeasurementSetup &setup)]({{% ref "/docs/core/Backend_class.md#loaddefaultsetup" %}})

[void setDefaultSetup()]({{% ref "/docs/core/Backend_class.md#setdefaultsetup" %}})

[void setSetup(MeasurementSetup &new_setup)]({{% ref "/docs/core/Backend_class.md#setsetup" %}})

[double currentTimeStamp() const]({{% ref "/docs/core/Backend_class.md#currenttimestamp" %}})

[CanTrace *getTrace()]({{% ref "/docs/core/Backend_class.md#gettrace" %}})

[void clearTrace()]({{% ref "/docs/core/Backend_class.md#cleartrace" %}})

[CanDbMessage *findDbMessage(const CanMessage &msg) const]({{% ref "/docs/core/Backend_class.md#finddbmessage" %}})

[CanInterfaceIdList getInterfaceList()]({{% ref "/docs/core/Backend_class.md#getinterfacelist" %}})

[CanDriver *getDriverById(CanInterfaceId id)]({{% ref "/docs/core/Backend_class.md#getdriverbyid" %}})

[CanInterface *getInterfaceById(CanInterfaceId id)]({{% ref "/docs/core/Backend_class.md#getinterfacebyid" %}})

[QString getInterfaceName(CanInterfaceId id)]({{% ref "/docs/core/Backend_class.md#getinterfacename" %}})

[QString getDriverName(CanInterfaceId id)]({{% ref "/docs/core/Backend_class.md#getdrivername" %}})

[CanDriver *getDriverByName(QString driverName)]({{% ref "/docs/core/Backend_class.md#getdriverbyname" %}})

[CanInterface *getInterfaceByDriverAndName(QString driverName, QString deviceName)]({{% ref "/docs/core/Backend_class.md#getinterfacebydriverandname" %}})

[pCanDb loadDbc(QString filename)]({{% ref "/docs/core/Backend_class.md#loaddbc" %}})

[void clearLog()]({{% ref "/docs/core/Backend_class.md#clearlog" %}})

[LogModel &getLogModel() const]({{% ref "/docs/core/Backend_class.md#getlogmodel" %}})

## 信号

---
void beginMeasurement()

void endMeasurement()

void onSetupChanged()

void onLogMessage(const QDateTime dt, const log_level_t level, const QString msg)

void onSetupDialogCreated(SetupDialog &dlg)

## 公共成员函数说明
### instance

---
    static Backend &instance()

静态函数，被调用时，会检查私有成员变量_instance是否为空(0)。

若为空，则创建一个Backend对象，赋值给_instance并返回。

否则，直接返回现有的Backend实例。

返回值：Backend类的实例的引用

### addCanDriver

---
    void addCanDriver(CanDriver &driver)

添加一个Can驱动

### startMeasurement

---
    bool startMeasurement()

调用该函数会从事先设置*的网络(network)和接口(interface)列表中，
依次获取网络及其中的Can接口，并分别启动一个新线程监听获取到的每个Can接口。

正常情况下，函数会发出beginMeasurement信号，并返回true。

*事先设置：通常是用户通过[SetupDialog](/docs/window/SetupDialog_class)设定的

### stopMeasurement

---
    void stopMeasurement()

调用此函数会向每一个监听线程发送停止请求，等待所有线程退出后，函数返回。

正常情况下，函数会发出endMeasurement信号，并返回true。

### isMeasurementRunning

---
     bool isMeasurementRunning() const
如果测量正在运行,返回true,否则返回false。

### getTimestampAtMeasurementStart

---
    double getTimestampAtMeasurementStart() const

返回测量开始时的时间戳。

### getUsecsAtMeasurementStart

---
    uint64_t getUsecsAtMeasurementStart() const

返回测量开始时的微秒数。

### getNsecsSinceMeasurementStart

---
    uint64_t getNsecsSinceMeasurementStart() const

返回测量开始后经过的纳秒数。

### getUsecsSinceMeasurementStart

---
    uint64_t getUsecsSinceMeasurementStart() const

返回测量开始后经过的微秒数。

### logMessage

---
    void logMessage(const QDateTime dt, const log_level_t level, const QString msg) 

将日志消息添加到日志模型(LogModel)中。具体实现是发送onLogMessage信号。

参数：
- dt: 日志消息的时间
- level: 日志消息的级别
- msg: 日志消息的内容

### getSetup

---
    MeasurementSetup &getSetup()

返回测量设置(MeasurementSetup)。具体实现是返回私有成员变量_setup。

### loadDefaultSetup

---
    void loadDefaultSetup(MeasurementSetup &setup)

加载默认设置到参数setup指定的MeasurementSetup对象中（尚未清楚何谓默认设置）。

### setDefaultSetup

---
    void setDefaultSetup()

相当于调用loadDefaultSetup(_setup)。

### setSetup

---
    void setSetup(MeasurementSetup &new_setup)

把参数new_setup中的设置应用到私有成员变量_setup中。

### currentTimeStamp

---
    double currentTimeStamp() const

返回当前时间戳（单位：毫秒）。

### getTrace

---
    CanTrace *getTrace()

返回私有成员变量_trace。（目前未研究Cantrace类）

### clearTrace

---
    void clearTrace()

清除私有成员变量_trace。（目前未研究Cantrace类）

### findDbMessage

---
    CanDbMessage *findDbMessage(const CanMessage &msg) const

未研究Canmeasurement类

### getInterfaceList

---
    CanInterfaceIdList getInterfaceList()

返回当前的接口(Interface)列表。

### getDriverById

---
    CanDriver *getDriverById(CanInterfaceId id)

返回指定id的Interface对应的Can驱动。如果不存在，属于严重错误

### getInterfaceById

---
    CanInterface *getInterfaceById(CanInterfaceId id)

返回指定id的Interface，如果不存在则返回0。

### getInterfaceName

---
    QString getInterfaceName(CanInterfaceId id)

返回指定id的接口(interface)的名称。如果不存在则返回空字符串，属于严重错误（试图获取不存在的接口的名称）。

### getDriverName

---
    QString getDriverName(CanInterfaceId id)

返回指定id的接口(interface)的驱动(driver)的名称。如果不存在则返回空字符串。

### getDriverByName

---
    CanDriver *getDriverByName(QString driverName)

返回指定名称的Can驱动。如果不存在则返回0。

### getInterfaceByDriverAndName

---
    CanInterface *getInterfaceByDriverAndName(QString driverName, QString deviceName)

在指定名称的driver中查找指定名称的Interface,并返回其名称。如果不存在则返回0。

### loadDbc

---
    pCanDb loadDbc(QString filename)

从指定的dbc数据库中加载数据并返回。

### clearLog

---
    void clearLog()

清除日志模型(LogModel)中的所有日志。

### getLogModel

---
    LogModel &getLogModel() const

返回私有成员变量_logModel指向的内存地址的内容。

