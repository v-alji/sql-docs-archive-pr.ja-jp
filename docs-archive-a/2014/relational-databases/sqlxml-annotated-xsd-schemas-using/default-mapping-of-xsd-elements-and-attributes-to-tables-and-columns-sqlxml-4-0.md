---
title: テーブルおよび列への XSD 要素と属性の既定のマッピング (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XSD schemas [SQLXML], mapping attributes and elements
- mapping schema [SQLXML], default mapping
- element mapping [SQLXML], default mapping
- element mapping [SQLXML]
- table mapping [SQLXML]
- annotated XSD schemas, mapping attributes and elements
- table/view mapping [SQLXML]
- column mapping [SQLXML]
- attribute mapping [SQLXML], default mapping
- default schema mapping
- table mapping [SQLXML], default mapping
- testing XPath query against schema
- xml data type [SQL Server], SQLXML
- table/view mapping [SQLXML], default mapping
- element/attribute mapping [SQLXML]
ms.assetid: 9a18e92a-6cfb-4a14-993a-663a95aabb63
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bccec2413e8a0a6e13283a0f3e5f63ab61e934b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640863"
---
# <a name="default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a><span data-ttu-id="bdac6-102">テーブルおよび列への XSD 要素および属性の既定のマッピング (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="bdac6-102">Default Mapping of XSD Elements and Attributes to Tables and Columns (SQLXML 4.0)</span></span>
  <span data-ttu-id="bdac6-103">既定では、XSD 注釈付きスキーマの複合型の要素は、指定されたデータベース内の同じ名前のテーブル (ビュー) にマップされ、単純型の要素または属性は、テーブル内の同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-103">By default, an element of complex type in an XSD annotated schema maps to the table (view) with the same name in the specified database, and an element or attribute of simple type maps to the column with the same name in the table.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bdac6-104">例</span><span class="sxs-lookup"><span data-stu-id="bdac6-104">Examples</span></span>  
 <span data-ttu-id="bdac6-105">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdac6-105">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="bdac6-106">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdac6-106">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-default-mapping"></a><span data-ttu-id="bdac6-107">A.</span><span class="sxs-lookup"><span data-stu-id="bdac6-107">A.</span></span> <span data-ttu-id="bdac6-108">既定のマッピングを指定する</span><span class="sxs-lookup"><span data-stu-id="bdac6-108">Specifying default mapping</span></span>  
 <span data-ttu-id="bdac6-109">この例では、XSD スキーマで注釈は指定されていません。</span><span class="sxs-lookup"><span data-stu-id="bdac6-109">In this example, no annotations are specified in the XSD schema.</span></span> <span data-ttu-id="bdac6-110">**\<Person.Contact>** 要素は複合型であるため、既定で AdventureWorks データベースの Person. Contact テーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-110">The **\<Person.Contact>** element is of complex type and, therefore, maps by default to the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="bdac6-111">要素のすべての属性 (ContactID、FirstName、LastName) **\<Person.Contact>** は単純型で、既定では、Person. Contact テーブル内の同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-111">All the attributes (ContactID, FirstName, LastName) of the **\<Person.Contact>** element are of simple type and map by default to columns with the same names in the Person.Contact table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  type="xsd:string" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="bdac6-112">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="bdac6-112">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="bdac6-113">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="bdac6-113">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="bdac6-114">MySchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-114">Save the file as MySchema.xml.</span></span>  
  
2.  <span data-ttu-id="bdac6-115">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="bdac6-115">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="bdac6-116">MySchema.xml を保存したディレクトリに MySchemaT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-116">Save the file as MySchemaT.xml in the same directory where you saved MySchema.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchema.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="bdac6-117">マッピング スキーマ (MySchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="bdac6-117">The directory path specified for the mapping schema (MySchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="bdac6-118">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema.xml"  
    ```  
  
3.  <span data-ttu-id="bdac6-119">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="bdac6-120">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdac6-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="bdac6-121">次に結果セットの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-121">Here is the partial result set:</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8" ?>  
<ROOT>  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong"/>  
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel"/>  
   ...  
</ROOT>  
```  
  
### <a name="b-mapping-an-xml-element-to-a-database-column"></a><span data-ttu-id="bdac6-122">B.</span><span class="sxs-lookup"><span data-stu-id="bdac6-122">B.</span></span> <span data-ttu-id="bdac6-123">XML 要素をデータベース列にマップする</span><span class="sxs-lookup"><span data-stu-id="bdac6-123">Mapping an XML element to a database column</span></span>  
 <span data-ttu-id="bdac6-124">この例では、注釈が使用されず、既定のマッピングが行われます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-124">In this example, default mapping also takes place because no annotations are used.</span></span> <span data-ttu-id="bdac6-125">**\<Person.Contact>** 要素は複合型であり、データベース内の同じ名前のテーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-125">The **\<Person.Contact>** element is of complex type and maps to the table with the same name in the database.</span></span> <span data-ttu-id="bdac6-126">要素 **\<FirstName>** および **\<LastName>** **EmployeeID**属性は単純型であるため、同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-126">The elements **\<FirstName>** and **\<LastName>** and the **EmployeeID** attribute are of simple type and, therefore, map to the columns with the same names.</span></span> <span data-ttu-id="bdac6-127">前の例との唯一の違いは、FirstName フィールドと LastName フィールドのマップに要素を使用する点です。</span><span class="sxs-lookup"><span data-stu-id="bdac6-127">The only difference between this and the previous example are that elements are used for mapping the FirstName and LastName fields.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="FirstName" type="xsd:string" />   
        <xsd:element name="LastName" type="xsd:string" />   
      </xsd:sequence>  
      <xsd:attribute name="ContactID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="bdac6-128">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="bdac6-128">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="bdac6-129">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="bdac6-129">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="bdac6-130">MySchemaElements.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-130">Save the file as MySchemaElements.xml.</span></span>  
  
2.  <span data-ttu-id="bdac6-131">次のテンプレート (MySchemaElementsT.xml) を作成し、前の手順と同じディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-131">Create the following template (MySchemaElementsT.xml), and save it in the same directory used in the previous step.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaElements.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="bdac6-132">マッピング スキーマに指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="bdac6-132">The directory path specified for the mapping schema is relative to the directory where the template is saved.</span></span> <span data-ttu-id="bdac6-133">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-133">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaElements.xml"  
    ```  
  
3.  <span data-ttu-id="bdac6-134">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-134">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="bdac6-135">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdac6-135">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="bdac6-136">次に結果セットの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-136">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1">  
    <FirstName>Gustavo</FirstName>  
    <LastName>Achong</LastName>  
  </Person.Contact>  
   ...  
</ROOT>  
```  
  
### <a name="c-mapping-an-xml-element-to-an-xml-data-type-column"></a><span data-ttu-id="bdac6-137">C.</span><span class="sxs-lookup"><span data-stu-id="bdac6-137">C.</span></span> <span data-ttu-id="bdac6-138">XML 要素を XML データ型の列にマップする</span><span class="sxs-lookup"><span data-stu-id="bdac6-138">Mapping an XML element to an XML data type column</span></span>  
 <span data-ttu-id="bdac6-139">この例では、注釈が使用されず、既定のマッピングが行われます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-139">In this example, default mapping also takes place because no annotations are used.</span></span> <span data-ttu-id="bdac6-140">**\<Production.ProductModel>** 要素は複合型であり、データベース内の同じ名前のテーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-140">The **\<Production.ProductModel>** element is of complex type and maps to the table with the same name in the database.</span></span> <span data-ttu-id="bdac6-141">**Productmodelid**属性は単純型であるため、同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-141">The **ProductModelID** attribute is of simple type and, therefore, map to the columns with the same names.</span></span> <span data-ttu-id="bdac6-142">このと前の例の唯一の違いは、要素が型を使用して **\<Instructions>** データ型を使用する列にマッピングされていることです `xml` `xsd:anyType` 。</span><span class="sxs-lookup"><span data-stu-id="bdac6-142">The only difference between this and the previous examples is that the **\<Instructions>** element is mapping to a column that uses the `xml` data type by using the `xsd:anyType` type.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Instructions" type="xsd:anyType" />   
      </xsd:sequence>  
      <xsd:attribute name="ProductModelID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="bdac6-143">`xml` データ型は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で導入されました。</span><span class="sxs-lookup"><span data-stu-id="bdac6-143">The `xml` data type was introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="bdac6-144">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="bdac6-144">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="bdac6-145">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="bdac6-145">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="bdac6-146">MySchemaXmlAnyElements.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-146">Save the file as MySchemaXmlAnyElements.xml.</span></span>  
  
2.  <span data-ttu-id="bdac6-147">次のテンプレート (MySchemaXmlAnyElementsT.xml) を作成し、前の手順と同じディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-147">Create the following template (MySchemaXmlAnyElementsT.xml), and save it in the same directory used in the previous step.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaXmlAnyElements.xml">  
            /Production.ProductModel[@ProductModelID=7]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="bdac6-148">マッピング スキーマに指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="bdac6-148">The directory path specified for the mapping schema is relative to the directory where the template is saved.</span></span> <span data-ttu-id="bdac6-149">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="bdac6-149">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaXmlAnyElements.xml"  
    ```  
  
3.  <span data-ttu-id="bdac6-150">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-150">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="bdac6-151">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdac6-151">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="bdac6-152">次に結果セットの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="bdac6-152">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductModel ProductModelID="7">  
    <Instructions>  
      <root xmlns="http:  
//schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstru  
ctions">  
...  
      </root>  
    <Instructions>  
  </Production.ProductModel>  
</ROOT>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bdac6-153">参照</span><span class="sxs-lookup"><span data-stu-id="bdac6-153">See Also</span></span>  
 <span data-ttu-id="bdac6-154">[SQLXML 4.0&#41;&#40;注釈付きスキーマのセキュリティに関する考慮事項](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="bdac6-154">[Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="bdac6-155">[XML データ &#40;SQL Server&#41;](../xml/xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bdac6-155">[XML Data &#40;SQL Server&#41;](../xml/xml-data-sql-server.md) </span></span>  
 [<span data-ttu-id="bdac6-156">SQLXML 4.0 での xml データ型のサポート</span><span class="sxs-lookup"><span data-stu-id="bdac6-156">xml Data Type Support in SQLXML 4.0</span></span>](../sqlxml/xml-data-type-support-in-sqlxml-4-0.md)  
  
  
