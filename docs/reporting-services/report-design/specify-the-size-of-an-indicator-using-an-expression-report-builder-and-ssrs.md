---
title: Указание размера индикатора с помощью выражения (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5a6ded6b52da2105d324ba835f6a747eb024f97a
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56298632"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a>Указание размера индикатора с помощью выражения (построитель отчетов и службы SSRS)
  Помимо цвета, направления и формы, для изменения визуального представления индикатора можно использовать его размер.  
  
 У индикатора есть коллекция состояний индикатора IndicatorStates. Коллекция IndicatorStates обычно имеет несколько состояний. Каждое состояние является частью коллекции и представляется значком. Вместе состояния представляют собой коллекцию IndicatorStates.  
  
 Для динамической настройки размера значков надо задать свойства элементов коллекции IndicatorStates на панели "Свойства" в построителе отчетов. Если панель **Свойства** не отображается, перейдите на вкладку **Вид** и выберите пункт **Свойства**.  
  
> [!NOTE]  
>  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]окно **Свойства** используется для установки свойств элемента. Если окно **Свойства** не открыто, нажмите клавишу F4.  
  
 Панель **Свойства** предоставляет доступ к свойствам коллекции IndicatorStates индикатора. Разные размеры значков задаются установкой свойства ScaleFactor коллекции IndicatorStates с помощью выражения. Дополнительные сведения см. в разделе [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
 Выражение, используемое для этой процедуры, также применяется для создания отчетов с разными размерами индикаторов, как показано в разделе [Индикаторы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a>Указание размера значка индикатора с помощью выражения  
  
1.  Щелкните индикатор, который нужно изменить.  
  
2.  На панели "Свойства" найдите свойство IndicatorStates.  
  
     Если панель "Свойства" организована по категориям, свойство IndicatorStates будет находиться в категории **Состояния** .  
  
3.  Нажмите кнопку с многоточием **(...)** рядом со свойством IndicatorStates. Откроется диалоговое окно **Редактор коллекции состояний индикатора** .  
  
     Выберите все элементы коллекции.  
  
4.  В списке **Выбор нескольких свойств** щелкните стрелку вниз рядом со свойством ScaleFactor и выберите **Выражение**.  
  
5.  В диалоговом окне **Выражение** введите выражение.  
  
     В следующем образце выражения размер значка изменяется в зависимости от значения поля **Продажи за год на дату** .  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     Дополнительные сведения см. в разделе [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Индикаторы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  
