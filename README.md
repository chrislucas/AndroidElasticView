# AndroidElasticView [![Build Status](https://travis-ci.org/whilu/AndroidElasticView.svg)](https://travis-ci.org/whilu/AndroidElasticView)
弹性View，像IOS中的效果。

## 开始使用
### 引入库
#### Gradle
```groovy
dependencies {
    compile 'co.lujun:androidelasticview:1.0.9'
}
```

#### 本地导入androidelasticview使用
######1、导入androidelasticview
######2、在Project下的settings.gradle中添加`include ':androidelasticview'`
######3、使用该库的Module/build.gradle中dependencies语句添加`compile project(':androidelasticview')`

### 使用
命名空间：xmlns:app="http://schemas.android.com/apk/res-auto"
提供两个自定义属性：
* `app:elastic_factor` (弹性因子，float类型，所有View都可以使用)
* `app:anim_duration` (回弹时间，integer类型，仅供ElasticScrollView使用，其他无效)

ElasticListView
```xml
<co.lujun.androidelasticview.ElasticListView
    android:id="@+id/listview"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:elastic_factor="0.5" />
```
```java
ElasticListView listView;
// 获取偏移量， type：0-下拉，1-上拉； offset-偏移量
listView.setOffsetChangeListener(new OnOffsetChangedListener() {
    @Override
    public void onOffsetChanged(int type, int offset) {
        Log.d(TAG, "type=" + type + ", offset=" + offset);
    }
});
// 容错处理抽取数目
listView.setErrorContainerNum(3);
// 获取列表滑动方向， isScrollToUp-true（手势向上滑）-false（手势向下滑）
listView.setScrollDirectionListener(new OnDirectionChangedListener() {
    @Override
    public void onDirectionChanged(boolean isScrollToUp) {
        Log.d(TAG, "isScrollToUp=" + isScrollToUp);
    }
});
//获取Gesture Fling手势方向
// 0-fling top, 1-fling bottom, 2-fling left, 3-fling right
listView.setGestureChangedListener(new OnGestureChangedListener() {
    @Override
    public void onGestureChanged(int gesture) {
        Log.d(TAG, "gesture=" + gesture);
    }
});
// 按下拉动过程中是否放开
listView.isUp();
```
ElasticScrollView
```xml
<co.lujun.androidelasticview.ElasticScrollView
    android:id="@+id/scrollview"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:elastic_factor="0.5"
    app:anim_duration="300">
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">
        <!-- child view-->

        <!-- end child view-->
    </LinearLayout>
</co.lujun.androidelasticview.ElasticScrollView>
```
ElasticRecycleView(Deprecated)

## SAMPLE
[sample apk下载](/sample/sample-release.apk)

## About
[ElasticScrollView原文实现方式(Android上实现仿IOS弹性ScrollView)](http://www.2cto.com/kf/201402/279066.html)

有任何问题，[email me](mailto:lujunat1993@gmail.com).

## License
Copyright (c) 2015 [lujun](http://lujun.co)

Licensed under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)