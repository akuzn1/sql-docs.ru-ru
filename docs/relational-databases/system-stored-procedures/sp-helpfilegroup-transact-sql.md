---
title: "sp_helpfilegroup (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs: TSQL
helpviewer_keywords: sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d70701850b1dbeff112f0d8683aa9e8b422722c3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает имена и атрибуты файловых групп, связанных с текущей базой данных.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@filegroupname =** ] **"***имя***"**  
 Логическое имя любой файловой группы в текущей базе данных. *имя* — **sysname**, значение по умолчанию NULL. Если *имя* не указан, перечисляются все файловые группы в текущей базе данных и отображается только первый результирующий набор, показанный в разделе «результирующие наборы».  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**имя_группы**|**sysname**|Имя файловой группы.|  
|**GroupID**|**smallint**|Числовой идентификатор файловой группы.|  
|**filecount**|**int**|Количество файлов в файловой группе.|  
  
 Если *имя* будет указано, то возвращается одна строка для каждого файла в файловой группе.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Логическое имя файла в файловой группе.|  
|**Идентификатор файла**|**smallint**|Числовой идентификатор файла.|  
|**Имя файла**|**nchar(260)**|Физическое имя, включающее путь к каталогу.|  
|**размер**|**nvarchar(15)**|Размер файла в килобайтах.|  
|**параметр MaxSize**|**nvarchar(15)**|Максимальный размер файла.<br /><br /> Максимальный размер, до которого может вырасти файл. Значение UNLIMITED в этом поле означает, что файл может расти, пока диск не будет заполнен.|  
|**Увеличение размера**|**nvarchar(15)**|Значение прироста размера файла. Параметр задает объем пространства, добавляемого к файлу каждый раз, когда требуется дополнительное пространство.<br /><br /> 0 = файл имеет фиксированный размер и не может расти.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. Возвращать все файловые группы в базе данных  
 В приведенном ниже примере возвращаются сведения о файловых группах в образце базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>Б. Возвращать все файлы в файловой группе  
 В приведенном ниже примере возвращаются сведения обо всех файлах файловой группы `PRIMARY` в образце базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Компонент Database Engine хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Файлы и файловые группы базы данных](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  