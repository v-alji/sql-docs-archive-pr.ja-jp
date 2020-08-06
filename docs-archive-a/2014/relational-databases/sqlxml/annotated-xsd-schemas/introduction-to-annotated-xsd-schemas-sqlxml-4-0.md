---
title: 注釈付き XSD スキーマの概要 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: rothja
ms.author: jroth
ms.openlocfilehash: b91be71569daa9e5bf4143be9f652617ba7c5b01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642683"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a><span data-ttu-id="a7011-102">注釈付き XSD スキーマの概要 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a7011-102">Introduction to Annotated XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="a7011-103">XML スキーマ定義 (XSD) 言語を使用して、リレーショナル データの XML ビューを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a7011-103">You can create XML views of relational data by using the XML Schema Definition (XSD) language.</span></span> <span data-ttu-id="a7011-104">作成したビューには、XML パス言語 (XPath) クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a7011-104">These views can then be queried by using XML Path language (XPath) queries.</span></span> <span data-ttu-id="a7011-105">これは、CREATE VIEW ステートメントを使用してビューを作成し、そのビューに対して SQL クエリを指定することに似ています。</span><span class="sxs-lookup"><span data-stu-id="a7011-105">This is similar to creating views by using CREATE VIEW statements and then specifying SQL queries against the view.</span></span>  
  
 <span data-ttu-id="a7011-106">XML スキーマでは、XML ドキュメントの構造とドキュメント内のデータに対するさまざまな制約が記述されます。</span><span class="sxs-lookup"><span data-stu-id="a7011-106">An XML schema describes the structure of an XML document and also describes the various constraints on the data in the document.</span></span> <span data-ttu-id="a7011-107">スキーマに対して XPath クエリを指定した場合、返される XML ドキュメントの構造は、XPath クエリの実行対象のスキーマによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="a7011-107">When you specify XPath queries against the schema, the structure of the XML document returned is determined by the schema against which the XPath query is executed.</span></span>  
  
 <span data-ttu-id="a7011-108">XSD スキーマでは、 **\<xsd:schema>** 要素はスキーマ全体を囲みます。すべての要素宣言が要素内に含まれている必要があり **\<xsd:schema>** ます。</span><span class="sxs-lookup"><span data-stu-id="a7011-108">In an XSD schema, the **\<xsd:schema>** element encloses the entire schema; all element declarations must be contained within the **\<xsd:schema>** element.</span></span> <span data-ttu-id="a7011-109">スキーマが存在する名前空間を定義する属性と、その要素のプロパティとしてスキーマで使用される名前空間を記述でき **\<xsd:schema>** ます。</span><span class="sxs-lookup"><span data-stu-id="a7011-109">You can describe attributes that define the namespace in which the schema resides and the namespaces that are used in the schema as properties of the **\<xsd:schema>** element.</span></span>  
  
 <span data-ttu-id="a7011-110">有効な XSD スキーマには、次のように定義された要素が含まれている必要があり **\<xsd:schema>** ます。</span><span class="sxs-lookup"><span data-stu-id="a7011-110">A valid XSD schema must contain the **\<xsd:schema>** element defined as follows:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 <span data-ttu-id="a7011-111">**\<xsd:schema>** 要素は、XML スキーマ名前空間の仕様 () から派生 http://www.w3.org/2001/XMLSchema します。</span><span class="sxs-lookup"><span data-stu-id="a7011-111">The **\<xsd:schema>** element is derived from the XML Schema namespace specification at http://www.w3.org/2001/XMLSchema.</span></span>  
  
## <a name="annotations-to-the-xsd-schema"></a><span data-ttu-id="a7011-112">XSD スキーマへの注釈</span><span class="sxs-lookup"><span data-stu-id="a7011-112">Annotations to the XSD Schema</span></span>  
 <span data-ttu-id="a7011-113">データベースへのマッピングを記述する注釈付きの XSD スキーマを使用して、データベースにクエリを実行し、結果を XML ドキュメントの形式で返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a7011-113">You can use an XSD schema with annotations that describe the mapping to a database, query the database, and return the results in the form of an XML document.</span></span> <span data-ttu-id="a7011-114">注釈は、データベースのテーブルと列に XSD スキーマをマップするために指定します。</span><span class="sxs-lookup"><span data-stu-id="a7011-114">Annotations are provided to map an XSD schema to database tables and columns.</span></span> <span data-ttu-id="a7011-115">XSD スキーマで作成した XML ビューに対して XPath クエリを指定すると、データベースにクエリが実行され、結果を XML として取得できます。</span><span class="sxs-lookup"><span data-stu-id="a7011-115">XPath queries can be specified against the XML view created by the XSD schema to query the database and obtain results as an XML.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7011-116">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 の XSD スキーマ言語では、[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] の注釈付き XML-Data Reduced (XDR) スキーマ言語で挿入された注釈がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a7011-116">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, the XSD schema language supports the annotations introduced with annotated XML-Data Reduced (XDR) schema language in [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="a7011-117">ただし、注釈付き XDR は、SQLXML 4.0 では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a7011-117">Annotated XDR is deprecated in SQLXML 4.0.</span></span>  
  
 <span data-ttu-id="a7011-118">リレーショナル データベースの場合、任意の XSD スキーマをリレーショナル ストアにマップすると便利です。</span><span class="sxs-lookup"><span data-stu-id="a7011-118">In the context of the relational database, it is useful to map the arbitrary XSD schema to a relational store.</span></span> <span data-ttu-id="a7011-119">これを実行する 1 つの方法は、XSD スキーマに注釈を付けることです。</span><span class="sxs-lookup"><span data-stu-id="a7011-119">One way to achieve this is to annotate the XSD schema.</span></span> <span data-ttu-id="a7011-120">注釈を持つ XSD スキーマは、*マッピングスキーマ*と呼ばれます。これは、XML データをリレーショナルストアにマップする方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a7011-120">An XSD schema with the annotations is referred to as a *mapping schema*, which provides information pertaining to how XML data is to be mapped to the relational store.</span></span> <span data-ttu-id="a7011-121">マッピング スキーマは、実質的にはリレーショナル データの XML ビューです。</span><span class="sxs-lookup"><span data-stu-id="a7011-121">A mapping schema is, in effect, an XML view of the relational data.</span></span> <span data-ttu-id="a7011-122">これらのマッピングを使用して、リレーショナル データを XML ドキュメントとして取得できます。</span><span class="sxs-lookup"><span data-stu-id="a7011-122">These mappings can be used to retrieve relational data as an XML document.</span></span>  
  
## <a name="namespace-for-annotations"></a><span data-ttu-id="a7011-123">注釈の名前空間</span><span class="sxs-lookup"><span data-stu-id="a7011-123">Namespace for Annotations</span></span>  
 <span data-ttu-id="a7011-124">XSD スキーマでは、名前空間**urn: schema-microsoft-com: mapping スキーマ**を使用して注釈を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7011-124">In an XSD schema, annotations are specified by using the namespace **urn:schemas-microsoft-com:mapping-schema**.</span></span> <span data-ttu-id="a7011-125">次の例に示すように、名前空間を指定する最も簡単な方法は、タグ内で名前空間を指定することです **\<xsd:schema>** 。</span><span class="sxs-lookup"><span data-stu-id="a7011-125">As shown in the following example, the easiest way to specify the namespace is to specify it in the **\<xsd:schema>** tag.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 <span data-ttu-id="a7011-126">使用される名前空間プレフィックスは任意です。</span><span class="sxs-lookup"><span data-stu-id="a7011-126">The namespace prefix that is used is arbitrary.</span></span> <span data-ttu-id="a7011-127">このドキュメントでは、 **sql**プレフィックスを使用して、注釈の名前空間を表し、この名前空間内の注釈を他の名前空間内の注釈と区別します。</span><span class="sxs-lookup"><span data-stu-id="a7011-127">In this documentation, the **sql** prefix is used to denote the annotation namespace and to distinguish annotations in this namespace from those in other namespaces.</span></span>  
  
## <a name="example-of-an-annotated-xsd-schema"></a><span data-ttu-id="a7011-128">注釈付き XSD スキーマの例</span><span class="sxs-lookup"><span data-stu-id="a7011-128">Example of an Annotated XSD Schema</span></span>  
 <span data-ttu-id="a7011-129">次の例では、XSD スキーマは要素で構成されて **\<Person.Contact>** います。</span><span class="sxs-lookup"><span data-stu-id="a7011-129">In the following example, the XSD schema consists of an **\<Person.Contact>** element.</span></span> <span data-ttu-id="a7011-130">要素には、 **\<Employee>** **ContactID**属性と **\<FirstName>** 子 **\<LastName>** 要素があります。</span><span class="sxs-lookup"><span data-stu-id="a7011-130">The **\<Employee>** element has a **ContactID** attribute and **\<FirstName>** and **\<LastName>** child elements:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="a7011-131">この XSD スキーマに、要素と属性をデータベースのテーブルと列にマップするため、注釈を追加します。</span><span class="sxs-lookup"><span data-stu-id="a7011-131">Annotations are added to this XSD schema to map its elements and attributes to the database tables and columns:</span></span>  
  
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
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="a7011-132">マッピングスキーマで **\<Contact>** は、要素は、注釈を使用して、サンプルの AdventureWorks データベースの Person. Contact テーブルにマップされ `sql:relation` ます。</span><span class="sxs-lookup"><span data-stu-id="a7011-132">In the mapping schema, the **\<Contact>** element is mapped to the Person.Contact table in the sample AdventureWorks database by using the `sql:relation` annotation.</span></span> <span data-ttu-id="a7011-133">また、`sql:field` 注釈によって、属性 ConID、FName、LName が Person.Contact テーブルの ContactID 列、FirstName 列、LastName 列にそれぞれマップされます。</span><span class="sxs-lookup"><span data-stu-id="a7011-133">The attributes ConID, FName, and LName are mapped to the ContactID, FirstName, and LastName columns in the Person.Contact table by using the `sql:field` annotations.</span></span>  
  
 <span data-ttu-id="a7011-134">この注釈付きの XSD スキーマによって、リレーショナル データの XML ビューが提供されます。</span><span class="sxs-lookup"><span data-stu-id="a7011-134">This annotated XSD schema provides the XML view of the relational data.</span></span> <span data-ttu-id="a7011-135">この XML ビューには、XPath 言語を使用してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a7011-135">This XML view can be queried using the XPath language.</span></span> <span data-ttu-id="a7011-136">XPath クエリを実行すると、SQL クエリによって返される行セットではなく、XML ドキュメントが返されます。</span><span class="sxs-lookup"><span data-stu-id="a7011-136">An XPath query returns an XML document as a result, instead of the rowset that is returned by SQL queries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7011-137">マッピング スキーマに指定するリレーショナル値 (テーブル名や列名など) の大文字小文字の区別は、SQL Server で使用される照合順序の、大文字小文字の区別の設定によって変わります。</span><span class="sxs-lookup"><span data-stu-id="a7011-137">In the mapping schema, case-sensitivity for the specified relational values (such as table name and column name) depends upon if SQL Server is using case-sensitive collation settings.</span></span> <span data-ttu-id="a7011-138">詳細については、「 [Collation and Unicode Support](../../collations/collation-and-unicode-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7011-138">For more information, see [Collation and Unicode Support](../../collations/collation-and-unicode-support.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="a7011-139">その他の参照情報</span><span class="sxs-lookup"><span data-stu-id="a7011-139">Other Resources</span></span>  
 <span data-ttu-id="a7011-140">XML スキーマ定義言語 (XSD)、XML パス言語 (XPath)、Extensible Stylesheet Language Transformations (XSLT) の詳細については、次の Web サイトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7011-140">You can find more information about XML Schema Definition language (XSD), XML Path language (XPath), and Extensible Stylesheet Language Transformations (XSLT) at the following Web sites:</span></span>  
  
-   <span data-ttu-id="a7011-141">XML スキーマパート 0: 入門、W3C 勧告 (http://www.w3.org/TR/xmlschema-0/)</span><span class="sxs-lookup"><span data-stu-id="a7011-141">XML Schema Part 0: Primer, W3C Recommendation (http://www.w3.org/TR/xmlschema-0/)</span></span>  
  
-   <span data-ttu-id="a7011-142">XML スキーマパート 1: 構造体、W3C 勧告 (http://www.w3.org/TR/xmlschema-1/)</span><span class="sxs-lookup"><span data-stu-id="a7011-142">XML Schema Part 1: Structures, W3C Recommendation (http://www.w3.org/TR/xmlschema-1/)</span></span>  
  
-   <span data-ttu-id="a7011-143">XML スキーマパート 2: データ型、W3C 勧告 (http://www.w3.org/TR/xmlschema-2/)</span><span class="sxs-lookup"><span data-stu-id="a7011-143">XML Schema Part 2:Datatypes, W3C Recommendation (http://www.w3.org/TR/xmlschema-2/)</span></span>  
  
-   <span data-ttu-id="a7011-144">XML パス言語 (XPath) (http://www.w3.org/TR/xpath)</span><span class="sxs-lookup"><span data-stu-id="a7011-144">XML Path Language (XPath) (http://www.w3.org/TR/xpath)</span></span>  
  
-   <span data-ttu-id="a7011-145">XSL 変換 (XSLT) (http://www.w3.org/TR/xslt)</span><span class="sxs-lookup"><span data-stu-id="a7011-145">XSL Transformations (XSLT) (http://www.w3.org/TR/xslt)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7011-146">参照</span><span class="sxs-lookup"><span data-stu-id="a7011-146">See Also</span></span>  
 <span data-ttu-id="a7011-147">[SQLXML 4.0&#41;&#40;注釈付きスキーマのセキュリティに関する考慮事項](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="a7011-147">[Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="a7011-148">注釈付き XDR スキーマ &#40;SQLXML 4.0 で非推奨とされました&#41;</span><span class="sxs-lookup"><span data-stu-id="a7011-148">Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;</span></span>](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
