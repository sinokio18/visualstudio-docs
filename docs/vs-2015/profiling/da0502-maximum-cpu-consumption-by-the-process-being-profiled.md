---
title: "DA0502: Maximum CPU consumption by the Process being profiled | Microsoft Docs"
ms.custom: ""
ms.date: "2018-06-30"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0502"
  - "vs.performance.DA0502"
  - "vs.performance.502"
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0502: Maximum CPU consumption by the Process being profiled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

The latest version of this topic can be found at [DA0502: Maximum CPU consumption by the Process being profiled](https://docs.microsoft.com/visualstudio/profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled).  
  
Rule Id|DA0502|  
|Category|Resource Monitoring|  
|Profiling method|All|  
|Message|This rule is for information only. The Process()\\% Processor Time counter measures CPU consumption of the process that you are profiling. The value reported is the maximum observed over all measurement intervals.|  
|Rule type|Informational|  
  
 When you profile by using the sampling, .NET memory, or resource contention methods, you must collect at least 10 samples to trigger this rule.  
  
## Rule Description  
 This message reports the maximum percentage of time that a processor was busy executing instructions from the application. The reported value is the maximum value reported among all the measurement intervals in which the process being profiled was active. The percentage can be greater than 100% on a machine with more than one processor.  
  
## How to Use the Rule Data  
 Use the rule value to compare the performance of different versions or builds of the program or to understand the performance of the application under different profiling scenarios.


