---
title: レポートのスクロール時にヘッダーを表示したままにする (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d37fcd38a402dc0f88ac002c679c1046d5b0b583
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739282"
---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a><span data-ttu-id="2512e-102">レポートのスクロール時にヘッダーを表示したままにする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2512e-102">Keep Headers Visible When Scrolling Through a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2512e-103">レポートを表示した後に、スクロールによって行ラベルや列ラベルが隠れないようにするために、行見出しまたは列見出しを固定できます。</span><span class="sxs-lookup"><span data-stu-id="2512e-103">To prevent row and column labels from scrolling out of view after rendering a report, you can freeze the row or column headings.</span></span>  
  
 <span data-ttu-id="2512e-104">行と列を制御する方法は、テーブルとマトリックスのどちらを使用しているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="2512e-104">How you control the rows and columns depends on whether you have a table or a matrix.</span></span> <span data-ttu-id="2512e-105">テーブルを使用している場合は、静的メンバー (行見出しと列見出し) を表示したままにするよう構成します。</span><span class="sxs-lookup"><span data-stu-id="2512e-105">If you have a table, you configure static members (row and column headings) to remain visible.</span></span> <span data-ttu-id="2512e-106">マトリックスを使用している場合は、行と列のグループ ヘッダーを表示したままにするよう構成します。</span><span class="sxs-lookup"><span data-stu-id="2512e-106">If you have a matrix, you configure row and column group headers to remain visible.</span></span>  
  
 <span data-ttu-id="2512e-107">レポートを Excel にエクスポートしても、ヘッダーは自動的には固定表示されません。</span><span class="sxs-lookup"><span data-stu-id="2512e-107">If you export the report to Excel, the header will not be frozen automatically.</span></span> <span data-ttu-id="2512e-108">Excel でウィンドウ枠を固定できます。</span><span class="sxs-lookup"><span data-stu-id="2512e-108">You can freeze the pane in Excel.</span></span> <span data-ttu-id="2512e-109">詳細については、「[Microsoft Excel へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)」の「**ページ ヘッダーとページ フッター**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2512e-109">For more information see the **Page Headers and Footers** section of [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2512e-110">テーブルに行グループおよび列グループがある場合でも、スクロール中にこれらのグループ ヘッダーを表示したままにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2512e-110">Even if a table has row and column groups, you cannot keep those group headers visible while scrolling</span></span>  
  
 <span data-ttu-id="2512e-111">次の図はテーブルを示しています。</span><span class="sxs-lookup"><span data-stu-id="2512e-111">The following image shows a table.</span></span>  
  
 <span data-ttu-id="2512e-112">![Table](../media/table.png "テーブル")</span><span class="sxs-lookup"><span data-stu-id="2512e-112">![Table](../media/table.png "Table")</span></span>  
  
 <span data-ttu-id="2512e-113">次の図はマトリックスを示しています。</span><span class="sxs-lookup"><span data-stu-id="2512e-113">The following image shows a matrix.</span></span>  
  
 <span data-ttu-id="2512e-114">![マトリックス](../media/matrix.png "Matrix")</span><span class="sxs-lookup"><span data-stu-id="2512e-114">![Matrix](../media/matrix.png "Matrix")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a><span data-ttu-id="2512e-115">スクロール中もマトリックス グループ ヘッダーを表示したままにするには</span><span class="sxs-lookup"><span data-stu-id="2512e-115">To keep matrix group headers visible while scrolling</span></span>  
  
1.  <span data-ttu-id="2512e-116">Tablix データ領域の行、列、またはコーナー ハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2512e-116">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="2512e-117">**[全般]** タブの **[行のヘッダー]** または **[列のヘッダー]** で、 **[スクロール中もヘッダーを表示したままにする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2512e-117">On the **General** tab, under **Row Headers** or **Column Headers**, select **Header should remain visible while scrolling**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a><span data-ttu-id="2512e-118">スクロール中も静的 Tablix メンバー (行または列) を表示したままにするには</span><span class="sxs-lookup"><span data-stu-id="2512e-118">To keep a static tablix member (row or column) visible while scrolling</span></span>  
  
1.  <span data-ttu-id="2512e-119">デザイン画面でテーブル内の任意の場所をクリックし、グループ化ペインにグループと静的メンバーを表示します。</span><span class="sxs-lookup"><span data-stu-id="2512e-119">On the design surface, click anywhere in the table to display static members, as well as groups, in the grouping pane.</span></span>  
  
     <span data-ttu-id="2512e-120">![グループ化ペイン](../media/grouppane-updated.png "グループ化ペイン")</span><span class="sxs-lookup"><span data-stu-id="2512e-120">![Grouping pane](../media/grouppane-updated.png "Grouping pane")</span></span>  
  
     <span data-ttu-id="2512e-121">行グループ ペインに、行グループ階層の静的メンバーおよび動的メンバーが階層的に表示され、列グループ ペインに、列グループ階層のメンバーが同様に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2512e-121">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy, and the Column groups pane shows a similar display for the column groups hierarchy.</span></span>  
  
2.  <span data-ttu-id="2512e-122">グループ化ペインの右側にある下矢印をクリックし、 **[詳細設定モード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2512e-122">On the right side of the grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span>  
  
3.  <span data-ttu-id="2512e-123">スクロール中も表示したままにする静的メンバー (行または列) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2512e-123">Click the static member (row or column) that you want to remain visible while scrolling.</span></span> <span data-ttu-id="2512e-124">プロパティ ペインに **[Tablix メンバー]** プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2512e-124">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
     <span data-ttu-id="2512e-125">![Tablix メンバー プロパティ](../media/grouppane-tablixmember-updated.png "Tablix メンバー プロパティ")</span><span class="sxs-lookup"><span data-stu-id="2512e-125">![Tablix Member properties](../media/grouppane-tablixmember-updated.png "Tablix Member properties")</span></span>  
  
4.  <span data-ttu-id="2512e-126">[プロパティ] ペインで、[ **Fixeddata** ] をに設定 `True` します。</span><span class="sxs-lookup"><span data-stu-id="2512e-126">In the Properties pane, set **FixedData** to `True`.</span></span>  
  
5.  <span data-ttu-id="2512e-127">スクロール中も表示したままにするすべての隣接するメンバーに対して、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="2512e-127">Repeat this for as many adjacent members as you want to keep visible while scrolling.</span></span>  
  
6.  <span data-ttu-id="2512e-128">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="2512e-128">Preview the report.</span></span>  
  
 <span data-ttu-id="2512e-129">レポートを下方向または横方向にスクロールしたときに、静的な Tablix メンバーが表示されたままになります。</span><span class="sxs-lookup"><span data-stu-id="2512e-129">As you page down or across the report, the static tablix members remain in view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2512e-130">参照</span><span class="sxs-lookup"><span data-stu-id="2512e-130">See Also</span></span>  
 <span data-ttu-id="2512e-131">[Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2512e-131">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2512e-132">[レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2512e-132">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2512e-133">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2512e-133">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2512e-134">[グループ単位でのヘッダーとフッターの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2512e-134">[Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2512e-135">[複数のページへの行および列ヘッダーの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2512e-135">[Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2512e-136">グループ化ペイン &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="2512e-136">Grouping Pane &#40;Report Builder&#41;</span></span>](grouping-pane-report-builder.md)  
  
  
