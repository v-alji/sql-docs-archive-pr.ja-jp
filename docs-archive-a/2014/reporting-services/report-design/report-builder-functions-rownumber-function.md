---
title: RowNumber 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f3d16188138c2f268305fddb092d56be870a3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640660"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a><span data-ttu-id="aab70-102">RowNumber 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="aab70-102">RowNumber Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="aab70-103">指定されたスコープの実行中の行数を返します。</span><span class="sxs-lookup"><span data-stu-id="aab70-103">Returns a running count of the number of rows for the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="aab70-104">構文</span><span class="sxs-lookup"><span data-stu-id="aab70-104">Syntax</span></span>  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aab70-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aab70-105">Parameters</span></span>  
 <span data-ttu-id="aab70-106">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="aab70-106">*scope*</span></span>  
 <span data-ttu-id="aab70-107">(`String`) 行数を評価するコンテキストを示すデータセット、データ領域、またはグループの名前か、NULL ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) です。</span><span class="sxs-lookup"><span data-stu-id="aab70-107">(`String`) The name of a dataset, data region, or group, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the context in which to evaluate the number of rows.</span></span> <span data-ttu-id="aab70-108">`Nothing` は、最も外側のコンテキスト (通常はレポート データセット) を示します。</span><span class="sxs-lookup"><span data-stu-id="aab70-108">`Nothing` specifies the outermost context, usually the report dataset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aab70-109">解説</span><span class="sxs-lookup"><span data-stu-id="aab70-109">Remarks</span></span>  
 <span data-ttu-id="aab70-110">`RowNumber`[RunningValue](report-builder-functions-runningvalue-function.md)が集計関数の実行中の値を返す場合と同様に、指定されたスコープ内の行数の実行中の値を返します。</span><span class="sxs-lookup"><span data-stu-id="aab70-110">`RowNumber` returns a running value of the count of rows within the specified scope, just as [RunningValue](report-builder-functions-runningvalue-function.md) returns the running value of an aggregate function.</span></span> <span data-ttu-id="aab70-111">スコープを指定すると、行数を 1 にリセットするタイミングが指定されます。</span><span class="sxs-lookup"><span data-stu-id="aab70-111">When you specify a scope, you specify when to reset the row count to 1.</span></span>  
  
 <span data-ttu-id="aab70-112">*scope* には、式を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="aab70-112">*scope* cannot be an expression.</span></span> <span data-ttu-id="aab70-113">*scope* には、コンテナー スコープを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aab70-113">*scope* must be a containing scope.</span></span> <span data-ttu-id="aab70-114">一般的なスコープは、外側から内側の順に、レポート データセット、データ領域、行グループまたは列グループです。</span><span class="sxs-lookup"><span data-stu-id="aab70-114">Typical scopes, from the outermost to the innermost containment, are report dataset, data region, row groups or column groups.</span></span>  
  
 <span data-ttu-id="aab70-115">列全体で値を増分するには、列グループの名前であるスコープを指定します。</span><span class="sxs-lookup"><span data-stu-id="aab70-115">To increment values across columns, specify a scope that is the name of a column group.</span></span> <span data-ttu-id="aab70-116">行の下方向に向かって数を増分するには、行グループの名前であるスコープを指定します。</span><span class="sxs-lookup"><span data-stu-id="aab70-116">To increment numbers down rows, specify a scope that is the name of a row group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aab70-117">行グループと列グループの両方を指定する複数の集計を含めた式はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="aab70-117">Including aggregates that specify both a row group and a column group in a single expression is not supported.</span></span>  
  
 <span data-ttu-id="aab70-118">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aab70-118">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="aab70-119">コード例</span><span class="sxs-lookup"><span data-stu-id="aab70-119">Code Example</span></span>  
 <span data-ttu-id="aab70-120">Tablix データ領域の詳細行の `BackgroundColor` プロパティに使用できる式を次に示します。この式では、各グループの詳細行の色を交互に設定し、常に先頭が白になるようにしています。</span><span class="sxs-lookup"><span data-stu-id="aab70-120">The following is an expression that you can use for the `BackgroundColor` property of a Tablix data region detail row to alternate the color of detail rows for each group, always beginning with White.</span></span>  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a><span data-ttu-id="aab70-121">参照</span><span class="sxs-lookup"><span data-stu-id="aab70-121">See Also</span></span>  
 <span data-ttu-id="aab70-122">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aab70-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aab70-123">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aab70-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aab70-124">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aab70-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="aab70-125">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="aab70-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
