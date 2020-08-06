---
title: テーブルおよび列への XSD 要素と属性の明示的なマッピング (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
author: rothja
ms.author: jroth
ms.openlocfilehash: f3400682b5f28835ca039912aab058691929a6c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633010"
---
# <a name="explicit-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a><span data-ttu-id="77589-102">テーブルおよび列への XSD 要素および属性の明示的なマッピング (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="77589-102">Explicit Mapping of XSD Elements and Attributes to Tables and Columns (SQLXML 4.0)</span></span>
  <span data-ttu-id="77589-103">XSD スキーマを使用してリレーショナル データベースの XML ビューを作成するときには、スキーマの要素と属性をデータベースのテーブルと列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="77589-103">When using an XSD schema to provide an XML view of the relational database , the elements and attributes of the schema must be mapped to tables and columns of the database.</span></span> <span data-ttu-id="77589-104">データベースのテーブルおよびビューの行は、XML ドキュメントの要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="77589-104">The rows in the database table/view will map to elements in the XML document.</span></span> <span data-ttu-id="77589-105">データベースの列値は属性または要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="77589-105">The column values in the database map to attributes or elements.</span></span>  
  
 <span data-ttu-id="77589-106">注釈付き XSD スキーマに対して XPath クエリを指定する場合、スキーマ内の要素と属性のデータは、マップ先のテーブルと列から取得されます。</span><span class="sxs-lookup"><span data-stu-id="77589-106">When XPath queries are specified against the annotated XSD schema, the data for the elements and attributes in the schema is retrieved from the tables and columns to which they map.</span></span> <span data-ttu-id="77589-107">データベースから単一の値を取得するには、XSD スキーマに指定されているマッピングに、リレーションとフィールドの両方の指定が必要です。</span><span class="sxs-lookup"><span data-stu-id="77589-107">To obtain a single value from the database, the mapping specified in the XSD schema must have both relation and field specification.</span></span> <span data-ttu-id="77589-108">要素または属性の名前が、マップ先のテーブル、ビューまたは列名と同じでない場合は、`sql:relation` 注釈と `sql:field` 注釈を使用して、XML ドキュメントの要素または属性から、データベースのテーブル、ビューまたは列へのマッピングを指定します。</span><span class="sxs-lookup"><span data-stu-id="77589-108">If the name of an element/attribute is not the same name as the table/view or column name to which it maps, the `sql:relation` and `sql:field` annotations are used to specify the mapping between an element or attribute in an XML document and the table (view) or column in a database.</span></span>  
  
## <a name="sql-relation"></a><span data-ttu-id="77589-109">sql-relation</span><span class="sxs-lookup"><span data-stu-id="77589-109">sql-relation</span></span>  
 <span data-ttu-id="77589-110">XSD スキーマ内の XML ノードをデータベース テーブルにマップするには、`sql:relation` 注釈を追加します。</span><span class="sxs-lookup"><span data-stu-id="77589-110">The `sql:relation` annotation is added to map an XML node in the XSD schema to a database table.</span></span> <span data-ttu-id="77589-111">ここではテーブルまたはビューの名前を `sql:relation` 注釈の値として指定します。</span><span class="sxs-lookup"><span data-stu-id="77589-111">The name of a table (view) is specified as the value of the `sql:relation` annotation.</span></span>  
  
 <span data-ttu-id="77589-112">`sql:relation` を要素に指定した場合は、この注釈のスコープが、要素の複合型定義で指定されているすべての属性と子要素に適用されます。これによって、注釈の記述を簡素化できます。</span><span class="sxs-lookup"><span data-stu-id="77589-112">When `sql:relation` is specified on an element, the scope of this annotation applies to all attributes and child elements that are described in the complex type definition of that element, therefore providing a shortcut in writing annotations.</span></span>  
  
 <span data-ttu-id="77589-113">注釈は、 `sql:relation` で有効な識別子 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が XML で有効でない場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="77589-113">The `sql:relation` annotation is also useful when identifiers that are valid in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are not valid in XML.</span></span> <span data-ttu-id="77589-114">たとえば、"Order Details" は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では有効なテーブル名ですが、XML では無効です。</span><span class="sxs-lookup"><span data-stu-id="77589-114">For example, "Order Details" is a valid table name in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but not in XML.</span></span> <span data-ttu-id="77589-115">この場合、`sql:relation` 注釈を使用して、次のようなマッピングを指定できます。</span><span class="sxs-lookup"><span data-stu-id="77589-115">In such cases, the `sql:relation` annotation can be used to specify the mapping, for example:</span></span>  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a><span data-ttu-id="77589-116">sql-field</span><span class="sxs-lookup"><span data-stu-id="77589-116">sql-field</span></span>  
 <span data-ttu-id="77589-117">`sql-field` 注釈では、要素または属性がデータベース列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="77589-117">The `sql-field` annotation maps an element or attribute to a database column.</span></span> <span data-ttu-id="77589-118">スキーマ内の XML ノードをデータベース列にマップするには、`sql:field` 注釈を追加します。</span><span class="sxs-lookup"><span data-stu-id="77589-118">The `sql:field` annotation is added to map an XML node in the schema to a database column.</span></span> <span data-ttu-id="77589-119">空のコンテンツ要素に `sql:field` は指定できません。</span><span class="sxs-lookup"><span data-stu-id="77589-119">You cannot specify `sql:field` on an empty content element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="77589-120">例</span><span class="sxs-lookup"><span data-stu-id="77589-120">Examples</span></span>  
 <span data-ttu-id="77589-121">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="77589-121">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="77589-122">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77589-122">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a><span data-ttu-id="77589-123">A.</span><span class="sxs-lookup"><span data-stu-id="77589-123">A.</span></span> <span data-ttu-id="77589-124">sql:relation 注釈と sql:field 注釈を指定する</span><span class="sxs-lookup"><span data-stu-id="77589-124">Specifying the sql:relation and sql:field annotations</span></span>  
 <span data-ttu-id="77589-125">この例では、XSD スキーマは、 **\<Contact>** および子要素と ContactID 属性を持つ複合型の要素で構成されて **\<FName>** **\<LName>** います。 **ContactID**</span><span class="sxs-lookup"><span data-stu-id="77589-125">In this example, the XSD schema consists of an **\<Contact>** element of complex type with **\<FName>** and **\<LName>** child elements and the **ContactID** attribute.</span></span>  
  
 <span data-ttu-id="77589-126">この注釈によって、 `sql:relation` **\<Contact>** 要素が AdventureWorks データベースの Person テーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="77589-126">The `sql:relation` annotation maps the **\<Contact>** element to the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="77589-127">注釈によっ `sql:field` て、要素が FirstName 列にマップされ、 **\<FName>** **\<LName>** 要素が LastName 列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="77589-127">The `sql:field` annotation maps the **\<FName>** element to the FirstName column and the **\<LName>** element to the LastName column.</span></span>  
  
 <span data-ttu-id="77589-128">**ContactID**属性に注釈が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="77589-128">No annotation is specified for the **ContactID** attribute.</span></span> <span data-ttu-id="77589-129">このため、既定のマッピングが使用され、属性が同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="77589-129">This results in a default mapping of the attribute to the column with the same name.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="77589-130">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="77589-130">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="77589-131">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="77589-131">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="77589-132">MySchema-annotated.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="77589-132">Save the file as MySchema-annotated.xml.</span></span>  
  
2.  <span data-ttu-id="77589-133">次のテンプレートをコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="77589-133">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="77589-134">MySchema-annotated.xml を保存したディレクトリに MySchema-annotatedT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="77589-134">Save the file as MySchema-annotatedT.xml in the same directory where you saved MySchema-annotated.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="77589-135">マッピング スキーマ (MySchema-annotated.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="77589-135">The directory path specified for the mapping schema (MySchema-annotated.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="77589-136">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="77589-136">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  <span data-ttu-id="77589-137">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="77589-137">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="77589-138">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77589-138">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="77589-139">次に結果セットの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="77589-139">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  
