---
title: Разработка безопасных приложений (Reporting Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d2e6e4ea444a243baf06b96448621d4f189d5efa
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027065"
---
# <a name="secure-development-reporting-services"></a>Разработка безопасных приложений (службы Reporting Services)
  Платформа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] обеспечивает надежную систему безопасности, которая может выполнять код в строго определенных рамках заданного администратором контекста безопасности. Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] используют систему безопасности платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], известную как защита доступа к коду (или защита доступа на основе признаков). Если в защите доступа доступа к коду пользователю предоставлен доверенный доступ к ресурсу, но выполняемый пользователем код не является доверенным, то доступ к ресурсу будет запрещен.  
  
 Система безопасности, основанная на коде, в противоположность отдельным пользователям, позволяет распространять правила безопасности на пользовательские сборки или модули данных, доставки, подготовки к просмотру и безопасности, создаваемые разработчиками для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Модуль может выполняться любым количеством пользователей служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], которые были неизвестны на этапе разработки. Пользовательским сборкам или модулям необходимы конкретные политики безопасности служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Эти политики безопасности представлены в платформе [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] как типы. Дополнительные сведения о защите доступа к коду см. в разделе «Защита доступа к коду» в документации по платформе [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
 [Управление доступом для кода в службах Reporting Services](code-access-security-in-reporting-services.md)  
 Основы защиты доступа к коду и настройка политики для пользовательских сборок и модулей в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Основные сведения о политиках безопасности](understanding-security-policies.md)  
 Описание различных типов сборок в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и влияние защиты доступа к коду на разрешения кода.  
  
 [Использование файлов политики безопасности служб Reporting Services](using-reporting-services-security-policy-files.md)  
 Описание различных компонент служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и соответствующих файлов конфигурации политик.  
  
  
