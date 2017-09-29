---
title: "REPLICATE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REPLICATE_TSQL
- REPLICATE
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], repeating
- REPLICATE function
- repeating character expressions
ms.assetid: 0cd467fb-3f22-471a-892c-0039d9f7fa1a
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d2260073409ce6d7b558c65f2528f63423fdf1eb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="replicate-transact-sql"></a>REPLICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Повторяет значение строки указанное число раз.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
REPLICATE ( string_expression ,integer_expression )   
```  
  
## <a name="arguments"></a>Аргументы  
 *String_Expression*  
 Выражение символьной строки или типа данных binary. *String_Expression* может быть символьных или двоичных данных.  
  
> [!NOTE]  
>  Если *string_expression* не относится к типу **varchar(max)** или **nvarchar(max)**, REPLICATE усекает возвращаемое значение до 8000 байт. Для возврата значений, превышающих 8 000 байт *string_expression* должен быть явно приведен к типу данных соответствующего больших значений.  
  
 *integer_expression*  
 Выражение любого целочисленного типа, включая **bigint**. Если *integer_expression* имеет отрицательное значение, возвращается значение NULL.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает тот же тип как *string_expression*.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-replicate"></a>A. Использование функции REPLICATE  
 В следующем примере производится четырехкратная репликация символа `0` в начале рабочей строки кода в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT [Name]  
, REPLICATE('0', 4) + [ProductLine] AS 'Line Code'  
FROM [Production].[Product]  
WHERE [ProductLine] = 'T'  
ORDER BY [Name];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Name                                               Line Code  
-------------------------------------------------- ---------  
HL Touring Frame - Blue, 46                        0000T   
HL Touring Frame - Blue, 50                        0000T   
HL Touring Frame - Blue, 54                        0000T   
HL Touring Frame - Blue, 60                        0000T   
HL Touring Frame - Yellow, 46                      0000T   
HL Touring Frame - Yellow, 50                      0000T  
...  
```  
  
### <a name="b-using-replicate-and-datalength"></a>Б. Использование функций REPLICATE и DATALENGTH  
 В следующем примере числа дополняются слева до указанной длины, как будто они были преобразованы из числового типа данных в символьный или Юникод.  
  
```  
IF EXISTS(SELECT name FROM sys.tables  
      WHERE name = 't1')  
   DROP TABLE t1;  
GO  
CREATE TABLE t1   
(  
 c1 varchar(3),  
 c2 char(3)  
);  
GO  
INSERT INTO t1 VALUES ('2', '2'), ('37', '37'),('597', '597');  
GO  
SELECT REPLICATE('0', 3 - DATALENGTH(c1)) + c1 AS 'Varchar Column',  
       REPLICATE('0', 3 - DATALENGTH(c2)) + c2 AS 'Char Column'  
FROM t1;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
Varchar Column        Char Column  
--------------------  ------------  
002                   2    
037                   37   
597                   597  
  
(3 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-replicate"></a>C: использование функции REPLICATE  
 Этот пример реплицирует `0` символ четыре раза на переднем плане `ItemCode` значение.  
  
```  
-- Uses AdventureWorks  
  
SELECT EnglishProductName AS Name,  
   ProductAlternateKey AS ItemCode,  
   REPLICATE('0', 4) + ProductAlternateKey AS FullItemCode  
FROM dbo.DimProduct  
ORDER BY Name;  
```  
  
 Ниже приведены первых строк в результирующем наборе.  
  
 `Name                     ItemCode       FullItemCode`  
  
 `------------------------ -------------- ---------------`  
  
 `Adjustable Race          AR-5381        0000AR-5381`  
  
 `All-Purpose Bike Stand   ST-1401        0000ST-1401`  
  
 `AWC Logo Cap             CA-1098        0000CA-1098`  
  
 `AWC Logo Cap             CA-1098        0000CA-1098`  
  
 `AWC Logo Cap             CA-1098        0000CA-1098`  
  
 `BB Ball Bearing          BE-2349        0000BE-2349`  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

