---
title: Отображение предполагаемого плана выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- zoom [SQL Server]
- estimated execution plan [SQL Server]
- displaying execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
- customizing execution plan display [SQL Server]
- modifying execution plan display
- custom zoom [SQL Server]
ms.assetid: e94aa576-4c0c-4c54-ad05-6c3432cc615b
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6f5f10a0a0fb1ce80ad8d6bc5018362669e7f26b
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53373006"
---
# <a name="display-the-estimated-execution-plan"></a>Отображение предполагаемого плана выполнения
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе описано создание графических предполагаемых планов выполнения с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. При создании расчетных планов выполнения запросы и пакеты [!INCLUDE[tsql](../../includes/tsql-md.md)] не выполняются. Поэтому расчетный план выполнения не содержит сведений времени выполнения, таких как фактические метрики использования ресурса и предупреждения времени выполнения. Вместо этого созданный план выполнения отображает наиболее вероятный план выполнения запроса, которому следовал бы компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] при фактическом выполнении запросов, а также отображает расчетное движение строк при выполнении нескольких операторов в плане.  
  
 Для использования этой возможности пользователи должны обладать соответствующими разрешениями на запуск запроса [!INCLUDE[tsql](../../includes/tsql-md.md)] , для которого создается графический план выполнения. Кроме того, пользователям должно быть предоставлено разрешение SHOWPLAN для всех баз данных, упоминаемых в запросе.  
  
## <a name="to-display-the-estimated-execution-plan-for-a-query"></a>Отображение предполагаемого плана выполнения запроса  
  
1.  На панели инструментов нажмите кнопку **Запрос к ядру СУБД**. Можно также нажать на панели инструментов кнопку **Открыть файл** , выбрать существующий запрос и, открыв его, просмотреть предполагаемый план выполнения.  
  
2.  Введите запрос, для которого нужно отобразить предполагаемый план выполнения.  
  
3.  В меню **Запрос** выберите **Показать предполагаемый план выполнения** или нажмите на панели инструментов кнопку **Показать предполагаемый план выполнения** . Предполагаемый план выполнения отображается на вкладке **План выполнения** на панели результатов. 

    ![Кнопка "Предполагаемый план выполнения" на панели инструментов](../../relational-databases/performance/media/estimatedexecplantoolbar.png "Кнопка \"Предполагаемый план выполнения\" на панели инструментов")    

    Для просмотра дополнительных сведений задержите указатель мыши над значками логического и физического оператора и просмотрите описание и свойства оператора в отобразившейся всплывающей подсказке. Также можно просмотреть свойства оператора в окне «Свойства». Если "Свойства" не видны, щелкните оператор правой кнопкой мыши и выберите **Свойства**. Выберите оператор для просмотра его свойств.  

    ![Свойства в меню правой кнопки мыши в операторе плана](../../relational-databases/performance/media/planproperties.png "Свойства в меню правой кнопки мыши в операторе плана")    
  
4.  Чтобы изменить отображение плана выполнения, щелкните правой кнопкой мыши план выполнения и выберите **Увеличить масштаб**, **Уменьшить масштаб**, **Пользовательский масштаб**или **Масштаб по размеру**. Кнопки**Увеличить масштаб** и **Уменьшить масштаб** позволяют увеличить или уменьшить план выполнения на фиксированную величину. **Настраиваемый масштаб** позволяет определить собственное значение, например масштаб в 80 процентов. При использовании пункта**Масштаб по размеру** план выполнения масштабируется до размеров панели результатов. Также можно включить **динамическое масштабирование**, повернув колесико мыши с зажатой клавишей CTRL.  

5.  Для перемещения по изображению плана выполнения используйте вертикальную и горизонтальную полосы прокрутки или **нажмите и удерживайте точку на любом пустом месте** плана выполнения и **перетаскивайте указатель мыши**. Или нажмите и удерживайте значок плюса (+) в правом нижнем углу окна плана выполнения, чтобы открыть миниатюру карты всего плана выполнения.
 
> [!NOTE] 
> Также можно использовать [SET SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md) для получения сведений о плане выполнения для каждой инструкции без ее выполнения. При использовании в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] на вкладке *Результаты* будет отображаться ссылка на план выполнения в графическом формате.   
