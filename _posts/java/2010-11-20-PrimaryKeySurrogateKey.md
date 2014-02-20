---
layout: post
title:  Primary Key的選擇 - Surrogate  Key 
date:   2010-11-20 23:23:15
categories: java 
tags : [database]
---
什麼是Surrogate key


Surrogate指的是選擇不具意義的欄位值做為Primary key

使用Surrogate key的優點

因為欄位值是沒有實際意義的，所以不會發生因為意義改變而必須跟著改變的情況。
舉例來說，在一個用來記錄使用者個人資料的table，如果使用帳號做為primary key，一旦使用者更換帳號，勢必會牽動許多相關聯的table, 因此這樣設計的系統，都不會充許使用者去更換帳號。相同的情況下，使用surrogate key做為使用者個人資料table的primary key，開發讓使用者更換帳號就不是什麼太困難的事了。

使用Surrogate key的缺點

因為欄位不具意義，某些情況下不易閱讀與記憶。
以剛剛的例子來說，相同的一個記錄使用者個人資料的table，另外再多一個用來記錄使用者所屬公司的Table，兩個Table都使用32位元長度的uuid做為primary key，在一些log機制裡，看到的都是一串32位元長度的亂數，無法一眼就看出這倒底是公司的資料還是做用者的資料，更不用說想要一眼就看出這是哪個使用者或是哪家公司。


Surrogate key的選用時機

取代使用多個欄位的複合鍵
取代編碼規則有可能改變的Primary Key

