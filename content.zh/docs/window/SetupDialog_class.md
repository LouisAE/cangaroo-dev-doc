---
title: SetupDialog类
type: docs
---

# SetupDialog类
此类继承自[QDialog](https://doc.qt.io/qt-5/qdialog.html)类

## 成员函数

---
### 公共成员函数
[bool showSetupDialog(MeasurementSetup &setup)]({{% ref "/docs/window/SetupDialog_class.md#showsetupdialog" %}})

[void addPage(QWidget *widget)]({{% ref "/docs/window/SetupDialog_class.md#addpage" %}})

[void displayPage(QWidget *widget)]({{% ref "/docs/window/SetupDialog_class.md#displaypage" %}})

## 信号

---
[void onShowInterfacePage(SetupDialog &dlg, MeasurementInterface *mi)]({{% ref "/docs/window/SetupDialog_class.md#onshowinterfacepage" %}})

## 槽函数

---
### 公共槽函数
[void treeViewSelectionChanged(const QItemSelection & selected, const QItemSelection & deselected)]({{% ref "/docs/window/SetupDialog_class.md#treeviewselectionchanged" %}})

[void treeViewContextMenu(const QPoint& pos)]({{% ref "/docs/window/SetupDialog_class.md#treeviewcontextmenu" %}})

## 公有成员函数说明

### showSetupDialog

---
    bool showSetupDialog(MeasurementSetup &setup)

被调用时会显示设置窗口

参数：
- setup：MeasurementSetup类的引用

返回值：用户点击确定(ok)按钮关闭窗口返回true，其它情况返回false

### addPage

---
    void addPage(QWidget *widget)

未知（猜测：和显示接口列表的框有关）
观察：程序启动时此函数会被执行多次
### displayPage

---
    void displayPage(QWidget *widget)

未知（猜测：和显示接口列表的框有关）

## 信号说明

---
### onShowInterfacePage
    void onShowInterfacePage(SetupDialog &dlg, MeasurementInterface *mi)
调试过程中未观察到此信号的发出

## 槽函数说明

---
### treeViewSelectionChanged
    void treeViewSelectionChanged(const QItemSelection & selected, const QItemSelection & deselected)
根据传入的两个参数的类型，在窗口右侧显示相应的设置页面。

调试过程中发现：当用户在窗口左侧列表选择项目时会触发此槽函数。

### treeViewContextMenu
    void treeViewContextMenu(const QPoint& pos)
调试过程中未观察到此槽函数的触发。

猜测和窗口显示的位置有关。