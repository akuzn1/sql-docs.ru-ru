---
title: Перемещение элементов страницы (диспетчер отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: fc83b8d2-bc79-4b56-8970-34a1cbbcc176
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 96d3310c489dea5aadc3e9b7e873dbb89ceee9bb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009689"
---
# <a name="move-items-page-report-manager"></a>Страница «Перемещение элементов» (диспетчер отчетов)
  Используйте страницу «Перемещение элементов», чтобы переместить отчет, папку или другой элемент в новое местоположение на сервере отчетов. Можно ввести путь нового местоположения или использовать представление дерева для указания нового местоположения в пространстве имен сервера отчетов. Переместить можно только те элементы, на перемещение которых есть разрешение и которые хранятся на текущем сервере отчетов.  
  
 При перемещении элемента, на который ссылается другой элемент (например, общего источника данных или модели, на которые ссылаются многие отчеты), сведения о пути к нему обновляются автоматически. Перемещение общего источника данных не разрывает соединения источника данных с использующими его отчетами и моделями. Если общий источник данных или модель перемещается в папку, для которой у пользователя отсутствуют разрешение, он все равно сможет выполнять любые отчеты, ссылающиеся на этот источник данных или модель, хотя этот элемент не будет виден пользователю в иерархии папок.  
  
 Для **Расположения**задайте полный путь к папке, начиная с имени корневой папки. Можно ввести имя пути или использовать представление дерева, чтобы указать нужную папку.  
  
> [!NOTE]  
>  Перемещение возможно не для всех элементов. Нельзя переместить такие зарезервированные папки, как «Корневая папка», «Мои отчеты» или «Папки пользователей». Нельзя переместить журнал отчета или моментальные снимки в другое место. Журнал и моментальные снимки всегда располагаются вместе с отчетом, на котором они основаны. Доступ к ним также осуществляется через этот отчет.  
  
## <a name="navigation"></a>Навигация  
 Чтобы перейти к этому местоположению в пользовательском интерфейсе, используйте следующие процедуры.  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-details-view"></a>Открытие страницы «Перемещение элементов» из страницы «Содержимое» в «Просмотр подробностей»  
  
1.  Откройте диспетчер отчетов и перейдите к папке, содержащей элемент, который нужно переместить. Также можно перемещать элементы с домашней страницы диспетчера отчетов.  
  
2.  На панели инструментов нажмите кнопку **Просмотр подробностей**.  
  
    > [!NOTE]  
    >  Если отображается только **Представление мозаики**, это означает, что текущим местоположением является **Просмотр подробностей**.  
  
3.  Установите флажок рядом с элементом, а затем на панели инструментов щелкните **Переместить** . Можно установить несколько флажков, если необходимо переместить несколько элементов в одно новое местоположение.  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-tiles-view"></a>Открытие страницы «Перемещение элементов» из страницы «Содержимое» в «Представление мозаики»  
  
1.  Откройте диспетчер отчетов и перейдите к папке, содержащей элемент, который нужно переместить. Также можно перемещать элементы с домашней страницы диспетчера отчетов.  
  
2.  На панели инструментов нажмите кнопку **Представление мозаики**.  
  
    > [!NOTE]  
    >  Если отображается только **Просмотр подробностей**, это означает, что текущим местоположением является **Представление мозаики**.  
  
3.  Подведите курсор к элементу и щелкните стрелку раскрывающегося списка.  
  
4.  В раскрывающемся меню выберите **Переместить**.  
  
###### <a name="to-open-the-move-items-page-from-the-general-properties-page-of-an-item"></a>Открытие страницы «Перемещение элементов» из страницы элемента «Общие свойства»  
  
1.  Откройте диспетчер отчетов и перейдите к папке, содержащей элемент, который нужно переместить. Также можно перемещать элементы с домашней страницы диспетчера отчетов.  
  
2.  Подведите курсор к элементу и щелкните стрелку раскрывающегося списка.  
  
3.  В раскрывающемся меню выберите **Управление**. Откроется страница свойств элемента «Общие».  
  
4.  На панели инструментов элемента нажмите кнопку **Переместить**.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Страница «Общие свойства», папки &#40;диспетчера отчетов&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md)   
 [Страница "Общие свойства", "Отчеты" (диспетчер отчетов)](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Страница «Общие свойства», ресурсы &#40;диспетчера отчетов&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md)   
 [Страница общих свойств, общих источников данных &#40;диспетчера отчетов&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md)   
 [Справка F1 диспетчера отчетов](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
