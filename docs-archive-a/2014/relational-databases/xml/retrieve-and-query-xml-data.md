---
title: XML データの取得および XML データに対するクエリの実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], retrieving
- XML instance retrieval
ms.assetid: 24a28760-1225-42b3-9c89-c9c0332d9c51
author: rothja
ms.author: jroth
ms.openlocfilehash: d387d1b96a57dcc7100368779f8ec6078fad5c7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713910"
---
# <a name="retrieve-and-query-xml-data"></a><span data-ttu-id="dc534-102">XML データの取得および XML データに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="dc534-102">Retrieve and Query XML Data</span></span>
  <span data-ttu-id="dc534-103">このトピックでは、XML データのクエリを実行するために指定する必要があるクエリ オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dc534-103">This topic describes the query options that you have to specify to query XML data.</span></span> <span data-ttu-id="dc534-104">また、XML インスタンスをデータベースに格納するときに保持されない部分についても説明します。</span><span class="sxs-lookup"><span data-stu-id="dc534-104">It also describes the parts of XML instances that are not preserved when they are stored in databases.</span></span>  
  
##  <a name="features-of-an-xml-instance-that-are-not-preserved"></a><a name="features"></a> <span data-ttu-id="dc534-105">保持されない XML インスタンスの機能</span><span class="sxs-lookup"><span data-stu-id="dc534-105">Features of an XML Instance That Are Not Preserved</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dc534-106">では、XML インスタンスの内容は保持されますが、XML データ モデルで重要と見なされない側面は保持されません。</span><span class="sxs-lookup"><span data-stu-id="dc534-106">preserves the content of the XML instance, but does not preserve aspects of the XML instance that are not considered to be significant in the XML data model.</span></span> <span data-ttu-id="dc534-107">つまり、取得した XML インスタンスは、サーバーに格納されたインスタンスと同一とは限りませんが、含まれている情報は同じです。</span><span class="sxs-lookup"><span data-stu-id="dc534-107">This means that a retrieved XML instance might not be identical to the instance that was stored in the server, but will contain the same information.</span></span>  
  
### <a name="xml-declaration"></a><span data-ttu-id="dc534-108">XML 宣言</span><span class="sxs-lookup"><span data-stu-id="dc534-108">XML Declaration</span></span>  
 <span data-ttu-id="dc534-109">インスタンスをデータベースに格納する場合は、そのインスタンスの XML 宣言は保持されません。</span><span class="sxs-lookup"><span data-stu-id="dc534-109">The XML declaration in an instance is not preserved when the instance is stored in the database.</span></span> <span data-ttu-id="dc534-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="dc534-110">For example:</span></span>  
  
```  
CREATE TABLE T1 (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T1 values (1, '<?xml version="1.0" encoding="windows-1252" ?><doc></doc>')  
GO  
SELECT Col2  
FROM T1  
```  
  
 <span data-ttu-id="dc534-111">結果は `<doc/>`です。</span><span class="sxs-lookup"><span data-stu-id="dc534-111">The result is `<doc/>`.</span></span>  
  
 <span data-ttu-id="dc534-112">`<?xml version='1.0'?>` などの XML 宣言は、XML データを `xml` データ型インスタンスに格納するときに保持されません。</span><span class="sxs-lookup"><span data-stu-id="dc534-112">The XML declaration, such as `<?xml version='1.0'?>`, is not preserved when storing XML data in an `xml` data type instance.</span></span> <span data-ttu-id="dc534-113">これは仕様です。</span><span class="sxs-lookup"><span data-stu-id="dc534-113">This is by design.</span></span> <span data-ttu-id="dc534-114">XML 宣言 () とその属性 (バージョン/エンコーディング/スタンドアロン) は、データを型に変換した後に失われ `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="dc534-114">The XML declaration () and its attributes (version/encoding/stand-alone) are lost after data is converted to type `xml`.</span></span> <span data-ttu-id="dc534-115">XML 宣言は、XML パーサーが使用するディレクティブとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="dc534-115">The XML declaration is treated as a directive to the XML parser.</span></span> <span data-ttu-id="dc534-116">XML データは、ucs-2 として内部的に保存されます。</span><span class="sxs-lookup"><span data-stu-id="dc534-116">The XML data is stored internally as ucs-2.</span></span> <span data-ttu-id="dc534-117">XML インスタンスのその他すべての PI は保持されます。</span><span class="sxs-lookup"><span data-stu-id="dc534-117">All other PIs in the XML instance are preserved.</span></span>  
  
  
### <a name="order-of-attributes"></a><span data-ttu-id="dc534-118">属性の順序</span><span class="sxs-lookup"><span data-stu-id="dc534-118">Order of Attributes</span></span>  
 <span data-ttu-id="dc534-119">XML インスタンス内の属性の順序は保持されません。</span><span class="sxs-lookup"><span data-stu-id="dc534-119">The order of attributes in an XML instance is not preserved.</span></span> <span data-ttu-id="dc534-120">`xml` 型の列に格納されている XML インスタンスにクエリを実行する場合、結果の XML の属性の順序は元の XML インスタンスとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc534-120">When you query the XML instance stored in the `xml` type column, the order of attributes in the resulting XML may be different from the original XML instance.</span></span>  
  
  
### <a name="quotation-marks-around-attribute-values"></a><span data-ttu-id="dc534-121">属性値を囲む引用符</span><span class="sxs-lookup"><span data-stu-id="dc534-121">Quotation Marks Around Attribute Values</span></span>  
 <span data-ttu-id="dc534-122">属性を囲む単一引用符および二重引用符は、保持されません。</span><span class="sxs-lookup"><span data-stu-id="dc534-122">Single quotation marks and double quotations marks around attribute values are not preserved.</span></span> <span data-ttu-id="dc534-123">属性値は、名前と値の組としてデータベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="dc534-123">The attribute values are stored in the database as a name and value pair.</span></span> <span data-ttu-id="dc534-124">引用符は格納されません。</span><span class="sxs-lookup"><span data-stu-id="dc534-124">The quotation marks are not stored.</span></span> <span data-ttu-id="dc534-125">XML インスタンスに対して XQuery を実行すると、結果の XML はシリアル化され、属性が二重引用符で囲まれます。</span><span class="sxs-lookup"><span data-stu-id="dc534-125">When an XQuery is executed against an XML instance, the resulting XML is serialized with double quotation marks around the attribute values.</span></span>  
  
```  
DECLARE @x xml  
-- Use double quotation marks.  
SET @x = '<root a="1" />'  
SELECT @x  
GO  
DECLARE @x xml  
-- Use single quotation marks.  
SET @x = '<root a=''1'' />'  
SELECT @x  
GO  
```  
  
 <span data-ttu-id="dc534-126">どちらのクエリからも、 `<root a="1" />`が返されます。</span><span class="sxs-lookup"><span data-stu-id="dc534-126">Both queries return = `<root a="1" />`.</span></span>  
  
  
### <a name="namespace-prefixes"></a><span data-ttu-id="dc534-127">名前空間プレフィックス</span><span class="sxs-lookup"><span data-stu-id="dc534-127">Namespace Prefixes</span></span>  
 <span data-ttu-id="dc534-128">名前空間プレフィックスは保持されません。</span><span class="sxs-lookup"><span data-stu-id="dc534-128">Namespace prefixes are not preserved.</span></span> <span data-ttu-id="dc534-129">`xml` 型の列に対して XQuery を指定した場合、結果のシリアル化された XML は、異なる名前空間プレフィックスを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc534-129">When you specify XQuery against an `xml` type column, the serialized XML result may return different namespace prefixes.</span></span>  
  
```  
DECLARE @x xml  
SET @x = '<ns1:root xmlns:ns1="abc" xmlns:ns2="abc">  
            <ns2:SomeElement/>  
          </ns1:root>'  
SELECT @x  
SELECT @x.query('/*')  
GO  
```  
  
 <span data-ttu-id="dc534-130">結果の名前空間プレフィックスは、異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc534-130">The namespace prefix in the result may be different.</span></span> <span data-ttu-id="dc534-131">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="dc534-131">For example:</span></span>  
  
```  
<p1:root xmlns:p1="abc"><p1:SomeElement/></p1:root>  
```  
  
  
##  <a name="setting-required-query-options"></a><a name="query"></a> <span data-ttu-id="dc534-132">必要なクエリ オプションの設定</span><span class="sxs-lookup"><span data-stu-id="dc534-132">Setting Required Query Options</span></span>  
 <span data-ttu-id="dc534-133">`xml`データ型のメソッドを使用して型の列または変数に対してクエリを実行する場合は、 `xml` 次のオプションを示すように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc534-133">When querying `xml` type columns or variables using `xml` data type methods, the following options must be set as shown.</span></span>  
  
|<span data-ttu-id="dc534-134">SET オプション</span><span class="sxs-lookup"><span data-stu-id="dc534-134">SET Options</span></span>|<span data-ttu-id="dc534-135">設定する値</span><span class="sxs-lookup"><span data-stu-id="dc534-135">Required Values</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="dc534-136">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="dc534-136">ANSI_NULLS</span></span>|<span data-ttu-id="dc534-137">ON</span><span class="sxs-lookup"><span data-stu-id="dc534-137">ON</span></span>|  
|<span data-ttu-id="dc534-138">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="dc534-138">ANSI_PADDING</span></span>|<span data-ttu-id="dc534-139">ON</span><span class="sxs-lookup"><span data-stu-id="dc534-139">ON</span></span>|  
|<span data-ttu-id="dc534-140">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="dc534-140">ANSI_WARNINGS</span></span>|<span data-ttu-id="dc534-141">ON</span><span class="sxs-lookup"><span data-stu-id="dc534-141">ON</span></span>|  
|<span data-ttu-id="dc534-142">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="dc534-142">ARITHABORT</span></span>|<span data-ttu-id="dc534-143">ON</span><span class="sxs-lookup"><span data-stu-id="dc534-143">ON</span></span>|  
|<span data-ttu-id="dc534-144">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="dc534-144">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="dc534-145">ON</span><span class="sxs-lookup"><span data-stu-id="dc534-145">ON</span></span>|  
|<span data-ttu-id="dc534-146">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="dc534-146">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="dc534-147">OFF</span><span class="sxs-lookup"><span data-stu-id="dc534-147">OFF</span></span>|  
|<span data-ttu-id="dc534-148">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="dc534-148">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="dc534-149">ON</span><span class="sxs-lookup"><span data-stu-id="dc534-149">ON</span></span>|  
  
 <span data-ttu-id="dc534-150">オプションが表示されるように設定されていない場合、データ型のメソッドに対するクエリおよび変更 `xml` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="dc534-150">If the options are not set as shown, queries and modifications on `xml` data type methods will fail.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="dc534-151">参照</span><span class="sxs-lookup"><span data-stu-id="dc534-151">See Also</span></span>  
 [<span data-ttu-id="dc534-152">XML データのインスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="dc534-152">Create Instances of XML Data</span></span>](create-instances-of-xml-data.md)  
  
  
