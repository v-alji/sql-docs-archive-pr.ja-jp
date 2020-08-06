---
title: Level 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dedbf00ce8330242c95e9592f649d95171f0987a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640676"
---
# <a name="level-function-report-builder-and-ssrs"></a><span data-ttu-id="5d827-102">Level 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5d827-102">Level Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5d827-103">再帰型階層の現在の深さのレベルを返します。</span><span class="sxs-lookup"><span data-stu-id="5d827-103">Returns the current level of depth in a recursive hierarchy.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="5d827-104">構文</span><span class="sxs-lookup"><span data-stu-id="5d827-104">Syntax</span></span>  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d827-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5d827-105">Parameters</span></span>  
 <span data-ttu-id="5d827-106">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="5d827-106">*scope*</span></span>  
 <span data-ttu-id="5d827-107">(`String`) (省略可)。</span><span class="sxs-lookup"><span data-stu-id="5d827-107">(`String`) (Optional).</span></span> <span data-ttu-id="5d827-108">集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。</span><span class="sxs-lookup"><span data-stu-id="5d827-108">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="5d827-109">*scope* を指定しない場合、現在のスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5d827-109">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="5d827-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="5d827-110">Return Type</span></span>  
 <span data-ttu-id="5d827-111">`Integer` を返します。</span><span class="sxs-lookup"><span data-stu-id="5d827-111">Returns an `Integer`.</span></span> <span data-ttu-id="5d827-112">*スコープ*がデータセットまたはデータ領域を指定した場合、または再帰的のグループ (つまり、要素のないグループ) を指定した場合 `Parent` 、は `Level` 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="5d827-112">If *scope* specifies a dataset or data region, or specifies a nonrecursive grouping (that is, a grouping with no `Parent` element), `Level` returns 0.</span></span> <span data-ttu-id="5d827-113">*scope* を指定しない場合は、現在のスコープのレベルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5d827-113">If *scope* is omitted, it returns the level of the current scope.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d827-114">解説</span><span class="sxs-lookup"><span data-stu-id="5d827-114">Remarks</span></span>  
 <span data-ttu-id="5d827-115">`Level` 関数から返される値は、0 を基準にしています。つまり、階層の最初のレベルは 0 です。</span><span class="sxs-lookup"><span data-stu-id="5d827-115">The value returned by the `Level` function is zero based; that is, the first level in a hierarchy is 0.</span></span>  
  
 <span data-ttu-id="5d827-116">`Level` 関数は、従業員一覧などの再帰型階層にインデントを付けるために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5d827-116">The `Level` function can be used to provide indentation in a recursive hierarchy, such as an employee list.</span></span>  
  
 <span data-ttu-id="5d827-117">再帰的型階層については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d827-117">For more information about recursive hierarchies, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d827-118">例</span><span class="sxs-lookup"><span data-stu-id="5d827-118">Example</span></span>  
 <span data-ttu-id="5d827-119">次のコード例では、Employees グループの行のレベルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5d827-119">The following code example provides the level of row in the Employees group:</span></span>  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d827-120">参照</span><span class="sxs-lookup"><span data-stu-id="5d827-120">See Also</span></span>  
 <span data-ttu-id="5d827-121">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5d827-121">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5d827-122">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5d827-122">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5d827-123">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5d827-123">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5d827-124">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5d827-124">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
