---
layout: post
title:  Primary Key的產生方式 
date:   2010-11-20 23:23:15
categories: java 
tags : [database]
---

Primary Key常見的幾種產生方法，可歸納如下﹕

1.  使用實際意義的值
    
    例如在使用者資料Table使用身份證字號，在國家資料中使用國家名稱縮寫。

2. Primary Key欄位最大值加一

    在新增一筆資料前，先去查詢該Table目前的Primary Key最大值，取得後加1 做為新資料的Primary Key 值。若發生有二筆資料同時要寫入的情況，會出現Primary Key重覆的錯誤。

3. 由一個專門的Table來管控

    在新增一筆資料前，把負責管控編號的Table的其中一個欄位值加1後取出，做為新資料的primary key值，這方法的效能要比上一種方法好，但一樣可能會發生Primary Key重覆的錯誤。

4. 自動編號

    在建立欄位時，直接設定欄位屬性為自動編號，或是像Oracle使用Sequence搭配Trigger來達成一樣的功能。這種方法的好處是編號方法是由資料庫本身在控制，不太容易會出現Primary Key重覆的錯誤。

5. 程式編號 - 依據時間

    Java的java.util.Date物件可取得自1970年1月1日到程式執行當時的毫秒數，可利用這個數值來做為資料的primary key，但在交易頻繁的系統中，還是有出現primary key重覆的風險。

6. 程式編號 - UUID

    Java也提供了產生通用唯一識別碼 (Universally Unique Identifier, UUID)的method，UUID不太可能會出現重覆的情況，因此也是Primary Key的好選擇。

### 後記

除了上述的六種方式外，還有許多產生primary key的方法，每一種方式都有它的優缺點，也因此，在什麼情況下，選擇哪一種方式，才是這個主題真正的課題。

