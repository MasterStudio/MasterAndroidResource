# 概述

## 资源结构

- Android 系统资源结构如下：(参考 [Google官方介绍](https://developer.android.google.cn/guide/topics/resources/providing-resources.html?hl=zh-cn) )
  ```text
  res/
  ├─ anim/      -> 定义 渐变动画的 XML 文件（属性动画也可以保存在此目录中，但是为了区分这两种类型，属性动画首选 animator/ 目录）
  ├─ animator/  -> 定义 属性动画的 XML 文件
  ├─ color/     -> 用于定义 颜色状态列表的 XML 文件
  ├─ drawable/  -> 用于定义 位图文件(.png、.9.png、.jpg、.gif) 或 可编译为图像资源的 XML 文件
  ├─ layout/    -> 用于定义 界面布局的 XML 文件
  ├─ menu/      -> 用于定义 应用菜单（如选项菜单、上下文菜单或子菜单）的 XML 文件
  ├─ mipmap/    -> 适用于不同启动器图标密度的可绘制对象文件
  ├─ raw/       -> 要以 原始形式保存的任意文件
  ├─ values/    -> 包含字符串、整型数和颜色等简单值的 XML 文件
  └─ xml/       -> 各种 XML 配置文件都必须保存在此处
  ```
  `res/` 下的文件夹为 **官方定义** 的资源文件夹，名字不能随意更改
- `anim/` 下 XML资源 的结构：
  ```xml
  ROOT
  ├─ <alpha>
  ├─ <rotate>
  ├─ <scale>
  ├─ <translate>
  ├─ <*Interpolator>
  ├─ <*Animation>
  └─ <set>
      ├─ <alpha>
      ├─ <rotate>
      ├─ <scale>
      ├─ <translate>
      └─ <set>
  ```
- `animator/` 下 XML资源 的结构：
  ```xml
  ROOT
  ├─ <animator>
  │   └─ <propertyValuesHolder>
  ├─ <objectAnimator>
  │   └─ <propertyValuesHolder>
  ├─ <selector>
  │   └─ <item android:animation="" android:state_xxx="true/false" />
  └─ <set>
      ├─ <animator>
      ├─ <objectAnimator>
      ├─ <propertyValuesHolder>
      └─ <set>
  ```
- `color/` 下 XML资源 的结构：
  ```xml
  ROOT
  └─ <selector>
      └─ <item android:color="" android:state_xxx="true/false" />
  ```
- `drawable/` 下 XML资源 的结构：
  ```xml
  ROOT
  ├─ <animated-rotate>
  │   └─ ROOT
  ├─ <animated-selector>
  │   ├─ <transition>
  │   │   └─ <animation-list>
  │   └─ <item android:drawable="" android:state_xxx="true/false" />
  ├─ <animated-vector>
  │   └─ <target />
  ├─ <animation-list>
  │   └─ <item android:drawable="" android:duration="" />
  ├─ <bitmap> <color> <nine-patch>
  ├─ <clip> <inset> <rotate> <scale>
  │   └─ ROOT
  ├─ <layer-list> <ripple> <transition>
  │   └─ <item android:drawable="" [width/height][direction][gravity] />
  ├─ <level-list>
  │   └─ <item android:drawable="" android:maxLevel="" android:minLevel=""/>
  ├─ <selector>
  │   └─ <item android:drawable="" android:state_xxx="true/false" />
  ├─ <shape>
  │   ├─ <corners />
  │   ├─ <gradient />
  │   ├─ <padding />
  │   ├─ <size />
  │   ├─ <solid />
  │   └─ <stroke />
  └─ <vector>
      ├─ <clip-path />
      ├─ <path />
      └─ <group>
          ├─ <clip-path />
          ├─ <path />
          └─ <group>
  ```
- `layout/` 下 XML资源 的结构：
  ```xml
  ROOT
  ├─ <[View] />
  ├─ <[ViewGroup]>
  │   ├─ <include>
  │   └─ ROOT
  ├─ <layout>
  │   ├─ <[View] />
  │   ├─ <[ViewGroup]>
  │   └─ <data>
  ├─ <merge>
  │   ├─ <[View] />
  │   ├─ <[ViewGroup]>
  │   ├─ <fragment>
  │   ├─ <include>
  │   └─ <view>
  ├─ <fragment class="" [id][fragmentXX][layout_XX] ...>
  │   ├─ <[View] />
  │   └─ <[ViewGroup]>
  └─ <view>
      ├─ <[View] />
      ├─ <[ViewGroup]>
      ├─ <fragment>
      ├─ <include>
      └─ <view>
  ```
- `menu/` 下 XML资源 的结构：
  ```xml
  ROOT
  └─ <menu>
      ├─ <group>       -> menu组
      │   └─ <item />
      └─ <item />      -> menu项
  ```
- `values/` 下 XML资源 的结构：
  ```xml
  ROOT
  └─ <resources>
      ├─ <array>              -> 任意类型的数组（TypedArray）
      ├─ <boolean>            -> 布尔值
      ├─ <color>              -> 十六进制颜色值
      ├─ <declare-styleable>  -> 声明自定义属性
      ├─ <dimension>          -> 尺寸值
      ├─ <fraction>           -> 相对比例值
      ├─ <item type="id"/>    -> 预定义ID
      ├─ <integer>            -> 整数值
      ├─ <integer-array>      -> 整数数组
      ├─ <plurals>            -> 复数字符串
      ├─ <string>             -> 字符串
      ├─ <string-array>       -> 字符数组
      └─ <style>              -> 样式
  ```
- `xml/` 下 XML资源 的结构：
  ```xml
  ROOT
  ├─ <account-authenticator />
  ├─ <appwidget-provider />
  ├─ <device-admin>
  │   └─ <uses-policies>
  │         ├─ <disable-camera />
  │         ├─ ...
  │         └─ <wipe-data />
  ├─ <preference-headers>
  │   └─ <header>
  │         ├─ <extra />
  │         └─ <intent />
  ├─ <searchable>
  │   └─ <actionkey />
  ├─ <Keyboard>
  │   └─ <Row>
  │         └─ <Key />
  ├─ <Preference> <PreferenceCategory> <PreferenceScreen>
  │   └─ <*Preference*>
  ├─ <MultiSelectListPreference>
  │   └─ <*Preference*>
  └─ <CheckBoxPreference> <EditTextPreference> <ListPreference> <RingtonePreference> <SwitchPreference>
      ├─ <extra />
      ├─ <intent />
      └─ <*Preference*>
  ```