---
layout: post
title:  Primary Key 
date:   2010-11-20 23:23:15
categories: java 
tags : [database]
---

### Primary Key 產生策略  

Primary Key常見的幾種產生方法，可歸納如下﹕

1.  使用實際意義的值
    
    例如在使用者資料Table使用身份證字號，在國家資料中使用國家名稱縮寫。


2. Primary Key 欄位最大值加一

   在新增一筆資料前，先去查詢該Table目前的Primary Key最大值，取得後加1 做為新資料的Primary Key 值。若發生有二筆資料同時要寫入的情況，會出現Primary Key重覆的錯誤。


3. 由一個 Table 來管控

   在新增一筆資料前，把負責管控編號的 Table 的其中一個欄位值加 1 後取出，做為新資料的 primary key 值，這方法的效能要比上一種方法好，但一樣可能會發生Primary Key重覆的錯誤。


4. 自動編號

   在建立欄位時，直接設定欄位屬性為自動編號，或是像 Oracle 使用 Sequence 搭配 Trigger 來達成一樣的功能。這種方法的好處是編號方法是由資料庫本身在控制，不會出現 Primary Key 重覆的錯誤。


5. 程式編號 - 依據時間

   Java 的 java.util.Date 物件可取得自1970年1月1日到程式執行當時的毫秒數，可利用這個數值來做為資料的 primary key，但在交易頻繁的系統中，還是有出現 primary key 重覆的風險。

6. 程式編號 - UUID

   Java也提供了產生通用唯一識別碼 (Universally Unique Identifier, UUID)的method，UUID不會出現重覆的情況，因此也是Primary Key的好選擇。


### 使用 Natural key 做為 Primary Key

#### 什麼是 Natural Key

Natural Key 指的是使用有意義的欄位值做為Primary Key


#### 使用Natural Key的優點

欄位值容易讀也容易記，也容易維護，此外，通常長度也不會太長，因此還可以節省資料庫空間。


#### 使用Natural Key的缺點

首先當然就是當原先用來建來的意義或規則改變時，欄位值要跟著修改，相關聯的table也要跟著修改，這可是個大工程。

使用Natural Key時，會出現需要用複合鍵當作key的情況，當這種情況出現時, 在設定另一個table的foreign key時, 也得使用多個欄位，同時也會造成在程式中的SQL較複雜。

在網頁應用程式中，常常需要將primary key當作連結網址中的一個參數，此時若primary key是敏感的個人資料時，便出現的資安問題，最常見的就是使用者資料以使用者的身份證字號做為primary key，一不小心，身份證字號就出現在網址列上了。

#### Natural Key的選用時機

1. 適合關聯較少的Table
2. 適合複合鍵較少的Table
3. 適合編碼規則不會改變的Table


### 使用 Surrogate key 做為 Primary Key

#### 什麼是Surrogate key

Surrogate指的是選擇不具意義的欄位值做為Primary key

#### 使用Surrogate key的優點

因為欄位值是沒有實際意義的，所以不會發生因為意義改變而必須跟著改變的情況。

舉例來說，在一個用來記錄使用者個人資料的table，如果使用帳號做為primary key，一旦使用者更換帳號，勢必會牽動許多相關聯的table, 因此這樣設計的系統，都不會充許使用者去更換帳號。相同的情況下，使用surrogate key做為使用者個人資料table的primary key，開發讓使用者更換帳號就不是什麼太困難的事了。

#### 使用Surrogate key的缺點

因為欄位不具意義，某些情況下不易閱讀與記憶。

以剛剛的例子來說，相同的一個記錄使用者個人資料的table，另外再多一個用來記錄使用者所屬公司的Table，兩個Table都使用32位元長度的uuid做為primary key，在一些log機制裡，看到的都是一串32位元長度的亂數，無法一眼就看出這倒底是公司的資料還是做用者的資料，更不用說想要一眼就看出這是哪個使用者或是哪家公司。


#### Surrogate key的選用時機

1. 取代使用多個欄位的複合鍵
2. 取代編碼規則有可能改變的Primary Key
