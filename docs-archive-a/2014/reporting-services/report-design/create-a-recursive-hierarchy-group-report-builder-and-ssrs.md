---
title: 再帰型階層グループの作成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8b830ba5-4d64-4348-a2b1-76b9338a1462
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf86c3989170ed8cd452168a558ead348258331e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634889"
---
# <a name="create-a-recursive-hierarchy-group-report-builder-and-ssrs"></a><span data-ttu-id="4da57-102">再帰型階層グループの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4da57-102">Create a Recursive Hierarchy Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4da57-103">再帰型階層グループは、組織階層内のマネージャーと従業員のリレーションシップを表す上司/部下構造など、複数の階層レベルから成る単一のレポート データセットのデータを編成します。</span><span class="sxs-lookup"><span data-stu-id="4da57-103">A recursive hierarchy group organizes data from a single report dataset that includes multiple hierarchical levels, such as the report-to structure for manager-employee relationships in an organizational hierarchy.</span></span>  
  
 <span data-ttu-id="4da57-104">テーブル内のデータを再帰型階層グループにまとめるには、まず、すべての階層データが含まれた単一のデータセットを用意しておく必要があります。グループ化するアイテムとグループ化の基準に使用するアイテムには別々のフィールドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4da57-104">Before you can organize data in a table as a recursive hierarchy group, you must have a single dataset that contains all the hierarchical data, You must have separate fields for the item to group and for the item to group by.</span></span> <span data-ttu-id="4da57-105">たとえば、従業員をそれぞれのマネージャーの子として再帰的にまとめるデータセットには、従業員名、従業員 ID、マネージャー名、マネージャー ID などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4da57-105">For example, a dataset where you want to group employees recursively under their manager might contain a name, an employee name, an employee ID, and a manager ID.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-recursive-hierarchy-group"></a><span data-ttu-id="4da57-106">再帰型階層グループを作成するには</span><span class="sxs-lookup"><span data-stu-id="4da57-106">To create a recursive hierarchy group</span></span>  
  
1.  <span data-ttu-id="4da57-107">デザイン ビューで、テーブルを追加して、表示するデータセット フィールドをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4da57-107">In Design view, add a table, and drag the dataset fields to display.</span></span> <span data-ttu-id="4da57-108">通常、階層として表示する必要のあるフィールドは最初の列にあります。</span><span class="sxs-lookup"><span data-stu-id="4da57-108">Typically, the field that you want to show as a hierarchy is in the first column.</span></span>  
  
2.  <span data-ttu-id="4da57-109">テーブル内の任意の場所を右クリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="4da57-109">Right-click anywhere in the table to select it.</span></span> <span data-ttu-id="4da57-110">選択したテーブルの詳細グループがグループ化ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da57-110">The Grouping pane displays the details group for the selected table.</span></span> <span data-ttu-id="4da57-111">行グループ ペインで、 **[詳細]** を右クリックし、 **[グループの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4da57-111">In the Row Groups pane, right-click **Details**, and then click **Edit Group**.</span></span> <span data-ttu-id="4da57-112">**[グループのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da57-112">The **Group Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="4da57-113">**[グループ式]** の **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4da57-113">In **Group expressions**, click **Add**.</span></span> <span data-ttu-id="4da57-114">新しい行がグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da57-114">A new row appears in the grid.</span></span>  
  
4.  <span data-ttu-id="4da57-115">**[グループ化の条件]** ボックスで、グループ化するフィールドを入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4da57-115">In the **Group on** list, type or select the field to group.</span></span>  
  
5.  <span data-ttu-id="4da57-116">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4da57-116">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="4da57-117">**[再帰的な親]** ボックスで、グループ化で親として使用するフィールドを入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4da57-117">In the **Recursive Parent** list, enter or select the field to group on.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="4da57-118">レポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="4da57-118">Run the report.</span></span> <span data-ttu-id="4da57-119">レポートに再帰型階層グループが表示されますが、階層を示すインデントはありません。</span><span class="sxs-lookup"><span data-stu-id="4da57-119">The report displays the recursive hierarchy group, although there is no indent to show the hierarchy</span></span>  
  
### <a name="to-format-a-recursive-hierarchy-group-with-indent-levels"></a><span data-ttu-id="4da57-120">再帰型階層グループにインデント レベルを設定するには</span><span class="sxs-lookup"><span data-stu-id="4da57-120">To format a recursive hierarchy group with indent levels</span></span>  
  
1.  <span data-ttu-id="4da57-121">階層書式を表示するためのインデント レベルを追加する対象フィールドが含まれているテキスト ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4da57-121">Click the text box that contains the field to which you want to add indent levels to display a hierarchy format.</span></span> <span data-ttu-id="4da57-122">テキスト ボックスのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da57-122">The properties for the text box appear in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4da57-123">プロパティ ペインが表示されない場合は、 **[表示]** タブの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4da57-123">If you do not see the Properties pane, click **Properties** on the **View** tab.</span></span>  
  
2.  <span data-ttu-id="4da57-124">[プロパティ] ペインで、ノードを展開し、 `Padding` [**左**] をクリックして、ドロップダウンリストからを選択し **\<Expression...>** ます。</span><span class="sxs-lookup"><span data-stu-id="4da57-124">In the Properties pane, expand the `Padding` node, click **Left**, and from the drop-down list, select **\<Expression...>**.</span></span>  
  
3.  <span data-ttu-id="4da57-125">式ペインで次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="4da57-125">In the Expression pane, type the following expression:</span></span>  
  
     `=CStr(2 + (Level()*10)) + "pt"`  
  
     <span data-ttu-id="4da57-126">Padding のプロパティはすべて、 *nnyy*形式の文字列が必要です。ここで、 *nn* は数字、 *yy* は単位です。</span><span class="sxs-lookup"><span data-stu-id="4da57-126">The Padding properties all require a string in the format *nnyy*, where *nn* is a number and *yy* is the unit of measure.</span></span> <span data-ttu-id="4da57-127">この例の式では、`Level` 関数を使用する文字列が構築され、再帰レベルに基づいて余白のサイズが増加されます。</span><span class="sxs-lookup"><span data-stu-id="4da57-127">The example expression builds a string that uses the `Level` function to increase the size of the padding based on recursion level.</span></span> <span data-ttu-id="4da57-128">たとえば、レベルが 1 の行では余白は 12 ポイント (2 + (1\*10)) に、レベルが 3 の行では 32 ポイント (2 + (3\*10)) になります。</span><span class="sxs-lookup"><span data-stu-id="4da57-128">For example, a row that has a level of 1 would result in a padding of (2 + (1\*10))=12pt, and a row that has a level of 3 would result in a padding of (2 + (3\*10))=32pt.</span></span> <span data-ttu-id="4da57-129">関数の詳細については `Level` 、「 [Level](report-builder-functions-level-function.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4da57-129">For information about the `Level` function, see [Level](report-builder-functions-level-function.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="4da57-130">レポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="4da57-130">Run the report.</span></span> <span data-ttu-id="4da57-131">グループ化されたデータの階層ビューがレポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da57-131">The report displays a hierarchical view of the grouped data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da57-132">参照</span><span class="sxs-lookup"><span data-stu-id="4da57-132">See Also</span></span>  
 <span data-ttu-id="4da57-133">[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4da57-133">[Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4da57-134">[データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4da57-134">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4da57-135">[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4da57-135">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="4da57-136">[テーブル &#40;レポート ビルダーおよび SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4da57-136">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4da57-137">[マトリックス &#40;レポート ビルダーおよび SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4da57-137">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4da57-138">[一覧 &#40;レポート ビルダーおよび SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4da57-138">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4da57-139">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4da57-139">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
