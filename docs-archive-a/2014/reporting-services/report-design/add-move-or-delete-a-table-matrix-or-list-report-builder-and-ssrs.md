---
title: テーブル、マトリックス、または一覧の追加、移動、または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b97c470-cde0-4bb1-a46e-5f5f5553feaa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 43941639a41c897a49cd34662b74de26a27e3f07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739354"
---
# <a name="add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs"></a><span data-ttu-id="28949-102">テーブル、マトリックス、または一覧の追加、移動、または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="28949-102">Add, Move, or Delete a Table, Matrix, or List (Report Builder and SSRS)</span></span>
  <span data-ttu-id="28949-103">データ領域には、レポート データセットのデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="28949-103">A data region displays data from a report dataset.</span></span> <span data-ttu-id="28949-104">またデータ領域には、テーブル、マトリックス、一覧、グラフ、およびゲージが含まれます。</span><span class="sxs-lookup"><span data-stu-id="28949-104">Data regions include table, matrix, list, chart, and gauge.</span></span> <span data-ttu-id="28949-105">1 つのデータ領域を別のデータ領域内に入れ子にするには、各データ領域を個別に追加し、子データ領域を親データ領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="28949-105">To nest one data region inside another, add each data region separately, and then drag the child data region onto the parent data region.</span></span>  
  
 <span data-ttu-id="28949-106">テーブルまたはマトリックス データ領域をレポートに追加するには、テーブルまたはマトリックスの新規作成ウィザードを実行するのが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="28949-106">The simplest way to add a table or matrix data region to your report is to run the New Table or New Matrix Wizard.</span></span> <span data-ttu-id="28949-107">これらのウィザードを使用すると、データ ソースへの接続の選択、フィールドの配置、およびレイアウトとスタイルの選択の手順を段階的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="28949-107">These wizards will guide you through the process of choosing a connection to a data source, arranging fields, and choosing the layout and style.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="28949-108">ウィザードは、レポート ビルダーでのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="28949-108">The wizard is available only in Report Builder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-table-or-matrix-to-a-report-by-using-the-new-table-or-new-matrix-wizard"></a><span data-ttu-id="28949-109">テーブルまたはマトリックスの新規作成ウィザードを使用してレポートにテーブルまたはマトリックスを追加するには</span><span class="sxs-lookup"><span data-stu-id="28949-109">To add a table or matrix to a report by using the New Table or New Matrix Wizard</span></span>  
  
1.  <span data-ttu-id="28949-110">**[挿入]** タブの **[テーブル]** または **[マトリックス]** をクリックし、次に **[テーブル ウィザード]** または **[マトリックス ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28949-110">On the **Insert** tab, click **Table** or **Matrix**, and then click **Table Wizard** or **Matrix Wizard**.</span></span>  
  
2.  <span data-ttu-id="28949-111">**NewTable**または**マトリックスの新規作成**ウィザードの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="28949-111">Follow the steps in the **NewTable** or **New Matrix** wizard.</span></span>  
  
3.  <span data-ttu-id="28949-112">**[ホーム]** タブで **[実行]** をクリックして、表示されたレポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="28949-112">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
4.  <span data-ttu-id="28949-113">レポートの作業を続行するには、 **[実行]** タブで **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28949-113">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
### <a name="to-add-a-data-region"></a><span data-ttu-id="28949-114">データ領域を追加するには</span><span class="sxs-lookup"><span data-stu-id="28949-114">To add a data region</span></span>  
  
1.  <span data-ttu-id="28949-115">**[データ領域]** グループの **[リボン]** で、追加するデータ領域をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28949-115">On the **Ribbon**, in the **Data Regions** group, click the data region to add.</span></span>  
  
2.  <span data-ttu-id="28949-116">デザイン画面をクリックし、次にマウスをドラッグして、必要なサイズのデータ領域のボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="28949-116">Click the design surface, and then drag to create a box that is the desired size of the data region.</span></span>  
  
3.  <span data-ttu-id="28949-117">レポート データ ペインからレポート データセット フィールドをデータ領域セルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="28949-117">Drag a report dataset field from the Report Data pane onto a data region cell.</span></span> <span data-ttu-id="28949-118">ここで、データ領域はレポート データセットのデータにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="28949-118">The data region is now bound to data from the report dataset.</span></span>  
  
### <a name="to-select-a-data-region"></a><span data-ttu-id="28949-119">データ領域を選択するには</span><span class="sxs-lookup"><span data-stu-id="28949-119">To select a data region</span></span>  
  
-   <span data-ttu-id="28949-120">Tablix データ領域では、コーナー ハンドルを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="28949-120">For a tablix data region, right-click the corner handle.</span></span> <span data-ttu-id="28949-121">グラフ データ領域またはゲージ データ領域では、データ領域内をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28949-121">For a chart or gauge data region, click in the data region.</span></span>  
  
     <span data-ttu-id="28949-122">1 つの選択ハンドルと 8 つのサイズ変更ハンドルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="28949-122">A selection handle and eight resizing handles appear.</span></span>  
  
     <span data-ttu-id="28949-123">入れ子になったデータ領域では、領域内を右クリックし、 **[選択]** をクリックして、目的のレポート アイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="28949-123">For nested data regions, right-click in the nested data region, click **Select**, and then select the report item you want.</span></span> <span data-ttu-id="28949-124">どのレポート アイテムが選択されているかを確認するには、プロパティ ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="28949-124">To verify which report item is selected, use the Properties pane.</span></span> <span data-ttu-id="28949-125">デザイン画面で選択したアイテムの名前が、プロパティ ペインのツール バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="28949-125">The name of the selected item on the design surface appears in the toolbar of the Properties pane.</span></span>  
  
### <a name="to-move-a-data-region"></a><span data-ttu-id="28949-126">データ領域を移動するには</span><span class="sxs-lookup"><span data-stu-id="28949-126">To move a data region</span></span>  
  
-   <span data-ttu-id="28949-127">データ領域を移動するには、データ領域の選択ハンドルをクリックしてドラッグします。</span><span class="sxs-lookup"><span data-stu-id="28949-127">To move a data region, click the selection handle of the data region and drag it.</span></span> <span data-ttu-id="28949-128">既存のレポート アイテムと揃えるには、スナップ線を使用します。</span><span class="sxs-lookup"><span data-stu-id="28949-128">Use snaplines to align it to existing report items.</span></span>  
  
     <span data-ttu-id="28949-129">ルーラーが表示されていない場合は、[表示] タブをクリックして **[ルーラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28949-129">If the ruler is not visible, click the View tab and select the **Ruler** option.</span></span>  
  
     <span data-ttu-id="28949-130">また方向キーを使用して、デザイン画面で選択しているデータ領域を移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="28949-130">Alternatively, use the arrow keys to move the selected data region on the design surface.</span></span>  
  
### <a name="to-delete-a-data-region"></a><span data-ttu-id="28949-131">データ領域を削除するには</span><span class="sxs-lookup"><span data-stu-id="28949-131">To delete a data region</span></span>  
  
-   <span data-ttu-id="28949-132">データ領域を選択し、領域内を右クリックして **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28949-132">Select the data region, right-click in the data region, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28949-133">参照</span><span class="sxs-lookup"><span data-stu-id="28949-133">See Also</span></span>  
 <span data-ttu-id="28949-134">[Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="28949-134">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="28949-135">[テーブル &#40;レポートビルダーと SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="28949-135">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="28949-136">[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="28949-136">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="28949-137">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="28949-137">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="28949-138">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="28949-138">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
