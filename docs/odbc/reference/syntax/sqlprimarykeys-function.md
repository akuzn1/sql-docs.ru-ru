---
title: "Функция SQLPrimaryKeys | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLPrimaryKeys
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPrimaryKeys
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC]
ms.assetid: 3f809b09-3c1b-415e-80c5-a603e8e25d5b
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 79261b649994d97d88f75a7ac1dd4d067c0354d6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlprimarykeys-function"></a>Функция SQLPrimaryKeys
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ODBC  
  
 **Сводка**  
 **SQLPrimaryKeys** возвращает имена столбцов, составляющих первичный ключ для таблицы. Драйвер возвращает данные в виде результирующего набора. Эта функция не поддерживает возврат первичные ключи из нескольких таблиц в рамках одного вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLPrimaryKeys(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *CatalogName*  
 [Вход] Имя каталога. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») обозначает те таблицы, которые не имеют каталоги. *CatalogName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *CatalogName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *CatalogName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения. Дополнительные сведения см. в разделе [аргументов функций каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Вход] Длина в символах **CatalogName*.  
  
 *SchemaName*  
 [Вход] Имя схемы. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») обозначает этих таблиц, у которых нет схемы. *SchemaName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *SchemaName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *SchemaName* — обычный аргумент; он интерпретируется буквально и его регистр не имеет значения.  
  
 *NameLength2*  
 [Вход] Длина в символах **SchemaName*.  
  
 *Имя_таблицы*  
 [Вход] Имя таблицы. Этот аргумент не может быть пустым указателем. *TableName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *TableName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *TableName* — обычный аргумент; он интерпретируется буквально и его регистр не имеет значения.  
  
 *NameLength3*  
 [Вход] Длина в символах **TableName*.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLPrimaryKeys** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL _HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLPrimaryKeys** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|24000|Недопустимое состояние курсора|(DM) курсор был открыт на *StatementHandle*, и **SQLFetch** или **SQLFetchScroll** бы была вызвана.<br /><br /> Курсор был открыт на *StatementHandle*, но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Транзакции выполнен откат из-за взаимоблокировку ресурсов в другой транзакции.|  
|40003|Неизвестный завершение операторов|Сбой подключения во время выполнения этой функции и не удается определить состояние транзакции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в * \*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY009|Недопустимое использование пустого указателя|(DM) *TableName* аргумент был пустым указателем.<br /><br /> Атрибут инструкции SQL_ATTR_METADATA_ID было задано значение SQL_TRUE, *CatalogName* аргумент являлся указателем null, и **SQLGetInfo** сведениями SQL_CATALOG_NAME тип возвращается в каталоге поддерживаются имена.<br /><br /> (DM) атрибут инструкции SQL_ATTR_METADATA_ID было задано значение SQL_TRUE и *SchemaName* аргумент был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLPrimaryKeys** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для * StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение одного из аргументов длина имени меньше 0, но не равно SQL_NTS, а также связанные имя аргумента является пустым указателем.<br /><br /> Значение одного из аргументов длина имени превышает значение максимальной длины для соответствующего имени.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Был указан каталог, а драйвер или источник данных не поддерживает каталоги.<br /><br /> Схема была указана и драйвера или источник данных не поддерживает схемы.<br /><br /> Сочетание текущих настроек атрибуты инструкции SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживается драйвером или источником данных.<br /><br /> Атрибут инструкции SQL_ATTR_USE_BOOKMARKS было задано значение SQL_UB_VARIABLE, а атрибут инструкции SQL_ATTR_CURSOR_TYPE был задан тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Время ожидания истекло до источника данных, запрошенный результирующий набор. Время ожидания задается с помощью **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
 **SQLPrimaryKeys** возвращает результаты в виде стандартных результирующий набор, упорядоченный по TABLE_CAT, по значениям TABLE_SCHEM, TABLE_NAME и KEY_SEQ. Сведения о том, как эти сведения может использоваться в разделе [использует данные из каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Следующие столбцы были переименованы для ODBC 3. *x*. Имя столбца изменения не влияют на обратной совместимости так, как привязать приложений, номер столбца.  
  
|Столбец ODBC 2.0|ODBC 3. *x* столбца|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Чтобы определить фактический длин столбцов TABLE_CAT, по значениям TABLE_SCHEM, TABLE_NAME и COLUMN_NAME, вызовите **SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN и SQL_MAX_COLUMN Параметры _NAME_LEN.  
  
> [!NOTE]  
>  Дополнительные сведения о общего использования, аргументы и возвращаемые данные функций каталога ODBC см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 В следующей таблице перечислены столбцы в результирующем наборе. Дополнительные столбцы вслед за столбец 6 (PK_NAME) можно определить с помощью драйвера. Приложение должно получить доступ к от драйвера отсчет от конца результирующего набора, а не порядковый номер явное указание. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Номер столбца|Тип данных|Комментарии|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Имя каталога таблицы первичного ключа; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет каталоги.|  
|ПО ЗНАЧЕНИЯМ TABLE_SCHEM (ODBC 1.0)|2|Varchar|Имя схемы таблицы первичного ключа; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет схемы.|  
|ИМЯ_ТАБЛИЦЫ (ODBC 1.0)|3|Varchar not NULL|Имя таблицы первичных ключей.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar not NULL|Имя столбца первичного ключа. Драйвер возвращает пустую строку для столбца, который не имеет имени.|  
|KEY_SEQ (ODBC 1.0)|5|Smallint, не NULL|Порядковый номер столбца (начиная с 1) ключа.|  
|PK_NAME (ODBC 2.0)|6|Varchar|Имя первичного ключа. Имеет значение NULL, если не применим к источнику данных.|  
  
## <a name="code-example"></a>Пример кода  
 В разделе [SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфера|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выборка блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Выборка одной строки или блока данных в направлении только вперед|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Возврат столбцов внешних ключей|[Функция SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|Получение статистики таблиц и индексов|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)