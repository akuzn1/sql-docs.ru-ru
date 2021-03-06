---
title: Как работать со службами CDC | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db5c718a-6e7f-48ec-82a3-9d5b131716e5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2cab5b109a8f9181235fa1b61d18a2f7a5976c80
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796046"
---
# <a name="how-to-work-with-cdc-services"></a>Как работать со службами CDC
  В этой процедуре описано, как использовать консоль управления службой CDC для подготовки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со службами Oracle CDC и для создания новой службы CDC.  
  
### <a name="to-work-with-cdc-services"></a>Работа со службами CDC  
  
1.  В меню **Пуск** выберите пункт **Конфигурация служб CDC для Oracle**.  
  
2.  На левой панели выберите **Локальные службы CDC** (корневой уровень).  
  
3.  Выполните одну или обе следующие задачи:  
  
    -   **Подготовка SQL Server**  
  
         Выберите этот параметр на панели **Действия** в правой части консоли конфигурации службы CDC.  
  
         Можно также щелкнуть правой кнопкой **Локальные службы CDC** и выбрать **Подготовить SQL Server**.  
  
         Откроется диалоговое окно подготовки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Oracle CDC.  
  
         Чтобы можно было подготовить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для служб Oracle CDC, имя входа должно соответствовать имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с предопределенной ролью сервера `dbcreator` . Это имя входа используется для создания базы данных MSXDBCDC, которая необходима для добавления служб Oracle CDC и позднее экземпляров Oracle CDC.  
  
         Сведения о том, как использовать это диалоговое окно, см. в разделе [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md). Сведения о включении экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для CDC см. в разделе [Подготовка SQL Server для CDC](how-to-prepare-sql-server-for-cdc.md).  
  
    -   **Создайте новую службу CDC.**  
  
         Щелкните пункт **Создать службу** на панели **Действия** в правой половине консоли настройки службы CDC.  
  
         Можно также щелкнуть правой кнопкой **Локальные службы CDC** и выбрать **Создать службу**.  
  
         Откроется диалоговое окно создания новой службы Oracle CDC.  
  
         Сведения о том, как использовать это диалоговое окно, см. в разделе [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md). Сведения о создании и редактировании службы CDC см. в разделе [Создание и изменение службы CDC](how-to-create-and-edit-a-cdc-service.md).  
  
         Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которое будет использоваться только службой Oracle CDC, должно быть членом предопределенной роли сервера `public` . В дополнение к этому других разрешений не требуется. Однако чтобы создать службу Oracle CDC, для имени входа необходимо установить разрешение на запись в базу данных MSXDBCDC, например для имени входа на сервер необходимо назначить роль **db_owner** . Если пользователь с именем входа, не имеющим разрешение на запись в базе данных MSXDBDCDC, попытается создать экземпляр Oracle CDC, выводится сообщение об ошибке. Нажмите кнопку **ОК** , чтобы открыть диалоговое окно «Подключение к SQL Server».  
  
         Сведения о вводе учетных данных для имени входа с разрешением на запись в базу данных MSXDBCDC, например для роли **db_owner** , см. в разделах [Создание и изменение службы CDC Oracle](create-and-edit-an-oracle-cdc-service.md) и [Соединение с SQL Server](connection-to-sql-server.md).  
  
## <a name="see-also"></a>См. также  
 [Работа со службами CDC](work-with-cdc-services.md)  
  
  
