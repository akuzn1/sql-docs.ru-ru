---
title: Ссылки на сборки в RDL-файле | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b15dcac49b4af0df2769080f51e0bf48289c2f60
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56011426"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Ссылки на сборки в RDL-файле
  Для поддержки использования сборок с пользовательским кодом в файлах определения отчета в спецификацию языка определения отчетов были включены два элемента: **CodeModules** и **Classes**.  
  
 Элемент **CodeModules** позволяет ссылаться на сборки с управляемым кодом в выражениях отчета. Элемент высокого уровня **CodeModules** содержит ссылку на сборку, используемую в файлах определения отчета для вызова специализированных функций. Запись в определении отчета, поддерживающая использование пользовательской сборки, может выглядеть следующим образом:  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Вместо вызова метода <xref:System.Reflection.Assembly.Load%2A> в пользовательском коде пользовательские сборки можно зарегистрировать либо вручную, добавив элементы **CodeModule** в RDL-файл, либо использовав вкладку **Ссылки** в диалоговом окне **Свойства отчета**. Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 Элемент **Classes** поддерживает использование членов экземпляров в определении отчета. **Classes** — это высокоуровневый элемент, содержащий ссылку на имя класса и имя экземпляра. Запись в определении отчета, поддерживающая использование членов экземпляров может выглядеть следующим образом:  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Дополнительные сведения о доступе к коду см. в разделе [Доступ к пользовательским сборкам посредством выражений](accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>См. также  
 [Использование пользовательских сборок с отчетами](using-custom-assemblies-with-reports.md)  
  
  
