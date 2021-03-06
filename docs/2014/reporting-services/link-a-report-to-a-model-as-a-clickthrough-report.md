---
title: Связывание отчета с моделью, как отчет с дополнительной информацией | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7d0ec49168e4a23a019eb91fc708e286bf0e1ac4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56037045"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a>Связывание отчета с моделью в качестве отчета с дополнительной информацией
  Вместо использования применяемых по умолчанию шаблонов отчетов с дополнительной информацией можно создать отчет в построителе отчетов, а затем установить его связь с конкретной сущностью в модели отчета. Когда пользователь, просматривающий отчет, щелкает мышью интерактивные данные в основном отчете, отчет отображается как отчет с дополнительной информацией. Для установления связи между отчетом и сущностью используется диспетчер отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Первичной, или базовой сущностью, используемой в отчете, должна быть та, с которой отчет связан.  
  
### <a name="to-start-report-manager-from-a-browser"></a>Запуск диспетчера отчетов из браузера  
  
1.  Откройте браузер [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer версии 6.0 или выше.  
  
2.  В адресной строке веб-браузера введите URL-адрес диспетчера отчетов. По умолчанию URL-адрес — http://\<*ComputerName*> / reports.  
  
### <a name="to-create-a-customized-clickthrough-report"></a>Создание пользовательского отчета с дополнительной информацией  
  
1.  Перейдите к модели отчета, к которой нужно добавить пользовательский отчет с дополнительной информацией.  
  
2.  Дважды щелкните эту модель.  
  
3.  Выберите **Дополнительная информация**.  
  
4.  Выберите сущность, к которой нужно присоединить пользовательский отчет с дополнительной информацией.  
  
    > [!NOTE]  
    >  Выбранная сущность должна быть базовой для пользовательского отчета с дополнительной информацией.  
  
5.  Для просмотра пользовательского отчета нужно выбрать один экземпляр выбранной сущности и нажать кнопку **Обзор** для одного экземпляра отчета.  
  
     -или-  
  
     Для просмотра пользовательского отчета нужно выбрать несколько экземпляров выбранной сущности и нажать кнопку **Обзор** для нескольких экземпляров отчета.  
  
6.  Выберите отчет, а затем нажмите **ОК**.  
  
7.  Нажмите кнопку **Применить**.  
  
## <a name="see-also"></a>См. также  
 [Отчеты с дополнительной информацией &#40;SSRS&#41;](reports/clickthrough-reports-ssrs.md)  
  
  
