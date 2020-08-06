---
title: ワイルドカード コンポーネントと内容検証 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- wildcard components [XML]
- content validation [XML]
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
author: rothja
ms.author: jroth
ms.openlocfilehash: 76ff2b48efb8cff0b98827fe8522405682c294e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633009"
---
# <a name="wildcard-components-and-content-validation"></a><span data-ttu-id="d09cd-102">ワイルドカード コンポーネントと内容検証</span><span class="sxs-lookup"><span data-stu-id="d09cd-102">Wildcard Components and Content Validation</span></span>
  <span data-ttu-id="d09cd-103">ワイルドカード コンポーネントは、コンテンツ モデルで使用できる表現の柔軟性を高めるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d09cd-103">Wildcard components are used to increase flexibility in what is allowed to appear in a content model.</span></span> <span data-ttu-id="d09cd-104">ワイルドカード コンポーネントは、次のように XSD 言語でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d09cd-104">These components are supported in the XSD language in the following ways:</span></span>  
  
-   <span data-ttu-id="d09cd-105">要素ワイルドカード コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="d09cd-105">Element wildcard components.</span></span> <span data-ttu-id="d09cd-106">これらは **\<xsd:any>** 要素で表現されます。</span><span class="sxs-lookup"><span data-stu-id="d09cd-106">These are represented by the **\<xsd:any>** element.</span></span>  
  
-   <span data-ttu-id="d09cd-107">属性ワイルドカード コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="d09cd-107">Attribute wildcard components.</span></span> <span data-ttu-id="d09cd-108">これらは **\<xsd:anyAttribute>** 要素で表現されます。</span><span class="sxs-lookup"><span data-stu-id="d09cd-108">These are represented by the **\<xsd:anyAttribute>** element.</span></span>  
  
 <span data-ttu-id="d09cd-109">両方のワイルドカード文字要素 ( **\<xsd:any>** および **\<xsd:anyAttribute>** ) で **processContents** 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d09cd-109">Both wildcard character elements, **\<xsd:any>** and **\<xsd:anyAttribute>**, support the use of a **processContents** attribute.</span></span> <span data-ttu-id="d09cd-110">この属性を使用して、ワイルドカード文字要素で関連付けられるドキュメントの内容の違反を、XML アプリケーションで検証する方法を示す値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d09cd-110">This lets you specify a value that indicates how XML applications handle the validation of document content associated with these wildcard character elements.</span></span> <span data-ttu-id="d09cd-111">検証方法を示す値には、次のようにそれぞれ異なる効果があります。</span><span class="sxs-lookup"><span data-stu-id="d09cd-111">These are the different values and their effect:</span></span>  
  
-   <span data-ttu-id="d09cd-112">**strict** 値は、内容を完全に検証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d09cd-112">The **strict** value specifies that the contents are fully validated.</span></span>  
  
-   <span data-ttu-id="d09cd-113">**skip** 値は、内容を検証しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="d09cd-113">The **skip** value specifies that the contents are not validated.</span></span>  
  
-   <span data-ttu-id="d09cd-114">**lax** 値は、スキーマ定義が有効な要素と属性だけを検証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d09cd-114">The **lax** value specifies that only elements and attributes for which schema definitions are available are validated.</span></span>  
  
## <a name="lax-validation-and-xsanytype-elements"></a><span data-ttu-id="d09cd-115">lax 検証と xs:anyType 要素</span><span class="sxs-lookup"><span data-stu-id="d09cd-115">Lax Validation and xs:anyType Elements</span></span>  
 <span data-ttu-id="d09cd-116">XML スキーマの仕様では、 **anyType** 型の要素には **lax** 検証が使用されています。</span><span class="sxs-lookup"><span data-stu-id="d09cd-116">The XML Schema specification uses **lax** validation for elements of the **anyType** type.</span></span> <span data-ttu-id="d09cd-117">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では lax 検証をサポートしていなかったので、 **anyType**型の要素にも strict 検証が適用されていました。</span><span class="sxs-lookup"><span data-stu-id="d09cd-117">Because [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] did not support lax validation, strict validation was applied for elements of the **anyType**.</span></span> <span data-ttu-id="d09cd-118">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]からは lax 検証がサポートされるようになったため、</span><span class="sxs-lookup"><span data-stu-id="d09cd-118">Beginning with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], lax validation is supported.</span></span> <span data-ttu-id="d09cd-119">**anyType** 型の要素の内容は lax 検証を使用して検証されます。</span><span class="sxs-lookup"><span data-stu-id="d09cd-119">Content of elements of type **anyType** will be validated using lax validation.</span></span>  
  
 <span data-ttu-id="d09cd-120">次の例は、lax 検証を示しています。</span><span class="sxs-lookup"><span data-stu-id="d09cd-120">The following example illustrates the lax validation.</span></span> <span data-ttu-id="d09cd-121">スキーマ要素 `e` は **anyType** 型です。</span><span class="sxs-lookup"><span data-stu-id="d09cd-121">The schema element `e` is of the **anyType** type.</span></span> <span data-ttu-id="d09cd-122">この例では、型指定された **xml** 変数を作成し、 **anyType** 型の要素の lax 検証を示します。</span><span class="sxs-lookup"><span data-stu-id="d09cd-122">The example creates typed **xml** variables and illustrates the lax validation of the element of the **anyType** type.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="http://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 <span data-ttu-id="d09cd-123">`<e>` の検証が成功するので、次の例は成功します。</span><span class="sxs-lookup"><span data-stu-id="d09cd-123">The following example succeeds, because the validation of `<e>` is successful:</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 <span data-ttu-id="d09cd-124">次の例は成功します。</span><span class="sxs-lookup"><span data-stu-id="d09cd-124">The following example succeeds.</span></span> <span data-ttu-id="d09cd-125">要素 `<c>` はスキーマで定義されていませんが、インスタンスは受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="d09cd-125">The instance is accepted, even though no element `<c>` is defined in the schema:</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 <span data-ttu-id="d09cd-126">次の例の XML インスタンスは拒否されます。これは、 `<a>` 要素の定義で文字列値が許可されていないためです。</span><span class="sxs-lookup"><span data-stu-id="d09cd-126">The XML instance in the following example is rejected, because the definition of the `<a>` element does not allow a string value.</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d09cd-127">参照</span><span class="sxs-lookup"><span data-stu-id="d09cd-127">See Also</span></span>  
 [<span data-ttu-id="d09cd-128">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="d09cd-128">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
