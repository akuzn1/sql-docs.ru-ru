---
title: "Повышение транзакции | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f37528588c5d302036bb39d3de4349c44120e86f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="transaction-promotion"></a>Повышение транзакции
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Транзакции *продвижение* описывает упрощенным локальным транзакциям, который может быть автоматически повышена до свободно распределяемых транзакций при необходимости. Когда управляемая хранимая процедура запускается в рамках транзакции базы данных на сервере, в контексте локальной транзакции запускается код CLR.  Если соединение с удаленным сервером открывается в рамках транзакции базы данных, это соединение с удаленным сервером прикрепляется к распределенной транзакции, а локальная транзакция автоматически повышается до распределенной транзакции. Таким образом повышение транзакции минимизирует избыток распределенных транзакций, откладывая создание распределенной транзакции до тех пор, пока в ней не возникнет необходимость. Повышение транзакций выполняется автоматически, если она была включена с помощью **Enlist** ключевое слово и не требует вмешательства разработчика. Поставщик данных .NET Framework для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает поддержку повышения транзакций с помощью классов в .NET Framework **System.Data.SqlClient** пространства имен.  
  
## <a name="the-enlist-keyword"></a>Ключевое слово Enlist  
 **ConnectionString** свойство **SqlConnection** поддерживает **Enlist** ключевое слово, которое указывает, является ли **System.Data.SqlClient** обнаруживать контексты транзакций и автоматически прикрепляет соединение к распределенной транзакции. Если для этого ключевого слова задано значение true (по умолчанию), соединение автоматически прикрепляется к текущему контексту транзакции открывающего потока. Если для этого ключевого слова задано значение false, то соединение SqlClient не будет взаимодействовать с распределенной транзакцией. Если **Enlist** не указан в строке соединения, соединение автоматически прикрепляется к распределенной транзакции, если она будет обнаружена при открытии соединения.  
  
## <a name="distributed-transactions"></a>Распределенные транзакции  
 Распределенные транзакции обычно потребляют значительные системные ресурсы. [!INCLUDE[msCoName](../../includes/msconame-md.md)]Координатор распределенных транзакций (MS DTC) управляет такими транзакциями и интегрирует все диспетчеры ресурсов, используемые в этих транзакциях. Повышение уровня транзакции, с другой стороны, является особой формой **System.Transactions** транзакцию, которая фактически передает работу простой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] транзакции. **System.Transactions**, **System.Data.SqlClient**, и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] координируют работу, выполняемую при обработке транзакции, при необходимости повышая ее до полностью распределенной транзакции.  
  
 Преимущество использования повышения транзакций том, что при открытии соединения с активной **TransactionScope** открытых транзакций и другие соединения не, транзакция фиксируется как упрощенная, а не дополнительных затрат, полностью распределенной транзакции. Дополнительные сведения о **TransactionScope**, в разделе [с помощью System.Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md).  
  
## <a name="see-also"></a>См. также:  
 [Интеграция со средой CLR и транзакции](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  