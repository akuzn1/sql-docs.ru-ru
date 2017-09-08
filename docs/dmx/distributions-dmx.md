---
title: "Распределения (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- column distributions [DMX]
- distributions [DMX]
- DMX [Analysis Services], distributions
- Data Mining Extensions [Analysis Services], distributions
ms.assetid: cfbb9f38-ae71-401e-867f-15c6a2b6fb97
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 85d01b1e2637b938d093fce3b4cfcc5c1f99abda
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="distributions-dmx"></a>Распределения (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], можно определить содержимое столбцов в структуре интеллектуального анализа данных влияет на то, как алгоритмы обрабатывают данные в этих столбцах при создании моделей интеллектуального анализа данных. В некоторых алгоритмах лучше задавать распределение для всех столбцов, содержащих непрерывные данные, до начала обработки модели в случае, если указанные столбцы содержат общие распределения значений. Если распределения не заданы, создаваемые модели интеллектуального анализа данных могут работать менее точно, чем модели с заданными распределениями, так как на вход алгоритмов будет подаваться меньшее количество данных для анализа.  
  
 Алгоритмы интеллектуального анализа данных [!INCLUDE[msCoName](../includes/msconame-md.md)] могут работать с данными следующих типов:  
  
 **ОБЫЧНЫЙ**  
 На основе значений столбца, содержащего непрерывные данные, может быть построена гистограмма с нормальным Гауссовским распределением.  
  
 **Логарифмическое нормальное**  
 На основе значений столбца, содержащего непрерывные данные, может быть построена гистограмма с нормально распределенной функцией логарифма значений.  
  
 **УНИВЕРСАЛЬНЫЙ**  
 На основе значений столбца непрерывных данных может быть сформирована плоская кривая, на которой все значения являются равновероятными.  
  
 Дополнительные сведения о [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмов интеллектуального анализа данных в разделе [алгоритмов интеллектуального анализа данных &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41; ](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md). Алгоритмы интеллектуального анализа данных третьих поставщиков могут также иметь возможность работы с другими типами распределений. Чтобы определить, какие типы распределения алгоритм поддерживает, используйте **SUPPORTED_DISTRIBUTION_FLAGS** набора строк схемы.  
  
 Дополнительные сведения о типах распределения см. в разделе [распределения столбцов &#40; интеллектуального анализа данных &#41;](../analysis-services/data-mining/column-distributions-data-mining.md).  
  
## <a name="see-also"></a>См. также:  
 [Содержимого типы &#40; интеллектуального анализа данных &#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использовании прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Основные сведения об инструкции расширений интеллектуального анализа данных Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
