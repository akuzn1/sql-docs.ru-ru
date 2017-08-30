---
title: "Параметры (преобразование) (AccessToSQL) проекта | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- conversion, options described
- Project Settings dialog box, Conversion
ms.assetid: bcebc635-c638-4ddb-924c-b9ccfef86388
caps.latest.revision: 16
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c9a9c7fb027bfd8f90d5310bb096eaef706aa353
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-conversion-accesstosql"></a>Параметры проекта (преобразование) (AccessToSQL)
Параметры преобразования проекта позволяют настраивать преобразование объектов из объектов базы данных доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объекты базы данных SQL Azure.  
  
Область преобразования доступна в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Используйте **параметры проекта** диалоговое окно «», чтобы задать параметры конфигурации для текущего проекта. Чтобы открыть параметры преобразования в **средства** последовательно выберите пункты **параметры проекта**, нажмите кнопку **Общие** в нижней части левой панели, а затем выберите **преобразование**.  
  
-   Используйте **параметры проекта по умолчанию** диалоговое окно «», чтобы задать параметры конфигурации для всех проектов. Чтобы открыть параметры преобразования в **средства** последовательно выберите пункты **параметры проекта по умолчанию**, выберите тип проекта миграции, для которого требуются параметры для просмотра / изменилось с **миграции целевой версии** раскрывающийся список, нажмите кнопку **Общие** в нижней части левой панели, а затем выберите **преобразование**.  
  
## <a name="options"></a>Параметры  
**Добавить первичный ключ**  
Создает новый первичный ключ в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблицу SQL Azure, если таблицы Access не имеет первичного ключа или уникального индекса.  
  
-   **Режим по умолчанию**: False  
  
-   **Режим оптимистичного**: False  
  
-   **Полный режим**: True  
  
При подключении к SQL Azure, он по умолчанию — True. **Добавить столбцы отметок времени**  
Указывает, следует ли SSMA создает значение отметки времени при необходимости.  
  
-   **Режим по умолчанию**: решить Let SSMA  
  
-   **Режим оптимистичного**: никогда  
  
-   **Полный режим**: решить Let SSMA  
  
**Включить отчет оценки данных с использованием преобразования оценки отчетов**  
Оценка данных включает в отчет оценки.  
  
-   **Режим по умолчанию**: True  
  
-   **Режим оптимистичного**: False  
  
-   **Полный режим**: True  
  
**Тип сообщения, когда первичный ключ содержит столбцы, допускающие значение NULL**  
Указывает тип сообщения (предупреждение, ошибка или ничего) SSMA выводится в области вывода, когда он находит первичные ключи для столбцов со значением NULL.  
  
-   **Режим по умолчанию**: предупреждение  
  
-   **Режим оптимистичного**: нет сообщений  
  
-   **Полный режим**: ошибка  
  
**Тип сообщения, если внешние ключевые столбцы имеют различные размеры**  
Указывает тип сообщения (предупреждение, ошибка или ничего) SSMA выводится в области вывода при обнаружении неверный внешний ключ текста.  
  
-   **Режим по умолчанию**: предупреждение  
  
-   **Режим оптимистичного**: нет сообщений  
  
-   **Полный режим**: ошибка  
  
**Тип сообщения, когда столбцов типа memo индексируются**  
Указывает тип сообщения (предупреждение, ошибка или ничего) SSMA выводится в области вывода при обнаружении индекс, который содержит **memo** столбца.  
  
-   **Режим по умолчанию**: предупреждение  
  
-   **Режим оптимистичного**: нет сообщений  
  
-   **Полный режим**: ошибка  
  
**Предупреждать, если сложный запрос использует символ-шаблон (\&#42;)**  
Выводит предупреждение в области вывода и список ошибок, когда имя столбца в инструкции SELECT является подстановочным знаком (*).  
  
-   **Режим по умолчанию**: True  
  
-   **Режим оптимистичного**: False  
  
-   **Полный режим**: True  
  
**Предупреждать при изменении имени идентификатора**  
Отображает сообщение в отчете оценки и в области вывода при изменении имени идентификатора объекта с SSMA.  
  
-   **Режим по умолчанию**: True  
  
-   **Режим оптимистичного**: False  
  
-   **Полный режим**: True  
  
**Предупреждать, когда будет заключаться в кавычки идентификатор**  
Отображает сообщение в отчете оценки и в области вывода при по SSMA будет заключаться в кавычки имя идентификатора объекта. Заключения в кавычки идентификаторов необходим в том случае, когда имя является зарезервированным словом или содержит специальные символы.  
  
-   **Режим по умолчанию**: True  
  
-   **Режим оптимистичного**: False  
  
-   **Полный режим**: True  
  
## <a name="see-also"></a>См. также:  
[Reference(Access) интерфейса пользователя](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
