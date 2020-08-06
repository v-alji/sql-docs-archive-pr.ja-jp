---
title: 'sql: マップ済み (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapped annotation
- element mapping [SQLXML], XML Bulk Load
- attribute mapping [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:mapped
- column mapping [SQLXML]
ms.assetid: 7042741e-ce4d-4912-9c4a-d77194a028fc
author: rothja
ms.author: jroth
ms.openlocfilehash: 2cbccf271e069cd87860af672fed6c4bab462b41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640846"
---
# <a name="sqlmapped-sqlxml-40"></a><span data-ttu-id="3beb5-102">sql:mapped (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="3beb5-102">sql:mapped (SQLXML 4.0)</span></span>
  <span data-ttu-id="3beb5-103">XML 一括読み込みで `sql:mapped` は、XSD スキーマの注釈が想定どおりに処理されます。つまり、マッピングスキーマで `sql:mapped="false"` 任意の要素または属性にが指定されている場合、Xml 一括読み込みでは、関連付けられたデータは対応する列に格納されません。</span><span class="sxs-lookup"><span data-stu-id="3beb5-103">XML Bulk Load processes the `sql:mapped` annotation in the XSD schema as expected-that is, if the mapping schema specifies `sql:mapped="false"` for any element or attribute, XML Bulk Load does not attempt to store the associated data in the corresponding column.</span></span>  
  
 <span data-ttu-id="3beb5-104">XML 一括読み込みでは、スキーマに記述されていないか、XSD スキーマで `sql:mapped="false"` 注釈が付けられているためマップされない要素と属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="3beb5-104">XML Bulk Load ignores elements and attributes that are not mapped (either because they are not described in the schema, or because they are annotated in the XSD schema with `sql:mapped="false"`).</span></span> <span data-ttu-id="3beb5-105">`sql:overflow-field` を使用してオーバフロー列が指定されている場合、マップされないデータはすべてこの列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="3beb5-105">All unmapped data goes into the overflow column, if such a column is specified by using `sql:overflow-field`.</span></span>  
  
 <span data-ttu-id="3beb5-106">たとえば、次の XSD スキーマを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="3beb5-106">For example, consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="1">  
<xsd:complexType>  
<xsd:sequence>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
       <xsd:attribute name="CustomerID"  type="xsd:integer" />  
       <xsd:attribute name="CompanyName" type="xsd:string" />  
       <xsd:attribute name="City"        type="xsd:string" />  
       <xsd:attribute name="HomePhone"   type="xsd:string"   
                                       sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:sequence>  
</xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="3beb5-107">**HomePhone**属性ではが指定されているため `sql:mapped="false"` 、XML 一括読み込みでは、この属性は対応する列にマップされません。</span><span class="sxs-lookup"><span data-stu-id="3beb5-107">Because the **HomePhone** attribute specifies `sql:mapped="false"`, XML Bulk Load does not map this attribute to the corresponding column.</span></span> <span data-ttu-id="3beb5-108">XSD スキーマでは、XML 一括読み込みでこの未使用データが格納されるオーバーフロー列 (**OverflowColumn**) が識別されます。</span><span class="sxs-lookup"><span data-stu-id="3beb5-108">The XSD schema identifies an overflow column (**OverflowColumn**) in which XML Bulk Load stores this unconsumed data.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="3beb5-109">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="3beb5-109">To test a working sample</span></span>  
  
1.  <span data-ttu-id="3beb5-110">次のテーブルを**tempdb**データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="3beb5-110">Create the following table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust  
              (CustomerID     int         PRIMARY KEY,  
               CompanyName    varchar(20) NOT NULL,  
               City           varchar(20) DEFAULT 'Seattle',  
               OverflowColumn nvarchar(200))  
    GO  
    ```  
  
2.  <span data-ttu-id="3beb5-111">この例のスキーマを SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="3beb5-111">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="3beb5-112">次のサンプル XML データを SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="3beb5-112">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai"   
                 City="NY" HomePhone="111-1111" />  
      <Customers CustomerID="1112" CompanyName="Dont Know"   
                 City="LA" HomePhone="222-2222" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="3beb5-113">XML 一括読み込みを実行するには、この [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) の例を Sample.vbs として保存し実行します。</span><span class="sxs-lookup"><span data-stu-id="3beb5-113">To execute XML Bulk Load, save and execute this [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as Sample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 <span data-ttu-id="3beb5-114">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="3beb5-114">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
   <ElementType name="Customers" sql:relation="Cust"  
                             sql:overflow-field="OverflowColumn" >  
      <AttributeType name="CustomerID" />  
      <AttributeType name="CompanyName"  />  
      <AttributeType name="City"  />  
      <AttributeType name="HomePhone" />  
      <attribute type="CustomerID"  />  
      <attribute type="CompanyName"  />  
      <attribute type="City" />  
      <attribute type="HomePhone" sql:map-field="0" />  
   </ElementType>  
</Schema>  
```  
  
  
