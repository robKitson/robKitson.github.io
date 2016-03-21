---
layout: post
title:  "My Error/Exception Handling Philosophy"
date:   2011-10-02 00:00:00 -0800
categories: 
---
Exceptions should be exceptional. They should signal a major problem within the application, or one of it's dependencies. They should be handled in the scope that is as close to the source of the error/exception as possible and only passed on when truly un-handleable. A system that throws a lot of exceptions, when functioning correctly, will make it very difficult to spot actual problems when they arise.

Errors/exceptions should be descriptive and specific.The more (relevant) information you can give me about what's going sideways, the better. I think custom exception classes play a critical role in providing this information. You can load them up with data that's relevant to the error and they can bubble up with that information until they are caught and at that point the the data they're holding can provide hints as to how to fix the problem. If you use the standard errors/exceptions, just changing the message of the exception, you will find yourself doing a lot of string comparison/manipulation in a catch block in order to figure out what the error is, and wether you can handle it.