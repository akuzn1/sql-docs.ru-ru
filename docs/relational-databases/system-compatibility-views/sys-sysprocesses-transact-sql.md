---
title: "sys.sysprocesses (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysprocesses_TSQL
- sys.sysprocesses_TSQL
- sys.sysprocesses
- sysprocesses
dev_langs: TSQL
helpviewer_keywords:
- sys.sysprocesses compatibility view
- sysprocesses system table
ms.assetid: 60a36d36-54b3-4bd6-9cac-702205a21b16
caps.latest.revision: "57"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b7800401c2f0d6d1fa3848407f07c826edeb5a73
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syssysprocesses-transact-sql"></a>sys.sysprocesses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о процессах, которые выполняются в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти процессы могут быть клиентскими или системными. Для доступа к sysprocesses либо необходимо быть в контексте главной базы данных, либо следует использовать трехчастное имя master.dbo.sysprocesses.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|spid|**smallint**|Идентификатор сеанса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|kpid|**smallint**|Идентификатор потока Windows.|  
|blocked|**smallint**|Идентификатор сеанса, блокирующего данный запрос. Если этот столбец содержит значение NULL, то запрос не блокирован или сведения о сеансе блокировки недоступны (или не могут быть идентифицированы).<br /><br /> -2 = Блокирующий ресурс принадлежит потерянной распределенной транзакции.<br /><br /> -3 = Блокирующий ресурс принадлежит отложенной транзакции восстановления.<br /><br /> -4 = Идентификатор сеанса владельца кратковременной блокировки не может быть определен из-за внутренних переходов состояния кратковременной блокировки.|  
|waittype|**binary(2)**|Зарезервировано.|  
|waittime|**bigint**|Текущее время ожидания в миллисекундах.<br /><br /> 0 = процесс не является ожидающим.|  
|lastwaittype|**nchar(32)**|Строка, обозначающая имя последнего или текущего типа ожидания.|  
|waitresource|**nchar(256)**|Текстовое представление ресурса блокировки.|  
|dbid|**smallint**|Идентификатор базы данных, используемый процессом в данный момент.|  
|uid|**smallint**|Идентификатор пользователя, выполнявшего команду. Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.|  
|cpu|**int**|Совокупное время ЦП для процесса. Запись обновляется для всех процессов независимо от значения параметра SET STATISTICS TIME (ON или OFF).|  
|physical_io|**bigint**|Совокупное количество операций чтения и записи для процесса.|  
|memusage|**int**|Число страниц в кэше процедур, выделенных в данный момент для этого процесса. Отрицательное значение показывает, что процесс освобождает память, выделенную другим процессом.|  
|login_time|**datetime**|Время регистрации клиентского процесса на сервере.|  
|last_batch|**datetime**|Время последнего вызова удаленной хранимой процедуры или инструкции EXECUTE клиентским процессом.|  
|ecid|**smallint**|Идентификатор контекста выполнения используется с целью идентифицировать подпроцессы, действующие от имени одного процесса, уникальным образом.|  
|open_tran|**smallint**|Количество транзакций, открытых для данного процесса.|  
|status|**nchar(30)**|Состояние идентификатора процесса. Возможные значения:<br /><br /> **Неактивные**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сбрасывает сеанс.<br /><br /> **под управлением** = сеанс запущен один или несколько пакетов. Если включен режим MARS, в сеансе может выполняться несколько пакетов. Дополнительные сведения см. в разделе [с помощью нескольких активных результирующих наборов &#40; Режим MARS &#41; ](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).<br /><br /> **фон** = сеанса запущена фоновая задача, например обнаружение взаимоблокировок.<br /><br /> **откат** = сеанс имеет отката транзакции в процессе.<br /><br /> **Ожидание** = сеанс ожидает доступности рабочего потока.<br /><br /> **готов к запуску** = задача в сеансе находится в очереди исполнителей планировщика, ожидая времени такта.<br /><br /> **spinloop** = задача сеанса ожидает освобождения объекта взаимоблокировки.<br /><br /> **Приостановить** = сеанс ожидает события, например ввода-вывода для завершения.|  
|sid|**binary(86)**|Идентификатор GUID для этого пользователя.|  
|hostname|**nchar(128)**|Имя рабочей станции.|  
|program_name|**nchar(128)**|Имя приложения.|  
|hostprocess|**nchar(10) в формате**|Идентификационный номер процесса рабочей станции.|  
|cmd|**nchar(16)**|Команда, выполняемая в данный момент.|  
|nt_domain|**nchar(128)**|Домен Windows для клиента, если применяется проверка подлинности Windows или доверительное соединение.|  
|nt_username|**nchar(128)**|Имя пользователя Windows для процесса, если применяется проверка подлинности Windows или доверительное соединение.|  
|net_address|**nchar(12)**|Связанный уникальный идентификатор для сетевого адаптера рабочей станции каждого пользователя. При входе пользователя в систему этот идентификатор вставляется в столбец net_address.|  
|net_library|**nchar(12)**|Столбец, в котором хранится библиотека клиентской сети. Каждый клиентский процесс подключается к сетевому подключению. С сетевыми подключениями связана сетевая библиотека, позволяющая им устанавливать соединение.|  
|loginame|**nchar(128)**|Имя входа.|  
|context_info|**binary(128)**|Данные, которые хранятся в пакете с помощью инструкции SET CONTEXT_INFO.|  
|sql_handle|**binary(20)**|Представляет пакет или объект, который выполняется в настоящий момент.<br /><br /> **Примечание** это значение формируется из адреса или в пакете памяти объекта. Оно не вычисляется с помощью алгоритма [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на основе хэша.|  
|stmt_start|**int**|Начальное смещение текущей инструкции SQL для заданной sql_handle.|  
|stmt_end|**int**|Конечное смещение текущей инструкции SQL для заданной sql_handle.<br /><br /> -1 = текущая инструкция переходит к концу результатов, возвращаемому функцией fn_get_sql для заданной sql_handle.|  
|request_id|**int**|Идентификатор запроса. Применяется для идентификаций запросов, выполняемых в текущем сеансе.|  
  
## <a name="remarks"></a>Замечания  
 Если пользователь имеет разрешение VIEW SERVER STATE на сервере, он увидит все выполняющиеся сеансы на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В противном случае пользователь увидит только текущий сеанс.  
  
## <a name="see-also"></a>См. также:  
 [&#40; динамические административные представления и функции, связанные с выполнением Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  