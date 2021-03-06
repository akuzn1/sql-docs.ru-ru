---
title: Страница "кэширование", общие наборы данных (диспетчер отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: eac372e9-d2a1-48a8-bbe5-09d101df16ea
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 65fe3e4979e620b3f49af5def2266c84e77cc616
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56017886"
---
# <a name="caching-page-shared-datasets-report-manager"></a>Страница «Кэширование», «Общие наборы данных» (диспетчер отчетов)
  Страница «Свойства кэширования» используется для задания параметров кэширования общего набора данных.  
  
> [!NOTE]  
>  Эта функция поддерживается не во всех выпусках [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Навигация  
 Чтобы перейти к этому местоположению в пользовательском интерфейсе, используйте следующую процедуру.  
  
### <a name="to-open-the-caching-properties-page-for-a-shared-dataset"></a>Открытие страницы «Свойства кэширования» для общего набора данных  
  
1.  Откройте диспетчер отчетов и найдите отчет, для которого необходимо настроить свойства общего набора данных.  
  
2.  Подведите указатель к общему набору данных и щелкните стрелку раскрывающегося списка.  
  
3.  В раскрывающемся списке выберите **Управление**. Откроется страница свойств отчета «Общие».  
  
4.  Перейдите на вкладку **Кэширование** .  
  
## <a name="options"></a>Параметры  
 **Кэширование общих наборов данных**  
 Помещает временную копию данных в кэш при первом открытии отчета, использующего этот общий набор данных. Следующие пользователи, запускающие этот отчет в период кэширования, получают кэшированную копию данных. Как правило, кэширование позволяет повысить производительность, поскольку вместо повторного выполнения запроса к набору данных возвращаются данные из кэша.  
  
 **Срок действия кэша через несколько минут**  
 Укажите количество минут, в течение которого должна сохраняться кэшированная копия данных. Как только срок действия временной копии истекает, данные из кэша больше не возвращаются. При следующем открытии отчета, использующего общий набор данных, выполняется запрос к нему и сервер отчетов снова помещает копию обновленных данных в кэш.  
  
 **Срок действия кэша по следующему расписанию**  
 Запланируйте момент времени, когда данные кэша станут недействительными и будут удалены из кэша. Расписание может быть общим или заданным только для текущего общего набора данных.  
  
 **Расписание по наборам данных**  
 Укажите расписание, используемое только для этого набора данных.  
  
 **Общее расписание**  
 Укажите расписание, совместно используемое отчетами, подписками и другими общими наборами данных.  
  
 **Применить**  
 Сохраните изменения.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Справка F1 диспетчера отчетов](../../2014/reporting-services/report-manager-f1-help.md)   
 [Общие наборы данных в кэше (службы SSRS)](report-server/cache-shared-datasets-ssrs.md)   
 [Расписания](subscriptions/schedules.md)  
  
  
