---
title: Введение в обработку исключений в службах Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b0415d5344999b61b026ef69879b607220a72031
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014925"
---
# <a name="introducing-exception-handling-in-reporting-services"></a>Знакомство с обработкой исключений в службах Reporting Services
  Если приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] направляет веб-службе сервера отчетов запрос, который эта служба не в состоянии обработать, служба возвращает клиенту исключение SOAP. Обработка исключений, формируемых веб-службой сервера отчетов, играет важную роль в создаваемых разработчиками приложениях, поскольку при возникновении ошибок приложения могут возвращать пользователям важные сведения.  
  
 В этом разделе содержатся конкретные данные, касающиеся обработки исключений, предотвращения ввода пользователями недопустимых значений и возврата пользователям значимых сведений об ошибках. Общие сведения об обработке исключений см. в разделе "Обработка и активизация исключений" документации пакета SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Обработка исключений в службах Reporting Services](handling-exceptions-in-reporting-services.md)|Содержит общие сведения об исключениях в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и о роли SOAP в возврате ошибок веб-служб.|  
|[Рекомендации по обработке исключений в службах Reporting Services](best-practices/best-practices-for-reporting-services-exception-handling.md)|Содержит рекомендации по обработке исключений в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[Класс SoapException в службах Reporting Services](soapexception-class/reporting-services-soapexception-class.md)|Описывает класс **SoapException** в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
