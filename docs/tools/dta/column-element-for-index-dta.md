---
title: Элемент COLUMN описания индекса (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 77972892b2efcac8554f79ea9c41720f9ae40277
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51290820"
---
# <a name="column-element-for-index-dta"></a>Элемент Column описания индекса (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Указывает столбцы, по которым создается индекс для пользовательской конфигурации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
 **Type**: необязательно. Указывает тип столбца индекса. Используйте тип данных **string** для указания этого атрибута при помощи следующих допустимых значений:  
  
-   **KeyColumn**  
  
     Указывает, что на столбец ссылается ключ индекса. Для установки этого атрибута используйте следующий синтаксис:  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     Дополнительные сведения о ключевых столбцах см. в разделе [Описания кластеризованных и некластеризованных индексов](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).  
  
-   **IncludedColumn**  
  
     Указывает, что столбец является включенным (а не ключевым) столбцом. Для установки этого атрибута используйте следующий синтаксис:  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     Дополнительные сведения о включенных столбцах см. в разделе [Создание индексов с включенными столбцами](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
 **SortOrder**: необязательно. Указывает порядок сортировки столбца. Используйте тип данных **string** для указания порядка сортировки **по возрастанию** или **по убыванию** , как показано ниже:  
  
```  
<Column SortOrder="Ascending">  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Для элемента **Index** можно задать не более 1024 столбцов.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Index (DTA)](../../tools/dta/index-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания столбца (DTA)](../../tools/dta/name-element-for-column-dta.md)|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
