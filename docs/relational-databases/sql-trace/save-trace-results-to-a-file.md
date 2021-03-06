---
title: Сохранение результатов трассировки в файл | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 168c3e17cbf01b4a4c85d4374b716d0bbf3b4f59
ms.sourcegitcommit: ddb682c0061c2a040970ea88c051859330b8ac00
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51570474"
---
# <a name="save-trace-results-to-a-file"></a>Сохранение результатов трассировки в файл
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Результаты трассировки можно сохранить в файле. Файл трассировки — это файл, в который записаны результаты трассировки. Файл трассировки может находиться в локальном каталоге (например, C:\\*имя_папки*\\*имя_файла.trc*) или в сетевом (например, \\\имя_компьютера\сетевое_имя\имя_файла.trc).  
  
 Файлы трассировки можно применять для:  
  
-   воспроизведения трассировок;  
  
-   Аудит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   выполнения анализа производительности;  
  
-   сравнения событий трассировки со счетчиками производительности для улучшения распознавания неполадок;  
  
-   выполнения анализа при помощи помощника по настройке ядра СУБД;  
  
-   оптимизации запросов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет результаты трассировки в файле, путь и имя которого указываются в качестве аргумента **@tracefile** хранимой процедуры **sp_trace_create**.  
  
> [!NOTE]  
>  Если для сохранения файла трассировки хранимой процедуре **sp_trace_create** передается путь к файлу, то этот каталог должен быть доступен серверу. Также помните, что если процедуре **sp_trace_create**передается путь к локальному каталогу, то это локальный каталог на данном сервере.  
  
 Если используется [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , результаты трассировки можно сохранить в файле или в таблице. Сохранение результатов трассировки в таблице обеспечивает такой же доступ, как и при сохранении трассировки в файле; помимо этого, для поиска определенных событий можно выполнять запросы к этой таблице.  
  
 Дополнительные сведения о сохранении результатов трассировки см. в разделах [Сохранить результаты трассировки в таблицу (приложение SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) и [Сохранить результаты трассировки в файл (приложение SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md).  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [Создание трассировки (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [Создание трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
