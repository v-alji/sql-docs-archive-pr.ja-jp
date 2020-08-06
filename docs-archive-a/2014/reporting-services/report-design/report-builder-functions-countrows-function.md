---
title: CountRows 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d5311dfc5dfcb89449a4039fdac4100fc5a3b47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640685"
---
# <a name="countrows-function-report-builder-and-ssrs"></a><span data-ttu-id="7466e-102">CountRows 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7466e-102">CountRows Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7466e-103">NULL 値の行を含めて、指定されたスコープ内の行数を返します。</span><span class="sxs-lookup"><span data-stu-id="7466e-103">Returns the number of rows in the specified scope, including rows with null values.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="7466e-104">構文</span><span class="sxs-lookup"><span data-stu-id="7466e-104">Syntax</span></span>  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7466e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7466e-105">Parameters</span></span>  
 <span data-ttu-id="7466e-106">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="7466e-106">*scope*</span></span>  
 <span data-ttu-id="7466e-107">(`String`) カウントするレポート アイテムを含むデータセット、データ領域、またはグループの名前です。</span><span class="sxs-lookup"><span data-stu-id="7466e-107">(`String`) The name of a dataset, data region, or group that contains the report items to count.</span></span>  
  
 <span data-ttu-id="7466e-108">*再帰*</span><span class="sxs-lookup"><span data-stu-id="7466e-108">*recursive*</span></span>  
 <span data-ttu-id="7466e-109">(**列挙型**) 省略可。</span><span class="sxs-lookup"><span data-stu-id="7466e-109">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="7466e-110">`Simple` (既定値) または `RdlRecursive` です。</span><span class="sxs-lookup"><span data-stu-id="7466e-110">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="7466e-111">集計を再帰的に実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7466e-111">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="7466e-112">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="7466e-112">Return Type</span></span>  
 <span data-ttu-id="7466e-113">`Integer` を返します。</span><span class="sxs-lookup"><span data-stu-id="7466e-113">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7466e-114">解説</span><span class="sxs-lookup"><span data-stu-id="7466e-114">Remarks</span></span>  
 <span data-ttu-id="7466e-115">`CountRows` は、指定されたスコープ内のすべての行 (NULL 値を持つ行を含む) をカウントします。</span><span class="sxs-lookup"><span data-stu-id="7466e-115">`CountRows` counts all rows in the specified scope, including rows that have null values.</span></span>  
  
 <span data-ttu-id="7466e-116">*scope* の値には、式を指定することができません。また、この値では、現在のスコープまたはコンテナー スコープを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7466e-116">The value of *scope* cannot be an expression and must refer to the current scope or a containing scope.</span></span>  
  
 <span data-ttu-id="7466e-117">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7466e-117">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="7466e-118">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7466e-118">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7466e-119">例</span><span class="sxs-lookup"><span data-stu-id="7466e-119">Example</span></span>  
 <span data-ttu-id="7466e-120">次のコード例では、(式 `GroupbyCategory` に基づいた) `[Category]`という名前の行グループ内の行数を計算する式を示します。</span><span class="sxs-lookup"><span data-stu-id="7466e-120">The following code example shows an expression that calculates the number of rows in a row group named `GroupbyCategory` (based on the expression `[Category]`).</span></span>  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="7466e-121">参照</span><span class="sxs-lookup"><span data-stu-id="7466e-121">See Also</span></span>  
 <span data-ttu-id="7466e-122">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7466e-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7466e-123">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7466e-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7466e-124">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7466e-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7466e-125">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7466e-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
