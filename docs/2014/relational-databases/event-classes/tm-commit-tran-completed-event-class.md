---
title: 'События класса TM: COMMIT Tran Completed, класс событий | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- 'TM: Commit Tran Completed event class'
ms.assetid: c102de15-f312-42a7-b52a-fc4879cc43aa
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 224bfd47c31c94e19935a97c6ed1cc726e233bb2
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52784706"
---
# <a name="tm-commit-tran-completed-event-class"></a>События класса TM: Класс события Commit Tran Completed
  События класса TM: Класс событий Commit Tran Completed указывает на завершение запроса COMMIT TRANSACTION. Запрос был отправлен клиентом через интерфейс управления транзакциями. Столбец EventSubClass указывает, будет ли начата новая транзакция после фиксации текущей транзакции.  
  
## <a name="tm-commit-tran-completed-event-class-data-columns"></a>События класса TM: столбцы данных класса событий Commit Tran Completed  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Да|  
|----------------------|---------------|-----------------|---------------|---------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|ClientProcessID|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`int`|Идентификатор базы данных, указанной в инструкции USE database, или базы данных по умолчанию, если для данного экземпляра инструкция USE database не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|DatabaseName|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|Ошибка|`int`|Номер ошибки для данного события. Часто это номер ошибки, который хранится в представлении каталога sys.messages.|31|Да|  
|EventClass|`int`|Тип события = 186.|27|Нет|  
|EventSequence|`int`|Порядковый номер данного события в запросе.|51|Нет|  
|EventSubClass|`int`|Тип подкласса события.<br /><br /> 1 = фиксация<br /><br /> 2 = фиксация и начало|21|Да|  
|GroupID|`int`|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LoginName|`nvarchar`|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|LoginSid|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|RequestID|`int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|ServerName|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|Success|`int`|1 = успешное завершение. 0 = неуспешное завершение (например, 1 означает, что проверка разрешений проходит, а 0 — что не проходит).|23|Да|  
|TextData|`ntext`|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
|XactSequence|`bigint`|Токен, который описывает текущую транзакцию.|50|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [COMMIT TRANSACTION (Transact-SQL)](/sql/t-sql/language-elements/commit-transaction-transact-sql)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
