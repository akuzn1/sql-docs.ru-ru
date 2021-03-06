---
title: Ограничение строк (мастер секционирования) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.typefilterexpression.f1
ms.assetid: eec8da8f-eab4-4ac4-a81d-995c814f88ca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b86cfeedd76af51b5f9d8cc4633c73ed9cc17ea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131714"
---
# <a name="restrict-rows-partition-wizard"></a>Ограничение строк (мастер секционирования)
  Используйте страницу **Ограничение на строки** для ограничения строк, которые будут извлечены из указанной таблицы, затем агрегированы и включены в секцию.  
  
> [!NOTE]  
>  Эта страница появляется только в случае, когда пользователем была выбрана сводная таблица на странице **Определение исходных сведений** .  
  
> [!CAUTION]  
>  Если задана таблица в разделе **Доступные таблицы** на странице **Определение исходных сведений** , которая используется другой секцией, необходимо задать запрос на странице **Ограничение на строки** или существует риск получить дублирующиеся данные в кубе.  
  
## <a name="options"></a>Параметры  
 **Укажите запрос для ограничения строк**  
 Выберите, чтобы ввести запрос, который ограничивает строки, в поле **Запрос** .  
  
 Если поле **Ввести предложение WHERE** пусто, в момент, когда этот параметр выбран, параметр заполняется инструкцией SQL, которая извлекает все столбцы и строки из предварительно выбранной таблицы.  
  
 **Запрос**  
 Введите или измените инструкцию SQL, используемую во время извлечения строк из таблицы в процессе обработки секции.  
  
> [!IMPORTANT]  
>  Указав предложение WHERE, для этой секции можно использовать вложенный набор записей. Данное действие необходимо во избежание дублирования данных в случае, если несколько параллельных секций функционируют с помощью единственной таблицы фактов.  
  
 **Проверить**  
 Проверка того, что инструкция в поле **Запрос** является корректной инструкцией SQL.  
  
## <a name="see-also"></a>См. также  
 [Секции &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
