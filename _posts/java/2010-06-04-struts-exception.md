---
layout: post
title:  Struts 的 ExceptionHandler 
date:   2010-06-04 23:23:15
categories: java 
tags : [struts, Exception]
---

在Struts中有一種類似JSP error page的錯誤處理機制，
使用方法一如Struts一般的設定方式，定義在組態檔struts-config.xml中。
Struts可以為任一個action特別設定各自的錯誤處理方式,
也可以設定統一的錯誤處理方式。

## 統一設定於 global-exceptions

在 struts-config.xml 中加入一塊 global-exceptions 的區塊，就能定義當出現某種特定的 exception 時，該由哪一個錯誤控制程式處理,
以及要導到哪一頁去。
這邊以 java.lang.Exception 為例，因為所有 exception 偕是繼承它而來，所以只要設定了這一項，
就能補抓下所有的Exception。

範例如下:

{% highlight xml %}

<global-exceptions>
<exception key="errors.token" 
       type="java.lang.Exception"  
       path="/error.jsp" 
       handler="example.ActionExceptionHandler" />
</global-exceptions>

{% endhighlight %}

 
type 指的就是這一個錯誤控制項目所要欄截處理的 Exception，
path 用來設定使用者最後看到的頁面，
handler 設定負責處理的程式。

example.ActionExceptionHandler 這支程式的原始碼如下:

{% highlight xml %}
          
public final class ActionExceptionHandler extends ExceptionHandler {
    public ActionForward execute(Exception ex, 
                                 ExceptionConfig ae,
                                 ActionMapping mapping,
                                 ActionForm formInstance,
                                 HttpServletRequest request,
                                 HttpServletResponse response)
        throws ServletException {
        
        ActionErrors errors = (ActionErrors) request.getAttribute(Globals.ERROR_KEY);
        
        //處理errors
            
        ActionForward forward =
            super.execute(ex, ae, mapping, formInstance, request, response);          
        return forward;
    }
}

{% endhighlight %}

在ActionExceptionHandler中,能取得ActionErrors，也能決定forward的目的地， 我們就能依照需求去量身打造各種不冋的錯誤處理方式。

## 個別設定

個別設定的設定方式與統一設定很接近，只是在struts設定檔中的位置不同而已。

{% highlight xml %}
.
.
<action  path="/test"  
         type="example.TestAction"      
         name="testForm">      
    <exception key="test.failure" path="test.jsp" type="Example.TestException"/> 
    <forward  name="success"          path="/success.jsp"/>
</action>
.
.
{% endhighlight %}


