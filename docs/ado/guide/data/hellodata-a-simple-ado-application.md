---
title: "HelloData: Простой ADO приложения | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HelloData sample application [ADO]
- ADO, samples
ms.assetid: de4bcd56-dac2-45e6-95ab-9fd7f25878fc
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a1c7d61c6349945274febc92e4e6b5acfcc379b9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="hellodata-a-simple-ado-application"></a>HelloData: Простой ADO приложения
Это простое приложение пошаговое выполнение каждой из четырех основных операций ADO: начало, проверки, изменение и обновление данных. Эти операции выполняются в образце базы данных Northwind, входящий в состав Microsoft® SQL Server. Чтобы сосредоточиться на основ ADO и снизить перегруженность кода, обработка ошибок в примере сводится к минимуму.  
  
### <a name="to-run-hellodata"></a>Для запуска HelloData  
  
1.  Создайте новый проект Visual Basic стандартный exe-файла, ссылающегося на библиотеку ADO. Дополнительные сведения см. в разделе [ссылающееся на библиотеки ADO](../../../ado/guide/referencing-the-ado-libraries.md).  
  
2.  Создание четырех кнопок в верхней части формы, установка **имя** и **заголовок** свойств значения, приведенные в таблице в конце этого раздела.  
  
3.  Ниже кнопок Добавить **управления DataGrid Microsoft** (Msdatgrd.ocx). Файл Msdatgrd.ocx входит в состав Visual Basic и расположен в папке \windows\system32 или \winnt\system32. Чтобы добавить элемент управления DataGrid в область элементов Visual Basic, выберите **компонентов... ** из **проекта** меню. Затем установите флажок рядом с элементом «элемент управления DataGrid Microsoft 6.0 (SP3) (OLE DB)» и нажмите кнопку **ОК**. Добавление элемента управления в проект, перетащите элемент управления DataGrid из области элементов на форму Visual Basic.  
  
4.  Создание **TextBox** в форме под сеткой и задать его свойства, как показано в таблице. Закончив формы должен быть похож на следующем рисунке.  
  
5.  Скопируйте код, приведенный в [HelloData кода](../../../ado/guide/data/hellodata-code.md)и вставьте его в окне редактора кода для формы. Нажмите клавишу **F5** выполнение кода.  
  
> [!NOTE]
>  В следующем примере и в руководстве пользователя «MyId» с паролем «123aBc» используется для проверки подлинности на сервере. Следует заменить эти значения, используя действительные учетные данные для сервера. Кроме того замените значение «MySQLServer» с именем сервера.  
  
 Подробное описание кода см. в разделе [комментарии на HelloData](../../../ado/guide/data/comments-on-hellodata.md).  
  
 ![Показывает форму Form1 для приложения HelloData VB](../../../ado/guide/data/media/hellodata.gif "HelloData")  
  
|Тип элемента управления|Свойство|Значение|  
|------------------|--------------|-----------|  
|форма|Имя|Form1|  
||Высота|6500|  
||Ширина|6500|  
|MS DataGrid|Имя|grdDisplay1|  
|TextBox|Имя|txtDisplay1|  
||Multiline|true|  
|Кнопки|Имя|cmdGetData|  
||Заголовок|Получение данных|  
|Кнопки|Имя|cmdExamineData|  
||Заголовок|Анализ данных|  
|Кнопки|Имя|cmdEditData|  
||Заголовок|Изменение данных|  
|Кнопки|Имя|cmdUpdateData|  
||Заголовок|Обновление данных|