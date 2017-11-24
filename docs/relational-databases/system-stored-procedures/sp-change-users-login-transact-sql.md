---
title: "sp_change_users_login (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/13/2016
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
- sp_change_users_login
- sp_change_users_login_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_change_users_login
ms.assetid: 1554b39f-274b-4ef8-898e-9e246b474333
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 207272f7644ab39055b7c6bb330faf6053353601
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spchangeuserslogin-transact-sql"></a>sp_change_users_login (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Сопоставляет существующего пользователя базы данных с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [ALTER USER](../../t-sql/statements/alter-user-transact-sql.md) вместо него.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_change_users_login [ @Action = ] 'action'   
    [ , [ @UserNamePattern = ] 'user' ]   
    [ , [ @LoginName = ] 'login' ]   
    [ , [ @Password = ] 'password' ]  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @Action=] '*действия*"  
 Описывает действие, которое будет выполнено процедурой. *Действие* — **varchar(10)**. *Действие* может иметь одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Auto_Fix**|Связывает запись пользователя в системном представлении каталога sys.database_principals в текущей базе данных с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеющим такое же имя. Если имени входа с таким же именем не существует, оно будет создано. Проверьте результат **Auto_Fix** инструкции, чтобы убедиться, что фактически сделана правильная ссылка. Избегайте использования **Auto_Fix** в ситуациях, чувствительных к безопасности.<br /><br /> При использовании **Auto_Fix**, необходимо указать *пользователя* и *пароль* Если имя входа еще не существует, в противном случае необходимо указать *пользователя*, но *пароль* будет игнорироваться. *Имя входа* должен иметь значение NULL. *пользователь* должен быть допустимым пользователем в текущей базе данных. Не может быть еще одного пользователя, сопоставленного с именем входа.|  
|**Отчет**|Перечисляет пользователей и соответствующие идентификаторы безопасности (SID) в текущей базе данных, которые не связаны ни с каким именем входа. *пользователь*, *входа*, и *пароль* должен иметь значение NULL или не указан.<br /><br /> Чтобы заменить параметр отчета запросом с помощью системных таблиц, сравните записи из **sys.server_prinicpals** с записями в **sys.database_principals**.|  
|**Update_One**|Связывает указанный *пользователя* текущей базы данных в существующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *входа*. *пользователь* и *входа* должен быть указан. *пароль* должен иметь значение NULL или не указан.|  
  
 [ @UserNamePattern=] '*пользователя*"  
 Имя пользователя в текущей базе данных. *пользователь* — **sysname**, значение по умолчанию NULL.  
  
 [ @LoginName=] '*входа*"  
 Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Имя входа* — **sysname**, значение по умолчанию NULL.  
  
 [ @Password=] '*пароль*"  
 Пароль, назначенный для нового [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, которое создано путем указания **Auto_Fix**. Если совпадающего имени входа уже существует, пользователя и имя входа сопоставлено и *пароль* игнорируется. Если совпадающего имени входа не существует, процедура sp_change_users_login создаст новый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа и назначит *пароль* как пароль для нового имени входа. *пароль* — **sysname**, и не должен иметь значение NULL.  
  
> **ВАЖНО!** Всегда используйте [надежный пароль.](../../relational-databases/security/strong-passwords.md)
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|UserName|**sysname**|Имя пользователя базы данных.|  
|UserSID|**varbinary(85)**|Идентификатор защиты пользователя.|  
  
## <a name="remarks"></a>Замечания  
 Используйте процедуру sp_change_users_login, чтобы связать пользователя базы данных в текущей базе данных с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если имя входа для пользователя изменилось, используйте процедуру sp_change_users_login, чтобы связать пользователя с новым именем входа без потери пользовательских разрешений. Новый *входа* не может быть sa и *пользователя*не может быть dbo, guest или пользователь INFORMATION_SCHEMA.  
  
 Процедура sp_change_users_login не может использоваться для сопоставления пользователей базы данных с участниками уровня Windows, сертификатами или асимметричными ключами.  
  
 Процедуру sp_change_users_login нельзя использовать с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданным на основе участника Windows, или с пользователем, созданным с помощью команды CREATE USER WITHOUT LOGIN.  
  
 Процедура sp_change_users_login не может выполняться в определяемой пользователем транзакции.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли базы данных db_owner. Только члены фиксированной серверной роли sysadmin могут указывать **Auto_Fix** параметр.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-showing-a-report-of-the-current-user-to-login-mappings"></a>A. Отображение отчета по текущим сопоставлениям пользователей именам входа  
 Следующий пример производит отчет по пользователям в текущей базе данных и их идентификаторам защиты (SIDs).  
  
```  
EXEC sp_change_users_login 'Report';  
```  
  
### <a name="b-mapping-a-database-user-to-a-new-sql-server-login"></a>Б. Сопоставление пользователя базы данных новому имени входа SQL Server  
 В следующем примере пользователь базы данных будет связан с новым именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пользователь базы данных `MB-Sales`, который сначала был сопоставлен с другим именем входа, будет повторно сопоставлен с именем входа `MaryB`.  
  
```  
--Create the new login.  
CREATE LOGIN MaryB WITH PASSWORD = '982734snfdHHkjj3';  
GO  
--Map database user MB-Sales to login MaryB.  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Update_One', 'MB-Sales', 'MaryB';  
GO  
```  
  
### <a name="c-automatically-mapping-a-user-to-a-login-creating-a-new-login-if-it-is-required"></a>В. Автоматическое сопоставление пользователя имени входа (создание при необходимости нового имени входа)  
 Следующий пример показывает, как использовать параметр `Auto_Fix`, чтобы сопоставить существующего пользователя с именем входа с таким же именем или создать имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Mary`, которое имеет пароль `B3r12-3x$098f6`, если имя входа `Mary` не существует.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Auto_Fix', 'Mary', NULL, 'B3r12-3x$098f6';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_adduser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_helplogins &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  