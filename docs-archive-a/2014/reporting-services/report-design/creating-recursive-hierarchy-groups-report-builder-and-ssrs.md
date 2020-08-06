---
title: 複数の再帰型階層グループの作成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aeb99e725c5c61a6dc66c83e53afbc43b1224582
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634867"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a><span data-ttu-id="690bf-102">複数の再帰型階層グループの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="690bf-102">Creating Recursive Hierarchy Groups (Report Builder and SSRS)</span></span>
  <span data-ttu-id="690bf-103">親と子の間のリレーションシップがデータセットのフィールドによって表される再帰データを表示するには、子フィールドに基づいてデータ領域グループ式を設定し、親フィールドに基づいて親プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="690bf-103">To display recursive data where the relationship between parent and child is represented by fields in the dataset, you can set the data region group expression based on the child field and set the Parent property based on the parent field.</span></span>  
  
 <span data-ttu-id="690bf-104">階層データの表示は、組織図に含まれている従業員など、再帰型階層グループでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="690bf-104">Displaying hierarchical data is a common use for recursive hierarchy groups, for example, employees in an organizational chart.</span></span> <span data-ttu-id="690bf-105">データセットには従業員とマネージャーの一覧が含まれており、マネージャー名は従業員の一覧にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="690bf-105">The dataset includes a list of employees and the managers, where the manager names also appear in the list of employees.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a><span data-ttu-id="690bf-106">再帰型階層の作成</span><span class="sxs-lookup"><span data-stu-id="690bf-106">Creating Recursive Hierarchies</span></span>  
 <span data-ttu-id="690bf-107">Tablix データ領域で再帰型階層を作成するには、子データを指定するフィールドにグループ式を設定し、親データを指定するフィールドにグループの親プロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="690bf-107">To build a recursive hierarchy in a tablix data region, you must set the group expression to the field that specifies the child data and the Parent property of the group to the field that specifies the parent data.</span></span> <span data-ttu-id="690bf-108">たとえば、従業員がマネージャーの監督下にある場合、従業員 ID およびマネージャー ID のフィールドを含んでいるデータセットでは、グループ式を従業員 ID に設定し、親プロパティをマネージャー ID に設定します。</span><span class="sxs-lookup"><span data-stu-id="690bf-108">For example, for a dataset that includes fields for employee ID and manager ID where employees report to managers, set the group expression to employee ID and the Parent property to manager ID.</span></span>  
  
 <span data-ttu-id="690bf-109">再帰型階層として定義されたグループ (親プロパティを使用しているグループ) には、グループ式は 1 つしか設定できません。</span><span class="sxs-lookup"><span data-stu-id="690bf-109">A group that is defined as a recursive hierarchy (that is, a group that uses the Parent property) can have only one group expression.</span></span> <span data-ttu-id="690bf-110">テキスト ボックスの余白に `Level` 関数を使用して、階層内のレベルに応じて従業員名をインデントできます。</span><span class="sxs-lookup"><span data-stu-id="690bf-110">You can use the `Level` function in text box padding to indent employee names based on their level in the hierarchy.</span></span>  
  
 <span data-ttu-id="690bf-111">詳細については、「[データ領域でのグループの追加または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)」と「[再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="690bf-111">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) and  [Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).</span></span>  
  
### <a name="aggregate-functions-that-support-recursion"></a><span data-ttu-id="690bf-112">再帰をサポートする集計関数</span><span class="sxs-lookup"><span data-stu-id="690bf-112">Aggregate Functions that support Recursion</span></span>  
 <span data-ttu-id="690bf-113">パラメーター *Recursive* を受け取る Reporting Services 集計関数を使用して、再帰型階層の集計データを計算できます。</span><span class="sxs-lookup"><span data-stu-id="690bf-113">You can use Reporting Services aggregate functions that accept the parameter *Recursive* to calculate summary data for a recursive hierarchy.</span></span> <span data-ttu-id="690bf-114">次の関数は、 `Recursive` パラメーターとしてを受け取ります: [Sum](report-builder-functions-sum-function.md)、 [Avg](report-builder-functions-avg-function.md)、 [Count](report-builder-functions-count-function.md)、 [CountDistinct](report-builder-functions-countdistinct-function.md)、 [CountRows](report-builder-functions-countrows-function.md)、 [Max](report-builder-functions-max-function.md)、 [Min](report-builder-functions-min-function.md)、 [StDev](report-builder-functions-stdev-function.md)、 [StDevP](report-builder-functions-stdevp-function.md)、 [Sum](report-builder-functions-sum-function.md)、 [Var](report-builder-functions-var-function.md)、および[VarP](report-builder-functions-varp-function.md)。</span><span class="sxs-lookup"><span data-stu-id="690bf-114">The following functions accept `Recursive` as a parameter: [Sum](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), and [VarP](report-builder-functions-varp-function.md).</span></span> <span data-ttu-id="690bf-115">詳細については、「 [集計関数リファレンス (レポート ビルダーおよび SSRS)](report-builder-functions-aggregate-functions-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="690bf-115">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690bf-116">参照</span><span class="sxs-lookup"><span data-stu-id="690bf-116">See Also</span></span>  
 <span data-ttu-id="690bf-117">[テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="690bf-117">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="690bf-118">[Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="690bf-118">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="690bf-119">[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="690bf-119">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="690bf-120">[テーブル &#40;レポート ビルダーおよび SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="690bf-120">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="690bf-121">[マトリックス &#40;レポート ビルダーおよび SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="690bf-121">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="690bf-122">[一覧 &#40;レポート ビルダーおよび SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="690bf-122">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="690bf-123">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="690bf-123">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
