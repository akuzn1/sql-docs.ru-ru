---
title: "Набор строк DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 3e514715-9fe6-4e6a-accb-4149ffd7e0bf
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8fd3bd96766ad26c21813f137f8f12452932dea7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>Набор строк DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS
  Предоставляет сведения на уровне столбцов и сегментов о таблицах хранилища, используемых в базе данных служб Analysis Services, работающей в табличном или [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] режиме. Этот набор строк используется главным образом для анализа и устранения неполадок.  
  
 **Применимо к:** табличные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS** набор строк содержит следующие столбцы.  
  
|**Имя столбца**|**Индикатор типа**|**Ограничение**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|**ИМЯ_БАЗЫ_ДАННЫХ**|**DBTYPE_WSTR**|Да|Указывает табличную базу данных.<br /><br /> **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS** строк может быть ограничен с помощью этого столбца. Если отсутствует, используется текущая база данных.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Да|Имя модели.<br /><br /> С помощью этого столбца можно ограничить набор строк **DISCOVER_STORAGE_TABLES** .|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Да|Имя группы мер.|  
|**ИМЯ_РАЗДЕЛА**|**DBTYPE_WSTR**|Да|Имя секции.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Имя измерения.|  
|**TABLE_ID**|**DBTYPE_WSTR**||Внутренний идентификатор сегмента таблицы.|  
|**ИДЕНТИФИКАТОР COLUMN_ID**|**DBTYPE_WSTR**||Внутренний идентификатор столбца.|  
|**СЕГМЕНТ _ЧИСЛО**|**DBTYPE_I8**||Порядковый номер сегмента в таблице.|  
|**TABLE_PARTTION_NUMBER**|**DBTYPE_I8**||Порядковый номер секции.|  
|**RECORDS_COUNT**|**DBTYPE_I8**||Количество записей в секции.|  
|**ALLOCATED_SIZE**|**DBTYPE_UI8**||Размер в байтах, выделенный сегменту столбцов.|  
|**USED_SIZE**|**DBTYPE_UI8**||Размер в байтах, используемый сегментом столбцов.|  
|**COMPRESSION_TYPE**|**DBTYPE_WSTR**||Тип сжатия, примененный к сегменту столбца. Это значение предназначено только для внутреннего использования и поддержки пользователей. Корпорация Майкрософт не публикует действительные значения или описания для этого столбца.|  
|**BITS_COUNT**|**DBTYPE_I8**||Число битов.|  
|**BOOKMARK_BITS_COUNT**|**DBTYPE_I8**||Число битов закладки.|  
|**VERTIPAQ_STATE**|**DBTYPE_WSTR**||Состояние сжатия VertiPaq для этого сегмента столбца. Значение может быть одним из следующих:<br /><br /> SKIPPED — сжатие VertiPaq пропущено.<br /><br /> COMPLETED — сжатие VertiPaq выполнено успешно.<br /><br /> TIMEBOXED — для сжатия VertiPaq задано ограничение по времени.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd45-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageSegments|  
  
## <a name="example"></a>Пример  
 Следующий запрос возвращает сегменты таблицы хранилища, связанные с атрибутом модели LastName, в текущей базе данных.  
  
```  
SELECT DISTINCT TABLE_ID, COLUMN_ID   
FROM $system.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS  
WHERE COLUMN_ID = 'LastName'  
ORDER BY TABLE_ID  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services наборы строк схемы](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  