---
layout: post
title:  Oracle 查詢Foreign Key 
date:   2012-03-05 23:23:15
categories: java 
tags : [database,oracle]
---

刪除資料時, 遇到 foreign 的限制而無法刪除時, 可使用 SQL 查詢 Forgin Key 的設定, 查出是卡在哪個table 的哪個欄位, 之後就能找出並刪除了

    select * 
      from ALL_CONS_COLUMNS t1 
     where t1.owner='username'
       and t1.CONSTRAINT_NAME='foreign_key_name';


