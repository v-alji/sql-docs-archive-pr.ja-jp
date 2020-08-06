---
title: 'Sql: マップトを使用した、結果の XML ドキュメントからのスキーマ要素の除外 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c79ae005b9630fcbfcd16bfc22c2aeb21b7bf9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640864"
---
# <a name="excluding-schema-elements-from-the-resulting-xml-document-using-sqlmapped-sqlxml-40"></a><span data-ttu-id="44385-102">sql:mapped を使用した、結果の XML ドキュメントからのスキーマ要素の除外 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="44385-102">Excluding Schema Elements from the Resulting XML Document Using sql:mapped (SQLXML 4.0)</span></span>
  <span data-ttu-id="44385-103">既定のマッピングでは、XSD スキーマのすべての要素と属性が、データベースのテーブルまたはビューと列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="44385-103">Every element and attribute in the XSD schema maps to a database table/view and column because of the default mapping.</span></span> <span data-ttu-id="44385-104">XSD スキーマで、データベース テーブル (ビュー) または列にマップせず、XML に表示しない要素を作成する場合は、`sql:mapped` 注釈を指定できます。</span><span class="sxs-lookup"><span data-stu-id="44385-104">If you want to create an element in the XSD schema that does not map to any database table (view) or column and that does not appear in the XML, you can specify the `sql:mapped` annotation.</span></span>  
  
 <span data-ttu-id="44385-105">`sql:mapped` 注釈は、データベースに格納されていないデータがスキーマにあり、そのスキーマを変更できない場合や、そのスキーマが他のソースからの XML の検証に使用されている場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="44385-105">The `sql:mapped` annotation is especially useful if the schema cannot be modified or if the schema is used to validate XML from other sources and yet contains data that is not stored in your database.</span></span> <span data-ttu-id="44385-106">`sql:mapped` 注釈は、マップされない要素と属性が XML ドキュメントに表示されないという点で、`sql:is-constant` と異なります。</span><span class="sxs-lookup"><span data-stu-id="44385-106">The `sql:mapped` annotation differs from `sql:is-constant` in that the unmapped elements and attributes do not appear in the XML document.</span></span>  
  
 <span data-ttu-id="44385-107">`sql:mapped` 注釈はブール値 (0 = false、1 = true) をとります。</span><span class="sxs-lookup"><span data-stu-id="44385-107">The `sql:mapped` annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="44385-108">指定できる値は 0、1、true、false です。</span><span class="sxs-lookup"><span data-stu-id="44385-108">The acceptable values are 0, 1, true, and false.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="44385-109">例</span><span class="sxs-lookup"><span data-stu-id="44385-109">Examples</span></span>  
 <span data-ttu-id="44385-110">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="44385-110">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="44385-111">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44385-111">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a><span data-ttu-id="44385-112">A.</span><span class="sxs-lookup"><span data-stu-id="44385-112">A.</span></span> <span data-ttu-id="44385-113">sql:mapped 注釈を指定する</span><span class="sxs-lookup"><span data-stu-id="44385-113">Specifying the sql:mapped annotation</span></span>  
 <span data-ttu-id="44385-114">他のソースからの XSD スキーマがあるとします。</span><span class="sxs-lookup"><span data-stu-id="44385-114">Assume you have an XSD schema from some other source.</span></span> <span data-ttu-id="44385-115">この XSD スキーマは **\<Person.Contact>** 、 **ContactID**、 **FirstName**、 **LastName**、および**ホームアドレス**属性を持つ要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="44385-115">This XSD schema consists of an **\<Person.Contact>** element with **ContactID**, **FirstName**, **LastName**, and **HomeAddress** attributes.</span></span>  
  
 <span data-ttu-id="44385-116">この XSD スキーマを AdventureWorks データベースの Person. Contact テーブルにマップする場合、 `sql:mapped` employee テーブルには従業員の自宅の住所が格納されないため、[ホーム**アドレス**] 属性にはが指定されています。</span><span class="sxs-lookup"><span data-stu-id="44385-116">In mapping this XSD schema to the Person.Contact table in the AdventureWorks database, `sql:mapped` is specified on the **HomeAddress** attribute because the Employees table does not store the home addresses of employees.</span></span> <span data-ttu-id="44385-117">この結果、マッピング スキーマに対して Xpath クエリを指定すると、属性はデータベースにマップされず、結果の XML ドキュメント内に返されません。</span><span class="sxs-lookup"><span data-stu-id="44385-117">As a result, this attribute is not mapped to the database and is not returned in the resulting XML document when an XPath query is specified against the mapping schema.</span></span>  
  
 <span data-ttu-id="44385-118">スキーマの残りの部分に対しては、既定のマッピングが適用されます。</span><span class="sxs-lookup"><span data-stu-id="44385-118">Default mapping takes place for the rest of the schema.</span></span> <span data-ttu-id="44385-119">**\<Person.Contact>** 要素は person. contact テーブルにマップされ、すべての属性は、person. contact テーブル内の同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="44385-119">The **\<Person.Contact>** element maps to the Person.Contact table, and all the attributes map to the columns with the same name in the Person.Contact table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="44385-120">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="44385-120">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="44385-121">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="44385-121">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="44385-122">sql-mapped.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="44385-122">Save the file as sql-mapped.xml.</span></span>  
  
2.  <span data-ttu-id="44385-123">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="44385-123">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="44385-124">sql-mapped.xml を保存したディレクトリに sql-mappedT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="44385-124">Save the file as sql-mappedT.xml in the same directory where you saved sql-mapped.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="44385-125">マッピング スキーマ (MySchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="44385-125">The directory path specified for the mapping schema (MySchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="44385-126">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="44385-126">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  <span data-ttu-id="44385-127">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="44385-127">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="44385-128">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44385-128">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="44385-129">結果セットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="44385-129">This is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 <span data-ttu-id="44385-130">マッピング スキーマで `sql:mapped` 属性に 0 を指定しているので、ContactID と FirstName、Lastname は存在しますが、HomeAddress は存在しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="44385-130">Note that the ContactID, FirstName, and LastName are present, but HomeAddress is not because the mapping schema specified 0 for the `sql:mapped` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44385-131">参照</span><span class="sxs-lookup"><span data-stu-id="44385-131">See Also</span></span>  
 [<span data-ttu-id="44385-132">テーブルおよび列への XSD 要素と属性の既定のマッピング &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="44385-132">Default Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
