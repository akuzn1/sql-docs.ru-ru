---
title: sysmergeschemaarticles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergeschemaarticles_TSQL
- sysmergeschemaarticles
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergeschemaarticles system table
ms.assetid: b5085979-2f76-48e1-bf3b-765a84003dd9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 581a6be7472818f983bc82ef3a717be0c0edaa48
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802816"
---
# <a name="sysmergeschemaarticles-transact-sql"></a>sysmergeschemaarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Осуществляет мониторинг статей со схемой для механизма репликации слиянием. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя статьи со схемой в публикации слиянием.|  
|**type**|**tinyint**|Тип статьи со схемой, который может иметь одно из следующих значений:<br /><br /> **0x20** = хранимая процедура статьи схемой.<br /><br /> **0x40** = статьи со схемой представление или индексированное представление статьи со схемой.|  
|**objID**|**int**|Идентификатор базового объекта статьи. Может быть идентификатором процедуры, представления, индексированного представления или определяемой пользователем функции.|  
|**artid**|**uniqueidentifier**|Идентификатор статьи.|  
|**Описание**|**nvarchar(255)**|Описание статьи.|  
|**pre_creation_command**|**tinyint**|Действие по умолчанию, выполняемое при создании статьи в базе данных подписки:<br /><br /> **0 =** none — Если таблица уже существует на подписчике, никакие действия не выполняются.<br /><br /> **1** = Удалить — удаляет таблицу перед ее повторным созданием.<br /><br /> **2** = delete — выполняет удаление предложения WHERE в фильтре подмножества.<br /><br /> **3** = Truncate — аналогично **2**, но вместо строк удаляются страницы. Однако предложение WHERE не используется.|  
|**pubid**|**uniqueidentifier**|Уникальный идентификатор публикации.|  
|**status**|**tinyint**|Состояние статьи со схемой, которое может иметь следующие значения:<br /><br /> **1** = Unsynced — скрипт начальной обработки для публикации таблицы будет выполнен при следующем запуске агента моментальных снимков.<br /><br /> **2** = active — скрипт начальной обработки для публикации таблицы будет выполнено.<br /><br /> **5** = New_inactive — для добавления.<br /><br /> **6** = New_active — для добавления.|  
|**creation_script**|**nvarchar(255)**|Путь и имя необязательного скрипта предварительного создания схемы статьи, используемого для создания целевой таблицы.|  
|**schema_option**|**binary(8)**|Битовая карта параметров формирования схемы для конкретной статьи только для схемы; это значение может быть результатом объединения следующих значений при помощи побитовой логической операции ИЛИ:<br /><br /> **0x00** = запретить использование сценариев агента моментальных снимков и использует предоставленный CreationScript.<br /><br /> **0x01** = формировать инструкции создания объектов (CREATE TABLE, CREATE PROCEDURE и т. д.).<br /><br /> **0x10** = формировать соответствующий кластеризованный индекс.<br /><br /> **0x20** = convert-определяемые пользователем типы данных в базовые типы данных.<br /><br /> **0x40** = формировать соответствующий некластеризованный индекс или индексы.<br /><br /> **0x80** = включить для первичных ключей объявления ссылочной целостности.<br /><br /> **0x100** = реплицировать пользовательские триггеры для статьи таблицы, в том случае, если они определены.<br /><br /> **0x200** = реплицировать ограничения внешнего ключа. Если таблица, указанная в ссылке, не является частью публикации, все ограничения внешнего ключа по опубликованной таблице не реплицируются.<br /><br /> **0x400** = реплицировать ограничения check.<br /><br /> **0x800** = реплицировать значения по умолчанию.<br /><br /> **0x1000** = реплицировать параметры сортировки на уровне столбцов.<br /><br /> **0x2000** = реплицировать расширенные свойства, связанные с исходным объектом опубликованной статьи.<br /><br /> **0x4000** = реплицировать уникальные ключи, если они определены для статьи таблицы.<br /><br /> **0x8000** = реплицировать первичный ключ и уникальные ключи в таблице статьи как ограничения при помощи инструкции ALTER TABLE.<br /><br /> Дополнительные сведения о возможных значениях **schema_option**, см. в разделе [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**destination_object**|**sysname**|Имя целевого объекта в базе данных подписки. Это значение применяется только к статьям со схемой, таким как хранимые процедуры, представления и пользовательские функции.|  
|**destination_owner**|**sysname**|Владелец объекта в базе данных подписки, если это не **dbo**.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
