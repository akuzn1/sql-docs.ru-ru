---
title: "Ограничения инструкции DROP таблицы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, DROP TABLE statement limitations
- DROP TABLE statement limitations [ODBC]
ms.assetid: 0a1c80f5-c9f2-4655-9bfd-0131b2f015a9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 65c47ece213312b749dee0e83b76e8de89cf3dc9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="drop-table-statement-limitations"></a>Удалите оператор ограничения таблицы
При использовании драйвера Microsoft Excel 5.0, 7.0 или 97 инструкцию DROP TABLE удаляет листа, но не удаляет имя листа. Так как имя листа по-прежнему существуют в книге, невозможно создать другой лист с тем же именем.