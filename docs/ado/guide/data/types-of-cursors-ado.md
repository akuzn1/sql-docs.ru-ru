---
title: Типы курсоров (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], types
ms.assetid: 7cc01544-e814-403b-bbfe-a2750bf921bd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db77de95e83e596a8a301fa65885ee640c742a71
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52543563"
---
# <a name="types-of-cursors-ado"></a>Типы курсоров (ADO)
Как правило приложение должно использовать самый простой курсор, который предоставляет доступ, необходимые данные. Дополнительные курсора характеристик некоторые особенности (однопроходный, только для чтения, статический прокрутки, без буферизации) имеет цену - в клиентской памяти, сетевой нагрузки или производительности. Во многих случаях параметры курсора по умолчанию создаются более сложные курсора, чем действительно требуется приложению.  
  
 Выбор типа курсора зависит от того, в том, как приложение использует результирующий набор, а также на несколько аспектов, включая размер результирующего набора, процент часто используемых данных, чувствительность к изменения данных и производительности приложений требования.  
  
 Самое простое Выбор курсора зависит от того, нужно ли изменить или просто просмотреть данные:  
  
-   Если нужно прокручивать набор результатов, но не изменения данных, используйте [последовательного](../../../ado/guide/data/forward-only-cursors.md) или [статический](../../../ado/guide/data/static-cursors.md) курсора.  
  
-   Если у вас есть большой результирующий набор и вам необходимо выбрать несколько строк, используйте [keyset](../../../ado/guide/data/keyset-cursors.md) курсора.  
  
-   Если вы хотите синхронизировать результирующий набор с последних добавляет, изменяет и удаляет все одновременно работающие пользователи, используйте [динамическое](../../../ado/guide/data/dynamic-cursors.md) курсора.  
  
 Несмотря на то, что каждый тип курсора кажется distinct, имейте в виду, что эти типы курсоров не так много разных видов просто в результате перекрывающиеся характеристики и параметры.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Курсоры последовательного доступа](../../../ado/guide/data/forward-only-cursors.md)  
  
-   [Статические курсоры](../../../ado/guide/data/static-cursors.md)  
  
-   [Курсоры ключевого набора](../../../ado/guide/data/keyset-cursors.md)  
  
-   [Динамические курсоры](../../../ado/guide/data/dynamic-cursors.md)  
  
## <a name="see-also"></a>См. также  
 [Однопроходные курсоры](../../../ado/guide/data/forward-only-cursors.md)   
 [Статические курсоры](../../../ado/guide/data/static-cursors.md)   
 [Управляемые набором ключей курсоры](../../../ado/guide/data/keyset-cursors.md)   
 [Динамические курсоры](../../../ado/guide/data/dynamic-cursors.md)
