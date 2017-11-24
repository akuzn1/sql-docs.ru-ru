---
title: "sys.dm_fts_parser (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_parser_TSQL
- dm_fts_parser
- dm_fts_parser_TSQL
- sys.dm_fts_parser
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_fts_parser dynamic management function
- troubleshooting [SQL Server], full-text search
ms.assetid: 2736d376-fb9d-4b28-93ef-472b7a27623a
caps.latest.revision: "37"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6dad0375eeffff881c1887fea3c82343202f6b77
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmftsparser-transact-sql"></a>sys.dm_fts_parser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает результат окончательного разметки после применения заданного [средство разбиения по словам](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md), [тезауруса](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md), и [списка стоп-слов](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md) сочетание входной строки запроса. Результат разметки эквивалентен выходным данным службы полнотекстового поиска для указанной строки запроса.  
  
 Функция sys.dm_fts_parser является функцией динамического управления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_fts_parser('query_string', lcid, stoplist_id, accent_sensitivity)  
```  
  
## <a name="arguments"></a>Аргументы  
 *QUERY_STRING*  
 Запрос, который необходимо подвергнуть синтаксическому анализу. *QUERY_STRING* может быть строковой цепочкой, [CONTAINS](../../t-sql/queries/contains-transact-sql.md) поддержку синтаксиса. Например, можно включить словоформы, тезаурус и логические операторы.  
  
 *lcid*  
 Код языка (LCID) средства разбиения по словам для синтаксического анализа *query_string*.  
  
 *stoplist_id*  
 Идентификатор списка стоп-слов, если таковая имеется, используемый средством разбиения по словам, обозначенную *lcid*. *stoplist_id* — **int**. Если указано значение NULL, список стоп-слов не используется. Если указано значение 0, используется системный список стоп-слов.  
  
 Идентификатор списка стоп-слов уникален в пределах базы данных. Чтобы получить идентификатор списка стоп-слов для полнотекстового индекса для данной таблицы, используйте [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md) представления каталога.  
  
 *accent_sensitivity*  
 Логическое значение, управляющее полнотекстовым поиском с учетом или без учета диакритических знаков. *accent_sensitivity* — **бит**, с помощью одного из следующих значений:  
  
|Значение|Учитывать диакритические знаки|  
|-----------|----------------------------|  
|0|Не учитывать<br /><br /> Слова, совпадающие во всем, кроме диакритических знаков, рассматриваются как идентичные.|  
|1|С учетом регистра<br /><br /> Слова, сходные по начертанию, но различающиеся диакритическими знаками, рассматриваются как разные.|  
  
> [!NOTE]  
>  Чтобы просмотреть текущую настройку этого значения для полнотекстового каталога, выполните следующую [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции: `SELECT fulltextcatalogproperty('` *catalog_name*`', 'AccentSensitivity');`.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|ключевое слово|**varbinary(128)**|Шестнадцатеричное представление данного ключевого слова, возвращенное средством разбиения по словам. Это представление используется для хранения ключевых слов в полнотекстовом индексе. Это значение не является удобной для чтения, однако полезно для конкретное ключевое слово для вывода, возвращаемого других динамических административных представлений, которые возвращают содержимое полнотекстового индекса, такими как [sys.dm_fts_index_keywords](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md) и [ sys.dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md).<br /><br /> **Примечание:** OxFF представляет собой специальный символ, который указывает конец файла или набора данных.|  
|group_id|**int**|Содержит целочисленное значение, помогающее различить логическую группу, из которой был сформирован данный термин. Например, выражение `Server AND DB OR FORMSOF(THESAURUS, DB)"` формирует следующие значения group_id для английского языка.<br /><br /> 1: сервер<br />2: БАЗЫ ДАННЫХ<br />3: БАЗЫ ДАННЫХ|  
|phrase_id|**int**|Содержит целочисленное значение, помогающее различать варианты альтернативных форм составных слов, формируемые средством разбиения по словам, таким средствам, как полнотекстовой поиск. Иногда составные слова (например, «multi-million») определяются средством разбиения по словам в нескольких альтернативных формах. Эти альтернативные формы (фразы) необходимо как-то различать.<br /><br /> Например, строка `multi-million` формирует следующие значения phrase_id для английского языка.<br /><br /> 1 для`multi`<br />1 для`million`<br />2 для`multimillion`|  
|occurrence|**int**|Указывает расположение каждого термина в результате анализа. Например, для фразы `SQL Server query processor` вхождение будет содержать следующие значения вхождения терминов из фразы для английского языка.<br /><br /> 1 для`SQL`<br />2 для`Server`<br />3 для`query`<br />4-для`processor`|  
|special_term|**nvarchar(4000)**|Содержит сведения о характеристиках термина, выданного средством разбиения по словам, в том числе:<br /><br /> Точное совпадение<br /><br /> пропускаемое слово;<br /><br /> конец предложения;<br /><br /> конец абзаца;<br /><br /> конец раздела.|  
|display_term|**nvarchar(4000)**|Содержит немашинную (предназначенную для человека) форму ключевого слова. Как и в случае с функциями, предназначенными для доступа к содержимому полнотекстового индекса, этот отображаемый термин может не быть идентичным исходному термину в силу ограниченности денормализации. Однако он должен быть достаточно точным, чтобы позволить отличить его от исходных входных данных.|  
|expansion_type|**int**|Содержит сведения о природе расширения данного термина, в том числе:<br /><br /> 0 — отдельное слово;<br /><br /> 2 — расширение-словоформа;<br /><br /> 4 — расширение/замена тезауруса.<br /><br /> Например, предположим, что тезаурус определяет слово run как расширение слова `jog`:<br /><br /> `<expansion>`<br /><br /> `<sub>run</sub>`<br /><br /> `<sub>jog</sub>`<br /><br /> `</expansion>`<br /><br /> Термин `FORMSOF (FREETEXT, run)` формирует следующие выходные данные:<br /><br /> `run` со значением expansion_type=0;<br /><br /> `runs` со значением expansion_type=2;<br /><br /> `running` со значением expansion_type=2;<br /><br /> `ran` со значением expansion_type=2;<br /><br /> `jog` со значением expansion_type=4.|  
|source_term|**nvarchar(4000)**|Термин или фраза, из которой сформирован или создан в результате анализа данный термин. Например, запрос для `word breakers" AND stemmers'` выдает следующие значения source_term для английского языка.<br /><br /> `word breakers`для display_term`word`<br />`word breakers`для display_term`breakers`<br />`stemmers`для display_term`stemmers`|  
  
## <a name="remarks"></a>Замечания  
 **sys.dm_fts_parser** поддерживает синтаксис и возможности полнотекстовых предикатов, например [CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)и функции, такие как [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md).  
  
## <a name="using-unicode-for-parsing-special-characters"></a>Использование формата Юникода для синтаксического анализа специальных символов  
 При синтаксическом анализе строки запроса, **sys.dm_fts_parser** использует параметры сортировки базы данных, к которому вы подключены, если не указать строку запроса в кодировке Юникод. Следовательно, для строки не в формате Юникод, которая содержит специальные символы, такие как u или c, выходные данные могут оказаться непредвиденными, поскольку зависят от параметров сортировки базы данных. Чтобы обработать строку запроса независимо от параметров сортировки базы данных, поместите перед строкой `N`, то есть `N'` *query_string*`'`.  
  
 Дополнительные сведения см. в подразделе «C. Отображение выходных данных строки, которая содержит специальные символы» далее в этом разделе.  
  
## <a name="when-to-use-sysdmftsparser"></a>Использование sys.dm_fts_parser  
 **sys.dm_fts_parser** может быть очень полезной при отладке. Некоторые важные варианты использования.  
  
-   Понять, как данное средство разбиения по словам рассматривает указанные входные данные.  
  
     Если запросом были возвращены непредвиденные результаты, вероятной причиной может быть способ, используемый средством разбиения по словам для анализа и разбиения данных. С помощью функции sys.dm_fts_parser можно обнаружить результат, передаваемый средством разбиения по словам в полнотекстовый индекс. Кроме того, можно увидеть, какие из терминов являются стоп-словами, по которым не выполняется поиск в полнотекстовом индексе. Является ли термин Стоп-слова для данного языка зависит от того, используется ли в список стоп-слов, заданные *stoplist_id* значение, которое объявлено в функции.  
  
     Обратите также внимание на флаг учета диакритических знаков, позволяющий пользователю увидеть, как будут анализироваться входные данные средством разбиения по словам — с учетом или без учета диакритических знаков.  
  
-   Понять, как парадигматический модуль работает с данными входными данными.  
  
     Можно выяснить, как средство разбиения по словам и парадигматический модуль анализируют термин запроса и его парадигматические формы, указав запрос CONTAINS или CONTAINSTABLE, содержащий следующее предложение FORMSOF:  
  
    ```  
    FORMSOF( INFLECTIONAL, query_term )  
    ```  
  
     Результаты позволяют определить, какие термины передаются в полнотекстовый индекс.  
  
-   Понять, как тезаурус расширяет или заменяет входные данные целиком или частично.  
  
     Также можно указать:  
  
    ```  
    FORMSOF( THESAURUS, query_term )  
    ```  
  
     Результаты этого запроса показывают, как взаимодействуют средство разбиения по словам и тезаурус при обработке термина запроса. Можно увидеть расширение или замены из тезауруса и определить результирующий запрос, который фактически выполняется в отношении полнотекстового индекса.  
  
     Обратите внимание, что если пользователь выполняет следующий код:  
  
    ```  
    FORMSOF( FREETEXT, query_term )  
    ```  
  
     Возможности словоформ и тезауруса применяются автоматически.  
  
 Кроме вышеперечисленных вариантов использования, функция sys.dm_fts_parser может значительно облегчить понимание и устранение множества других возможных проблем, связанных с полнотекстовым запросом.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **sysadmin** фиксированной server роли и права доступа для указанного списка стоп-слов.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-the-output-of-a-given-word-breaker-for-a-keyword-or-phrase"></a>A. Отображение выходных данных указанного средства разбиения по словам для ключевого слова или фразы  
 В следующем примере средство разбиения по словам для английского языка с кодом языка 1033, не имеющее списка стоп-слов, возвращает выходные данные для следующей строки запроса:  
  
 `The Microsoft business analysis`  
  
 Диакритические знаки не учитываются.  
  
```  
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis" ', 1033, 0, 0);  
```  
  
### <a name="b-displaying-the-output-of-a-given-word-breaker-in-the-context-of-stoplist-filtering"></a>Б. Отображение выходных данных указанного средства разбиения по словам в контексте фильтрации по списку стоп-слов  
 В следующем примере средство разбиения по словам для английского языка с кодом языка 1033, имеющее список английских стоп-слов с идентификатором 77, возвращает выходные данные для следующей строки запроса:  
  
 `"The Microsoft business analysis" OR "MS revenue"`  
  
 Диакритические знаки не учитываются.  
  
```  
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis"  OR " MS revenue" ', 1033, 77, 0);  
```  
  
### <a name="c-displaying-the-output-of-a-string-that-contains-special-characters"></a>В. Отображение выходных данных строки, которая содержит специальные символы  
 В следующем примере для синтаксического анализа строки на французском языке используется формат Юникод:  
  
 `français`  
  
 В этом примере указывается код языка для французского языка, `1036`, и идентификатор стоп-слов, определенных пользователем, `5`. Диакритические знаки учитываются.  
  
```  
SELECT * FROM sys.dm_fts_parser(N'français', 1036, 5, 1);  
```  
  
## <a name="see-also"></a>См. также:  
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Настройка и управление файлами тезауруса для полнотекстового поиска](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Настройка и управление стоп-словами и списками стоп-слов для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Запрос с Full-Text Search](../../relational-databases/search/query-with-full-text-search.md)   
 [Запрос с Full-Text Search](../../relational-databases/search/query-with-full-text-search.md)   
 [Защищаемые объекты](../../relational-databases/security/securables.md)  
  
  