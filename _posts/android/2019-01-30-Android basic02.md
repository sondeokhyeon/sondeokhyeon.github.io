---
layout: post
title : Android Basic02
categories: android
tags: [android]
comments : true
---

**안드로이드 basic02**

### 안드로이드 View02

안드로이드의 화면 배치는 크게 두가지를 사용한다.  
한가지는 Px(Pixel)이 있고 DP(Device Independence Pixel)픽셀은 절대적 크기를 지정할 때 사용한다. (디바이스의 넓이, 높이와는 별도로 컴포넌트가 고정된다.)   
DP는 디바이스의 크기를 대비하여 컴포넌트를 구성한다 (디바이스의 크기와 별도로 비율이 맞춰서 배치된다)

### 안드로이드 View03

viewComponent의 크기는 DP나 PX 뿐만이 아니라 컴포넌트에 따라 크기를 지정하는 방법도 있다.

해당 속성은 아래와 같다

**Contents의 크기만큼 지정**

    android:layout_width  = "wrap_content"
    android:layout_height = "wrap_content"

**부모컴포넌트의 크기만큼 지정**

    android:layout_width  = "match_parent"
    android:layout_width  = "match_parent"


### 안드로이드 View04

ViewComponent를 기획/개발 의도에 맞게 적절히 배치하려면 여백이 필수이다.   
안드로이드에서 여백은 두가지가 있다.   
한가지는 margin 이고 한가지는 padding이다   
(CSS를 다뤄봤다면 이 부분 알것이다.)
margin의 경우에는 부모를 기준으로 여백으로 발생하고   
paddong의 경우에는 컴포넌트 자체가 여백이 발생한다.

- margin 

    android:layout_margin           = "0dp"   
    // 위 아래 좌 우 모두 마진을 줄떄 사용  
    android:layout_marginHorizontal = "0dp"  
    // 좌 우 마진만 줄때 사용    
    android:layout_marginVertical   = "0dp"   
    // 위 아래 마진만 줄때 사용   
    android:layout_marginleft       = "0dp"   
    android:layout_marginright      = "0dp"   
    android:layout_margintop        = "0dp"   
    android:layout_marginbottom     = "0dp"

   > <a href="https://lanace.blogspot.com/2016/12/android-layoutmarginstart.html">Android layout_marginStart와 layout_marginLeft의 차이<a/>   
   (궁금한 사람들은 들어가서 보시길...)   


- padding   

    android:layout_padding           = "0dp"   
    android:layout_paddingHorizontal = "0dp"  
    android:layout_paddingVertical   = "0dp"   
    android:layout_paddingleft       = "0dp"   
    android:layout_paddingright      = "0dp"   
    android:layout_paddingtop        = "0dp"   
    android:layout_paddingbottom     = "0dp"   



