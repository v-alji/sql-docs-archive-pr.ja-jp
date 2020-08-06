---
title: 'Sql を使用した定数要素の作成: 定数 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: rothja
ms.author: jroth
ms.openlocfilehash: 8deedd8547d6bc3f0154eedb889ad908750f071a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717625"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a><span data-ttu-id="62d8c-102">sql:is-constant を使用した、定数要素の作成 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="62d8c-102">Creating Constant Elements Using sql:is-constant (SQLXML 4.0)</span></span>
  <span data-ttu-id="62d8c-103">定数要素 (つまり、データベーステーブルまたは列にマップされない XSD スキーマの要素) を指定するには、注釈を使用し `sql:is-constant` ます。</span><span class="sxs-lookup"><span data-stu-id="62d8c-103">To specify a constant element-that is, an element in the XSD schema that does not map to any database table or column-you can use the `sql:is-constant` annotation.</span></span> <span data-ttu-id="62d8c-104">この注釈はブール値 (0 = false、1 = true) をとります。</span><span class="sxs-lookup"><span data-stu-id="62d8c-104">This annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="62d8c-105">指定できる値は 0、1、true、false です。</span><span class="sxs-lookup"><span data-stu-id="62d8c-105">The acceptable values are 0, 1, true, and false.</span></span> <span data-ttu-id="62d8c-106">`sql:is-constant` 注釈は、属性のない要素に指定できます。</span><span class="sxs-lookup"><span data-stu-id="62d8c-106">The `sql:is-constant` annotation can be specified on an element that does not have any attributes.</span></span> <span data-ttu-id="62d8c-107">この注釈を値 true (または 1) と共に要素に指定した場合、その要素は XML ドキュメント内に表示されますが、データベースにはマップされなくなります。</span><span class="sxs-lookup"><span data-stu-id="62d8c-107">If it is specified on an element with the value true (or 1), that element is not mapped to the database but still appears in the XML document.</span></span>  
  
 <span data-ttu-id="62d8c-108">`sql:is-constant` 注釈は次の目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="62d8c-108">The `sql:is-constant` annotation can be used for:</span></span>  
  
-   <span data-ttu-id="62d8c-109">最上位要素を XML ドキュメントに追加する。</span><span class="sxs-lookup"><span data-stu-id="62d8c-109">Adding a top-level element to the XML document.</span></span> <span data-ttu-id="62d8c-110">XML では、ドキュメントに 1 つの最上位要素 (ルート要素) が必要です。</span><span class="sxs-lookup"><span data-stu-id="62d8c-110">XML requires a single top-level element (root element) for the document.</span></span>  
  
-   <span data-ttu-id="62d8c-111">**\<Orders>** すべての注文をラップする要素などのコンテナー要素を作成する。</span><span class="sxs-lookup"><span data-stu-id="62d8c-111">Creating container elements, such as an **\<Orders>** element that wraps all orders.</span></span>  
  
 <span data-ttu-id="62d8c-112">`sql:is-constant`注釈は要素に追加でき **\<complexType>** ます。</span><span class="sxs-lookup"><span data-stu-id="62d8c-112">The `sql:is-constant` annotation can be added to a **\<complexType>** element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="62d8c-113">例</span><span class="sxs-lookup"><span data-stu-id="62d8c-113">Examples</span></span>  
 <span data-ttu-id="62d8c-114">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="62d8c-114">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="62d8c-115">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d8c-115">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a><span data-ttu-id="62d8c-116">A.</span><span class="sxs-lookup"><span data-stu-id="62d8c-116">A.</span></span> <span data-ttu-id="62d8c-117">sql:is-constant を指定してコンテナー要素を追加する</span><span class="sxs-lookup"><span data-stu-id="62d8c-117">Specifying sql:is-constant to add a container element</span></span>  
 <span data-ttu-id="62d8c-118">この注釈付き XSD スキーマで **\<CustomerOrders>** は、値が1の属性を指定することによって、が定数要素として定義され `sql:is-constant` ます。</span><span class="sxs-lookup"><span data-stu-id="62d8c-118">In this annotated XSD schema, **\<CustomerOrders>** is defined as a constant element by specifying the `sql:is-constant` attribute with a value of 1.</span></span> <span data-ttu-id="62d8c-119">したがって、 **\<CustomerOrders>** は、どのデータベーステーブルまたは列にもマップされません。</span><span class="sxs-lookup"><span data-stu-id="62d8c-119">Therefore, **\<CustomerOrders>** is not mapped to any database table or column.</span></span> <span data-ttu-id="62d8c-120">この定数要素は、子要素で構成さ **\<Order>** れます。</span><span class="sxs-lookup"><span data-stu-id="62d8c-120">This constant element consists of the **\<Order>** child elements.</span></span>  
  
 <span data-ttu-id="62d8c-121">**\<CustomerOrders>** はどのデータベーステーブルまたは列にもマップされませんが、結果の XML には子要素を含むコンテナー要素として表示され **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="62d8c-121">Although **\<CustomerOrders>** does not map to any database table or column, it still appears in the resulting XML as a container element containing the **\<Order>** child elements.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="62d8c-122">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="62d8c-122">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="62d8c-123">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="62d8c-123">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="62d8c-124">isConstant.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="62d8c-124">Save the file as isConstant.xml.</span></span>  
  
2.  <span data-ttu-id="62d8c-125">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="62d8c-125">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="62d8c-126">isConstant.xml を保存したディレクトリに isConstantT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="62d8c-126">Save the file as isConstantT.xml in the same directory where you saved isConstant.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="62d8c-127">マッピング スキーマ (isConstant.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="62d8c-127">The directory path specified for the mapping schema (isConstant.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="62d8c-128">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="62d8c-128">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  <span data-ttu-id="62d8c-129">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="62d8c-129">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="62d8c-130">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d8c-130">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="62d8c-131">結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="62d8c-131">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
