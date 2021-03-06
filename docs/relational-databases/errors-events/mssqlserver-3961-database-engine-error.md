---
title: MSSQLSERVER_3961 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: db54d59b321bba28f6231679a8098f041e08cd2f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647202"
---
# <a name="mssqlserver3961"></a>MSSQLSERVER_3961
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3961|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|XACT_METADATA_INVALID|  
|Текст сообщения|Ошибка транзакции в режиме изоляции моментального снимка в базе данных «%.*ls»: объект, к которому производится обращение в данной инструкции, был изменен инструкцией DDL другой, параллельной транзакции после начала данной транзакции.  Это запрещено, поскольку управление версиями метаданных не поддерживается. Одновременное обновление метаданных может привести к несогласованности при совместном использовании с режимом изоляции моментального снимка.|  
  
## <a name="explanation"></a>Объяснение  
Эта ошибка может произойти при запросе метаданных в режиме изоляции моментального снимка при одновременном обновлении этих метаданных параллельной инструкцией DDL. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает управление версиями метаданных. Поэтому не все операции DDL могут выполняться в явной транзакции, работающей с уровнем изоляции моментального снимка. Неявная транзакция, по определению, — это единственная инструкция, для которой возможно выполнение семантики изоляции моментального снимка, даже для инструкций DDL. Следующие инструкции DDL нельзя использовать после инструкции BEGIN TRANSACTION в условиях изоляции моментального снимка: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME, а также любые инструкции DDL среды CLR. Эти инструкции разрешены к использованию в неявных транзакциях, работающих при уровне изоляции моментального снимка. Неявная транзакция, по определению, — это единственная инструкция, для которой возможно выполнение семантики изоляции моментального снимка, даже для инструкций DDL.  
  
## <a name="user-action"></a>Действие пользователя  
Перед запросом метаданных измените уровень изоляции моментального снимка на другой уровень изоляции, например на уровень изоляции зафиксированной операции чтения.  
  
