---
title: Измерение положения точки останова | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0e1525b5210d94f4a1a9f219a757daa893731f5d
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53328354"
---
# <a name="edit-a-breakpoint-location"></a>Изменение положения точки останова
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Положение точки останова задает строку и символ, где находится точка останова в файле скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] . Положение точки останова можно изменить и перенести точку останова в другое место в скрипте или в другой скрипт.  
  
## <a name="editing-a-location"></a>Изменение положения  
 При изменении положения точки останова она перемещается в новое место вместе со всеми существующими свойствами, такими как число попаданий или условие.  
  
#### <a name="to-edit-a-breakpoint-location"></a>Изменение положения точки останова  
  
1.  В окне редактора щелкните метку точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Положение** .  
  
     -или-  
  
     В окне **Точки останова** щелкните метку точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Положение** .  
  
2.  В диалоговом окне **Точка останова в файле** в поле **Файл** укажите новый файл, в поле **Строка** укажите новую строку, а в поле **Символ** укажите новое расположение в строке. Если новый указанный файл уже открыт в окне редактора запросов, точка останова перемещается в это окно редактора. Если файл не открыт, открывается новое окно редактора, в него загружается указанный файл и точка останова перемещается в новое расположение.  
  
     При отладке **параметр** Разрешить наличие отличий в исходном коде от первоначальной версии [!INCLUDE[tsql](../../includes/tsql-md.md)]не учитывается.  
  
## <a name="see-also"></a>См. также:  
 [Настройка счетчика числа попаданий](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Задание действия в точке останова](../../relational-databases/scripting/specify-a-breakpoint-action.md)   
 [Задание условия точки останова](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Задание фильтра точек останова](../../relational-databases/scripting/specify-a-breakpoint-filter.md)  
