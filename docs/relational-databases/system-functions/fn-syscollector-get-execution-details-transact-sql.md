---
title: fn_syscollector_get_execution_details (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_syscollector_get_execution_details_TSQL
- fn_syscollector_get_execution_details
dev_langs:
- TSQL
helpviewer_keywords:
- fn_syscollector_get_execution_details function
ms.assetid: d59ddf0c-72c0-4c57-bc83-aef260e4e105
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 032b424c0ac7706962d17520b47d6b8ec447a536
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845164"
---
# <a name="fnsyscollectorgetexecutiondetails-transact-sql"></a>fn_syscollector_get_execution_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает записи журнала служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] (sysssislog), совпадающие с идентификатором package_execution_id для данного пакета. Таблица содержит одну строку для каждой записи журнала, сформированной пакетами или их задачами и контейнерами во время выполнения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_syscollector_get_execution_details ( log_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *log_id*  
 Локальный уникальный идентификатор для журнала выполнения. *log_id* — **int**.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**int**|Уникальный идентификатор для записи журнала.|  
|event|**sysname**|Имя события, которое сформировало запись журнала.|  
|computer|**nvarchar**|Компьютер, на котором был запущен пакет, когда была сформирована запись журнала.|  
|оператор|**nvarchar**|Имя пользователя или агента, запустившего пакет, который сформировал запись журнала.|  
|источник|**nvarchar**|Имя исполняемого объекта, который сформировал запись журнала.|  
|sourceid|**uniqueidentifier**|Идентификатор GUID исполняемого объекта, который сформировал запись журнала.|  
|executionid|**uniqueidentifier**|Идентификатор GUID экземпляра выполнения исполняемого объекта, который сформировал запись журнала.|  
|starttime|**datetime**|Время начала выполнения пакета.|  
|endtime|**datetime**|Время завершения выполнения пакета.|  
|datacode|**int**|Целочисленное значение, которое указывает на событие, связанное с записью журнала. Значение 0 указывает, что событие не передало идентификатор.|  
|databytes|**image**|Массив байтов, который указывает на возвращаемое значение.|  
|message|**nvarchar**|Описание события и сведения, связанные с событием.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для **dc_operator**.  
  
## <a name="see-also"></a>См. также  
 [Включение средств ведения журналов в SQL Server Data Tools](../../integration-services/performance/integration-services-ssis-logging.md#server_logging)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
