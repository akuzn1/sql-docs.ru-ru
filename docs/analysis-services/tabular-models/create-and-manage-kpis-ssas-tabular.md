---
title: Создание и управление ключевыми показателями эффективности в табличных моделях служб Analysis Services | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ae17e727367b702967ec879ed8469973ab3b812
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072091"
---
# <a name="create-and-manage-kpis"></a>Создание и управление ключевыми показателями эффективности 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  В этой статье описывается создание, изменение или удаление ключевого показателя Эффективности (ключевой показатель эффективности) в табличной модели. Чтобы создать ключевой показатель Эффективности, выберите меру, результатом которого является значение базового ключевого показателя Эффективности. Затем в диалоговом окне «Ключевой показатель эффективности» необходимо выбрать вторую меру или абсолютное значение, на основании которого будет вычисляться целевое значение. Затем можно определить пороговые значения состояний, которые определяют эффективность между базовой и целевой мерами.  
  
## <a name="tasks"></a>Задания  
  
> [!IMPORTANT]  
>  Перед тем как создать ключевой показатель эффективности, необходимо создать базовую меру, оценивающую значение. Затем базовую меру можно расширить до ключевого показателя эффективности. Описываются способы создания меры в другом разделе [Создание и управление меры](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md). Для KPI необходимо целевое значение. В качестве этого значения можно использовать другую, определенную ранее меру или абсолютное значение. После расширения базовой меры до KPI можно выбрать целевое значение и определить пороги состояния в диалоговом окне ключевого показателя эффективности.  
  
###  <a name="bkmk_create_KPI"></a> Создание ключевого показателя эффективности  
  
1.  В сетке мер щелкните правой кнопкой мыши меру, которая будет являться базовой (значение), а затем выберите пункт **Создать ключевой показатель эффективности**.  
  
2.  В диалоговом окне **Ключевой показатель эффективности** в поле **Определение целевого значения**выберите одно из следующих значений.  
  
     Выберите пункт **Мера**, а затем выберите целевую меру из списка.  
  
     Выберите **Абсолютное значение**и введите числовое значение.  
  
3.  В окне **Определение состояния порогов**установите значения нижнего и верхнего порогов.  
  
4.  В окне **Выбор стиля значка**выберите тип изображения.  
  
5.  Нажмите кнопку **Описания**и введите описания для ключевого показателя эффективности, «Значения», «Состояния» и «Цели».  
  
> [!TIP]  
>  Проверить ключевой показатель эффективности можно с помощью функции анализа в Microsoft Excel. Дополнительные сведения см. в разделе [анализ в Excel](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
###  <a name="bkmk_edit_KPI"></a> Изменение ключевого показателя эффективности  
  
-   В сетке мер щелкните правой кнопкой мыши меру, являющуюся базовой мерой (значением) ключевого показателя эффективности, и выберите пункт **Изменить параметры ключевого показателя эффективности**.  
  
###  <a name="bkmk_delete"></a> Удаление ключевого показателя эффективности и базовой меры  
  
-   В сетке мер щелкните правой кнопкой мыши меру, являющуюся базовой мерой (значением) ключевого показателя эффективности, и выберите пункт **Удалить**.  
  
###  <a name="bkmk_delete_KPI"></a> Удаление ключевого показателя эффективности с сохранением базовой меры  
  
-   В сетке мер щелкните правой кнопкой мыши меру, являющуюся базовой мерой (значением) ключевого показателя эффективности, и выберите пункт **Удалить ключевой показатель эффективности**.  
  
## <a name="alt-shortcuts"></a>Сочетания клавиш с ALT  
  
|Раздел пользовательского интерфейса|Команда клавиши|  
|----------------|-----------------|  
|Базовая мера ключевого показателя эффективности|ALT+B|  
|Состояние ключевого показателя эффективности|ALT + S|  
|Measure|ALT+M|  
|Абсолютное значение|ALT + A|  
|Определение состояния порогов|ALT+U|  
|Выбор стиля значка|ALT+I|  
|Тренд|ALT+T|  
|Описания|ALT+D|  
|Тренд|ALT+T|  
  
## <a name="see-also"></a>См. также  
 [Ключевые показатели эффективности](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [меры](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [Создание и managemeasures](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)  
  
  
