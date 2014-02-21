---
layout: post
title:  Struts 2 簡介 
date:   2010-11-20 23:23:15
categories: java 
tags : [Framework,Struts2]
---

Struts 2 是一個基於MVC模型的Web Framework。聽到Struts 2這個名字，很自然的會和Struts 1聯想在一起，事實上，Struts 1 和 Struts 2 是完全不一樣的框架。Struts 2的前身是名為WebWork 2 的Web Framework，在早期是個非常受到開發人員喜愛的架構，許多人甚至認為它比Struts更加優秀。後來為了結合兩邊社群的力量，同時也為了開發出個集各家所長的框架，因此就有了Struts 2。

一開始發行的Struts 2版本，可說是將WebWork 2的程式碼改了package名稱而己，隨著版本的演進才慢慢有了不同

Struts 2 的特點


Action可以完全是一個POJO , 不用繼承任何的class, 提高了程式碼重覆使用的可能性。它也提供了一些基本的Action類別，可以加速開發的速度。

每個請求都會產一個新的Action實例，因此是thread safe的。在Struts 1, 則是所有來自client端的請求都由同一個Action實例來負責，在不小心的情況下, 會讓所有用戶共用變數，而出現A用戶看到B用戶資料的情況。

Action不需倚賴Servlet API, 所以Struts 2 的Action 可以在Servlet Container的環境之外運作。換句話說，要執行一個Action不需要啟動Tomcat, 也不用輸入一串網址去觸發一個Action，這個特性使得測試可以很容易進行。雖然如此，Struts 2的Action還是提供了取得原始HttpServletRequest及HttpServletResponse的方法。

String 2 直接由Action接收參數, 比起Struts 1的Action 加上 Form Bean的組合更簡潔。

String 2 更提供了欄截器, 可以在進入Actoin前或離開Action後, 去執行一些動作。在Struts 2 本身就己經提供了很多的欄截器可直接使用，例如檔案上傳、國際化、logger機制、計時功能等等，除此之外，更能註冊開發人員自行撰寫的欄截器，例如可以拿來驗證身份權限。

總結

Struts 2 在許多方面都非常優秀，對放一個專案的開發速度或維護成本，都有幫助。
