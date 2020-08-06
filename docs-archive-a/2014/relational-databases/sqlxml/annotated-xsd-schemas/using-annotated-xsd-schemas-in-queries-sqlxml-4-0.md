---
title: クエリでの注釈付き XSD スキーマの使用 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
author: rothja
ms.author: jroth
ms.openlocfilehash: c3038ea234f707da7a87a030cb4110510f5a77c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642686"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a><span data-ttu-id="3f756-102">クエリでの注釈付き XSD スキーマの使用 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="3f756-102">Using Annotated XSD Schemas in Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="3f756-103">注釈付きスキーマに対してクエリを指定し、XSD スキーマに対してテンプレートで XPath クエリを指定して、データベースからデータを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="3f756-103">You can specify queries against an annotated schema to retrieve data from the database by specifying XPath queries in a template against the XSD schema.</span></span>  
  
 <span data-ttu-id="3f756-104">**\<sql:xpath-query>** 要素を使用すると、注釈付きスキーマで定義されている XML ビューに対して XPath クエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3f756-104">The **\<sql:xpath-query>** element allows you to specify an XPath query against the XML view that is defined by the annotated schema.</span></span> <span data-ttu-id="3f756-105">XPath クエリの実行対象となる注釈付きスキーマは、要素の属性を使用して識別され `mapping-schema` **\<sql:xpath-query>** ます。</span><span class="sxs-lookup"><span data-stu-id="3f756-105">The annotated schema against which the XPath query is to be executed is identified by using the `mapping-schema` attribute of the **\<sql:xpath-query>** element.</span></span>  
  
 <span data-ttu-id="3f756-106">テンプレートは、1 つ以上のクエリを含む有効な XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="3f756-106">Templates are valid XML documents that contain one or more queries.</span></span> <span data-ttu-id="3f756-107">FOR XML クエリと XPath クエリでは、ドキュメント フラグメントが返されますが、</span><span class="sxs-lookup"><span data-stu-id="3f756-107">The FOR XML and XPath queries return a document fragment.</span></span> <span data-ttu-id="3f756-108">テンプレートは、ドキュメントフラグメントのコンテナーとして機能します。そのため、1つの最上位要素を指定する方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="3f756-108">Templates act as containers for the document fragments; templates thus provide a way to specify a single, top-level element.</span></span>  
  
 <span data-ttu-id="3f756-109">このトピックの例では、テンプレートを使用して注釈付きスキーマに対する XPath クエリを指定し、データベースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="3f756-109">The examples in this topic use templates to specify an XPath query against an annotated schema to retrieve data from the database.</span></span>  
  
 <span data-ttu-id="3f756-110">たとえば、次の注釈付きスキーマを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="3f756-110">For example, consider this annotated schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="3f756-111">わかりやすくするため、この XSD スキーマは Schema2.xml というファイルに格納されているものとします。</span><span class="sxs-lookup"><span data-stu-id="3f756-111">For the purpose of illustration, this XSD schema is stored in file named Schema2.xml.</span></span> <span data-ttu-id="3f756-112">ここで、次のテンプレート ファイル (Schema2T.xml) で指定されている注釈付きスキーマに対し、XPath クエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3f756-112">You could then have an XPath query against the annotated schema specified in the following template file (Schema2T.xml):</span></span>  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 <span data-ttu-id="3f756-113">SQLXML 4.0 のテスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用すると、テンプレート ファイルの一部としてクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3f756-113">You can then create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the query as part of a template file.</span></span> <span data-ttu-id="3f756-114">詳細については、「 [SQLXML 4.0&#41;で非推奨とされた注釈付き XDR スキーマ &#40;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f756-114">For more information, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="using-inline-mapping-schemas"></a><span data-ttu-id="3f756-115">インライン マッピング スキーマの使用</span><span class="sxs-lookup"><span data-stu-id="3f756-115">Using Inline Mapping Schemas</span></span>  
 <span data-ttu-id="3f756-116">注釈付きスキーマはテンプレートに直接含めることができます。このテンプレートで、インライン スキーマに対する XPath クエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3f756-116">An annotated schema can be included directly in a template, and then an XPath query can be specified in the template against the inline schema.</span></span> <span data-ttu-id="3f756-117">テンプレートはアップデートグラムとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f756-117">The template can also be an updategram.</span></span>  
  
 <span data-ttu-id="3f756-118">テンプレートには複数のインライン スキーマを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3f756-118">A template can include multiple inline schemas.</span></span> <span data-ttu-id="3f756-119">テンプレートに含まれているインラインスキーマを使用するには、要素に一意の値を指定して**id**属性を指定 **\<xsd:schema>** し、 **#idvalue**を使用してインラインスキーマを参照します。</span><span class="sxs-lookup"><span data-stu-id="3f756-119">To use an inline schema that is included in a template, specify the **id** attribute with a unique value on the **\<xsd:schema>** element, and then use **#idvalue** to reference the inline schema.</span></span> <span data-ttu-id="3f756-120">**Id**属性は、XDR スキーマで使用される**sql: id** ({urn: schema-microsoft-com: xml} id) と同じ動作です。</span><span class="sxs-lookup"><span data-stu-id="3f756-120">The **id** attribute is identical in behavior to the **sql:id** ({urn:schemas-microsoft-com:xml-sql}id) used in XDR schemas.</span></span>  
  
 <span data-ttu-id="3f756-121">たとえば、次のテンプレートでは、2 つのインライン注釈付きスキーマを指定しています。</span><span class="sxs-lookup"><span data-stu-id="3f756-121">For example, the following template specifies two inline-annotated schemas:</span></span>  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 <span data-ttu-id="3f756-122">このテンプレートでは 2 つの XPath クエリも指定しています。</span><span class="sxs-lookup"><span data-stu-id="3f756-122">The template also specifies two XPath queries.</span></span> <span data-ttu-id="3f756-123">各要素は、 **\<xpath-query>** 属性を指定することによって、マッピングスキーマを一意に識別し `mapping-schema` ます。</span><span class="sxs-lookup"><span data-stu-id="3f756-123">Each of the **\<xpath-query>** elements uniquely identifies the mapping schema by specifying the `mapping-schema` attribute.</span></span>  
  
 <span data-ttu-id="3f756-124">テンプレートでインラインスキーマを指定する場合は、 `sql:is-mapping-schema` 要素で注釈も指定する必要があり **\<xsd:schema>** ます。</span><span class="sxs-lookup"><span data-stu-id="3f756-124">When you specify an inline schema in the template, the `sql:is-mapping-schema` annotation must also be specified on the **\<xsd:schema>** element.</span></span> <span data-ttu-id="3f756-125">`sql:is-mapping-schema` はブール値 (0 = false、1=true) をとります。</span><span class="sxs-lookup"><span data-stu-id="3f756-125">The `sql:is-mapping-schema` takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="3f756-126">**Sql:-mapping-schema = "1"** のインラインスキーマは、インライン注釈が付けられたスキーマとして扱われ、XML ドキュメントでは返されません。</span><span class="sxs-lookup"><span data-stu-id="3f756-126">An inline schema with **sql:is-mapping-schema="1"** is treated as inline annotated schema and is not returned in the XML document.</span></span>  
  
 <span data-ttu-id="3f756-127">`sql:is-mapping-schema` 注釈は、テンプレートの名前空間 `urn:schemas-microsoft-com:xml-sql` に属しています。</span><span class="sxs-lookup"><span data-stu-id="3f756-127">The `sql:is-mapping-schema` annotation belongs to the template namespace `urn:schemas-microsoft-com:xml-sql`.</span></span>  
  
 <span data-ttu-id="3f756-128">この例をテストするには、テンプレート (InlineSchemaTemplate.xml) をローカルのディレクトリに保存した後、SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="3f756-128">To test this example, save the template (InlineSchemaTemplate.xml) in a local directory and then create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="3f756-129">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f756-129">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="3f756-130">`mapping-schema` **\<sql:xpath-query>** テンプレート内の要素 (XPath クエリがある場合) またはアップデートグラムの要素に属性を指定することに加えて、 **\<updg:sync>** 次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3f756-130">In addition to specifying the `mapping-schema` attribute on the **\<sql:xpath-query>** element in a template (when there is an XPath query), or on **\<updg:sync>** element in an updategram, you can do the following:</span></span>  
  
-   <span data-ttu-id="3f756-131">テンプレートの `mapping-schema` **\<ROOT>** 要素 (グローバル宣言) に属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f756-131">Specify the `mapping-schema` attribute on the **\<ROOT>** element (global declaration) in the template.</span></span> <span data-ttu-id="3f756-132">ここで指定したマッピング スキーマは、すべての XPath およびアップデートグラム ノードで、明示的に `mapping-schema` 注釈が指定されていない場合に既定のスキーマとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="3f756-132">This mapping schema then becomes the default schema that will be used by all XPath and updategram nodes that have no explicit `mapping-schema` annotation.</span></span>  
  
-   <span data-ttu-id="3f756-133">`mapping schema`ADO オブジェクトを使用して属性を指定し `Command` ます。</span><span class="sxs-lookup"><span data-stu-id="3f756-133">Specify the `mapping schema` attribute by using the ADO `Command` object.</span></span>  
  
 <span data-ttu-id="3f756-134">`mapping-schema`要素または要素で指定された属性の **\<xpath-query>** **\<updg:sync>** 優先順位は最も高くなります。 ADO `Command` オブジェクトの優先順位は最も低くなります。</span><span class="sxs-lookup"><span data-stu-id="3f756-134">The `mapping-schema` attribute that is specified on the **\<xpath-query>** or **\<updg:sync>** element has the highest precedence; the ADO `Command` object has the lowest precedence.</span></span>  
  
 <span data-ttu-id="3f756-135">テンプレートで XPath クエリを指定し、XPath クエリの実行対象となるマッピングスキーマを指定しない場合、XPath クエリは**dbobject**型クエリとして扱われることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3f756-135">Note that if you specify an XPath query in a template and do not specify a mapping schema against which the XPath query is executed, the XPath query is treated as a **dbobject** type query.</span></span> <span data-ttu-id="3f756-136">たとえば、次のテンプレートを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="3f756-136">For example, consider this template:</span></span>  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 <span data-ttu-id="3f756-137">このテンプレートでは、XPath クエリが指定されていますが、マッピング スキーマが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="3f756-137">The template specifies an XPath query but it does not specify a mapping schema.</span></span> <span data-ttu-id="3f756-138">したがって、このクエリは**dbobject**型クエリとして扱われます。 productphoto はテーブル名、 @ProductPhotoID = ' 100 ' は、ID 値が100の製品写真を検索する述語です。</span><span class="sxs-lookup"><span data-stu-id="3f756-138">Therefore, this query is treated as a **dbobject** type query in which Production.ProductPhoto is the table name and @ProductPhotoID='100' is a predicate that finds a product photo with the ID value of 100.</span></span> <span data-ttu-id="3f756-139">@LargePhoto値の取得元の列を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f756-139">@LargePhoto is the column from which to retrieve the value.</span></span>  
  
  
