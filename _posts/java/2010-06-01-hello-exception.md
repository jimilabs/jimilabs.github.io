---
layout: post
title:  異常處理 上
date:   2010-06-01 23:23:15
categories: java 
tags : [Exception]
---


異常處理是Java語言一個重要的特性，在實作上也不可避免的需要去處理, 運用．因此也就有了充分了解的必要．

當程式發生異常時，就會進入異常控制流，這是一種類似goto語法的機制，會讓程式的流程進入到以下三種情況之一：

catch區塊
finally區塊
呼叫端
catch區塊

Java語言提供了try - catch的語法來讓開發人員處理異常，當我們使用try - catch將一段可能會丟出Exception的程式碼包起來後，當異常發生時，就會進入catch區塊．


    public void test1() { 
        try { 
            test2(); 
        } catch (Exception e) { 
            // 異常處理 
        }  
    } 
 
    public void test2() throws Exception{ 
        throw new Exception("test2"); 
    } 


### finally 區塊


有二種情況會進入finally區塊

**第一種： 先經過catch區塊，再進入finally**

ex.

    public void test1() { 
        try { 
            test2(); 
        } catch (Exception e) { 
            // 異常處理 
        } finally { 
           // 異常處理  
        }  
    } 
 
    public void test2() throws Exception{ 
        throw new Exception("test2"); 
    } 


**第二種：直接進入finally**

ex.

    public void test1() throws Exception {
        try { 
            test2(); 
        } finally { 
            // 異常處理  
        }  
    } 
 
    public void test2() throws Exception{ 
        throw new Exception("test2"); 
    } 


呼叫端

    public void test1() throws Exception { 
        test2(); 
    } 

    public void test2() throws Exception{ 
        throw new Exception("test2"); 
    } 


以上是當異常發生時，程式的流向，也是我們能處理異常的三個地方．


### 二種處理方式：

1. 補捉下來，並處理。

2. 不補捉，丟給呼叫端處理。

3. 補捉下來，再拋出一個新的異常。

ex. 

    public void test1() { 
        try { 
            test2(); 
        } catch (Exception e) { 
            throw new MyException(); 
        }  
    } 
 
    public void test2() throws Exception{ 
        throw new Exception("test2"); 
    } 


這麼做的好處是：

將 Jav a的異常類別，轉換為系統面的異常，會有助於在發生問題時的除錯。
也可在自訂的異常類別中，封裝異常處理的程序，例如：log
 
