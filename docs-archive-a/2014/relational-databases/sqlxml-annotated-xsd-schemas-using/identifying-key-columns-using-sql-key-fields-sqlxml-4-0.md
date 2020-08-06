---
title: 'Sql: キーフィールドを使用したキー列の識別 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nesting XML results
- proper nesting in results [SQLXML]
- sql:key-fields
- XSD schemas [SQLXML], key columns
- identifying key columns [SQLXML]
- annotated XSD schemas, key columns
- key columns [SQLXML]
- relationships [SQLXML], key columns
- hierarchical relationships [SQLXML]
- key-fields annotation
ms.assetid: 1a5ad868-8602-45c4-913d-6fbb837eebb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ab12b34874a54bad2e08a96d08ebd0cc994f946
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741665"
---
# <a name="identifying-key-columns-using-sqlkey-fields-sqlxml-40"></a><span data-ttu-id="3422a-102">sql:key-fields を使用した、キー列の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="3422a-102">Identifying Key Columns Using sql:key-fields (SQLXML 4.0)</span></span>
  <span data-ttu-id="3422a-103">XSD スキーマに対して XPath クエリを指定する場合、結果内に適切な入れ子を生成するには、多くの場合キー情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="3422a-103">When an XPath query is specified against an XSD schema, key information is required in most cases to obtain proper nesting in the result.</span></span> <span data-ttu-id="3422a-104">`sql:key-fields` 注釈の指定は、適切な階層を確実に生成するための 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="3422a-104">Specifying the `sql:key-fields` annotation is a way of ensuring that the appropriate hierarchy is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3422a-105">適切な入れ子を生成するには、テーブルにマップする要素に `sql:key-fields` を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3422a-105">To ensure proper nesting, it is recommended that you specify `sql:key-fields` for elements that map to tables.</span></span> <span data-ttu-id="3422a-106">作成される XML は、基になる結果セットの順序指定に影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="3422a-106">The XML produced is sensitive to the ordering of the underlying result set.</span></span> <span data-ttu-id="3422a-107">`sql:key-fields` を指定しない場合、適切な XML が作成されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3422a-107">If `sql:key-fields` is not specified, the XML generated might not be formed properly.</span></span>  
  
 <span data-ttu-id="3422a-108">`sql:key-fields` の値で、リレーションの行を一意に識別する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="3422a-108">The value of `sql:key-fields` identifies the column(s) that uniquely identify the rows in the relation.</span></span> <span data-ttu-id="3422a-109">行を一意に識別するために複数の列が必要な場合、列の値はスペースで区切られます。</span><span class="sxs-lookup"><span data-stu-id="3422a-109">If more than one column is required to uniquely identify a row, the column values are delimited by spaces.</span></span>  
  
 <span data-ttu-id="3422a-110">要素に `sql:key-fields` 要素と子要素の間に定義されているが含まれていて **\<sql:relationship>** も、親要素で指定されているテーブルの主キーを提供していない場合は、注釈を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3422a-110">You must use the `sql:key-fields` annotation when an element contains a **\<sql:relationship>** that is defined between the element and a child element but does not provide the primary key of the table that is specified in the parent element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3422a-111">例</span><span class="sxs-lookup"><span data-stu-id="3422a-111">Examples</span></span>  
 <span data-ttu-id="3422a-112">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="3422a-112">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="3422a-113">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3422a-113">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-producing-the-appropriate-nesting-when-sqlrelationship-does-not-provide-sufficient-information"></a><span data-ttu-id="3422a-114">A.</span><span class="sxs-lookup"><span data-stu-id="3422a-114">A.</span></span> <span data-ttu-id="3422a-115">\<sql:relationship>が十分な情報を提供しない場合に適切な入れ子を生成する</span><span class="sxs-lookup"><span data-stu-id="3422a-115">Producing the appropriate nesting when \<sql:relationship> does not provide sufficient information</span></span>  
 <span data-ttu-id="3422a-116">この例では、`sql:key-fields` をどこに指定すればよいかを示します。</span><span class="sxs-lookup"><span data-stu-id="3422a-116">This example shows where `sql:key-fields` must be specified.</span></span>  
  
 <span data-ttu-id="3422a-117">次のスキーマについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="3422a-117">Consider the following schema.</span></span> <span data-ttu-id="3422a-118">スキーマでは、要素と要素の間の階層を指定します。この要素は、 **\<Order>** **\<Customer>** **\<Order>** 要素が親で **\<Customer>** あり、要素が子です。</span><span class="sxs-lookup"><span data-stu-id="3422a-118">The schema specifies a hierarchy between the **\<Order>** and **\<Customer>** elements in which the **\<Order>** element is the parent and the **\<Customer>** element is a child.</span></span>  
  
 <span data-ttu-id="3422a-119">この **\<sql:relationship>** タグは、親子関係を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3422a-119">The **\<sql:relationship>** tag is used to specify the parent-child relationship.</span></span> <span data-ttu-id="3422a-120">このタグでは、Sales.SalesOrderHeader テーブルの CustomerID を親キーとして識別し、Sales.Customer テーブルの子キー CustomerID を参照します。</span><span class="sxs-lookup"><span data-stu-id="3422a-120">It identifies CustomerID in the Sales.SalesOrderHeader table as the parent key that refers to the CustomerID child key in the Sales.Customer table.</span></span> <span data-ttu-id="3422a-121">に指定された情報 **\<sql:relationship>** は、親テーブル (SalesOrderHeader) 内の行を一意に識別するのに十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="3422a-121">The information provided in **\<sql:relationship>** is not sufficient to uniquely identify rows in the parent table (Sales.SalesOrderHeader).</span></span> <span data-ttu-id="3422a-122">`sql:key-fields` 注釈を指定しないと、不正確な階層が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3422a-122">Therefore, without the `sql:key-fields` annotation, the hierarchy that is generated is inaccurate.</span></span>  
  
 <span data-ttu-id="3422a-123">でが指定されている `sql:key-fields` **\<Order>** 場合、注釈は親 (SalesOrderHeader テーブル) 内の行を一意に識別し、その子要素はその親の下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3422a-123">With `sql:key-fields` specified on **\<Order>**, the annotation uniquely identifies the rows in the parent (Sales.SalesOrderHeader table), and its child elements appear below its parent.</span></span>  
  
 <span data-ttu-id="3422a-124">スキーマは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3422a-124">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrdCust"  
        parent="Sales.SalesOrderHeader"  
        parent-key="CustomerID"  
        child="Sales.Customer"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
               sql:key-fields="SalesOrderID">  
   <xsd:complexType>  
     <xsd:sequence>  
     <xsd:element name="Customer" sql:relation="Sales.Customer"   
                       sql:relationship="OrdCust"  >  
       <xsd:complexType>  
         <xsd:attribute name="CustID" sql:field="CustomerID" />  
         <xsd:attribute name="SoldBy" sql:field="SalesPersonID" />  
       </xsd:complexType>  
     </xsd:element>  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name= "CustomerID" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="3422a-125">このスキーマの実際のサンプルを作成するには</span><span class="sxs-lookup"><span data-stu-id="3422a-125">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="3422a-126">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="3422a-126">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="3422a-127">KeyFields1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="3422a-127">Save the file as KeyFields1.xml.</span></span>  
  
2.  <span data-ttu-id="3422a-128">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="3422a-128">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="3422a-129">KeyFields1.xml を保存したディレクトリに KeyFields1T.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="3422a-129">Save the file as KeyFields1T.xml in the same directory where you saved KeyFields1.xml.</span></span> <span data-ttu-id="3422a-130">このテンプレートの XPath クエリでは、CustomerID が3未満のすべての要素が返され **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="3422a-130">The XPath query in the template returns all the **\<Order>** elements with a CustomerID of less than 3.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="KeyFields1.xml">  
            /Order[@CustomerID < 3]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="3422a-131">マッピング スキーマ (KeyFields1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="3422a-131">The directory path specified for the mapping schema (KeyFields1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="3422a-132">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3422a-132">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields1.xml"  
    ```  
  
3.  <span data-ttu-id="3422a-133">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="3422a-133">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="3422a-134">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3422a-134">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="3422a-135">結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3422a-135">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
    <Order SalesOrderID="43860" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="44501" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="45283" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    .....  
</ROOT>  
```  
  
### <a name="b-specifying-sqlkey-fields-to-produce-proper-nesting-in-the-result"></a><span data-ttu-id="3422a-136">B.</span><span class="sxs-lookup"><span data-stu-id="3422a-136">B.</span></span> <span data-ttu-id="3422a-137">sql:key-fields を指定して結果内に適切な入れ子を生成する</span><span class="sxs-lookup"><span data-stu-id="3422a-137">Specifying sql:key-fields to produce proper nesting in the result</span></span>  
 <span data-ttu-id="3422a-138">次のスキーマでは、を使用して階層が指定されていません **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="3422a-138">In the following schema, there is no hierarchy specified using **\<sql:relationship>**.</span></span> <span data-ttu-id="3422a-139">`sql:key-fields` 注釈を指定して、HumanResources.Employee テーブルの従業員を一意に識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3422a-139">The schema still requires specifying the `sql:key-fields` annotation to uniquely identify employees in the HumanResources.Employee table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="HumanResources.Employee" sql:key-fields="EmployeeID" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Title">  
          <xsd:complexType>  
            <xsd:simpleContent>  
              <xsd:extension base="xsd:string">  
                 <xsd:attribute name="EmployeeID" type="xsd:integer" />  
              </xsd:extension>  
            </xsd:simpleContent>  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="3422a-140">このスキーマの実際のサンプルを作成するには</span><span class="sxs-lookup"><span data-stu-id="3422a-140">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="3422a-141">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="3422a-141">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="3422a-142">KeyFields2.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="3422a-142">Save the file as KeyFields2.xml.</span></span>  
  
2.  <span data-ttu-id="3422a-143">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="3422a-143">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="3422a-144">KeyFields2.xml を保存したディレクトリに KeyFields2T.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="3422a-144">Save the file as KeyFields2T.xml in the same directory where you saved KeyFields2.xml.</span></span> <span data-ttu-id="3422a-145">このテンプレートの XPath クエリでは、すべての要素が返され **\<HumanResources.Employee>** ます。</span><span class="sxs-lookup"><span data-stu-id="3422a-145">The XPath query in the template returns all the **\<HumanResources.Employee>** elements:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="KeyFields2.xml">  
        /HumanResources.Employee  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="3422a-146">マッピング スキーマ (KeyFields2.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="3422a-146">The directory path specified for the mapping schema (KeyFields2.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="3422a-147">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3422a-147">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields2.xml"  
    ```  
  
3.  <span data-ttu-id="3422a-148">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="3422a-148">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="3422a-149">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3422a-149">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="3422a-150">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3422a-150">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <HumanResources.Employee>  
    <Title EmployeeID="1">Production Technician - WC60</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="2">Marketing Assistant</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="3">Engineering Manager</Title>   
  </HumanResources.Employee>  
  ...  
</ROOT>  
```  
  
  
