---
layout: post

title:  在 Eclipse 上安裝 CCCQ 的 plugin 

date:   2010-11-18 23:23:15

categories: java 

tags : [eclipse]

---

CC / CQ指的是 ClearCase / ClearQuest，是 IBM Rational 所開發的版本控制及需求管理軟體，
其client端軟體可以透過plugin的方式，整合在eclipse中，開發人員能很便利的在慣用的開發環境中使用。

 這邊所使用的eclipse版本是由官方網站所提供的 “Eclipse IDE for Java EE Developers” ，

### 安裝GEF

GEF指的是 Graphical Editing Framework ，這是之後要安裝的plugin所需要用到的Framework。
在eclipse 的功能表選單中選擇
    
    Help → Install New Software → Add

![image](http://1.bp.blogspot.com/_NUW79mJV03k/TOVMSCI8lUI/AAAAAAAACJA/XArlTnDLKiA/s320/2010-11-14_014115.jpg)


在出現的對話視窗中輸入:

* Name: GEF
* Location: http://download.eclipse.org/tools/gef/updates/releases/

按下確定並完成安裝。

### 安裝CCRC


CCRC 即 ClearCase Remote Client

重複上述的步驟 ，在eclipse的功能表選單中選擇﹕

    Help → Install New Software → Add

在出現的對話方塊中，輸入

* Name: CCRC
* Location: http://[clearcase server]/ccrc/update

由location可以知道，在ClearCase Server安裝完成之後，就提供了eclipse plugin的下載功能，除此之外，由Server所取回的plugin版本也能確保是相容於Server本身的


