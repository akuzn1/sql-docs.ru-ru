---
title: "TODATETIMEOFFSET (Transact-SQL) | Документы Microsoft"
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
- TO_DATETIMEOFFSET_TSQL
- SWITCH_TZ_TSQL
- SWITCH_TZ
- TO_DATETIMEOFFSET
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], TODATETIMEOFFSET
- TODATETIMEOFFSET function
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: b5fafc08-efd4-4a3b-a0b3-068981a0a685
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77d42b2484563d162d78e1caad28389cc26f6cee
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="todatetimeoffset-transact-sql"></a>TODATETIMEOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает **datetimeoffset** значение, которое преобразовывается из **datetime2** выражение.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
TODATETIMEOFFSET ( expression , time_zone )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) , которая разрешается [datetime2](../../t-sql/data-types/datetime2-transact-sql.md) значение.  
  
> [!NOTE]  
>  Выражение не может иметь тип **текст**, **ntext**, или **изображения** , так как эти типы нельзя неявно преобразовать в **varchar** или **nvarchar**.  
  
 *time_zone*  
 Выражение, которое представляет смещение часового пояса в минутах (если это - целое число), например -120, или в часах и минутах (если это - строка), например "+13.00". Диапазон охватывает значения от +14 до -14 (в часах). Выражение приводится к местному времени для указанного часового пояса time_zone.  
  
> [!NOTE]  
>  Если выражение является символьной строкой, оно должно иметь формат {+|-}TZH:THM.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **DateTimeOffset**. Точность в долях секунды совпадает со значением *datetime* аргумент.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-time-zone-offset-of-the-current-date-and-time"></a>A. Изменение смещения часового пояса для текущего значения даты и времени  
 В следующем примере смещение пояса для текущего значения даты и времени изменяется на часовой пояс `-07:00`.  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="b-changing-the-time-zone-offset-in-minutes"></a>Б. Изменение смещения часового пояса в минутах  
 В следующем примере текущий часовой пояс изменяется на `-120` минут.  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="c-adding-a-13-hour-time-zone-offset"></a>В. Добавление 13-часового смещения часового пояса  
 В следующем примере 13-часовое смещение часового пояса добавляется к дате и времени.  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-changing-the-time-zone-offset-of-the-current-date-and-time"></a>Г. Изменение смещения часового пояса для текущего значения даты и времени  
 В следующем примере смещение пояса для текущего значения даты и времени изменяется на часовой пояс `-07:00`.  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="e-changing-the-time-zone-offset-in-minutes"></a>Д. Изменение смещения часового пояса в минутах  
 В следующем примере текущий часовой пояс изменяется на `-120` минут.  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="f-adding-a-13-hour-time-zone-offset"></a>Е. Добавление 13-часового смещения часового пояса  
 В следующем примере 13-часовое смещение часового пояса добавляется к дате и времени.  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="see-also"></a>См. также:  
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Данных даты и времени типы и функции &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [В ЧАСОВОМ ПОЯСЕ &#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  

