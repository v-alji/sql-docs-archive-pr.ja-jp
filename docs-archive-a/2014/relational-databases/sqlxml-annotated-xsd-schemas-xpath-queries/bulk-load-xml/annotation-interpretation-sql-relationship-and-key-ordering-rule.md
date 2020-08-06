---
title: 'sql: relationship とキーの順序付け規則 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
author: rothja
ms.author: jroth
ms.openlocfilehash: 716e911676dc81539fc641bee139d92e29dc49db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642718"
---
# <a name="sqlrelationship-and-the-key-ordering-rule-sqlxml-40"></a><span data-ttu-id="f0505-102">sql:relationship とキーの順序付け規則 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f0505-102">sql:relationship and the Key Ordering Rule (SQLXML 4.0)</span></span>
  <span data-ttu-id="f0505-103">XML 一括読み込みでは、ノードがスコープ内に入るときにレコードが生成され、ノードがスコープ外に出るときに、これらのレコードが Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。したがって、レコードのデータはノードのスコープ内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0505-103">Because XML Bulk Load generates records as their nodes enter into scope and sends those records to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as their nodes exit scope, the data for the record must be present within the scope of the node.</span></span>  
  
 <span data-ttu-id="f0505-104">次の XSD スキーマについて考えてみます。このスキーマで **\<Customer>** は、 **\<Order>** 要素と要素 (1 人の顧客が多数の注文を配置できます) の間の一対多リレーションシップが要素を使用して指定されてい `<sql:relationship>` ます。</span><span class="sxs-lookup"><span data-stu-id="f0505-104">Consider the following XSD schema, in which the one-to-many relationship between **\<Customer>** and **\<Order>** elements (one customer can place many orders) is specified by using the `<sql:relationship>` element:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"<>   
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
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="f0505-105">**\<Customer>** 要素ノードがスコープ内に入ると、XML 一括読み込みでは顧客レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f0505-105">As the **\<Customer>** element node enters into scope, XML Bulk Load generates a customer record.</span></span> <span data-ttu-id="f0505-106">このレコードは、XML 一括読み込みが読み取られるまで保持さ **\</Customer>** れます。</span><span class="sxs-lookup"><span data-stu-id="f0505-106">This record stays until XML Bulk Load reads **\</Customer>**.</span></span> <span data-ttu-id="f0505-107">要素ノードの処理では、 **\<Order>** XML 一括読み込みでは、 `<sql:relationship>` **\<Customer>** **\<Order>** **customerid**属性が指定されていないため、親要素から custorder テーブルの customerid 外部キー列の値を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f0505-107">In processing the **\<Order>** element node, XML Bulk Load uses `<sql:relationship>` to obtain the value of the CustomerID foreign key column of the CustOrder table from the **\<Customer>** parent element, because the **\<Order>** element does not specify the **CustomerID** attribute.</span></span> <span data-ttu-id="f0505-108">つまり、要素を定義する際には、 **\<Customer>** を指定する前に、スキーマで**CustomerID**属性を指定する必要があり `<sql:relationship>` ます。</span><span class="sxs-lookup"><span data-stu-id="f0505-108">This means that in defining the **\<Customer>** element, you must specify the **CustomerID** attribute in the schema before you specify `<sql:relationship>`.</span></span> <span data-ttu-id="f0505-109">それ以外の場合、 **\<Order>** 要素がスコープ内に入ると、Xml 一括読み込みでは CustOrder テーブルのレコードが生成されます。また、Xml 一括読み込みが終了タグに達すると、 **\</Order>** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CustomerID 外部キー列の値なしでレコードがに送信されます。</span><span class="sxs-lookup"><span data-stu-id="f0505-109">Otherwise, when an **\<Order>** element enters into scope, XML Bulk Load generates a record for the CustOrder table, and when the XML Bulk Load reaches the **\</Order>** end tag, it sends the record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] without the CustomerID foreign key column value.</span></span>  
  
 <span data-ttu-id="f0505-110">この例のスキーマを SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="f0505-110">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="f0505-111">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="f0505-111">To test a working sample</span></span>  
  
1.  <span data-ttu-id="f0505-112">次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0505-112">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
               CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
               CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="f0505-113">次のサンプル データを SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="f0505-113">Save the following sample data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>    
      <Customers>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
        <CustomerID>1111</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>    
        <Order OrderID="3" />  
        <CustomerID>1112</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
        <CustomerID>1113</CustomerID>  
      </Customers>  
    </ROOT>  
    ```  
  
3.  <span data-ttu-id="f0505-114">XML 一括読み込みを実行するには、次の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) の例を MySample.vbs として保存し、実行します。</span><span class="sxs-lookup"><span data-stu-id="f0505-114">To execute XML Bulk Load, save and execute the following [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as MySample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
     <span data-ttu-id="f0505-115">この結果、XML 一括読み込みでは CustOrder テーブルの CustomerID 外部キー列に NULL 値が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="f0505-115">The result is that XML Bulk Load inserts a NULL value in the CustomerID foreign key column of the CustOrder table.</span></span> <span data-ttu-id="f0505-116">子要素が子要素の前に出現するように XML サンプルデータを変更すると、 **\<CustomerID>** **\<Order>** 必要な結果が得られます。 Xml 一括読み込みでは、指定された外部キー値が列に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="f0505-116">If you revise the XML sample data so that the **\<CustomerID>** child element appears before the **\<Order>** child element, you get the expected result: XML Bulk Load inserts the specified foreign key value into the column.</span></span>  
  
 <span data-ttu-id="f0505-117">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="f0505-117">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID"  />  
   <ElementType name="CompanyName" />  
   <ElementType name="City"        />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
                 <sql:relationship  
                        key-relation    ="Cust"  
                        key             ="CustomerID"  
                        foreign-key     ="CustomerID"  
                        foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
  
