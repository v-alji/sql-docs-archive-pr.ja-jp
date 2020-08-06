---
title: 階段状レポートの作成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5933c4f0-c713-4ecb-b521-ff46c9c63fff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d845993ac1462cef2d39638101e5c7b9fc314b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634880"
---
# <a name="create-a-stepped-report-report-builder-and-ssrs"></a><span data-ttu-id="06134-102">階段状レポートの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="06134-102">Create a Stepped Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="06134-103">階段状レポートでは、次の例に示すように、親グループとその下でインデントされた詳細行または子グループが、同一の列内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="06134-103">A stepped report shows detail rows or child groups indented under a parent group in the same column, as shown in the example below:</span></span>  
  
 <span data-ttu-id="06134-104">![レンダリングされた階段状レポート](../media/steppedreportrendered.gif "レンダリングされた階段状レポート")</span><span class="sxs-lookup"><span data-stu-id="06134-104">![Rendered stepped report](../media/steppedreportrendered.gif "Rendered stepped report")</span></span>  
  
 <span data-ttu-id="06134-105">従来の表形式のレポートでは、親グループがレポート上の隣接する列に配置されます。</span><span class="sxs-lookup"><span data-stu-id="06134-105">Traditional table reports place the parent group in an adjacent column on the report.</span></span> <span data-ttu-id="06134-106">新しい Tablix データ領域を使用すると、グループと、詳細行または子グループを同じ列に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="06134-106">The new tablix data region enables you to add a group and detail rows or child groups to the same column.</span></span> <span data-ttu-id="06134-107">グループ行を詳細行または子グループ行と区別するには、フォントの色などの書式設定を適用するか、詳細行にインデントを設定します。</span><span class="sxs-lookup"><span data-stu-id="06134-107">To differentiate the group rows from the detail or child group rows, you can apply formatting such as font color, or you can indent the detail rows.</span></span>  
  
 <span data-ttu-id="06134-108">このトピックの手順では、手動で階段状レポートを作成する方法を示しますが、新しいテーブル/マトリックス ウィザードを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="06134-108">The procedures in this topic show you how to manually create a stepped report, but you can also use the New Table and Matrix Wizard.</span></span> <span data-ttu-id="06134-109">このウィザードには、階段状レポートのレイアウトが用意されているため、このようなレポートを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="06134-109">It provides the layout for stepped reports, making it easy to create them.</span></span> <span data-ttu-id="06134-110">ウィザードを完了した後、レポートをさらに拡張できます。</span><span class="sxs-lookup"><span data-stu-id="06134-110">After you complete the wizard, you can further enhance the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06134-111">ウィザードは、レポート ビルダーでのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="06134-111">The wizard is available only in Report Builder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-stepped-report"></a><span data-ttu-id="06134-112">階段状レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="06134-112">To create a stepped report</span></span>  
  
1.  <span data-ttu-id="06134-113">テーブル レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="06134-113">Create a table report.</span></span> <span data-ttu-id="06134-114">たとえば、Tablix データ領域を挿入し、データ行にフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="06134-114">For example, insert a tablix data region and add fields to the Data row.</span></span>  
  
2.  <span data-ttu-id="06134-115">レポートに親グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="06134-115">Add a parent group to your report.</span></span>  
  
    1.  <span data-ttu-id="06134-116">テーブル内の任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="06134-116">Click anywhere in the table to select it.</span></span> <span data-ttu-id="06134-117">グループ化ペインに、行グループ ペインのグループの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="06134-117">The Grouping pane displays the Details group in the Row Groups pane.</span></span>  
  
    2.  <span data-ttu-id="06134-118">グループ化ペインで、グループの詳細を右クリックし、 **[グループの追加]** をポイントして **[親グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06134-118">In the Grouping Pane, right-click the Details Group, point to **Add Group**, and then click **Parent Group**.</span></span>  
  
    3.  <span data-ttu-id="06134-119">**[Tablix のグループ]** ダイアログ ボックスで、グループの名前を指定し、グループ式を入力するかドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="06134-119">In the **Tablix Group** dialog box, provide a name for the group and type or select a group expression from the drop-down list.</span></span> <span data-ttu-id="06134-120">ボックスの一覧には、レポート データ ペインで使用できる簡単なフィールド式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="06134-120">The drop-down list displays the simple field expressions that are available in the Report Data pane.</span></span> <span data-ttu-id="06134-121">たとえば、[PostalCode] は、データセット内の PostalCode フィールドの簡単なフィールド式です。</span><span class="sxs-lookup"><span data-stu-id="06134-121">For example, [PostalCode] is a simple field expression for the PostalCode field in a dataset.</span></span>  
  
    4.  <span data-ttu-id="06134-122">**[グループ ヘッダーの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06134-122">Select **Add group header**.</span></span> <span data-ttu-id="06134-123">このオプションを選択すると、グループの上部にグループ ラベルおよびグループ合計の静的行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="06134-123">This option adds a static row above the group for the group label and group totals.</span></span> <span data-ttu-id="06134-124">同様に、 **[グループ フッターの追加]** を選択して、グループの下に静的行を追加できます。</span><span class="sxs-lookup"><span data-stu-id="06134-124">Likewise, you can select **Add group footer** to add a static row below the group.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="06134-125">これで、基本的なテーブル レポートが作成されました。</span><span class="sxs-lookup"><span data-stu-id="06134-125">You now have a basic tabular report.</span></span> <span data-ttu-id="06134-126">レポートが表示されると、1 つの列にグループ インスタンス値、1 つ以上の列にグループ化された詳細データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="06134-126">When it is rendered, you see one column with the group instance value, and one or more columns with grouped detail data.</span></span> <span data-ttu-id="06134-127">デザイン画面でのデータ領域の外観は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="06134-127">The following figure shows what the data region might look like on the design surface.</span></span>  
  
     <span data-ttu-id="06134-128">![グループを含むテーブル データ領域](../media/tabledataregionwithgroup.gif "グループを含むテーブル データ領域")</span><span class="sxs-lookup"><span data-stu-id="06134-128">![Table data region with group](../media/tabledataregionwithgroup.gif "Table data region with group")</span></span>  
  
     <span data-ttu-id="06134-129">レポートを表示したときの表示データ領域の外観は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="06134-129">The following figure shows how the rendered data region might look when you view the report.</span></span>  
  
     <span data-ttu-id="06134-130">![レンダリングされたグループ化レポート](../media/tablereportrendered.gif "レンダリングされたグループ化レポート")</span><span class="sxs-lookup"><span data-stu-id="06134-130">![Rendered grouped report](../media/tablereportrendered.gif "Rendered grouped report")</span></span>  
  
3.  <span data-ttu-id="06134-131">段階状レポートを作成する場合、最初の列にグループ インスタンスを表示する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="06134-131">For a stepped report, you do not need the first column that shows the group instance.</span></span> <span data-ttu-id="06134-132">その代わり、グループ ヘッダー セル内の値をコピーし、グループ列を削除し、グループ ヘッダー行内の最初のテキスト ボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="06134-132">Instead, copy the value in the group header cell, delete the group column, and paste in the first text box in the group header row.</span></span> <span data-ttu-id="06134-133">グループ列を削除するには、グループ列またはセルを右クリックして、 **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06134-133">To remove the group column, right-click the group column or cell, and click **Delete Columns**.</span></span> <span data-ttu-id="06134-134">デザイン画面でのデータ領域の外観は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="06134-134">The following figure shows what the data region might look like on the design surface.</span></span>  
  
     <span data-ttu-id="06134-135">![グループ ヘッダー行のあるデータ領域](../media/tabledataregiongroupheader.gif "グループ ヘッダー行のあるデータ領域")</span><span class="sxs-lookup"><span data-stu-id="06134-135">![Data region with group header row](../media/tabledataregiongroupheader.gif "Data region with group header row")</span></span>  
  
4.  <span data-ttu-id="06134-136">グループ ヘッダー行の下で、同じ列にある詳細行にインデントを設定するには、詳細データ セルの余白を変更します。</span><span class="sxs-lookup"><span data-stu-id="06134-136">To indent the detail rows under the group header row in the same column, change the padding of the detail data cell.</span></span>  
  
    1.  <span data-ttu-id="06134-137">インデントを設定する詳細フィールドが含まれているセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="06134-137">Select the cell with the detail field that you want to indent.</span></span> <span data-ttu-id="06134-138">そのセルのテキスト ボックス プロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="06134-138">The text box properties for that cell appear in the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="06134-139">プロパティ ペインの **[配置]** で、 **[余白]** のプロパティを展開します。</span><span class="sxs-lookup"><span data-stu-id="06134-139">In the Properties pane, under **Alignment**, expand the properties for **Padding**.</span></span>  
  
    3.  <span data-ttu-id="06134-140">**左側**には、のような新しい埋め込み値を入力 `.5in` します。</span><span class="sxs-lookup"><span data-stu-id="06134-140">For **Left**, type a new padding value, such as `.5in`.</span></span> <span data-ttu-id="06134-141">指定された値の余白分、セル内のテキストがインデント設定されます。</span><span class="sxs-lookup"><span data-stu-id="06134-141">Padding indents the text in the cell by the value you specify.</span></span> <span data-ttu-id="06134-142">余白の既定値は 2 ポイントです。</span><span class="sxs-lookup"><span data-stu-id="06134-142">The default padding is 2 points.</span></span> <span data-ttu-id="06134-143">余白のプロパティの有効な値として、0 (ゼロ) 以上の正の数の後に、サイズ指定子を入力します。</span><span class="sxs-lookup"><span data-stu-id="06134-143">Valid values for the Padding properties are zero or a positive number, followed by a size designator.</span></span>  
  
         <span data-ttu-id="06134-144">サイズ指定子は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="06134-144">Size designators are:</span></span>  
  
        |||  
        |-|-|  
        |`in`|<span data-ttu-id="06134-145">インチ (1 インチ = 2.54 cm)</span><span class="sxs-lookup"><span data-stu-id="06134-145">Inches (1 inch = 2.54 centimeters)</span></span>|  
        |`cm`|<span data-ttu-id="06134-146">センチメートル</span><span class="sxs-lookup"><span data-stu-id="06134-146">Centimeters</span></span>|  
        |`mm`|<span data-ttu-id="06134-147">mm</span><span class="sxs-lookup"><span data-stu-id="06134-147">Millimeters</span></span>|  
        |`pt`|<span data-ttu-id="06134-148">ポイント (1 ポイント = 1/72 インチ)</span><span class="sxs-lookup"><span data-stu-id="06134-148">Points (1 point = 1/72 inch)</span></span>|  
        |`pc`|<span data-ttu-id="06134-149">パイカ (1 パイカ = 12 ポイント)</span><span class="sxs-lookup"><span data-stu-id="06134-149">Picas (1 pica = 12 points)</span></span>|  
  
     <span data-ttu-id="06134-150">データ領域は次の例にようになります。</span><span class="sxs-lookup"><span data-stu-id="06134-150">Your data region will look similar to the following example.</span></span>  
  
     <span data-ttu-id="06134-151">![階段状レポートのデータ領域](../media/steppedreportdataregion.gif "階段状レポートのデータ領域")</span><span class="sxs-lookup"><span data-stu-id="06134-151">![Data region for stepped report](../media/steppedreportdataregion.gif "Data region for stepped report")</span></span>  
  
     <span data-ttu-id="06134-152">**段階状レポート レイアウトのデータ領域**</span><span class="sxs-lookup"><span data-stu-id="06134-152">**Data Region for Stepped Report Layout**</span></span>  
  
     <span data-ttu-id="06134-153">**[ホーム]** タブで **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06134-153">On the **Home** tab Click **Run**.</span></span> <span data-ttu-id="06134-154">レポートに、子グループ値がインデント設定されたグループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="06134-154">The report displays the group with indented levels for the child group values.</span></span>  
  
### <a name="to-create-a-stepped-report-with-multiple-groups"></a><span data-ttu-id="06134-155">複数のグループを含む階段状レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="06134-155">To create a stepped report with multiple groups</span></span>  
  
1.  <span data-ttu-id="06134-156">前の手順の説明に従ってレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="06134-156">Create a report as described in the previous procedure.</span></span>  
  
2.  <span data-ttu-id="06134-157">追加のグループをレポートに追加します。</span><span class="sxs-lookup"><span data-stu-id="06134-157">Add additional groups to your report.</span></span>  
  
    1.  <span data-ttu-id="06134-158">行グループ ペインで、グループを右クリックし、 **[グループの追加]** をクリックして、追加するグループの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="06134-158">In the Row Groups pane, right-click the group, click **Add Group**, and then choose the type of group you want to add.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="06134-159">データ領域にグループを追加するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="06134-159">There are several ways to add groups to a data region.</span></span> <span data-ttu-id="06134-160">詳細については、「 [&#40;レポートビルダーと SSRS&#41;」の「データ領域でのグループの追加または削除](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06134-160">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
    2.  <span data-ttu-id="06134-161">**[Tablix のグループ]** ダイアログ ボックスで、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="06134-161">In the **Tablix Group** dialog box, type a name.</span></span>  
  
    3.  <span data-ttu-id="06134-162">**[グループ式]** で、式を入力するか、グループ化の対象となるデータセット フィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="06134-162">In **Group expression**, type an expression or select a dataset field to group on.</span></span> <span data-ttu-id="06134-163">式を作成するには、式 (**[fx]**) ボタンをクリックして **[式]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="06134-163">To create an expression, click the expression (**fx**) button to open the **Expression** dialog box.</span></span>  
  
    4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="06134-164">グループ データを表示するセルの埋め込みを変更します。</span><span class="sxs-lookup"><span data-stu-id="06134-164">Change the padding for the cell that displays the group data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06134-165">参照</span><span class="sxs-lookup"><span data-stu-id="06134-165">See Also</span></span>  
 <span data-ttu-id="06134-166">[ページヘッダーとページフッター &#40;レポートビルダーと SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06134-166">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="06134-167">[レポートアイテムの書式設定 &#40;レポートビルダーと SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06134-167">[Formatting Report Items &#40;Report Builder and SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="06134-168">[Tablix データ領域 &#40;レポートビルダーと SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06134-168">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="06134-169">[テーブル &#40;レポートビルダーと SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06134-169">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="06134-170">[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06134-170">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="06134-171">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06134-171">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="06134-172">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="06134-172">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
