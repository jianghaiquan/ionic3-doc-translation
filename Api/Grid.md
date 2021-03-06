# Grid #

 `ion-grid, [ion-grid]`

栅格是一个构建自定义布局的强大的移动端优先的 flexbox 系统。它深受 [Bootstrap 栅格系统](http://v4-alpha.getbootstrap.com/layout/grid/) 的影响。

栅格由三个单元组成 —— 一个 栅格、行（多行）和列（多列）。列将会扩展填满它所在的行，并且为了适应其他的列，将会调整大小。栅格建立在 12 列布局之上。列的数量和断点可以使用 Sass 进行完全的定制。

- [它如何工作的](#1)
- [栅格尺寸](#2)
- [栅格属性](#3)
- [默认的断点](#4)
- [自动列布局](#5)
 - [宽度相等](#5.1)
 - [设置一列的宽度](#5.2)
 - [可变的宽度](#5.3)
- [响应式属性](#6)
 - [所有的断点](#6.1)
 - [水平堆放](#6.2)
- [重排序](#7)
 - [Offsetting columns](#7.1)
 - [Push and pull](#7.3)
- [对齐](#8)
 - [垂直对齐](#8.1)
 - [水平对齐](#8.2)
- [定制栅格](#9)
 - [列的数量和padding](#9.1)
 - [Grid tiers](#9.1)

### 它如何工作的？ ###
栅格是可以一个由任意数量的行、列组成的移动端优先的系统。它是由 flexbox 建立的，flexbox 使它具有响应式的特点。栅格可以写成一个元素 （`<ion-grid>`），或者可以任何元素添加一个属性（`<div ion-row>`）。
