---
title: srv_got_attention (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_got_attention
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1b2b13668c9402d947937b4cc7aeb581c253d6a8
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358396"
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Проверяет, следует ли прервать выполнение текущего задания или разорвать соединение, и возвращает TRUE, если текущее задание было прервано или соединение разорвано.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL srv_got_attention  
(SRV_PROC *  
srvproc  
);  
  
```  
  
#### <a name="parameters"></a>Параметры  
 *srvproc*  
 Указатель, определяющий подключение к базе данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает TRUE, если выполнение текущего пакета было прервано или соединение разорвано. Возвращает FALSE, если текущий пакет по-прежнему выполняется или соединение существует.  
  
## <a name="remarks"></a>Примечания  
 Расширенная хранимая процедура, которая выполняется в течение длительного времени, должна периодически проверять соединение с сервером путем вызова функции **srv_got_attention**, чтобы завершиться, когда прерывается выполнение текущего пакета или разрывается соединение.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
