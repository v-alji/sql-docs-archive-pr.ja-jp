---
title: InScope 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62c4ad5de7af1ac0762df29deaa17953a8a378db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640678"
---
# <a name="inscope-function-report-builder-and-ssrs"></a><span data-ttu-id="5cde6-102">InScope 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5cde6-102">InScope Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5cde6-103">アイテムの現在のインスタンスが、指定したスコープ内にあるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5cde6-103">Indicates whether the current instance of an item is in the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="5cde6-104">構文</span><span class="sxs-lookup"><span data-stu-id="5cde6-104">Syntax</span></span>  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cde6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5cde6-105">Parameters</span></span>  
 <span data-ttu-id="5cde6-106">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="5cde6-106">*scope*</span></span>  
 <span data-ttu-id="5cde6-107">(`String`) スコープを指定するデータセット、データ領域、またはグループの名前です。</span><span class="sxs-lookup"><span data-stu-id="5cde6-107">(`String`) The name of a dataset, data region, or group that specifies a scope.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="5cde6-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="5cde6-108">Return Type</span></span>  
 <span data-ttu-id="5cde6-109">`Boolean` を返します。</span><span class="sxs-lookup"><span data-stu-id="5cde6-109">Returns a `Boolean`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cde6-110">解説</span><span class="sxs-lookup"><span data-stu-id="5cde6-110">Remarks</span></span>  
 <span data-ttu-id="5cde6-111">関数は、 `InScope` レポートアイテムの現在のインスタンスのスコープをテストして、 *scope*パラメーターで指定されたスコープのメンバーシップを調べます。</span><span class="sxs-lookup"><span data-stu-id="5cde6-111">The `InScope` function tests the scope of the current instance of a report item for membership in the scope specified by the *scope*parameter.</span></span>  
  
 <span data-ttu-id="5cde6-112">*Scope* には、式を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="5cde6-112">*Scope* cannot be an expression.</span></span>  
  
 <span data-ttu-id="5cde6-113">`InScope` 関数は、通常、動的スコープを利用するデータ領域で使用されます。</span><span class="sxs-lookup"><span data-stu-id="5cde6-113">A typical use for the `InScope` function is in data regions that have dynamic scoping.</span></span> <span data-ttu-id="5cde6-114">たとえば、`InScope` をデータ領域のセル内のドリルスルー リンクに使用して、クリックされたセルに応じて異なるレポート名とパラメーター セットが返されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5cde6-114">For example, `InScope` can be used in a drillthrough link in a data region cells to provide a different report name and different sets of parameters depending on which cell is clicked.</span></span> <span data-ttu-id="5cde6-115">この例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="5cde6-115">An example of this is as follows:</span></span>  
  
-   <span data-ttu-id="5cde6-116">次の式では、ドリルスルー リンクのレポート名として使用し、 `ProductDetail` グループ内のセルがクリックされた場合は `Month` レポートが開き、それ以外のセルがクリックされた場合は `ProductSummary` レポートが開くようにしています。</span><span class="sxs-lookup"><span data-stu-id="5cde6-116">The following expression, used as the report name in a drillthrough link, opens the `ProductDetail` report if the clicked cell is in the `Month` group, and the `ProductSummary` report if it is not.</span></span>  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   <span data-ttu-id="5cde6-117">次の式では、詳細レポート パラメーターの `Omit` プロパティに使用し、`Product` グループ内のセルがクリックされた場合のみ、目的のレポートにパラメーターが渡されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="5cde6-117">The following expression, used in the `Omit` property of a drillthrough report parameter, will pass the parameter to the target report only if the clicked cell is in the `Product` group.</span></span>  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 <span data-ttu-id="5cde6-118">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cde6-118">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cde6-119">例</span><span class="sxs-lookup"><span data-stu-id="5cde6-119">Example</span></span>  
 <span data-ttu-id="5cde6-120">次のコード例では、アイテムの現在のインスタンスが、 `Product` データセット、データ領域、またはグループのスコープにあるかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="5cde6-120">The following code example indicates whether the current instance of the item is in the `Product` dataset, data region, or group scope.</span></span>  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cde6-121">参照</span><span class="sxs-lookup"><span data-stu-id="5cde6-121">See Also</span></span>  
 <span data-ttu-id="5cde6-122">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5cde6-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5cde6-123">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5cde6-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5cde6-124">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5cde6-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5cde6-125">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5cde6-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
