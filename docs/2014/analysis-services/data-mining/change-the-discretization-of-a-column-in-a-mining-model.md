---
title: Изменение дискретизации столбца в модели интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d69ba0371f77692f53464cc889ae8204f87d4cd1
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52542351"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>изменить дискретизацию столбца в модели интеллектуального анализа данных
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] автоматически дискретизируют значения — именно, он ячеек данных в числовом столбце в определенных сценариях. Например, если в данных содержатся непрерывные числовые данные и создается модель дерева принятия решений, каждый столбец непрерывных данных автоматически будет сегментирован (в зависимости от распределения данных). Если вам необходимо управлять процессом дискретизации данных, измените свойства столбца структуры интеллектуального анализа данных, управляющие использованием данных в модели.  
  
 Общие сведения о задании свойств в модели интеллектуального анализа данных см. в разделе [Столбцы модели интеллектуального анализа данных](mining-model-columns.md).  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>Отображение свойств столбца модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** в конструкторе интеллектуального анализа данных щелкните правой кнопкой мыши либо заголовок столбца, содержащего имя модели интеллектуального анализа данных, либо строку сетки, содержащую имя алгоритма. Потом выберите **Свойства**.  
  
     В окне **Свойства** отображаются свойства, связанные с моделью интеллектуального анализа данных в целом.  
  
2.  В столбце **Структура** , расположенном на левой стороне экрана, щелкните по столбцу, содержащему подлежащие дискретизации непрерывные числовые данные.  
  
     Окно **Свойства** изменится и будет отображать только те свойства, которые связаны с выбранным столбцом.  
  
### <a name="to-change-the-discretization-method"></a>Изменение метода дискретизации  
  
1.  В **свойства интеллектуального анализа данных** окно, щелкните текстовое поле рядом с полем **содержимого**и выберите `Discretized` из раскрывающегося списка.  
  
     В окне <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> и <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> включены.  
  
2.  В **свойства** окно, щелкните текстовое поле рядом с полем <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> и выберите один из следующих значений: `Automatic`, `EqualAreas`, или `Cluster`.  
  
    > [!NOTE]  
    >  Если использование столбца установлено в значение `Ignore`, **свойства** пустое окно для столбца.  
  
     Новое значение вступает в силу после выбора другого элемента в конструкторе.  
  
3.  На вкладке **Свойства** щелкните по текстовому полю <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> и введите числовое значение.  
  
    > [!NOTE]  
    >  После изменения данных свойств необходимо выполнить повторную обработку структуры и всех моделей, для которых должны действовать новые настройки.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по модели интеллектуального анализа данных](mining-model-tasks-and-how-tos.md)  
  
  
