---
title: 'sql: overflow フィールド (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: f005182b-6151-432d-ab22-3bc025742cd3
author: rothja
ms.author: jroth
ms.openlocfilehash: ea52eb642964844a03304d082632c2b7157f723b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642720"
---
# <a name="sqloverflow-field-sqlxml-40"></a><span data-ttu-id="432b0-102">sql:overflow-field (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="432b0-102">sql:overflow-field (SQLXML 4.0)</span></span>
  <span data-ttu-id="432b0-103">スキーマでは、XML ドキュメントからのすべての未使用データを受け取るオーバーフロー列を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="432b0-103">In a schema, you can identify a column as an overflow column to receive all unconsumed data from the XML document.</span></span> <span data-ttu-id="432b0-104">この列は、スキーマ内で `sql:overflow-field` 注釈により指定します。</span><span class="sxs-lookup"><span data-stu-id="432b0-104">This column is specified in the schema by using the `sql:overflow-field` annotation.</span></span> <span data-ttu-id="432b0-105">オーバーフロー列は複数指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="432b0-105">It is possible to have multiple overflow columns.</span></span>  
  
 <span data-ttu-id="432b0-106">`sql:overflow-field` 注釈が定義されている XML ノード (要素または属性) がスコープ内に入るとオーバーフロー列がアクティブになり、未使用データがこの列に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="432b0-106">Whenever an XML node (element or attribute) for which there is a `sql:overflow-field` annotation defined enters into scope, the overflow column is activated and receives unconsumed data.</span></span> <span data-ttu-id="432b0-107">ノードがスコープ外に出ると、オーバーフロー列はアクティブではなくなります。それまでのオーバーフロー フィールドがある場合は、XML 一括読み込みによってそのフィールドがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="432b0-107">When the node goes out of scope, the overflow column is no longer active and XML Bulk Load makes the previous overflow field (if any) active.</span></span>  
  
 <span data-ttu-id="432b0-108">XML 一括読み込みでは、オーバーフロー列へのデータの格納時に、`sql:overflow-field` が定義されている親要素の開始タグと終了タグも格納されます。</span><span class="sxs-lookup"><span data-stu-id="432b0-108">As it stores data in the overflow column, XML Bulk Load also stores the opening and closing tags of the parent element for which `sql:overflow-field` is defined.</span></span>  
  
 <span data-ttu-id="432b0-109">たとえば、次のスキーマでは、要素と要素が記述されて **\<Customers>** **\<CustOrder>** います。</span><span class="sxs-lookup"><span data-stu-id="432b0-109">For example, the following schema describes the **\<Customers>** and **\<CustOrder>** elements.</span></span> <span data-ttu-id="432b0-110">これらの要素それぞれに、オーバーフロー列が指定されています。</span><span class="sxs-lookup"><span data-stu-id="432b0-110">Each of these elements identifies an overflow column:</span></span>  
  
```  
<?xml version="1.0" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
 <xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
        parent="Cust"  
        parent-key="CustomerID"  
        child="CustOrder"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
 </xsd:annotation>  
 <xsd:element name="ROOT" sql:is-constant="1">  
  <xsd:complexType>  
    <xsd:sequence>   
      <xsd:element name="Customers"   
                   sql:relation="Cust"  
                   sql:overflow-field="OverflowColumn">  
        <xsd:complexType>  
             <xsd:sequence>   
             <xsd:element name="CustomerID" type="xsd:integer"/>  
             <xsd:element name="CompanyName"  type="xsd:string"/>  
             <xsd:element name="City" type="xsd:string"/>  
             <xsd:element name="Order"  
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder"  
                          sql:overflow-field="OverflowColumn">  
               <xsd:complexType>  
                 <xsd:attribute name="OrderID"/>  
                 <xsd:attribute name="CustomerID"/>  
               </xsd:complexType>  
             </xsd:element>  
          </xsd:sequence>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="432b0-111">スキーマでは、 **\<Customer>** 要素は Cust テーブルにマップされ、 **\<Order>** 要素は custorder テーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="432b0-111">In the schema, the **\<Customer>** element maps to the Cust table and the **\<Order>** element maps to the CustOrder table.</span></span>  
  
 <span data-ttu-id="432b0-112">要素と要素は、どちらも **\<Customer>** **\<Order>** オーバーフロー列を識別します。</span><span class="sxs-lookup"><span data-stu-id="432b0-112">Both the **\<Customer>** and **\<Order>** elements identify an overflow column.</span></span> <span data-ttu-id="432b0-113">したがって、XML 一括読み込みでは、すべての未使用の子要素と要素の属性が、 **\<Customer>** Cust テーブルのオーバーフロー列と、 **\<Order>** custorder テーブルのオーバーフロー列にある要素のすべての未使用の子要素と属性に保存されます。</span><span class="sxs-lookup"><span data-stu-id="432b0-113">Thus, XML Bulk Load saves all the unconsumed child elements and attributes of the **\<Customer>** element in the overflow column of the Cust table, and all the unconsumed child elements and attributes of the **\<Order>** element in the overflow column of the CustOrder table.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="432b0-114">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="432b0-114">To test a working sample</span></span>  
  
1.  <span data-ttu-id="432b0-115">この例のスキーマを SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="432b0-115">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="432b0-116">次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="432b0-116">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
              CustomerID     int         PRIMARY KEY,  
              CompanyName    varchar(20) NOT NULL,  
              City           varchar(20) DEFAULT 'Seattle',  
              OverflowColumn nvarchar(200))  
    GO  
    CREATE TABLE CustOrder (  
              OrderID        int         PRIMARY KEY,  
              CustomerID     int         FOREIGN KEY REFERENCES  
                                              Cust(CustomerID),  
              OverflowColumn nvarchar(200))  
    GO  
    ```  
  
3.  <span data-ttu-id="432b0-117">次のサンプル XML データを SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="432b0-117">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
          <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
     </Customers>  
     <Customers>  
       <CustomerID>1112</CustomerID>  
       <CompanyName>Toms Spezialitten</CompanyName>  
       <City><![CDATA[LA]]> </City>  
       <xyz><address>111 Maple, Seattle</address></xyz>     
       <Order OrderID="3" />  
     </Customers>  
       <Customers>  
       <CustomerID>1113</CustomerID>  
       <CompanyName>Victuailles en stock</CompanyName>  
       <Order OrderID="4" />  
      </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="432b0-118">XML 一括読み込みを実行するには、この [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) の例を Sample.vbs として保存し実行します。</span><span class="sxs-lookup"><span data-stu-id="432b0-118">To execute XML Bulk Load, save and execute this [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as Sample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
