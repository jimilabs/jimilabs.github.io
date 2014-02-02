---
layout: post
title:  JSP 的 ERROR PAGE 
date:   2014-01-31 23:23:15
categories: java 
tags : [jsp]
---

ERROR PAGE是JSP中的錯誤控制機制，本篇文章將以一個簡單的範例來說明．

這個範例需要建立三個JSP頁面：

1. form.jsp

2. form_action.jsp

3. error.jsp

在form.jsp裡有一個表單，裡面有個文字欄位，用來輸入一個日期，這邊以"生日"做代表，

原始碼如下：

{% highlight html %}

<%@ page language="java" 
  contentType="text/html; charset=UTF-8"  
  pageEncoding="UTF-8" 
  errorPage="error.jsp" 
%> 
<html> 
   <head> 
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
      <title>Form</title> 
  </head> 
<body> 
    <form action="form_action.jsp" method="post"> 
        <label>生日</label> 
        <input type="text" name="birthday"> 
        <input type="submit"> 
    </form> 
</body> 
</html>

{% endhighlight %}  
 
 

另一個頁面就是處理這個表單的form_action.jsp，負責將使用者輸入的日期拆解出年,月,日.

若使用者沒有正確的輸入資料，那麼在這一頁就會出現exception，

為了掌控這一個頁面可能發生的Exception，我們在jsp的宣告上多加一行：

{% highlight java %}
errorPage="error.jsp"
{% endhighlight %}  

代表當exception出現時，指定由error.jsp這一頁來處理．

這個頁面的原始碼如下：

{% highlight java %}

<%@ page language="java" 
  contentType="text/html; charset=UTF-8"  
  pageEncoding="UTF-8" 
  errorPage="error.jsp" 
%> 
<%@page import="java.text.SimpleDateFormat"%> 
<%@page import="java.util.Date"%> 
<%@page import="java.util.Calendar"%> 
<html> 
  <head> 
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
<title>Insert title here</title> 
  </head> 
<body> 
<%  
  String birthday = request.getParameter("birthday"); 
  SimpleDateFormat sdf = new SimpleDateFormat("yyyyMMdd"); 
  Date birthdayDate = sdf.parse(birthday); 
  Calendar birthdayCal = Calendar.getInstance(); 
  birthdayCal.setTime(birthdayDate); 
%> 
生日: 
  <%=birthdayCal.get(Calendar.YEAR)%>年 
  <%=birthdayCal.get(Calendar.MONTH)+1%>月 
  <%=birthdayCal.get(Calendar.DATE)%>日 
</body> 
</html> 
{% endhighlight %}  

正常運作的畫面:

form.jsp



form_action.jsp


在完全不輸入資料，或是資料格式錯誤時，就會發生exception，然後就會導到error.jsp，

error.jsp與一般JSP頁面最大的不同，是它宣告了 isErrorPage="true"，


而error page所能提供的最明顯的好處是可以美化錯誤畫面，

這邊提供一個範例：

   
{% highlight java %}

<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8" isErrorPage="true" %> 
<html> 
   <head> 
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">  
   </head> 
<body> 

系統出現異常! 

<!-- 
<%= exception.toString() %> 
--> 
</body> 
</html> 

{% endhighlight %}  
   
在這個範例裡，當系統發生exception時，一般的使用者會看到的，是容易理解文字，
甚至還可以留下客服人員的連絡方式，如email或電話．
而工程人員，也可以借由檢視原始檔來查看發生問題的真正原因。
