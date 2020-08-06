---
title: キャッシュの管理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdc5bcd2e0500749edfa298a871b6fec7243ddfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639736"
---
# <a name="managing-caches-xmla"></a><span data-ttu-id="35406-102">キャッシュの管理 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="35406-102">Managing Caches (XMLA)</span></span>
  <span data-ttu-id="35406-103">XML for Analysis (XMLA) の[clearcache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla)コマンドを使用して、指定したディメンションまたはパーティションのキャッシュを消去できます。</span><span class="sxs-lookup"><span data-stu-id="35406-103">You can use the [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) command in XML for Analysis (XMLA) to clear the cache of a specified dimension or partition.</span></span> <span data-ttu-id="35406-104">キャッシュをクリアすると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] そのオブジェクトのキャッシュが強制的に再構築されます。</span><span class="sxs-lookup"><span data-stu-id="35406-104">Clearing the cache forces [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to rebuild the cache for that object.</span></span>  
  
## <a name="specifying-objects"></a><span data-ttu-id="35406-105">オブジェクトの指定</span><span class="sxs-lookup"><span data-stu-id="35406-105">Specifying Objects</span></span>  
 <span data-ttu-id="35406-106">コマンドの[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティには、 `ClearCache` 次のいずれかのオブジェクトに対してのみオブジェクト参照を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="35406-106">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `ClearCache` command can contain an object reference only for one of the following objects.</span></span> <span data-ttu-id="35406-107">以下に該当しないオブジェクトに対するオブジェクト参照が含まれる場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="35406-107">An error occurs if an object reference is for an object other than one of following objects:</span></span>  
  
 <span data-ttu-id="35406-108">データベース</span><span class="sxs-lookup"><span data-stu-id="35406-108">Database</span></span>  
 <span data-ttu-id="35406-109">データベースに含まれるすべてのディメンションおよびパーティションのキャッシュを消去します。</span><span class="sxs-lookup"><span data-stu-id="35406-109">Clears the cache for all dimensions and partitions contained in the database.</span></span>  
  
 <span data-ttu-id="35406-110">Dimension</span><span class="sxs-lookup"><span data-stu-id="35406-110">Dimension</span></span>  
 <span data-ttu-id="35406-111">指定されたディメンションのキャッシュを消去します。</span><span class="sxs-lookup"><span data-stu-id="35406-111">Clears the cache for the specified dimension.</span></span>  
  
 <span data-ttu-id="35406-112">キューブ</span><span class="sxs-lookup"><span data-stu-id="35406-112">Cube</span></span>  
 <span data-ttu-id="35406-113">キューブのメジャー グループに含まれるすべてのパーティションのキャッシュを消去します。</span><span class="sxs-lookup"><span data-stu-id="35406-113">Clears the cache for all partitions contained in the measure groups for the cube.</span></span>  
  
 <span data-ttu-id="35406-114">[メジャー グループ]</span><span class="sxs-lookup"><span data-stu-id="35406-114">Measure group</span></span>  
 <span data-ttu-id="35406-115">メジャー グループに含まれるすべてのパーティションのキャッシュを消去します。</span><span class="sxs-lookup"><span data-stu-id="35406-115">Clears the cache for all partitions contained in the measure group.</span></span>  
  
 <span data-ttu-id="35406-116">Partition</span><span class="sxs-lookup"><span data-stu-id="35406-116">Partition</span></span>  
 <span data-ttu-id="35406-117">指定されたパーティションのキャッシュを消去します。</span><span class="sxs-lookup"><span data-stu-id="35406-117">Clears the cache for the specified partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35406-118">参照</span><span class="sxs-lookup"><span data-stu-id="35406-118">See Also</span></span>  
 [<span data-ttu-id="35406-119">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="35406-119">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
