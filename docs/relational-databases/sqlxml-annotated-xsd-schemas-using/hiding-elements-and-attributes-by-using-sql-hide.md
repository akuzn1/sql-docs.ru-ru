---
title: "Скрытие элементов и атрибутов с помощью SQL: hide | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hiding elements
- element mapping [SQLXML], hiding attributes and elements
- hide annotation
- sql:hide
- table/view mapping [SQLXML], hiding attributes and elements
- table mapping [SQLXML], hiding attributes and elements
- hiding attributes
- annotated XSD schemas, hiding attributes and elements
- attribute mapping [SQLXML], hiding attributes and elements
- column mapping [SQLXML]
- element hiding [SQLXML]
- XSD schemas [SQLXML], hiding attributes and elements
- attribute hiding [SQLXML]
ms.assetid: 0978301b-f068-46b6-82b9-dc555161f52e
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80e87266ddb172a77d2e0185cf45096406902d3b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="hiding-elements-and-attributes-by-using-sqlhide"></a>Скрытие элементов и атрибутов при помощи sql:hide
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]При выполнении запроса XPath к схеме XSD результирующий XML-документ содержит элементы и атрибуты, заданные в схеме. Можно указать, что некоторые элементы и атрибуты быть скрыты в схеме с помощью **SQL: hide** заметки. Это может оказаться полезным в тех случаях, когда критерий выбора запроса требует определенных элементов или атрибутов в схеме, но они не должны возвращаться в формируемом XML-документе.  
  
 **SQL: hide** заметка имеет логическое значение (0 = false, 1 = true). Допустимые значения: 0, 1, true и false.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для выполнения примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlhide-on-an-attribute"></a>A. Указание sql:hide для атрибута  
 В этом примере схема XSD состоит из  **\<Person.Contact >** элемент с **ContactID**, **FirstName**, и **LastName** атрибуты.  
  
 **\<Person.Contact >** элемент имеет сложный тип и, таким образом, сопоставляется с таблицей с тем же именем (сопоставление по умолчанию). Все атрибуты  **\<Person.Contact >** элемента относятся к простому типу и сопоставляются со столбцами с теми же именами в Person.Contacttable базы данных AdventureWorks. В схеме **SQL: hide** заметка указывается для **ContactID** атрибута. При выполнении запроса XPath к этой схеме **ContactID** не возвращается в XML-документе.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  sql:hide="true" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем Hide.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем HideT.xml в том же каталоге, где был сохранен файл HideT.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Hide.xml">  
            /Person.Contact[@ContactID="1"]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл Hide.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\Hide.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результирующий набор:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <Person.Contact FirstName="Gustavo" LastName="Achong" />   
</ROOT>  
```  
  
 Когда **SQL: hide** указана для элемента, элемент и его атрибуты или дочерние элементы не отображаются в XML-документ, который создается. Вот другой схемы XSD, в котором **SQL: hide** указано на  **\<OD >** элемента:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:annotation>  
    <xsd:documentation>  
      Sales.Customer-Sales.SalesOrderHeader-Sales.SalesOrderDetail Schema  
      Copyright 2004 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="CustomerOrder"  
         parent="Sales.Customer"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Sales.SalesOrderHeader" />  
       <sql:relationship name="OrderOrderDetails"  
                  parent="Sales.SalesOrderHeader"  
                  parent-key="SalesOrderID"  
                  child-key="SalesOrderID"  
                  child="Sales.SalesOrderDetail"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Sales.Customer">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
                     maxOccurs="unbounded"   
                     sql:relationship="CustomerOrder">  
          <xsd:complexType>  
            <xsd:sequence>  
               <xsd:element name="OD" sql:relation="Sales.SalesOrderDetail"                                       maxOccurs="unbounded"                                       sql:relationship="OrderOrderDetails"                                       sql:hide="1">  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:string"/>  
                    <xsd:attribute name="ProductID" type="xsd:string"/>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string"/>  
          <xsd:attribute name="OID" sql:field="SalesOrderID"   
                                    type="xsd:string"/>  
          <xsd:attribute name="OrderDate" type="xsd:date"/>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CID" sql:field="CustomerID"   
                                type="xsd:string"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 При выполнении запроса XPath (например `/Customers[@CID="1"]`), заданный относительно этой схемы XML-документа, которое создается, не включает  **\<OD >** элемент и его дочерние элементы, как показано в следующем частичном результате:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers CID="1">  
    <Order CustomerID="1" OID="43860" OrderDate="2001-08-01" />   
    <Order CustomerID="1" OID="44501" OrderDate="2001-11-01" />   
    <Order CustomerID="1" OID="45283" OrderDate="2002-02-01" />   
    <Order CustomerID="1" OID="46042" OrderDate="2002-05-01" />   
  </Customers>  
</ROOT>  
```  
  
  