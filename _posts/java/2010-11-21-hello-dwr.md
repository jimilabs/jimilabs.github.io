---
layout: post
title:  DWR 簡介
date:   2010-11-21 23:23:15
categories: java 
tags : [DWR]
---

DWR是一種AJAX的Java實作，除了可以簡化AJAX的使用外，最特別的地方在於開發人員能夠經由DWR直接使用頁面上的JavaScript呼叫Java程式中的method。

* 專案名稱﹕ Direct Web Remoting ( DWR )
* 官方網站﹕ http://directwebremoting.org/dwr/

**AJAX簡介**

非同步JavaScript和XML(Asynchronous JavaScript and XML, AJAX)，是一種建立互動式網頁的技術。對使用者來說，最大的好處是在不用更新整個頁面的情況下，擔獨更新頁面裡的部份內容，由於只更新了部份內容，因此也節省了網路頻寬的使用，最大的缺點則是無法使用瀏覽器的後退功能。AJAX並不是一個新技術，但在Google的gamil大量使用ajax後, 才流行起來。


### 簡介

![image](http://directwebremoting.org/dwr/media/howitworks.png)

上面的圖片說明的是DWR是如何被使用的。

DWR的運作包含了二個部份

1. Client端的JavaScript
    - 截取每個client向server的請求
    - 重新包裝產生JavaScript的參數物件
    - 根據client端的環境，生成最佳化的JavaScript
    - 將Server處理完成的結果回傳給Client


2. Server端的Servlet
    - 負責DWR的初始配置
    - 對Server請求的單一入口
    - 分發請求
    - 輸出執行結果
    

### 安裝設定

* 專案名稱﹕ Direct Web Remoting
* 官方網站﹕ http://directwebremoting.org/dwr/

#### 取得dwr.jar

首先要做的，是到 DWR 的下載頁面將 dwr.jar 下載回來

* 下載頁面﹕ http://directwebremoting.org/dwr/downloads/index.html
* 直接下載﹕ https://dwr.dev.java.net/files/documents/2427/126494/dwr.jar

目前在下載頁可以看到二個 DWR 版本，一個是 3.rc1 , 另一個 2.0.6。 因為3.rc1 目前是屬於還在開發中的版本，因此建議大家下載2.0.6的版本。

下載回來的 dwr.jar，要放置在網站應用程式的\WEB-INF\lib底下

在web.xml加入DwrServlet

編輯web.xml , 在其中加入以下的DWR Servlet設定

{% highlight xml %}

<servlet>
  <servlet-name>dwr-invoker</servlet-name>
  <display-name>DWR Servlet</display-name>
  <servlet-class>org.directwebremoting.servlet.DwrServlet</servlet-class>

  <init-param>
    <param-name>initApplicationScopeCreatorsAtStartup</param-name>
    <param-value>true</param-value>
  </init-param>

  <init-param>
    <param-name>maxWaitAfterWrite</param-name>
    <param-value>-1</param-value>
  </init-param>

  <load-on-startup>1</load-on-startup>
</servlet>

<servlet-mapping>
  <servlet-name>dwr-invoker</servlet-name>
  <url-pattern>/dwr/*</url-pattern>
</servlet-mapping>

{% endhighlight %}

加入 dwr.xml

DWR的運作依賴dwr.xml的設定，因此我們需要在\WEB-INF底下再加入一個dwr.xml
下面是一個簡單的配置範例

{% highlight xml %}

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE dwr PUBLIC 
  "-//GetAhead Limited//DTD Direct Web Remoting 2.0//EN" 
  "http://getahead.org/dwr/dwr20.dtd">
<dwr>
  <allow>
    <create creator="new" javascript="Clock" scope="application">
        <param name="class" value="example.Clock"/>
    </create>
  </allow>
</dwr>

{% endhighlight %}

以上面的設定為例，經過這樣的設定，就能在頁面上透過使用一個名為Clock的JavaScript物件來呼作example.Clock這個Class裡面的method了。    


