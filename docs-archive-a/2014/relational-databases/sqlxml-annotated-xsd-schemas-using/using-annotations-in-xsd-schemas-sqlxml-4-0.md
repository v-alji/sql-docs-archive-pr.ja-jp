---
title: XSD スキーマでの注釈の使用 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: rothja
ms.author: jroth
ms.openlocfilehash: e2be94aa5815593d7a5a2e0c00bcd8849e81484e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640859"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a><span data-ttu-id="e0469-102">XSD スキーマでの注釈の使用 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e0469-102">Using Annotations in XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="e0469-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 では、XML-Data Reduced (XDR) スキーマ言語で導入された注釈と同様に、XSD スキーマ言語で注釈がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e0469-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0, the XSD schema language supports annotations in a manner similar to the annotations introduced in the XML-Data Reduced (XDR) schema language.</span></span> <span data-ttu-id="e0469-104">XSD では、XDR でサポートされない追加の注釈も導入されています。</span><span class="sxs-lookup"><span data-stu-id="e0469-104">There are additional annotations introduced in XSD that are not supported in XDR.</span></span>  
  
 <span data-ttu-id="e0469-105">XSD スキーマでこれらの注釈を使用して、XML とリレーショナルのマッピングを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e0469-105">These annotations can be used within the XSD schema to specify XML-to-relational mapping.</span></span> <span data-ttu-id="e0469-106">これには、XSD スキーマ内の要素および属性から、データベース内のテーブル (ビュー) および列へのマッピングが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e0469-106">This includes mapping between elements and attributes in the XSD schema to tables (views) and columns in the databases.</span></span>  
  
 <span data-ttu-id="e0469-107">注釈を指定しない場合は、既定のマッピングが行われます。</span><span class="sxs-lookup"><span data-stu-id="e0469-107">If you do not specify the annotations, default mapping takes place.</span></span> <span data-ttu-id="e0469-108">既定では、複合型の XSD 要素は指定したデータベースのテーブルまたはビュー名にマップされ、単純型の要素または属性は、要素または属性と同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="e0469-108">By default, an XSD element with a complex type maps to a table (view) name in the specified database, and an element or attribute with a simple type maps to the column with the same name as the element or attribute.</span></span>  
  
 <span data-ttu-id="e0469-109">これらの注釈を使用して、XML 内の階層リレーションシップを指定することもできます。これは、XSD スキーマがリレーショナルデータの XML ビューであるためです。</span><span class="sxs-lookup"><span data-stu-id="e0469-109">These annotations can also be used to specify the hierarchical relationships in XML-thus representing the relationships in the database, because an XSD schema is simply an XML view of relational data.</span></span>  
  
 <span data-ttu-id="e0469-110">ここでは、XSD スキーマで使用できる注釈について説明し、それらの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-110">This section provides descriptions of the annotations you can use with XSD schemas and examples of their usage.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0469-111">すべての例では、それぞれの注釈付き XSD スキーマに対して、単純な XPath クエリを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0469-111">All the examples in this section specify simple XPath queries against the annotated XSD schema described in each example.</span></span> <span data-ttu-id="e0469-112">前提条件として、XPath 言語について理解していることが必要です。</span><span class="sxs-lookup"><span data-stu-id="e0469-112">Familiarity with the XPath language is assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0469-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e0469-113">In This Section</span></span>  
 [<span data-ttu-id="e0469-114">&#40;SQLXML 4.0&#41;の XSD 注釈</span><span class="sxs-lookup"><span data-stu-id="e0469-114">XSD Annotations &#40;SQLXML 4.0&#41;</span></span>](xsd-annotations-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-115">XSD スキーマで使用できる注釈と、その説明、および同等の XDR 注釈を一覧で示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-115">Lists the annotations you can use with XSD schemas, their descriptions, and the equivalent annotations for XDR.</span></span>  
  
 [<span data-ttu-id="e0469-116">テーブルおよび列への XSD 要素と属性の既定のマッピング &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-116">Default Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-117">既定のマッピングについて説明し、既定のマッピングに関連するタスクの例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-117">Explains default mapping and provides examples of tasks related to default mapping.</span></span>  
  
 [<span data-ttu-id="e0469-118">テーブルおよび列への XSD 要素と属性の明示的なマッピング &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-118">Explicit Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 <span data-ttu-id="e0469-119">`sql:relation` 注釈と `sql:field` 注釈の明示的なマッピングについて説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-119">Explains explicit mapping with the `sql:relation` and `sql:field` annotations, and provides examples.</span></span>  
  
 [<span data-ttu-id="e0469-120">Sql: relationship を使用したリレーションシップの指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-120">Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-121">`sql:relationship` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-121">Describes and provides examples of the `sql:relationship` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-122">Sql: relationship での sql: 逆属性の指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-122">Specifying the sql:inverse Attribute on sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-123">`sql:inverse` 注釈について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0469-123">Describes the `sql:inverse` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-124">Sql を使用した定数要素の作成: &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-124">Creating Constant Elements Using sql:is-constant &#40;SQLXML 4.0&#41;</span></span>](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-125">`sql:is-constant` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-125">Describes and provides examples of the `sql:is-constant` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-126">Sql: マップト &#40;SQLXML 4.0&#41;を使用した結果の XML ドキュメントからのスキーマ要素の除外</span><span class="sxs-lookup"><span data-stu-id="e0469-126">Excluding Schema Elements from the Resulting XML Document Using sql:mapped &#40;SQLXML 4.0&#41;</span></span>](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 <span data-ttu-id="e0469-127">`sql:mapped` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-127">Describes and provides examples of the `sql:mapped` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-128">Sql: limit-field および sql: limit-value &#40;SQLXML 4.0&#41;を使用した値のフィルター処理</span><span class="sxs-lookup"><span data-stu-id="e0469-128">Filtering Values Using sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 <span data-ttu-id="e0469-129">`sql:limit-field` 注釈と `sql:limit-value` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-129">Describes and provides examples of the `sql:limit-field` and `sql:limit-value` annotations.</span></span>  
  
 [<span data-ttu-id="e0469-130">Sql: キーフィールド &#40;SQLXML 4.0&#41;を使用したキー列の識別</span><span class="sxs-lookup"><span data-stu-id="e0469-130">Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;</span></span>](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-131">`sql:key-fields` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-131">Describes and provides examples of the `sql:key-fields` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-132">TargetNamespace 属性を使用してターゲットの名前空間を指定する &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-132">Specifying a Target Namespace Using the targetNamespace Attribute &#40;SQLXML 4.0&#41;</span></span>](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-133">について説明し、 **targetNamespace**属性の例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-133">Describes and provides examples of the **targetNamespace** attribute.</span></span>  
  
 [<span data-ttu-id="e0469-134">Sql: prefix &#40;SQLXML 4.0&#41;を使用した有効な ID、IDREF、IDREFS 型の属性の作成</span><span class="sxs-lookup"><span data-stu-id="e0469-134">Creating Valid ID, IDREF, and IDREFS Type Attributes Using sql:prefix &#40;SQLXML 4.0&#41;</span></span>](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-135">`sql:prefix` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-135">Describes and provides examples of the `sql:prefix` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-136">データ型の強制型変換と sql: datatype 注釈 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-136">Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;</span></span>](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-137">`sql:datatype` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-137">Describes and provides examples of the `sql:datatype` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-138">XSD データ型から XPath データ型へのマッピング &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-138">Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-139">XSD、XDR、および XPath のデータ型の対照表と、関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-139">Provides a table that compares XSD, XDR, and XPath datatypes and lists the relevant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conversions.</span></span>  
  
 [<span data-ttu-id="e0469-140">Sql を使用した CDATA セクションの作成: &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-140">Creating CDATA Sections Using sql:use-cdata &#40;SQLXML 4.0&#41;</span></span>](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-141">`sql:use-data` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-141">Describes and provides examples of the `sql:use-data` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-142">Sql: encode &#40;SQLXML 4.0&#41;を使用した BLOB データへの URL 参照の要求</span><span class="sxs-lookup"><span data-stu-id="e0469-142">Requesting URL References to BLOB Data Using sql:encode &#40;SQLXML 4.0&#41;</span></span>](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 <span data-ttu-id="e0469-143">`sql:encode` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-143">Describes and provides examples of the `sql:encode` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-144">Sql: overflow フィールドを使用した未使用データの取得 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0469-144">Retrieving Unconsumed Data Using the sql:overflow-field &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 <span data-ttu-id="e0469-145">`sql:overflow-field` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-145">Describes and provides examples of the `sql:overflow-field` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-146">sql:hide を使用した要素と属性の非表示</span><span class="sxs-lookup"><span data-stu-id="e0469-146">Hiding Elements and Attributes by Using sql:hide</span></span>](hiding-elements-and-attributes-by-using-sql-hide.md)  
 <span data-ttu-id="e0469-147">`sql:hide` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-147">Describes and provides examples of the `sql:hide` annotation.</span></span>  
  
 [<span data-ttu-id="e0469-148">sql:identity 注釈と sql:guid 注釈の使用</span><span class="sxs-lookup"><span data-stu-id="e0469-148">Using the sql:identity and sql:guid Annotations</span></span>](using-the-sql-identity-and-sql-guid-annotations.md)  
 <span data-ttu-id="e0469-149">`sql:identity` 注釈と `sql:guid` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-149">Describes and provides examples of the `sql:identity` and `sql:guid` annotations.</span></span>  
  
 [<span data-ttu-id="e0469-150">sql:max-depth を使用した、再帰リレーションシップの深さの指定</span><span class="sxs-lookup"><span data-stu-id="e0469-150">Specifying Depth in Recursive Relationships by Using sql:max-depth</span></span>](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 <span data-ttu-id="e0469-151">`sql:max-depth` 注釈について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0469-151">Describes and provides examples of the `sql:max-depth` annotation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0469-152">参照</span><span class="sxs-lookup"><span data-stu-id="e0469-152">See Also</span></span>  
 [<span data-ttu-id="e0469-153">SQLXML 4.0&#41;&#40;注釈付きスキーマのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="e0469-153">Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
