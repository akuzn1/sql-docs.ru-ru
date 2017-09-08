---
title: "ALTER DATABASE SET HADR (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET HADR
- SET_HADR_TSQL
- HADR_TSQL
- HADR
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER DATABASE statement, AlwaysOn Availability Group
- ALTER DATABASE statement, SET HADR options
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], Transact-SQL statements
- Availability Groups [SQL Server], databases
ms.assetid: 20e6e803-d6d5-48d5-b626-d1e0a73d174c
caps.latest.revision: 44
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3799bc24ab3cfa9f0d65c961f69b72210c6cccef
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-transact-sql-set-hadr"></a>SET HADR ALTER DATABASE (Transact-SQL) 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе приведен синтаксис инструкции ALTER DATABASE для параметра [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] параметры базы данных-получателя. Может только один параметр SET HADR инструкции ALTER DATABASE. Эти параметры поддерживаются только во вторичных репликах.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER DATABASE database_name  
   SET HADR   
   {  
        { AVAILABILITY GROUP = group_name | OFF }  
   | { SUSPEND | RESUME }  
   }  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя изменяемой базы данных-получателя.  
  
 SET HADR  
 Выполняет указанную команду [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] в указанной базе данных.  
  
 {ГРУППА ДОСТУПНОСТИ  **=**  *имя_группы* | {OFF}  
 Присоединяет базу данных доступности к указанной группе доступности или исключает ее из группы, как показано ниже.  
  
 *имя_группы*  
 Присоединяет указанную базу данных на вторичной реплике, размещенной на экземпляре сервера, на котором выполнена команда, к группе доступности, задаваемой параметром group_name.  
  
 Необходимые условия для выполнения этой операции следующие:  
  
-   База данных должна быть уже добавлена в группу доступности на основной реплике.  
  
-   Основная реплика должна быть активной. Сведения об устранении неполадок неактивной основной реплики, см. в разделе [Устранение неполадок всегда в конфигурации групп доступности (SQL Server)](http://go.microsoft.com/fwlink/?LinkId=225834).  
  
-   Основная реплика должна находиться в интерактивном режиме, а дополнительная реплика должна быть подключена к основной реплике.  
  
-   База данных-получатель должна быть восстановлена с применением параметра WITH NORECOVERY из недавней резервной копии баз данных и журнала основной базы данных, причем резервная копия журнала должна быть достаточно новой, чтобы позволять базе данных-получателю «догнать» основную базу данных.  
  
    > [!NOTE]  
    >  Добавление базы данных к группе доступности, подключитесь к экземпляру сервера, на котором размещена первичная реплика и использовать [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md)*имя_группы* Добавления базы данных *имя_базы_данных*  инструкции.  
  
 Дополнительные сведения см. в статье [Присоединение базы данных-получателя к группе доступности (SQL Server)](../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
 OFF  
 Удаляет указанную базу данных-получатель из группы доступности.  
  
 Удаление базы данных-получателя может быть полезным в случае, если ее состояние значительно отстает от состояния основной базы данных, и ожидать длительной синхронизации состояния нежелательно. После удаления базы данных-получателя, вы можете обновить ее, восстановив последовательность резервных копий до последней резервной копии журнала (с помощью восстановления... С ПАРАМЕТРОМ WITH NORECOVERY).  
  
> [!IMPORTANT]  
>  Чтобы полностью удалить базу данных доступности из группы доступности, подключитесь к экземпляру сервера, на котором размещена первичная реплика и использовать [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md)*имя_группы* удалить База данных *имя_базы_данных_доступности* инструкции. Дополнительные сведения см. в разделе [удалить базы данных-источника из группы доступности &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
 SUSPEND  
 Приостанавливает перемещение данных в базу данных-получатель. Команда SUSPEND возвращается сразу после принятия репликой, в которой размещена целевая база данных, но фактическая приостановка базы данных происходит асинхронно.  
  
 Область воздействия зависит от того, где выполняется инструкция ALTER DATABASE:  
  
-   Если приостанавливается база данных-получатель во вторичной реплике, то будет приостановлена только локальная база данных-получатель. Существующие соединения в предназначенной для чтения вторичной реплике остаются применимыми. Новые соединения с приостановленной базой данных в предназначенной только для чтения вторичной реплике не допускаются, пока движение данных не будет возобновлено.  
  
-   Если приостанавливается база данных в первичной реплике, то будет приостановлена передача данных в соответствующие базы данных-получатели каждой из вторичных реплик. Существующие соединения в удобном для чтения вторичной реплике остаются применимыми, и не будут подключаться новые соединения с намерением чтения вторичные реплики для чтения.  
  
-   Если движение данных приостановлено из-за принудительного перехода на другой ресурс вручную, то соединения с новой вторичной репликой не допускаются до тех пор, пока движение данных остается приостановленным.  
  
 Если приостанавливается база данных во вторичной реплике, и база данных, и реплика становятся несинхронизированными и отмечаются как NOT SYNCHRONIZED.  
  
> [!IMPORTANT]  
>  Пока база данных-получатель остается приостановленной, в очереди отправки соответствующей основной базы данных накапливаются неотправленные записи журнала транзакций. Соединения с вторичной репликой возвращают данные, которые были доступными ко времени приостановки движения данных.  
  
> [!NOTE]  
>  Приостановка и возобновление вторичной базы данных AlwaysOn не непосредственно влияет на доступность базы данных-источника, хотя Приостановка базы данных-получателя может повлиять возможности избыточности и отработки отказа для базы данных-источника, до приостановки База данных-получатель возобновляется. Этим она отличается от зеркального отображения базы данных, где состояние зеркального отображения приостанавливается как в зеркальной базе данных, так и в основной базе данных, до тех пор пока не возобновится зеркальное отображение. Приостановка базы данных-источника AlwaysOn приостанавливает перемещение данных для всех соответствующих баз данных-получателей, а функции избыточности и отработки отказа для этой базы данных не работают до тех пор, пока работа базы данных-источника не будет возобновлена.  
  
 Дополнительные сведения см. в разделе [приостановки базы данных доступности &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/suspend-an-availability-database-sql-server.md).  
  
 RESUME  
 Возобновляет приостановленную передачу данных в указанную базу данных-получатель. Команда RESUME возвращается сразу после принятия репликой, в которой размещена целевая база данных, но фактическое возобновление базы данных происходит асинхронно.  
  
 Область воздействия зависит от того, где выполняется инструкция ALTER DATABASE:  
  
-   Если возобновляется база данных-получатель во вторичной реплике, то будет возобновлена только локальная база данных-получатель. Перемещение данных возобновляется, если база данных не была также приостановлена в основной реплике.  
  
-   Если восстанавливается база данных в первичной реплике, то будет восстановлена передача данных во все вторичные реплики, в которых соответствующие базы данных-получатели не были также приостановлены локально. Чтобы возобновить базу данных-получатель, которая была по отдельности приостановлена во вторичной реплике, подключитесь к экземпляру сервера, на котором размещена вторичная реплика, и возобновите базу данных в этом сеансе.  
  
     В режиме синхронной фиксации состояние базы данных меняется на SYNCHRONIZING. Если в данный момент ни одна другая база данных не приостановлена, состояние реплики также меняется на SYNCHRONIZING.  
  
     Дополнительные сведения см. ниже в разделе [Возобновление базы данных доступности (SQL Server)](../../database-engine/availability-groups/windows/resume-an-availability-database-sql-server.md).  
  
## <a name="database-states"></a>Состояния базы данных  
 При присоединении базы данных-получателя к группе доступности локальная вторичная реплика изменяет состояние этой базы данных-получателя с RESTORING на ONLINE. Если база данных-получатель удаляется из группы доступности, локальная вторичная реплика возвращает базу данных в состояние RESTORING. Это позволяет применять к такой базе данных-получателю последовательные резервные копии журналов из основной базы данных.  
  
## <a name="restrictions"></a>Ограничения  
 Выполнение инструкций ALTER DATABASE вне транзакций и пакетов.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER на базу данных. Присоединение базы данных к группе доступности требуется членство в **db_owner** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере база данных-получатель `AccountsDb1` включается в локальную вторичную реплику группы доступности `AccountsAG`.  
  
```  
ALTER DATABASE AccountsDb1 SET HADR AVAILABILITY GROUP = AccountsAG;  
```  
  
> [!NOTE]  
>  Пример использования инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в контексте см. в статье [Создание группы доступности (Transact-SQL)](../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [Обзор групп доступности AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) [Диагностика конфигурации групп доступности AlwaysOn &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md) 
  
  