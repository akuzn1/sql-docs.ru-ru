---
title: "Использование транзакций | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 93335b496f798658f2840a1a02757ed0949b9760
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="using-transactions"></a>Использование транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] управление объектов (SMO), обработка транзакций выполняется через подключение к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> объекта. <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Ссылается объект <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server> объекта установления соединения. Такие методы, как <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> и <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A>, принадлежат свойству объекта <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений SMO](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  