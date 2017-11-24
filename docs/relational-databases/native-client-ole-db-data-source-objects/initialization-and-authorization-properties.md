---
title: "Свойства инициализации и авторизации | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- authorization [OLE DB]
- properties [OLE DB]
- SQL Server Native Client OLE DB provider, initialization properties
- SQL Server Native Client OLE DB provider, authorization properties
- initialization properties [OLE DB]
ms.assetid: 913ab38c-e443-446c-b326-7447e95aa7f9
caps.latest.revision: "59"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6837fe5d825a12287cd46c122e5d3bcfc69c4e05
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="initialization-and-authorization-properties"></a>Свойства инициализации и авторизации
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует свойства инициализации и авторизации OLE DB следующим образом.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_AUTH_CACHE_AUTHINFO|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не кэширует данные для проверки подлинности.<br /><br /> При попытке задать значение этого свойства поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED. *DwStatus* структуры DBPROP указывает DBPROPSTATUS_NOTSUPPORTED.|  
|DBPROP_AUTH_ENCRYPT_PASSWORD|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента использует стандартный [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] механизмов безопасности для скрытия паролей.<br /><br /> При попытке задать значение этого свойства поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED. *DwStatus* структуры DBPROP указывает DBPROPSTATUS_NOTSUPPORTED.|  
|DBPROP_AUTH_INTEGRATED|Если DBPROP_AUTH_INTEGRATED имеет значение NULL, пустой строки или значение «SSPI» типа VT_BSTR, то поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует для авторизации доступа пользователя к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указанной в свойствах DBPROP_INIT_DATASOURCE и DBPROP_INIT_CATALOG, механизм проверки подлинности Windows.<br /><br /> Если задано значение VT_EMPTY (по умолчанию), то используется безопасность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Имя входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пароль указываются в свойствах DBPROP_AUTH_USERID и DBPROP_AUTH_PASSWORD.|  
|DBPROP_AUTH_MASK_PASSWORD|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует стандартный механизм безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для скрытия паролей.<br /><br /> При попытке задать значение этого свойства поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED. *DwStatus* структуры DBPROP указывает DBPROPSTATUS_NOTSUPPORTED.|  
|DBPROP_AUTH_PASSWORD|Пароль назначается для имени входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда выбрана проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это свойство используется для авторизации доступа к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBPROP_AUTH_PERSIST_ENCRYPTED|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не шифрует данные проверки подлинности при сохранении.<br /><br /> При попытке задать значение этого свойства поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED. *DwStatus* структуры DBPROP указывает DBPROPSTATUS_NOTSUPPORTED.|  
|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет значения для проверки подлинности, включая образ пароля (если указано). Шифрование не предусмотрено.|  
|DBPROP_AUTH_USERID|Имя входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда выбрана проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это свойство используется для авторизации доступа к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBPROP_INIT_ASYNCH|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает асинхронную инициализацию.<br /><br /> Параметр DBPROPVAL_ASYNCH_INITIALIZE в свойстве dbprop_init_asynch **IDBInitialize::Initialize** станет вызов без блокировки. Дополнительные сведения см. в разделе [выполнение асинхронных операций](../../relational-databases/native-client/features/performing-asynchronous-operations.md).|  
|DBPROP_INIT_CATALOG|Имя существующей базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], к которой выполняется подключение.|  
|DBPROP_INIT_DATASOURCE|Сетевое имя сервера, где запущен экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если существует несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполняющимся на компьютере, для подключения к определенному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значение DBPROP_INIT_DATASOURCE указывается в качестве  *\\\ServerName\InstanceName*. Escape-последовательность \\\ используется обратной косой черты.|  
|DBPROP_INIT_GENERALTIMEOUT|Указывает количество секунд до истечения времени запроса, кроме инициализации источника данных и выполнения команды. Значение 0 указывает на бесконечное время ожидания. Поставщики, работающие через сетевые соединения, в распределенных сценариях или сценариях на основе транзакций, могут реализовать поддержку этого свойства, чтобы принудительно сократить время ожидания задействованного компонента в случае длительного выполнения запроса. Временем ожидания для инициализации источника данных или выполнения команд по-прежнему управляют свойства DBPROP_INIT_TIMEOUT и DBPROP_COMMANDTIMEOUT, соответственно.<br /><br /> Свойство DBPROP_INIT_GENERALTIMEOUT доступно только для чтения, и при попытке задать для него *dwstatus* возвращается ошибка DBPROPSTATUS_NOTSETTABLE.|  
|DBPROP_INIT_HWND|Дескриптор Windows из вызывающего приложения. Действительный дескриптор окна необходим для инициализации диалогового окна, если разрешен запрос свойств инициализации.|  
|DBPROP_INIT_IMPERSONATION_LEVEL|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает корректировку уровня олицетворения.<br /><br /> При попытке задать значение этого свойства поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED. *DwStatus* структуры DBPROP указывает DBPROPSTATUS_NOTSUPPORTED.|  
|DBPROP_INIT_LCID|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит проверку кода локали и возвращает ошибку, если код локали не поддерживается или не установлен на клиенте.|  
|DBPROP_INIT_LOCATION|При попытке задать значение этого свойства поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED. *DwStatus* структуры DBPROP указывает DBPROPSTATUS_NOTSUPPORTED.|  
|DBPROP_INIT_MODE|При попытке задать значение этого свойства поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED. *DwStatus* структуры DBPROP указывает DBPROPSTATUS_NOTSUPPORTED.|  
|DBPROP_INIT_PROMPT|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает все режимы запросов на инициализацию источника данных. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию использует для этого свойства значение DBPROMPT_NOPROMPT.|  
|DBPROP_INIT_PROTECTION_LEVEL|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает уровень защиты для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> При попытке задать значение этого свойства поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED. *DwStatus* структуры DBPROP указывает DBPROPSTATUS_NOTSUPPORTED.|  
|DBPROP_INIT_PROVIDERSTRING|См. строку поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ниже в этом разделе.|  
|DBPROP_INIT_TIMEOUT|Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку при инициализации, если в течение указанного количества секунд не удалось установить соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 В специфический для поставщика наборе свойств DBPROPSET_SQLSERVERDBINIT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента определяет следующие дополнительные свойства инициализации.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|SSPROP_AUTH_OLD_PASSWORD|Тип: VT_BSTR<br /><br /> Записи R Чтение и запись:<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Описание: Действующей или устаревшей пароль. Дополнительные сведения см. в разделе [программно изменять пароли](../../relational-databases/native-client/features/changing-passwords-programmatically.md).|  
|SSPROP_INIT_APPNAME|Тип: VT_BSTR<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Описание: Имя клиентского приложения.|  
|SSPROP_INIT_AUTOTRANSLATE|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_TRUE<br /><br /> Описание: Преобразование символов OEM/ANSI.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента преобразует символьные строки ANSI, отправляемые между клиентом и сервером с использованием Юникода свести к минимуму проблемы сопоставления символов национального алфавита кодовые страницы на клиенте и сервере:<br /><br /> Данные клиента DBTYPE_STR, отправленные в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char**, **varchar**, или **текст** переменной, параметра или столбца преобразуются в Юникод с использованием кодовой страницы ANSI клиента (ACP) и затем преобразуются из Юникода с помощью ACP сервера.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**char**, **varchar**, или **текст** данные, отправляемые в переменную DBTYPE_STR на клиенте преобразуются в Юникод с использованием ACP сервера и затем преобразуется из Юникода с помощью ACP клиента.<br /><br /> Эти преобразования выполняются на клиенте поставщиком OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для этого на клиенте должна быть доступна та же кодовая страница, что используется на сервере.<br /><br /> Следующие параметры не влияют на преобразования, выполняемые для этих передач.<br /><br /> Данные клиента DBTYPE_WSTR в Юникоде, отправленные в **char**, **varchar**, или **текст** на сервере.<br /><br /> **char**, **varchar**, или **текст** сервера данные, отправляемые в переменной DBTYPE_WSTR в Юникоде на клиенте.<br /><br /> Данные клиента ANSI DBTYPE_STR, отправленные в Юникоде **nchar**, **nvarchar**, или **ntext** на сервере.<br /><br /> Юникод **char**, **varchar**, или **текст** сервера данные, отправляемые в переменную ANSI DBTYPE_STR на стороне клиента.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не выполняет преобразование символов.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не преобразует клиента символов ANSI DBTYPE_STR данные, отправляемые **char**, **varchar**, или **текст** переменных, параметров или столбцов на сервере. Преобразование не выполняется на **char**, **varchar**, или **текст** данные, отправляемые с сервера в переменные DBTYPE_STR на клиенте.<br /><br /> Если на клиенте и на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются разные ACP, то символы национальных алфавитов могут быть преобразованы неправильно.|  
|SSPROP_INIT_CURRENTLANGUAGE|Тип: VT_BSTR<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Описание: A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя языка. Указывает язык, используемый для выбора и форматирования системных сообщений. Язык должен быть установлен на компьютере, на котором запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в противном случае инициализация источника данных не будет выполнена.|  
|SSPROP_INIT_DATATYPECOMPATIBILITY|Тип: VT_UI2<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: 0<br /><br /> Описание: Совместимость типов данных позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и объектов данных ActiveX (ADO) приложения. Если установлено значение 0 (по умолчанию), то используется та же обработка типов данных, которая применяется поставщиком. Если установлено значение 80, то для обработки типов данных используются только типы данных [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Дополнительные сведения см. в разделе [с помощью ADO с собственным клиентом SQL Server](../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).|  
|SSPROP_INIT_ENCRYPT|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Для шифрования данных, передаваемых по сети, необходимо присвоить свойству SSPROP_INIT_ENCRYPT имеет значение VARIANT_TRUE.<br /><br /> Если включено принудительное шифрование протокола, то шифрование данных производится всегда, независимо от значения SSPROP_INIT_ENCRYPT. Если оно отключено, а для свойства SSPROP_INIT_ENCRYPT задано значение VARIANT_TRUE, то шифрование будет выполняться.<br /><br /> Если шифрование протокола отключено, а для свойства SSPROP_INIT_ENCRYPT задано значение VARIANT_FALSE, то шифрование не будет выполняться.|  
|SSPROP_INIT_FAILOVERPARTNER|Тип: VT_BSTR<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Описание: Определяет имя участника отработки отказа для зеркального отображения базы данных. Является свойством инициализации и может быть задано только перед инициализацией. После инициализации оно будет возвращать имя партнера по обеспечению отработки отказа (если есть), возвращенное сервером-источником.<br /><br /> Это позволяет смарт-приложениям кэшировать последний определенный сервер резервного копирования, однако они должны учитывать, что данные обновляются только при первом установлении соединения (или при возобновлении, при наличии пула) и могут устареть в случае длительных соединений.<br /><br /> После установления соединения приложение может запросить этот атрибут, чтобы идентифицировать партнера по обеспечению отработки отказа. Если сервер-источник не имеет партнера по обеспечению отработки отказа, то это свойство вернет пустую строку. Дополнительные сведения см. в разделе [использование зеркального отображения базы данных](../../relational-databases/native-client/features/using-database-mirroring.md).|  
|SSPROP_INIT_FILENAME|Тип: VT_BSTR<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Описание: Задает имя первичного файла присоединяемой базы данных. Эта база данных присоединяется и становится для соединения базой данных по умолчанию. Перед использованием свойства SSPROP_INIT_FILENAME необходимо указать имя базы данных в свойстве инициализации DBPROP_INIT_CATALOG. Если имя базы данных не существует, то выполняется поиск имени первичного файла, указанного в свойстве SSPROP_INIT_FILENAME, и присоединяется база данных с именем, указанным в свойстве DBPROP_INIT_CATALOG. Если база данных уже была присоединена, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ее снова не присоединяет.|  
|SSPROP_INIT_MARSCONNECTION|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Определяет, разрешены для соединения нескольких активные результирующие наборы (MARS). Перед установлением соединения с базой данных этот параметр должен быть установлен в значение true. Дополнительные сведения см. в разделе [с помощью нескольких активных результирующих наборов &#40; Режим MARS &#41; ](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).|  
|SSPROP_INIT_NETWORKADDRESS|Тип: VT_BSTR<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Описание: Сетевой адрес сервера, где запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указанного в свойстве DBPROP_INIT_DATASOURCE.|  
|SSPROP_INIT_NETWORKLIBRARY|Тип: VT_BSTR<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Описание: Имя сетевой библиотеки (DLL), используемый для обмена данными с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не должно включать путь или расширение DLL.<br /><br /> Значение по умолчанию можно настроить с помощью средства настройки клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Примечание: Только TCP и именованные каналы поддерживаются этим свойством. Если указан префикс, то это приведет к образованию двойного префикса и вызовет ошибку, поскольку это свойство создает префиксы внутри себя.|  
|SSPROP_INIT_PACKETSIZE|Тип: VT_I4<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Описание: Размер сетевого пакета в байтах. Значение свойства «размер пакета» должно находиться в диапазоне от 512 до 32 767. По умолчанию для поставщика OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство «размер сетевого пакета» имеет значение 4 096.|  
|SSPROP_INIT_TAGCOLUMNCOLLATION|Тип: BOOL<br /><br /> Записи R Чтение и запись:<br /><br /> По умолчанию: FALSE<br /><br /> Описание: Используются во время обновления базы данных, при использовании серверных курсоров. Это свойство добавляет к данным сведения о параметрах сортировки, полученные с сервера, а не кодовую страницу клиента. В настоящее время это свойство используется только процессом обработки распределенных запросов, поскольку он знает параметры сортировки данных назначения и может правильно их преобразовать.|  
|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Используется для включения или отключения проверки сертификата сервера. Это свойство доступно для чтения и записи, но попытка его установки после установления соединения приведет к ошибке.<br /><br /> Это свойство не используется, если на клиенте настроен запрос проверки сертификата. Однако приложение может использовать его вместе со свойством SSPROP_INIT_ENCRYPT, чтобы обеспечить шифрование соединения с сервером, даже если на клиенте не установлен сертификат и не настроен запрос проверки сертификата.<br /><br /> Клиентские приложения могут запрашивать это свойство после открытия соединения для получения используемых параметров шифрования и проверки.<br /><br /> Примечание: Использование шифрования без сертификата проверки обеспечивает частичную защиту от перехвата пакетов, но не защищает от атак в середине. Оно лишь позволяет шифровать имя входа и данные, передаваемые на сервер, без проверки сертификата сервера.<br /><br /> Дополнительные сведения см. в разделе [использование шифрования без проверки](../../relational-databases/native-client/features/using-encryption-without-validation.md).|  
|SSPROP_INIT_USEPROCFORPREP|Тип: VT_I4<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: SSPROPVAL_USEPROCFORPREP_ON<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использование хранимой процедуры. Определяет использование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] временные хранимые процедуры для поддержки **ICommandPrepare** интерфейса. Это свойство имело значение только при соединении с сервером SQL Server 6.5. Для более поздних версий это свойство не используется.<br /><br /> SSPROPVAL_USEPROCFORPREP_OFF: Временная хранимая процедура не создается при подготовке команды.<br /><br /> SSPROPVAL_USEPROCFORPREP_ON: Временная хранимая процедура создается при подготовке команды. Временные хранимые процедуры удаляются при освобождении сеанса.<br /><br /> SSPROPVAL_USEPROCFORPREP_ON_DROP: Временная хранимая процедура создается при подготовке команды. Процедура удаляется, если команда не поддерживается с **ICommandPrepare::Unprepare**, когда новая команда для объекта команды методом **ICommandText::SetCommandText**, или освобождения всех ссылок на команду приложения.|  
|SSPROP_INIT_WSID|Тип: VT_BSTR<br /><br /> R Чтение и запись: чтение и запись<br /><br /> Описание: Строка, идентифицирующая рабочую станцию.|  
  
 В специфический для поставщика наборе свойств DBPROPSET_SQLSERVERDATASOURCEINFO [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента определяет дополнительные свойства см. в разделе [свойства сведений об источнике данных](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md) для получения дополнительной информации.  
  
## <a name="the-sql-server-native-client-ole-db-provider-string"></a>Строка поставщика OLE DB для собственного клиента SQL Server  
 Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распознает синтаксис ODBC в значениях свойств строки поставщика. Свойство строки поставщика задается как значение свойства инициализации DBPROP_INIT_PROVIDERSTRING при установлении соединения с источником данных OLE DB. Это свойство содержит данные для подключения, определяемые поставщиком OLE DB и необходимые для установления соединения с источником данных OLE DB. В этой строке элементы разделяются точкой с запятой. За последним элементом в строке также должна стоять точка с запятой. Каждый элемент состоит из ключевого слова, символа «=» и значения, переданного при инициализации. Например:  
  
```  
Server=MyServer;UID=MyUserName;  
```  
  
 Потребитель не должен использовать свойство строки поставщика с поставщиком OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Потребитель может задать любое свойство инициализации, отраженное в строке поставщика, с помощью свойств инициализации, определяемых поставщиком OLE DB или поставщиком OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список ключевых слов, доступных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента в разделе [с помощью ключевых слов строки подключения с собственным клиентом SQL Server](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
## <a name="see-also"></a>См. также:  
 [Объекты источника данных &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  