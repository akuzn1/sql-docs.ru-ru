---
title: CREATE EXTERNAL RESOURCE POOL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL RESOURCE POOL
- CREATE EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE POOL
- EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE
- EXTERNAL_RESOURCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL RESOURCE POOL statement
ms.assetid: 8cc798ad-c395-461c-b7ff-8c561c098808
author: HeidiSteen
ms.author: heidist
manager: cgronlund
ms.openlocfilehash: 49baad50d950578b9d2bbb96b4168c730056b307
ms.sourcegitcommit: 7c052fc969d0f2c99ad574f99076dc1200d118c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2019
ms.locfileid: "55570677"
---
# <a name="create-external-resource-pool-transact-sql"></a>CREATE EXTERNAL RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Создает внешний пул, используемый для определения ресурсов для внешних процессов. Пул ресурсов представляет подмножество физических ресурсов (память и ЦП) экземпляра ядра СУБД. Регулятор ресурсов позволяет администратору базы данных распределять ресурсы сервера по пулам ресурсов, используя до 64 пулов.

+ Для [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] в [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] внешний пул управляет `rterm.exe`, `BxlServer.exe` и другими сформированными процессами.

+ Для [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] в [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] внешний пул управляет `rterm.exe`, `python.exe`, `BxlServer.exe` и другими сформированными процессами.

  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE EXTERNAL RESOURCE POOL pool_name  
[ WITH (  
    [ MAX_CPU_PERCENT = value ]  
    [ [ , ] AFFINITY CPU =    
            {  
                AUTO   
              | ( <cpu_range_spec> )   
              | NUMANODE = ( <NUMA_node_id> )   
            } ]   
    [ [ , ] MAX_MEMORY_PERCENT = value ]  
    [ [ , ] MAX_PROCESSES = value ]   
    )   
]  
[ ; ]  
  
<CPU_range_spec> ::=    
{ CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]  
```  
  
## <a name="arguments"></a>Аргументы

*pool_name*  
Определяемое пользователем имя внешнего пула ресурсов. *pool_name* является буквенно-цифровым и может содержать до 128 символов. Этот аргумент должен быть уникальным внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и должен соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md).  

MAX_CPU_PERCENT =*value*  
Указывает максимальную среднюю пропускную способность ЦП для всех запросов во внешнем пуле ресурсов при возникновении состязания за ресурсы ЦП. *value* имеет тип integer и значение по умолчанию 100. Диапазон допустимых значений для *value* — от 1 до 100.

AFFINITY {CPU = AUTO | ( \<CPU_range_spec> ) | NUMANODE = (\<NUMA_node_range_spec>)} Подключает внешний пул ресурсов к конкретным ЦП. Значение по умолчанию — AUTO.

AFFINITY CPU = **(** \<CPU_range_spec> **)** сопоставляет внешний пул ресурсов с ЦП [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], определенными с помощью CPU_IDs.

При использовании AFFINITY NUMANODE = **(** \<NUMA_node_range_spec> **)** внешний пул ресурсов сопоставляется с физическими процессорами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], соответствующими данному узлу NUMA или диапазону узлов. 

MAX_MEMORY_PERCENT =*value*  
Указывает общий объем памяти сервера, который может использоваться для запросов в данном внешнем пуле ресурсов. *value* имеет тип integer и значение по умолчанию 100. Диапазон допустимых значений для *value* — от 1 до 100.

MAX_PROCESSES =*value*  
Указывает максимально допустимое количество процессов для внешнего пула ресурсов. Укажите 0, чтобы задать неограниченный порог для пула, который впоследствии ограничивается только ресурсами компьютера. Значение по умолчанию равно 0.

## <a name="remarks"></a>Remarks

[!INCLUDE[ssDE](../../includes/ssde-md.md)] реализует пул ресурсов при выполнении инструкции [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md).

Общие сведения о пулах ресурсов см. в разделах [Пул ресурсов Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md), [sys.resource_governor_external_resource_pools (Transact-SQL)](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md) и [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).

Сведения об управлении внешними пулами ресурсов для машинного обучения см. в статье [Resource governance for machine learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md) (Управление ресурсами для машинного обучения в SQL Server). 

## <a name="permissions"></a>Разрешения

Требуется разрешение `CONTROL SERVER`.

## <a name="examples"></a>Примеры

Следующая инструкция определяет внешний пул, который ограничивает загрузку ЦП до 75 процентов. Инструкция также определяет максимальный объем памяти — 30 процентов доступной памяти на компьютере.

```sql
CREATE EXTERNAL RESOURCE POOL ep_1
WITH (  
    MAX_CPU_PERCENT = 75
    , AFFINITY CPU = AUTO
    , MAX_MEMORY_PERCENT = 30
);
GO
ALTER RESOURCE GOVERNOR RECONFIGURE;
GO
```
  
## <a name="see-also"></a>См. также раздел

[Параметр конфигурации сервера external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)
[sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
[ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
[DROP EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)
[CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)
[CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)
[Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
[sys.resource_governor_external_resource_pools (Transact-SQL)](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)
[sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)
[ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)
