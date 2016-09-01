---
layout:     post
title:      "SQL server deadlock"
subtitle:   " \"\""
date:       2016-08-30 12:00:00
author:     "damonluffy"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - SQL Server
---

> “”



use the below sql to find the deadlock:

select    
    request_session_id spid,   
    OBJECT_NAME(resource_associated_entity_id) tableName    
from    
    sys.dm_tran_locks   
where    
    resource_type='OBJECT'

 

then kill spid.

 

Sometimes, the deadlock is caused by the connections created by SQL studio management. you need to close all these connections.
