---
layout: post
title:  Spring MVC 的 Exception Resolver
date:   2010-06-05 23:23:15
categories: java 
tags : [Spring, Spring MVC, Exception]
---

如同JSP的ERROR PAGE 或Struts的ExceptionHandler，

Spring MVC也有一套錯誤控制機制，

在處理上，可以分二種方式，

一種是不特別處理，只在錯誤發生時，將頁面導到特定的網頁，

當然，對於不同的Exception，可各自導到不同的頁面。

這邊提供一個例子:

在Spring MVC的設定檔中，宣告如下的設定:


{% highlight xml %}
            
<bean id="viewResolver"
  class="org.springframework.web.servlet. view.InternalResourceViewResolver">
  <property name="prefix">
      <value>/WEB-INF/jsp/</value>
  </property>
  <property name="suffix">
      <value>.jsp</value>
  </property>
</bean>

            
<bean id="exceptionResolver"
  class="org.springframework.web.servlet.handler.SimpleMappingExceptionResolver">    
  <property name="exceptionMappings">
    <props>
        <prop key="java.sql.IOException">
            ioErrorPage
        </prop>    
        <prop key="java.sql.SQLException"> 
            sqlErrorPage        
        </prop>
    </props>
  </property>
</bean>
{% endhighlight %}

當發生IOException的錯誤時，就會導到sqlErrorPage.jsp

發生SQLException的錯誤時，則導到ioErrorPage.jsp。

接著來看另一種處理方式，在發生錯誤時，由自訂的程式去做處理。

 
{% highlight xml %}
<bean class="example.ExceptionResolver">
  <property name="exceptionMappings">
    <props>
      <prop key="org.springframework.transaction.TransactionException">dataAccessFailure</prop>
    </props>
  </property>
  <property name="defaultErrorView" value="errors/general-error" />

</bean>
{% endhighlight %}


在exceptionMappings區塊中所設定的便是Exception所對應的程式

負責處理的主要程式是example.ExceptionResolver，

            
{% highlight java %}
public class ExceptionResolver extends SimpleMappingExceptionResolver {		
    
    protected ModelAndView doResolveException(HttpServletRequest request, 
    HttpServletResponse response, Object handler, Exception ex) {
    
	//處理錯誤
		     
    return super.doResolveException(request, response, handler, ex);
    }
}
{% endhighlight %}

在這支程式裡面，我們就能依照自己的需求，對發生的錯誤加以處理了。


