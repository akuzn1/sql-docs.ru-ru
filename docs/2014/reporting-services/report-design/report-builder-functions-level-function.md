---
title: Функция Level (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a0eab4c54be4f849a735b7da4de54a9b85cb78f3
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56285312"
---
# <a name="level-function-report-builder-and-ssrs"></a>Функция Level (построитель отчетов и службы SSRS)
  Возвращает текущий уровень глубины в рекурсивной иерархии.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (`String`) (Необязательно) Имя набора данных, группы или области данных, содержащих элементы отчета, к которым применяется агрегатная функция. Если аргумент *scope* не задан, используется текущая область.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает значение типа `Integer`. Если *область* указывает набор данных, область данных или нерекурсивное группирование (т. е группирование имеющее `Parent` элемент), `Level` возвращает 0. Если параметр *scope* не указан, то возвращается уровень текущей области.  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые функцией `Level` значения отсчитываются от нуля, т. е. первым уровнем в иерархии является 0.  
  
 Функция `Level` может использоваться для обеспечения автоматического определения отступов в рекурсивной иерархии, такой как список сотрудников.  
  
 Дополнительные сведения о рекурсивных иерархиях см. в разделе [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода показывает уровень строки в группе «Сотрудники»:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>См. также  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
