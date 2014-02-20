---
layout: post
title:  在 eclipse 使用 ant 出現的錯誤訊息 invalid source release 
date:   2010-09-20 23:23:15
categories: java 
tags : [exception]
---
會出現這樣的訊息最主要的原因是ant的javac任務指定了java 版本, 但用來執行ant的jvm版本郤不支援javac任務所指定的版本, 例如jvm版本是1.5, 但javac任務指定了1.6版.
實際來看一下.
在ant的build.xml中一個javac任務如下:

{% highlight xml %}

<javac destdir="${webclasses.dir}" source="1.6" failonerror="true">;     
    <src path="${src.dir}"/>;  
    <classpath refid="master-classpath"/>;     
</javac>;  

{% endhighlight %} 


若eclipse使用的JVM為1.5的情況下, 執行build.xml時,會出現以下的錯誤訊息

<pre>
build:
    [javac] Compiling 425 source files to W:\dist\itschool\WEB-INF\classes
    [javac] javac: invalid source release: 1.6
    [javac] Usage: javac &lt;options&gt; &lt;source files&gt;
    [javac] where possible options include:  
    [javac] Generate all debugging info     
 
BUILD FAILED
</pre>

**解決方法**

解決方法有二個, 一個是變更eclipse使用的JVM版本, 另一個是指定執行build.xml時的JVM版本.
eclipse使用的JVM主要取決於系統的JAVA_HOME設定, 所以只要將JAVA_HOME設定指到JDK 1.6的版本即可, 除了改變JAVA_HOME的設定外, 也可以編輯eclipse.ini, 加入一個啟動參數vm, 再將參數值指到JDK所在的位置, 也能達到相同的效果
-vm 
C:\jdk1.6.0_21\bin\javaw.exe
 
另一個辦法是指定build.xml執行時的JVM版本, 在eclipse中的build.xml檔案上按下滑鼠右鍵, 在顯示的選單上選擇 Run As –&gt; External Tools Configurations
2010-09-20_095545
在出現的畫面中, 選擇JVM的頁籤, 再選擇適合的JVM版本即可.
2010-09-20_101356
