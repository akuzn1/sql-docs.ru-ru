---
title: "Учебники по SQL Server Python | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 70b2ada0c6b2cade444af1f7dde67f0adfd90b35
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="sql-server-python-tutorials"></a>Учебники по SQL Server Python

В этой статье список учебники и образцы, демонстрирующие использование Python с 2017 г. SQL Server. Эти образцы и демонстрационные материалы Вы узнаете:

+ Запуск Python из T-SQL
+ Что такое удаленных и локальных вычислительных контекстов, и как можно выполнять код Python, с помощью имени компьютера SQL Server
+ Создание программы-оболочки кода Python в хранимой процедуре
+ Оптимизация кода Python для производственной среды SQL
+ Реальные сценарии для внедрения в приложениях машинного обучения

Сведения о требованиях и установки см. в разделе [необходимых компонентов](#bkmk_Prerequisites).

## <a name="bkmk_pythontutorials"></a>Учебники Python

+ [Запуск Python в T-SQL](run-python-using-t-sql.md)

   Основные сведения о том, как вызывать Python в T-SQL, используя механизм расширяемости первыми в SQL Server 2016.

+ [Создать модель в Python с помощью revoscalepy машинного обучения](use-python-revoscalepy-to-create-model.md)

   Вы создадите модель с помощью **rxLinMod**, в новом **revoscalepy** библиотеки. Будет запускать код из удаленного терминала Python, а моделирования будет выполняться в контексте вычислений SQL Server.

+ [Аналитика в базе данных Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)

  НОВЫЕ ФУНКЦИИ! Построение комплексное решение Python, с помощью T-SQL для хранимой процедуры. Весь код Python включено.

+ [Развертывание и использование модели Python](..\python\publish-consume-python-code.md)

  Узнайте о развертывании Python модель, используя последнюю версию Microsoft Server обучения машины.

## <a name="python-samples"></a>Образцы Python

Эти образцы, демонстрационные материалы, предоставленные группой разработчиков SQL Server и выделите способы использования аналитики, внедренный в реальных приложениях.

+ [Создать прогнозную модель с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Узнайте, как использовать машинного обучения для прогнозирования будущих внаем, что позволяет бизнес-планом и персонал будущих требований бизнеса ski аренды.

  > [!TIP]
  > Теперь включает собственный оценки из моделей Python!

+ [Выполнение клиента кластеризации с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Узнайте, как использовать алгоритм Kmeans для выполнения незащищенных кластеризации клиентов.

## <a name="bkmk_Prerequisites"></a>Предварительные требования

Чтобы использовать эти учебники, необходимо установить службы SQL Server 2017 г машины обучения (в базе данных). 2017 г. SQL Server поддерживает R или Python. Тем не менее необходимо установить системы расширяемости, которая поддерживает машинного обучения и выберите в качестве языка для установки Python. На одном компьютере можно установить R и Python.

> [!NOTE]
>
> Поддержка Python — это новая функция в SQL Server 2017 г. и требуется CTP-версии 2.0 или более поздней версии. Несмотря на то, что функция находится в предварительной версии и не поддерживается для рабочей среды, мы приглашаем вас опробовать его и отправить отзыв.

**SQL Server 2017**

После запуска программы установки SQL Server, не забывайте следующие важные действия:

+ Включение возможности выполнения внешнего сценария, запустив `sp_configure 'external scripts enabled', 1`.
+ Перезапустите сервер.
+ Убедитесь в наличии необходимых разрешений на службу, которая обращается к внешней среде выполнения.
+ Убедитесь в наличии необходимых разрешений для подключения к серверу для чтения данных, а также для создания объектов базы данных, необходимые для образца вашей учетной записи пользователя Windows или имя входа SQL.

Если возникли трудности, см. статью для некоторых распространенных проблем: [Устранение неполадок службы машины обучения](../machine-learning-troubleshooting-faq.md)

## <a name="see-also"></a>См. также:

[Учебные материалы по R в SQL Server](sql-server-r-tutorials.md)
