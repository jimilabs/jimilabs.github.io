---
layout: post
title:  Natural Key 
date:   2010-11-20 23:23:15
categories: java 
tags : [Database]
---

**什麼是 Natural Key**

Natural Key 指的是使用有意義的欄位值做為Primary Key

**使用Natural Key的優點**

欄位值容易讀也容易記，也容易維護，此外，通常長度也不會太長，因此還可以節省資料庫空間。

**使用Natural Key的缺點**

首先當然就是當原先用來建來的意義或規則改變時，欄位值要跟著修改，相關聯的table也要跟著修改，這可是個大工程。

使用Natural Key時，會出現需要用複合鍵當作key的情況，當這種情況出現時, 在設定另一個table的foreign key時, 也得使用多個欄位，同時也會造成在程式中的SQL較複雜。

在網頁應用程式中，常常需要將primary key當作連結網址中的一個參數，此時若primary key是敏感的個人資料時，便出現的資安問題，最常見的就是使用者資料以使用者的身份證字號做為primary key，一不小心，身份證字號就出現在網址列上了。

**Natural Key的選用時機**

適合關聯較少的Table
適合複合鍵較少的Table
適合編碼規則不會改變的Table
