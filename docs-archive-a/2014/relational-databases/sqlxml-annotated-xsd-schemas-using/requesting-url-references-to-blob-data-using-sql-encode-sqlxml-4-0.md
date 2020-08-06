---
title: 'Sql: encode を使用した BLOB データへの URL 参照の要求 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a9f5edcfab4a9d7307327d97bc2099c78c666c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644389"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a><span data-ttu-id="ca326-102">sql:encode を使用した、BLOB データへの URL 参照の要求 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="ca326-102">Requesting URL References to BLOB Data Using sql:encode (SQLXML 4.0)</span></span>
  <span data-ttu-id="ca326-103">注釈付き XSD スキーマで、属性 (または要素) が Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の BLOB 列にマップされた場合、XML 内に返されるデータは Base 64 エンコード形式になります。</span><span class="sxs-lookup"><span data-stu-id="ca326-103">In an annotated XSD schema, when an attribute (or element) is mapped to a BLOB column in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data is returned in Base 64-encoded format within XML.</span></span>  
  
 <span data-ttu-id="ca326-104">後で BLOB データをバイナリ形式で取得するときに使用できるよう、データへの参照 (URI) を返す場合は、`sql:encode` 注釈を指定します。</span><span class="sxs-lookup"><span data-stu-id="ca326-104">If you want a reference to the data (a URI) to be returned that can be used later to retrieve the BLOB data in a binary format, specify the `sql:encode` annotation.</span></span> <span data-ttu-id="ca326-105">`sql:encode` は、単純型の属性または要素に指定できます。</span><span class="sxs-lookup"><span data-stu-id="ca326-105">You can specify `sql:encode` on an attribute or element of simple type.</span></span>  
  
 <span data-ttu-id="ca326-106">`sql:encode` 注釈を指定すると、フィールド値の代わりにフィールドへの URL を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="ca326-106">Specify the `sql:encode` annotation to indicate that a URL to the field should be returned instead of the value of the field.</span></span> <span data-ttu-id="ca326-107">`sql:encode` では主キーに基づいて、URL での単一選択が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ca326-107">`sql:encode` depends on the primary key to generate a singleton select in the URL.</span></span> <span data-ttu-id="ca326-108">主キーは、注釈を使用して指定でき `sql:key-fields` ます。</span><span class="sxs-lookup"><span data-stu-id="ca326-108">The primary key can be specified using the `sql:key-fields` annotation.</span></span>  
  
 <span data-ttu-id="ca326-109">`sql:encode` 注釈には、"url" または "default" の値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ca326-109">The `sql:encode` annotation can be assigned the "url" or the "default" value.</span></span> <span data-ttu-id="ca326-110">"default" の場合、データは Base 64 エンコード形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="ca326-110">A value of "default" returns data in Base 64-encoded format.</span></span>  
  
 <span data-ttu-id="ca326-111">`sql:encode` 注釈は、`sql:use-cdata` と共に使用したり、ID、IDREF、IDREFS、NMTOKEN、または NMTOKENS 属性型に指定したり、</span><span class="sxs-lookup"><span data-stu-id="ca326-111">The `sql:encode` annotation cannot be used with `sql:use-cdata` or on the ID, IDREF, IDREFS, NMTOKEN, or NMTOKENS attribute types.</span></span> <span data-ttu-id="ca326-112">XSD **fixed**属性と共に使用することもできません。</span><span class="sxs-lookup"><span data-stu-id="ca326-112">It can also not be used with XSD **fixed** attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca326-113">BLOB 型の列は、キーの一部または外部キーとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ca326-113">BLOB-type columns cannot be used as a part of a key or foreign key.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ca326-114">例</span><span class="sxs-lookup"><span data-stu-id="ca326-114">Examples</span></span>  
 <span data-ttu-id="ca326-115">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca326-115">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="ca326-116">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca326-116">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a><span data-ttu-id="ca326-117">A.</span><span class="sxs-lookup"><span data-stu-id="ca326-117">A.</span></span> <span data-ttu-id="ca326-118">BLOB データへの URL 参照を取得するため、sql:encode を指定する</span><span class="sxs-lookup"><span data-stu-id="ca326-118">Specifying sql:encode to obtain a URL reference to BLOB data</span></span>  
 <span data-ttu-id="ca326-119">この例では、マッピングスキーマで `sql:encode` **LargePhoto**属性にを指定して、特定の製品写真への URI 参照を取得します (Base 64 エンコード形式でバイナリデータを取得するのではなく)。</span><span class="sxs-lookup"><span data-stu-id="ca326-119">In this example, the mapping schema specifies `sql:encode` on the **LargePhoto** attribute to retrieve the URI reference to a specific product photo (instead of retrieving the binary data in Base 64-encoded format).</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="ca326-120">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="ca326-120">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="ca326-121">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="ca326-121">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="ca326-122">sqlEncode.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="ca326-122">Save the file as sqlEncode.xml.</span></span>  
  
2.  <span data-ttu-id="ca326-123">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="ca326-123">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="ca326-124">sqlEncode.xml を保存したディレクトリに sqlEncodeT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="ca326-124">Save the file as sqlEncodeT.xml in the same directory where you saved sqlEncode.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="ca326-125">マッピング スキーマ (sqlEncode.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="ca326-125">The directory path specified for the mapping schema (sqlEncode.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="ca326-126">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ca326-126">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  <span data-ttu-id="ca326-127">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="ca326-127">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="ca326-128">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca326-128">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="ca326-129">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ca326-129">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
