---
title: "ГРАДУСОВ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DEGREES
- DEGREES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DEGREES function
- number of degrees
ms.assetid: 5208de3c-90a3-4f59-a7e3-10b01bf285bb
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be6c730a4f7f6a280cd54e0f01b52a5579267c80
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="degrees-transact-sql"></a>DEGREES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает для значения угла в радианах соответствующее значение в градусах.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DEGREES ( numeric_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) точных числовых или приблизительных числовых типа данных, за исключением **бит** тип данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Возвращает тот же тип, что и аргумент *numeric_expression*.  
  
## <a name="examples"></a>Примеры  
 В следующем примере вычисляется значение в градусах, соответствующее PI/2 радиан.  
  
```  
SELECT 'The number of degrees in PI/2 radians is: ' +   
CONVERT(varchar, DEGREES((PI()/2)));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The number of degrees in PI/2 radians is 90         
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере вычисляется значение в градусах, соответствующее PI/2 радиан.  
  
```  
SELECT 'The number of degrees in PI/2 radians is: ' +   
CONVERT(varchar, DEGREES((PI()/2)));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The number of degrees in PI/2 radians is 90         
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

