# 窗口设计

## MDI窗体

把一些子窗体，全部排到父窗体中。

### 步骤

1. 首先确定一个父窗体。 将父窗体的`IsMdiContainer`属性设置为true。
2. 创建子窗体，并且使用`MdiParent`属性设置他们的父窗体。MdiParent = 父窗体对象。

### 拓展

- 设置子窗口的排列。`LayoutMdi(MdiLayout。枚举类型)`;

