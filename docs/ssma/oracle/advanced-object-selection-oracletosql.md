---
title: "Расширенный выбор объектов (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c978fba4-c953-4ed0-a21d-1b38e7225552
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: v-pelars
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 350b223034355afa675d0a18300028841edeee71
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="advanced-object-selection--oracletosql"></a>Выбор дополнительных объектов (OracleToSQL)
**Расширенный объект раздела** диалоговое окно позволяет отфильтровать объекты базы данных с помощью строки и подстроки в имени объекта, а затем выберите или отмените выделение этих объектов. SSMA выполняет преобразование и миграцию операций на выбранных объектов.  
  
Чтобы открыть это диалоговое окно, щелкните правой кнопкой мыши в обозревателе метаданных и выберите **Расширенный выбор объекта**.  
  
При первом открытии диалоговое окно, нажмите кнопку **Показать элементы подкатегорий** для отображения всех объектов, имеющих метаданные, загруженный в проект. После этого можно вводить строки для фильтрации элементов. Например введите строку «company», чтобы отобразить все элементы, имена которых содержат эту строку.  
  
Прежде чем использовать это диалоговое окно, можно принудительно SSMA для загрузки всех метаданных, преобразование схем или сохранении проекта.  
  
## <a name="options"></a>Параметры  
**Проверьте все элементы**  
Добавляет флажок рядом с пунктами. Эти элементы будут выбираться сразу в обозревателе метаданных.  
  
**Снимите флажки всех элементов**  
Снимает флажок рядом с пунктами. В обозревателе метаданных будет немедленно очистить эти элементы.  
  
**Режим списка**  
Отображение отфильтрованных элементов в списке.  
  
**Режим просмотра таблицы**  
Отображение отфильтрованных элементов в таблице.  
  
**Отображаются только загруженных элементов.**  
Переключение отображения категорий или элементов. При выборе этой кнопки SSMA показывает все элементы, которые соответствуют критериям фильтра и те, которые были ранее загружены. Если эта кнопка не установлен, SSMA показаны папки категории.  
  
**Фильтр**  
Введите строку, которую вы хотите использовать для фильтрации элементов. Например, чтобы найти все доступные элементы, которые содержат строку «ID», в имя элемента, введите строку «ID» в **фильтра** поле.  
  
Если элементы условия фильтра, категории или элементы будут отображаться при вводе строки. Чтобы увидеть совпадающие элементы, рекомендуется нажать кнопку **отображаются только загрузить элементы** кнопки.  
  
**Очистить фильтр**  
Очищает **фильтра** поле.  
  
