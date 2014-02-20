---
layout: post
title:  JMeter 使用入門 HTTP Request 
date:   2010-11-21 23:23:15
categories: java 
tags : [JMeter]
---
JMeter 的功能非常多，這邊以最常見的用途為例 -- http request 測試，說明JMeter的使用方法

- 專案名稱﹕ Apache JMeter
- 官方網站﹕ http://jakarta.apache.org/jmeter/
- 檔案下載﹕ http://apache.stu.edu.tw//jakarta/jmeter/binaries/jakarta-jmeter-2.4.zip

## 安裝啟動

將下載回來的檔案 jakarta-jmeter-2.4.zip 解壓縮，在其中的資料匣bin裡，執行jmeter.bat，就完成軟體的安裝與啟動。

![image](http://4.bp.blogspot.com/_NUW79mJV03k/TOj9vv1hDUI/AAAAAAAACJE/Re2ieoiWqTU/s1600/2010-11-21_190805.jpg)

起始畫面



可以看到畫面上顯示的是中文，對於看慣英文的人，可能有些用語一時會看不懂，如果想改成英文，可以至選單修改﹕



選項 --> 選擇一種語言 --> 英文


基於中文是預設語言，因此接下來的內容用語，還是用軟體的中文用詞為主。

1. 新增執行緒群組

新增執行緒群組的方法為﹕


**功能選單**

編輯 -- 新增 -- Threads (Users) -- 執行緒群組


執行緒群組可視為一個完整測試的基本單位。

![image](http://1.bp.blogspot.com/_NUW79mJV03k/TOkC4VqIfSI/AAAAAAAACJI/hEXHWpU8QWA/s400/2010-11-21_192919.jpg)


畫面上有幾個重要的欄位
執行緒數量﹕ 有多少連線連上
啟動延遲﹕ 一個連線連上多久後，下一個連線才連上
迴圈次數﹕ 執行該連結多少次

2. 新增HTTP要求預設值

首先新增一個HTTP 要求預設值，之後新增的HTTP要求都會以這個預設值為，
因此在這邊先將主機名稱及端口號碼寫好，後續在加入測試時，就不用一個一個填。

3. 新增接聽



**功能選單**
編輯 -- 新增 -- 接聽 -- 檢視表格式結果


接聽的功能是用來查看測試後的結果。

4. 新增HTTP要求


**功能選單**
編輯 -- 新增 -- 取樣 -- HTTP要求


![image](http://4.bp.blogspot.com/_NUW79mJV03k/TOkIkh-K_pI/AAAAAAAACJM/RhSTSHdfcGY/s400/2010-11-21_195114.jpg)


這邊設定的, 就是用來模擬使用者連上網站的連結。
主要的設定是路徑及參數，也可以設定方法是POST或是GET

5. 開始

在開始測試之前，先由左邊的功能列切換到接聽項目，再到上方的功能表點選


**功能選單**
執行 -- 開始


接著, 在右方的畫面就會出現測試結果了

![image](http://2.bp.blogspot.com/_NUW79mJV03k/TOkIy7qmlHI/AAAAAAAACJQ/2chi0_p02Xw/s400/2010-11-21_195536.jpg)

