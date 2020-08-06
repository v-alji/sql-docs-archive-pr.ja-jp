---
title: SQLXML 4.0 | での XPath クエリの使用Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML]
- annotated XSD schemas, XPath queries
- queries [SQLXML], XPath
- XML views [SQLXML]
ms.assetid: 7814d099-81ec-4fb8-894a-729cdbb5015a
author: rothja
ms.author: jroth
ms.openlocfilehash: 80d82513b22d2a50aedb37955a210dd33746db86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642697"
---
# <a name="using-xpath-queries-in-sqlxml-40"></a><span data-ttu-id="738c6-102">SQLXML 4.0 での XPath クエリの使用</span><span class="sxs-lookup"><span data-stu-id="738c6-102">Using XPath Queries in SQLXML 4.0</span></span>
  <span data-ttu-id="738c6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では注釈付き XSD スキーマがサポートされており、データベースに格納されているリレーショナル データの XML ビューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="738c6-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support for annotated XSD schemas allows you to create XML views of the relational data stored in the database.</span></span> <span data-ttu-id="738c6-104">XPath 言語のサブセットを使用すると、注釈付き XSD スキーマで作成された XML ビューに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="738c6-104">You can use a subset of the XPath language to query the XML views created by an annotated XSD schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="738c6-105">SQLXML 4.0 の XPath クエリを理解するには、XML ビューと、それに関連するテンプレートやマッピング スキーマなどの概念について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="738c6-105">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="738c6-106">詳細については、「[注釈付き XSD スキーマの概要 &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="738c6-106">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="738c6-107">XPath の詳細については、「」の World Wide Web コンソーシアム (W3C) で定義されている XPath 標準を参照してください http://www.w3.org/TR/xpath 。</span><span class="sxs-lookup"><span data-stu-id="738c6-107">For more information about XPath, see the XPath standard defined by the World Wide Web Consortium (W3C) at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="738c6-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="738c6-108">In This Section</span></span>  
 [<span data-ttu-id="738c6-109">XPath クエリの使用の概要 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="738c6-109">Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;</span></span>](introduction-to-using-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="738c6-110">SQLXML 4.0 での XPath クエリの使用について、W3C XPath 仕様でサポートされている機能とサポートされていない機能など、概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="738c6-110">Provides introductory information about XPath queries in SQLXML 4.0, including supported and unsupported functionality from the W3C XPath specification.</span></span>  
  
 [<span data-ttu-id="738c6-111">SQLXML 4.0 &#40;の場所のパスを指定する&#41;</span><span class="sxs-lookup"><span data-stu-id="738c6-111">Specifying a Location Path &#40;SQLXML 4.0&#41;</span></span>](location-path/specifying-a-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="738c6-112">XPath クエリでロケーション パスを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="738c6-112">Describes how to specify location paths in XPath queries.</span></span>  
  
 [<span data-ttu-id="738c6-113">サンプル XPath クエリ &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="738c6-113">Sample XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/sample-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="738c6-114">SQLXML 4.0 での XPath クエリの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="738c6-114">Provides sample XPath queries for SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="738c6-115">&#40;SQLXML 4.0&#41;の XPath データ型</span><span class="sxs-lookup"><span data-stu-id="738c6-115">XPath Data Types &#40;SQLXML 4.0&#41;</span></span>](xpath-data-types-sqlxml-4-0.md)  
 <span data-ttu-id="738c6-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および XSD のデータ型とは大きく異なる、XPath データ型について説明します。</span><span class="sxs-lookup"><span data-stu-id="738c6-116">Describes XPath data types, which are significantly different from those of both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and XSD.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738c6-117">参照</span><span class="sxs-lookup"><span data-stu-id="738c6-117">See Also</span></span>  
 [<span data-ttu-id="738c6-118">クライアント側の XML 書式設定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="738c6-118">Client-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](../sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
