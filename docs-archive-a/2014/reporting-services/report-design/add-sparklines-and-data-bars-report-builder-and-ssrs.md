---
title: スパークラインとデータ バーの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55ec15354cdc78dd9678b9466f30d2fca0a73adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632911"
---
# <a name="add-sparklines-and-data-bars-report-builder-and-ssrs"></a><span data-ttu-id="c8e39-102">スパークラインとデータ バーの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c8e39-102">Add Sparklines and Data Bars (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c8e39-103">スパークラインとデータ バーは小さく簡潔なグラフであり、余分な情報を最小限に抑えて多くの情報を伝えます。</span><span class="sxs-lookup"><span data-stu-id="c8e39-103">Sparklines and data bars are small, spare charts that convey a lot of information with little extraneous detail.</span></span> <span data-ttu-id="c8e39-104">詳細については、「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8e39-104">For more information about them, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c8e39-105">通常、スパークラインとデータ バーは、テーブルまたはマトリックス内のセルに置かれます。</span><span class="sxs-lookup"><span data-stu-id="c8e39-105">Sparklines and data bars are most commonly placed in cells in a table or matrix.</span></span> <span data-ttu-id="c8e39-106">スパークラインには、それぞれ 1 つの系列のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8e39-106">Sparklines usually display only one series each.</span></span> <span data-ttu-id="c8e39-107">データ バーには、1 つまたは複数のデータ ポイントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c8e39-107">Data bars can contain one or more data points.</span></span> <span data-ttu-id="c8e39-108">スパークラインとデータ バーでは、テーブルまたはマトリックスで各行の系列情報を繰り返す場合にその効果が得られます。</span><span class="sxs-lookup"><span data-stu-id="c8e39-108">Both sparklines and data bars derive their impact from repeating the series information for each row in the table or matrix.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-sparkline-or-data-bar-to-a-table-or-matrix"></a><span data-ttu-id="c8e39-109">テーブルまたはマトリックスにスパークラインまたはデータ バーを追加するには</span><span class="sxs-lookup"><span data-stu-id="c8e39-109">To add a sparkline or data bar to a table or matrix</span></span>  
  
1.  <span data-ttu-id="c8e39-110">表示するデータを含むテーブルまたはマトリックスを作成していない場合は、それらを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8e39-110">If you have not done so already, create a table or matrix with the data you want to display.</span></span> <span data-ttu-id="c8e39-111">詳細については、「[(レポート ビルダーおよび SSRS)](tables-report-builder-and-ssrs.md)」または「[マトリックス (レポート ビルダーおよび SSRS)](create-a-matrix-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8e39-111">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="c8e39-112">テーブルまたはマトリックスに列を挿入します。</span><span class="sxs-lookup"><span data-stu-id="c8e39-112">Insert a column in your table or matrix.</span></span> <span data-ttu-id="c8e39-113">詳細については、「[列の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8e39-113">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="c8e39-114">**[挿入]** タブで、 **[スパークライン]** または **[データ バー]** をクリックし、新しい列のセル内をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8e39-114">On the **Insert** tab, click **Sparkline** or **Data Bar**, and then click in a cell in the new column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8e39-115">スパークラインをテーブル内の詳細グループに置くことはできません。</span><span class="sxs-lookup"><span data-stu-id="c8e39-115">You cannot place sparklines in a detail group in a table.</span></span> <span data-ttu-id="c8e39-116">グループに関連付けられているセルにのみ置くことができます。</span><span class="sxs-lookup"><span data-stu-id="c8e39-116">They must go in a cell associated with a group.</span></span>  
  
4.  <span data-ttu-id="c8e39-117">**[スパークラインの種類の変更] または [データ バーの種類の変更]** ダイアログ ボックスで、目的のスパークラインまたはデータ バーの種類をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8e39-117">In the **Change Sparkline/Data Bar Type** dialog box, click the kind of sparkline or data bar you want, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c8e39-118">スパークラインまたはデータ バーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8e39-118">Click the sparkline or data bar.</span></span>  
  
     <span data-ttu-id="c8e39-119">**グラフ データ** ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="c8e39-119">The **Chart Data** pane opens.</span></span>  
  
6.  <span data-ttu-id="c8e39-120">**[値]** 領域で、 **[フィールドの追加]** のプラス記号 (**+**) をクリックし、グラフ化する値のあるフィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8e39-120">In the **Values** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want charted.</span></span>  
  
7.  <span data-ttu-id="c8e39-121">**[カテゴリ グループ]** 領域で、 **[フィールドの追加]** のプラス記号 (**+**) をクリックし、グループ化に使用する値のフィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8e39-121">In the **Category Groups** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want to group by.</span></span>  
  
     <span data-ttu-id="c8e39-122">通常、各行に 1 つの系列を使用するので、スパークラインまたはデータ バーでは **[系列グループ]** 領域にフィールドを追加しません。</span><span class="sxs-lookup"><span data-stu-id="c8e39-122">Typically for sparklines and data bars, you will not add a field to the **Series Group** area because you only want one series for each row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e39-123">参照</span><span class="sxs-lookup"><span data-stu-id="c8e39-123">See Also</span></span>  
 <span data-ttu-id="c8e39-124">[グラフ &#40;レポートビルダーと SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c8e39-124">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c8e39-125">テーブル内のグラフまたはマトリックスでのデータの整列 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c8e39-125">Align the Data in a Chart in a Table or Matrix &#40;Report Builder and SSRS&#41;</span></span>](align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
