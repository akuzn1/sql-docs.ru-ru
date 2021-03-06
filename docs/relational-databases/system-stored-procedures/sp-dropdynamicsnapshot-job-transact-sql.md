---
title: sp_dropdynamicsnapshot_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e4612c7b20e448eecbd6c83a3d09d0796dcff542
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126264"
---
# <a name="spdropdynamicsnapshotjob-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет отфильтрованное задание моментального снимка данных для публикации с параметризованными фильтрами строк. Эта хранимая процедура выполняется на издателе в базе данных публикации. Если задание удаляется, все связанные данные, удалятся из [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) системная таблица.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"**_публикации_**"**  
 Имя публикации, из которой удаляется отфильтрованное задание моментального снимка данных. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@dynamic_snapshot_jobname**=] **"**_dynamic_snapshot_jobname_**"**  
 Имя удаляемого отфильтрованного задания моментального снимка данных. *dynamic_snapshot_jobname*имеет тип sysname, и если это не указаны значения по умолчанию для любого задания имени будет связан с *dynamic_snapshot_jobid*.  
  
 [ **@dynamic_snapshot_jobid**=] **"**_dynamic_snapshot_jobid_**"**  
 Идентификатор созданного задания моментального снимка удаляемых данных. *dynamic_snapshot_jobid*— **uniqueidentifier**, по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Только *dynamic_snapshot_jobid*или *dynamic_snapshot_jobname* можно указать. Если значения не заданы для любого *dynamic_snapshot_jobid*или *dynamic_snapshot_jobname*, удаление всех заданий динамического моментального снимка для публикации.  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 *ignore_distributor* — **бит**, значение по умолчанию **0**. Этот аргумент может использоваться для удаления динамического задания моментального снимка, не выполняя задачи очистки на распространителе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropdynamicsnapshot** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_dropdynamicsnapshot**.  
  
## <a name="see-also"></a>См. также  
 [sp_adddynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
