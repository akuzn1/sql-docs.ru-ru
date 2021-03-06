---
title: Настройка доступа к внешним данным в PolyBase с помощью универсальных типов ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 10/16/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 3cb5efcb4c4abdc29aa71bf4a5e59ebe039d8a9e
ms.sourcegitcommit: ee76381cfb1c16e0a063315c9c7005f10e98cfe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072849"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Настройка PolyBase для доступа к внешним данным в SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

PolyBase в SQL Server 2019 позволяет подключаться к совместимым источникам данных ODBC через соединитель ODBC. 

## <a name="prerequisites"></a>предварительные требования

Примечание. Эта функция поддерживает только SQL Server в Windows. 

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md).

Сначала скачайте и установите драйвер ODBC источника данных, к которому нужно подключиться на всех узлах PolyBase. После установки драйвера вы можете просмотреть и протестировать его в разделе "Администратор источников данных ODBC".

![Масштабируемые группы PolyBase](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

> **ВАЖНО!**
> 
> Для улучшения работы запросов включите для драйвера пулы соединений. Это можно сделать в разделе "Администратор источников данных ODBC".
> 
> **Примечание**
> 
> При создании внешнего источника данных (шаг 3 выше) потребуется указать имя драйвера (в примере обведено красным).

## <a name="create-an-external-table"></a>Создание внешней таблицы

Чтобы запросить данные из источника ODBC, нужно создать внешние таблицы, позволяющие ссылаться на внешние данные. Этот раздел содержит пример кода для создания внешних таблиц.

В этом разделе будут созданы следующие объекты.

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Создайте в базе данных главный ключ, если его нет. Это необходимо для шифрования секрета учетных данных.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
     ```
    ## <a name="arguments"></a>Аргументы
    PASSWORD ='password'

    Пароль, который использовался при шифровке главного ключа базы данных. Аргумент password должен соответствовать требованиям политики паролей Windows на компьютере, где размещается экземпляр SQL Server.

1. Создайте учетные данные в области базы данных для доступа к источнику ODBC.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL credential_name
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

     ```sql
    /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( 
    LOCATION = odbc://<ODBC server address>[:<port>],
    CONNECTION_OPTIONS = 'Driver={<Name of Installed Driver>};
    ServerNode = <name of server  address>:<Port>',
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
    );

     ```


1.  Создайте внешние таблицы для представления данных, хранимых во внешнем источнике, с помощью инструкции [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
     ```sql
     /*  LOCATION: ODBC data source table/view
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE customer(
     C_CUSTKEY INT NOT NULL,
     C_NAME VARCHAR(25) NOT NULL,
     C_ADDRESS VARCHAR(40) NOT NULL,
     C_NATIONKEY INT NOT NULL,
     C_PHONE CHAR(15) NOT NULL,
     C_ACCTBAL DECIMAL(15,2) NOT NULL,
     C_MKTSEGMENT CHAR(10) NOT NULL,
     C_COMMENT VARCHAR(117) NOT NULL
      )
      WITH (
      LOCATION='customer',
      DATA_SOURCE= external_data_source_name
     );
      ```

1. **Необязательно**. Создайте статистику внешней таблицы.

    Чтобы обеспечить оптимальную производительность запросов, мы советуем создать статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, применения фильтров и статистических выражений.

     ```sql
      CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
