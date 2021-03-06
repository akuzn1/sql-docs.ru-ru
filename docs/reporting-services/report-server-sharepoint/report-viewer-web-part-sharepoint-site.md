---
title: Веб-часть "Средство просмотра отчетов" на сайте SharePoint (SSRS) | Документы Майкрософт
ms.date: 11/15/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c849ec1ee515263b54b4931be59780ab5bf8ae75
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52415751"
---
# <a name="report-viewer-web-part-on-a-sharepoint-site---reporting-services"></a>Веб-часть "Средство просмотра отчетов" на сайте SharePoint (службы Reporting Services)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)]  [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2016-2019](../../includes/ssrs-appliesto-sharepoint-2016-2019.md)] [!INCLUDE[ssrs-appliesto-not-sharepoint-online](../../includes/ssrs-appliesto-not-sharepoint-online.md)]

Веб-часть средства просмотра отчетов является настраиваемой. Она позволяет просматривать, печатать и экспортировать отчеты на сервере отчетов на сайте SharePoint. Веб-часть "Средство просмотра отчетов" связана с расширением файлов определения отчетов (RDL), которые обрабатываются сервером отчетов служб Microsoft SQL Server Reporting Services. 

Новейшая веб-часть средства просмотра отчетов может также работать с отчетами с разбиением на страницы, развернутыми на сервере отчетов Power BI. Веб-часть не поддерживает отчеты Power BI.

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>Причины повторного представления веб-части средства просмотра отчетов

Веб-часть средства просмотра отчетов входила в состав надстройки служб Reporting Services для продуктов SharePoint. Она была предназначена для серверов отчетов в режиме интеграции с SharePoint. После выхода SQL Server 2016 режим интеграции с SharePoint был объявлен устаревшим.

Начиная с SQL Server 2017, существует только один режим установки для служб Reporting Services: **собственный режим**. С помощью веб-части средства просмотра страниц можно внедрить все типы отчетов. Для этого следует использовать параметр URL-адреса *rs:Embed=true*. Внедрение отчетов в страницы SharePoint — это процесс интеграции, который был необходим клиентам, а обновленная веб-часть средства просмотра отчетов поддерживает реализацию этой возможности для отчетов с разбиением на страницы.

Несмотря на то, что веб-часть средства просмотра отчетов вполне подходит для внедрения отчета с разбиением на страницы на страницу SharePoint, обновленная веб-часть средства просмотра отчетов предлагает дополнительные функции.

* Отображение или скрытие определенных кнопок панели инструментов
* Переопределение значений параметров отчета
* Подключение веб-частей фильтра к параметрам отчета

## <a name="download-the-report-viewer-web-part-solution-package"></a>Скачивание пакета решения веб-части "Средство просмотра отчетов"

Веб-часть "Средство просмотра отчетов" доступна в Центре загрузки Майкрософт.

[Скачать пакет решения веб-части "Средство просмотра отчетов"](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>Рекомендации и ограничения

Перечисленные ниже пункты относятся к обновленной веб-части средства просмотра отчетов.

* Веб-часть можно использовать только на *классических* страницах SharePoint.
* Для внедрения в веб-часть средства просмотра отчетов поддерживаются только отчеты с разбиением на страницы (RDL). Чтобы внедрить отчеты Power BI или мобильные отчеты, можно использовать параметр URL-адреса *rs:Embed=true*.

## <a name="next-steps"></a>Следующие шаги

Сведения о начале работы с обновленной веб-частью средства просмотра отчетов см. в статье [Развертывание веб-части средства просмотра отчетов на сайте SharePoint](deploy-report-viewer-web-part.md).
