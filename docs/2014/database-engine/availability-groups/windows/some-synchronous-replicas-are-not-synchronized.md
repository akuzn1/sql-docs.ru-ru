---
title: Некоторые синхронные реплики не синхронизированы | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2423a011e75d346d196ebe5ebac2597ac30914a1
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53374706"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>Некоторые синхронные реплики не синхронизированы
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние синхронизации данных синхронных реплик|  
|**Проблема**|Некоторые синхронные реплики не синхронизированы.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|группа доступности|  
  
## <a name="description"></a>Описание  
 Эта политика сворачивает состояние синхронизации данных всех реплик доступности и проверяет наличие реплик доступности, состояние синхронизации которых отличается от ожидаемого. Политика находится в неисправном состоянии, если любая асинхронная реплика не находится в состоянии SYNCHRONIZING, а любая синхронная реплика не находится в состоянии SYNCHRONIZED. Состояние политики исправно при других условиях.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблемы и ее решении доступны в разделе [Некоторые синхронные реплики не синхронизированы](https://go.microsoft.com/fwlink/p/?LinkId=220853) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 В этой группе доступности не синхронизирована по меньшей мере одна реплика доступности. Состоянием синхронизации реплики может быть либо SYNCHONIZING либо NOT SYNCHRONIZING.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте состояние политики реплики доступности для поиска реплики доступности с неверным состоянием синхронизации, после чего устраните неполадку в реплике доступности.  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
