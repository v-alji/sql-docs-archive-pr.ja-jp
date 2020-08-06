---
title: FOR XML での PATH モードの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
author: rothja
ms.author: jroth
ms.openlocfilehash: ce0cf811f1e610d14a94993b54c51ea079f613e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641521"
---
# <a name="use-path-mode-with-for-xml"></a><span data-ttu-id="4c279-102">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="4c279-102">Use PATH Mode with FOR XML</span></span>
  <span data-ttu-id="4c279-103">「 [FOR XML を使用した XML の構築](for-xml-sql-server.md)」で説明したように、PATH モードを使用すると、要素と属性の組み合わせが容易になります。</span><span class="sxs-lookup"><span data-stu-id="4c279-103">As described in [Constructing XML Using FOR XML](for-xml-sql-server.md), the PATH mode provides a simpler way to mix elements and attributes.</span></span> <span data-ttu-id="4c279-104">入れ子構造を使用することで、複雑なプロパティも容易に表現できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4c279-104">PATH mode is also a simpler way to introduce additional nesting for representing complex properties.</span></span> <span data-ttu-id="4c279-105">FOR XML EXPLICIT モードのクエリを使用してこのような XML を行セットから作成することもできますが、煩雑になりかねない EXPLICIT モードのクエリに比べて PATH モードでは同じことを簡潔に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4c279-105">You can use FOR XML EXPLICIT mode queries to construct such XML from a rowset, but the PATH mode provides a simpler alternative to the potentially cumbersome EXPLICIT mode queries.</span></span> <span data-ttu-id="4c279-106">PATH モードに、入れ子の FOR XML クエリと、 **xml** 型のインスタンスを返す TYPE ディレクティブを組み合わせることで、簡潔なクエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="4c279-106">PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.</span></span>  
  
 <span data-ttu-id="4c279-107">PATH モードでは、列名または列の別名が XPath 式として処理されます。</span><span class="sxs-lookup"><span data-stu-id="4c279-107">In PATH mode, column names or column aliases are treated as XPath expressions.</span></span> <span data-ttu-id="4c279-108">XPath 式は XML に値がどのようにマップされているかを示します。</span><span class="sxs-lookup"><span data-stu-id="4c279-108">These expressions indicate how the values are being mapped to XML.</span></span> <span data-ttu-id="4c279-109">各 XPath 式は、行要素に対して相対的に生成されるノードの種類 (属性、要素、スカラー値など) および名前と階層を提供する相対 XPath です。</span><span class="sxs-lookup"><span data-stu-id="4c279-109">Each XPath expression is a relative XPath that provides the item type., such as the attribute, element, and scalar value, and the name and hierarchy of the node that will be generated relative to the row element.</span></span>  
  
 <span data-ttu-id="4c279-110">ここでは、さまざまな条件における行セットでの列のマッピングについて説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="4c279-110">This section describes mapping columns in a rowset under various conditions, and provides examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c279-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4c279-111">In This Section</span></span>  
  
-   [<span data-ttu-id="4c279-112">名前のない列</span><span class="sxs-lookup"><span data-stu-id="4c279-112">Columns without a Name</span></span>](columns-without-a-name.md)  
  
-   [<span data-ttu-id="4c279-113">名前のある列</span><span class="sxs-lookup"><span data-stu-id="4c279-113">Columns with a Name</span></span>](columns-with-a-name.md)  
  
-   [<span data-ttu-id="4c279-114">名前をワイルドカード文字で指定した列</span><span class="sxs-lookup"><span data-stu-id="4c279-114">Columns with a Name Specified as a Wildcard Character</span></span>](columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [<span data-ttu-id="4c279-115">XPath ノード テストの名前が付いた列</span><span class="sxs-lookup"><span data-stu-id="4c279-115">Columns with the Name of an XPath Node Test</span></span>](columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [<span data-ttu-id="4c279-116">パスを data&#40;&#41; として指定した列の名前</span><span class="sxs-lookup"><span data-stu-id="4c279-116">Column Names with the Path Specified as data&#40;&#41;</span></span>](column-names-with-the-path-specified-as-data.md)  
  
-   [<span data-ttu-id="4c279-117">NULL 値が含まれる列の既定動作</span><span class="sxs-lookup"><span data-stu-id="4c279-117">Columns that Contain a Null Value By Default</span></span>](columns-that-contain-a-null-value-by-default.md)  
  
-   [<span data-ttu-id="4c279-118">PATH モードでの名前空間のサポート</span><span class="sxs-lookup"><span data-stu-id="4c279-118">Namespace Support in PATH Mode</span></span>](namespace-support-in-path-mode.md)  
  
-   [<span data-ttu-id="4c279-119">例: PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="4c279-119">Examples: Using PATH Mode</span></span>](examples-using-path-mode.md)  
  
## <a name="see-also"></a><span data-ttu-id="4c279-120">参照</span><span class="sxs-lookup"><span data-stu-id="4c279-120">See Also</span></span>  
 <span data-ttu-id="4c279-121">[WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span><span class="sxs-lookup"><span data-stu-id="4c279-121">[Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span></span>  
 <span data-ttu-id="4c279-122">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4c279-122">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="4c279-123">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4c279-123">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
