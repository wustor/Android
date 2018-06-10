
#### 四周牵引

```
layout_constraintLeft_toLeftOf: 将目标控件的左侧牵引到另外一个控件的左侧
layout_constraintRight_toLeftOf: 将目标控件的右侧牵引到另外一个控件的左侧
layout_constraintLeft_toRightOf: 将目标控件的左侧牵引到另外一个控件的右侧
layout_constraintRight_toRightOf: 将目标控件的右侧牵引到另外一个控件的右侧
layout_constraintTop_toTopOf: 将目标控件的上侧牵引到另外一个控件的上侧
layout_constraintTop_toBottomOf: 将目标控件的上侧牵引到另外一个控件的下侧
layout_constraintBottom_toTopOf: 将目标控件的下侧牵引到另外一个控件的上侧
layout_constraintBottom_toBottomOf:将目标控件的下侧牵引到另外一个控件的下侧
```

#### 基线对齐

```
layout_constrainBaseline_toBaselineOf:与目标控件的基线对齐
start，end类（与left,right类似）
layout_constrainStart_toEndOf:将目标控件的左侧与另一控件的右侧对齐
layout_constrainStart_toStartOf：将目标控件的左侧与另一控件的左侧对齐
layout_constrainEnd_toStartOf：将目标控件的右侧与另一控件的左侧对齐
layout_constrainEnd_toEndOf：将目标控件的右侧与另一控件的右侧对齐
```


#### 布局边距

```
layout_marginStart:左边距
layout_marginEnd:右边距
layout_marginLeft:左边距
layout_marginRight:右边距
layout_marginLeft:左边距
layout_marginTop:上边距
layout_marginBottom:下边距
```


#### 基准线（guideline）

```
orientation:vertical/horizontal  基准线的方向
layout_constrainGuide_begin:基准线起点
layout_constrainGuide_end:基准线终点
layout_constrainGuide_percent:基准线百分比模式，用于指定位置
```


#### 牵引力

```
layout_constrainHorizontal_bias:水平方向上的牵引力
layout_constrainVertical_bias:垂直方向上的牵引力
```


#### 链样式（ChainStyle）
当几个控件互相牵引，组成一个链时，此时我们可以对该链的布局进行一些调整，类似flexbox的属性： 
常见的属性有：spread, packed, spread_inside

#### layout_constrainHorizontal_chainStyle:水平方向上的样式
layout_constrainVertical_chainStyle:垂直方向上的样子

套用官网的示例： 
chain styles
![权重](https://developer.android.google.cn/reference/android/support/constraint/resources/images/chains-styles.png)
链权重
同样的，当几个控件组成链时，可以像LinearLayout一样，对其设置权重分布，调节大小


```
layout_constrainVertical_weight:设置该控件在链中的权重
```

#### 宽高属性
ConstrainLayout的宽高属性与普通的布局有所不同，其属性分为三种：wrap_content，具体数值，match_contraint。其中前两种和其他布局类似，当宽高属性设置为match_contraint时，其xml属性显示为：0dp，表现属性为布满约束的区域。

与此同时，ConstrainLayout还支持一种比例的属性：

layout_constrainDimensionRatio:"w,13:2"/"h, 23:23",其中w,h可以不注明， 默认为宽高比
constraintDimensionRatio
这个属性就是把一个View的尺寸设为特定的宽高比，比如设置一张图片的宽高比为 1：1，4：3， 16：9 等。通过使用ConstraintLayout，只需使用layout_constraintDimensionRatio属性即可。


```
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/constraintLayout"
    tools:context="com.constraintlayout.app.MainActivity"
    >

    <ImageView
        android:id="@+id/cat_image"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintDimensionRatio="4:3"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintHorizontal_bias="0"
        android:src="@mipmap/cat"
        />

    <ImageView
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:src="@mipmap/ic_launcher"
        app:layout_constraintDimensionRatio="4:3"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/cat_image"
        app:layout_constraintVertical_bias="0.0"
        app:layout_constraintRight_toRightOf="parent" />

</android.support.constraint.ConstraintLayout>
```


