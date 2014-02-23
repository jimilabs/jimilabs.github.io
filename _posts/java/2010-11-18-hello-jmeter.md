---
layout: post
title:  JMeter 簡介 
date:   2010-11-18 23:23:15
categories: java 
tags : [JMeter]
---

### 簡介

![image](http://jakarta.apache.org/jmeter/images/logo.jpg)


許多的系統會有效能上的要求，舉凡網頁在多少時間內要完成載入、同時上線人數，或是某個特定功能的回應速度。對系統進行這方面的測試就稱為壓力測試，而 JMeter 就是一套免費並且是open source的壓力測試軟體。

JMeter 是屬於 Apache Software Foundation 所開發及維謢的專案， 相關資訊如下﹕

* 專案名稱﹕Apache JMeter
* 官方網站﹕http://jakarta.apache.org/jmeter/

JMeter 所能進行的測試項目有﹕

* HTTP
* HTTPS
* SOAP
* Database
* LDAP
* JMS
* POP3
* IMAP

一般系統會使用到的協定都含蓋了。

在測試過程，JMeter提供了圖形化的界面，使得開發人員可以很清楚的知道每個測試頁面的測試結果，另一個好用的功能是可以使用錄制腳本的方式，對步驟較多的功能進行一個完整操作流程的測試。

#### 取得 JMeter

可至官網取得下載的相關頁面及學, 或是透過 這個連結 下載JMeter 2.4版。

#### 安裝 JMeter

下載回來的檔案，會是一個壓縮檔，將它解壓縮到系統磁碟內即完成安裝。

#### 執行 JMeter

在JMeter的安裝資料匣內，還有個bin的資料匣，在裡面有個可執行檔 jmeter.bat，執行後出現以下的畫面，就表示軟體啟動成功了。


通常，在系統上線前，開發人員才會對系統進行壓力測試，其實，若能在開發階段就一邊開發，一邊壓力測試，更能早點發現系統效能的瓶頸，也能及早修正，會是更好的做法。

