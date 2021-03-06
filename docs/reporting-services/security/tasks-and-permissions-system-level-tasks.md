---
title: Задачи уровня системы | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f81807777e84d0f05181b25174896e5b4bc2bdd7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835452"
---
# <a name="tasks-and-permissions---system-level-tasks"></a>Задачи и разрешения — задачи на уровне системы
  Задача системного уровня представляет собой коллекцию разрешений, касающихся операций, применяемых ко всему сайту сервера отчетов в целом. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают также задачи уровня элемента, которые относятся к конкретным элементам. Дополнительные сведения см. в разделе [Задачи уровня элемента](../../reporting-services/security/tasks-and-permissions-item-level-tasks.md). Дополнительные сведения о задачах и правах в целом см. в разделе [Tasks and Permissions](../../reporting-services/security/tasks-and-permissions.md).  
  
> [!NOTE]  
>  При работе с такими задачами программно необходимо использовать методы, которые поддерживают задачи системного уровня. Дополнительные сведения см. в разделе <xref:ReportService2010.ReportingService2010.ListTasks%2A> и <xref:ReportService2010.ReportingService2010.ListRoles%2A>.  
  
## <a name="permissions-in-system-level-tasks"></a>Разрешения в задачах системного уровня  
 Следующая таблица указывает совокупность разрешений для каждой системной задачи. Разрешения перечисляются только в справочных целях, чтобы обеспечить более детальное описание функций, доступных с помощью каждой задачи.  
  
|Задача|Разрешения|  
|----------|-----------------|  
|Выполнение определений отчета|Выполнение определений отчетов (имена разрешения и задачи одинаковы)|  
|Создание событий|Создание событий|  
|Управление заданиями|Считывание системных свойств<br /><br /> Обновление системных свойств|  
|Управление свойствами сервера отчетов|Считывание системных свойств<br /><br /> Обновление системных свойств|  
|Управление ролями|Создание ролей<br /><br /> Удаление ролей<br /><br /> Считывание свойств роли<br /><br /> Обновление свойств роли|  
|Управление общими расписаниями|Создание расписаний|  
|Управление безопасностью сервера отчетов|Считывание правил безопасности системы<br /><br /> Обновление правил безопасности системы|  
|Просмотр свойств сервера отчетов|Считывание системных свойств|  
|Просмотр общих расписаний|Считывание расписаний|  
  
## <a name="see-also"></a>См. также:  
 [Предоставление разрешений на сервер отчетов в собственном режиме](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
