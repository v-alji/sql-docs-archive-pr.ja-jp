---
title: 'Sql を使用した CDATA セクションの作成: Using-cdata (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: rothja
ms.author: jroth
ms.openlocfilehash: c0ba0787efbda400590a75f0f3529e3df8819e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644397"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a><span data-ttu-id="68759-102">sql:use-cdata を使用した、CDATA セクションの作成 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="68759-102">Creating CDATA Sections Using sql:use-cdata (SQLXML 4.0)</span></span>
  <span data-ttu-id="68759-103">XML では、文字がマークアップ文字として処理されないよう、文字を含むテキスト ブロックをエスケープするときに CDATA セクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="68759-103">In XML, CDATA sections are used to escape blocks of text that contain characters that would otherwise be recognized as markup characters.</span></span>  
  
 <span data-ttu-id="68759-104">Microsoft のデータベースには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML パーサーによってマークアップ文字として扱われる文字が含まれる場合があります。たとえば、山かっこ ( \< and > )、小なり記号 (<=)、アンパサンド (&) は、マークアップ文字として扱われます。</span><span class="sxs-lookup"><span data-stu-id="68759-104">A database in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can sometimes contain characters that are treated as markup characters by the XML parser; for example, angle brackets (\< and >), the less-than-or-equal-to symbol (<=), and the ampersand (&) are treated as markup characters.</span></span> <span data-ttu-id="68759-105">この種類の特殊文字は、CDATA セクションで囲むことでマークアップ文字として扱われないようにできます。</span><span class="sxs-lookup"><span data-stu-id="68759-105">However, you can wrap this type of special characters in a CDATA section to prevent them from being treated as markup characters.</span></span> <span data-ttu-id="68759-106">CDATA セクション内の文字は、XML パーサーでプレーン テキストとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="68759-106">The text within the CDATA section is treated by the XML parser as plain text.</span></span>  
  
 <span data-ttu-id="68759-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で返されるデータを CDATA セクションで囲むには、`sql:use-cdata` 注釈を使用します。この注釈では、`sql:field` で指定される列の値を CDATA セクションで囲むかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="68759-107">The `sql:use-cdata` annotation is used to specify that the data returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be wrapped in a CDATA section (that is, it indicates whether the value from a column that is specified by `sql:field` should be enclosed in a CDATA section).</span></span> <span data-ttu-id="68759-108">`sql:use-cdata` 注釈は、データベース列にマップされる要素だけに指定できます。</span><span class="sxs-lookup"><span data-stu-id="68759-108">The `sql:use-cdata` annotation can be specified only on elements that map to a database column.</span></span>  
  
 <span data-ttu-id="68759-109">`sql:use-cdata` 注釈はブール値 (0 = false、1 = true) をとります。</span><span class="sxs-lookup"><span data-stu-id="68759-109">The `sql:use-cdata` annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="68759-110">指定できる値は 0、1、true、false です。</span><span class="sxs-lookup"><span data-stu-id="68759-110">The acceptable values are 0, 1, true, and false.</span></span>  
  
 <span data-ttu-id="68759-111">この注釈は、`sql:url-encode` と共に使用したり、ID、IDREF、IDREFS、NMTOKEN、NMTOKENS 属性型に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="68759-111">This annotation cannot be used with `sql:url-encode` or on the ID, IDREF, IDREFS, NMTOKEN, and NMTOKENS attribute types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="68759-112">例</span><span class="sxs-lookup"><span data-stu-id="68759-112">Examples</span></span>  
 <span data-ttu-id="68759-113">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="68759-113">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="68759-114">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68759-114">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a><span data-ttu-id="68759-115">A.</span><span class="sxs-lookup"><span data-stu-id="68759-115">A.</span></span> <span data-ttu-id="68759-116">要素に対して sql:use-cdata を指定する</span><span class="sxs-lookup"><span data-stu-id="68759-116">Specifying sql:use-cdata on an element</span></span>  
 <span data-ttu-id="68759-117">次のスキーマで `sql:use-cdata` は、が要素内のに対して 1 (True) に設定されてい **\<AddressLine1>** **\<Address>** ます。</span><span class="sxs-lookup"><span data-stu-id="68759-117">In the following schema, `sql:use-cdata` is set to 1 (True) for the **\<AddressLine1>** within the **\<Address>** element.</span></span> <span data-ttu-id="68759-118">この結果、データは CDATA セクション内に返されます。</span><span class="sxs-lookup"><span data-stu-id="68759-118">As a result, the data is returned in a CDATA section.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="68759-119">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="68759-119">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="68759-120">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="68759-120">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="68759-121">UseCData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="68759-121">Save the file as UseCData.xml.</span></span>  
  
2.  <span data-ttu-id="68759-122">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="68759-122">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="68759-123">UseCData.xml を保存したディレクトリに UseCDataT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="68759-123">Save the file as UseCDataT.xml in the same directory where you saved UseCData.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="68759-124">マッピング スキーマ (UseCData.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="68759-124">The directory path specified for the mapping schema (UseCData.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="68759-125">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="68759-125">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  <span data-ttu-id="68759-126">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="68759-126">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="68759-127">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68759-127">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="68759-128">結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="68759-128">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
