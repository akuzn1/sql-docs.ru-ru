---
title: Запуск трассировки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1c53c039d6194edbc37438ef30ac4fef0113ae87
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794066"
---
# <a name="start-a-trace"></a>Запуск трассировки
  После определения новой трассировки или создания шаблона при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]можно запускать, приостанавливать или останавливать сбор данных, используя новое определение трассировки или новый шаблон.  
  
## <a name="starting-a-trace"></a>Запуск трассировки  
 Когда запускается трассировка, а определенным источником является экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] или служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает очередь, служащую для временного хранения данных о зарегистрированных серверных событиях.  
  
 При обращении к инструменту трассировки SQL посредством приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] открывается новое окно трассировки (если ни одно такое окно еще не открыто) и немедленно выполняется регистрация данных.  
  
 Если обращение следует к механизму трассировки SQL с использованием системных хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] , трассировку нужно запускать каждый раз, когда экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] начинает регистрацию данных. После запуска трассировки можно изменить только ее имя.  
  
> [!NOTE]  
>  При работе с существующими трассировками можно просматривать свойства, но нельзя изменять их. Чтобы изменить свойства, необходимо остановить или приостановить трассировку.  
  
## <a name="see-also"></a>См. также  
 [Автоматически запустить трассировку после соединения с сервером (приложение SQL Server Profiler)](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Приостановить трассировку (приложение SQL Server Profiler)](pause-a-trace-sql-server-profiler.md)   
 [Остановка трассировки (приложение SQL Server Profiler)](stop-a-trace-sql-server-profiler.md)   
 [Очистить окно трассировки (приложение SQL Server Profiler)](clear-a-trace-window-sql-server-profiler.md)   
 [Провести трассировку после ее приостановки или прекращения (приложение SQL Server Profiler)](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  
