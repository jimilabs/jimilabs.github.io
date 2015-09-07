---
layout: post
title:  log4j.properties 
date:   2012-08-08 23:23:15
categories: java 
tags : [log4j]
---

雖然用很久了, 但要建立一個新的log4j設定檔時, 還是會需要重新搜尋一些相關資料, 所以還是寫一篇備查

{% highlight xml %}

log4j.rootLogger=INFO, stdout 

# 標準輸出
log4j.appender.stdout=org.apache.log4j.ConsoleAppender

# stdout uses PatternLayout.
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%d{ABSOLUTE} %-5p %c:%L %M - %m%n

# 檔案輸出
log4j.appender.file=org.apache.log4j.DailyRollingFileAppender
log4j.appender.file.File=/logs/edm.log
log4j.appender.file.DatePattern='.' yyyy-MM-dd
log4j.appender.file.layout=org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern=%d{ABSOLUTE} %-5p %c:%L %M - %m%n
log4j.logger.jimilabs=DEBUG

{% endhighlight %} 

