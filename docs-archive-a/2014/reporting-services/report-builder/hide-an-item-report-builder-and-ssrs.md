---
title: 項目の非表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.visibility.f1
- "10503"
ms.assetid: 9d78f8de-959b-456f-8947-687fa6e2ba91
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56e834204698369687528c622cf6167a492766f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634294"
---
# <a name="hide-an-item-report-builder-and-ssrs"></a><span data-ttu-id="af048-102">アイテムを非表示にする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="af048-102">Hide an Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="af048-103">レポート パラメーターやその他の式を指定して、アイテムを条件付きで非表示にする場合は、レポート アイテムの表示/非表示を設定します。</span><span class="sxs-lookup"><span data-stu-id="af048-103">Set the visibility of a report item when you want to conditionally hide an item based on a report parameter or some other expression that you specify.</span></span>

 <span data-ttu-id="af048-104">また、ドリルダウン レポートなどで、レポートのテキスト ボックスをクリックすることによってレポート アイテムの表示と非表示をユーザーが切り替えられるようなレポートを設計することもできます。</span><span class="sxs-lookup"><span data-stu-id="af048-104">You can also design a report to allow the user to toggle the visibility of report items based on clicking text boxes in the report, for example, for a drilldown report.</span></span> <span data-ttu-id="af048-105">詳細については、「 [アイテムへの展開または折りたたみアクションの追加 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af048-105">For more information, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="af048-106">以下に、定数または式に基づいて表示レポートでのレポート アイテムの表示または非表示を切り替える手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="af048-106">The following procedures describe how to show or hide a report item in a rendered report based on a constant or an expression.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-hide-a-report-item"></a><span data-ttu-id="af048-107">レポート アイテムを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="af048-107">To hide a report item</span></span>

1.  <span data-ttu-id="af048-108">レポート デザイン ビューで、レポート アイテムを右クリックし、 **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="af048-108">In report design view, right-click the report item and open its **Properties** page.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="af048-109">テーブルまたはマトリックス データ領域全体を選択するには、領域内をクリックして選択し、行ハンドル、列ハンドル、またはコーナー ハンドルを右クリックして、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af048-109">To select an entire table or matrix data region, click in the data region to select it, right-click a row, column, or corner handle, and then click **Tablix Properties**.</span></span>

2.  <span data-ttu-id="af048-110">[**表示] をクリックします。**</span><span class="sxs-lookup"><span data-stu-id="af048-110">Click **Visibility.**</span></span>

3.  <span data-ttu-id="af048-111">**[レポートの初期実行時]** で、レポートを初めて表示する際にアイテムを非表示にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="af048-111">In **When the report is initially run**, specify whether to hide the item when you first view the report:</span></span>

    -   <span data-ttu-id="af048-112">アイテムを表示する場合は、 **[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af048-112">To display the item, click **Show**.</span></span>

    -   <span data-ttu-id="af048-113">アイテムを非表示にする場合は、 **[非表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af048-113">To hide the item, click **Hide**.</span></span>

    -   <span data-ttu-id="af048-114">実行時に評価される式を指定するには、 **[式を基に表示/非表示を切り替える]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af048-114">To specify an expression that is evaluated at run-time, click **Show or hide based on an expression**.</span></span> <span data-ttu-id="af048-115">**[式]** ダイアログ ボックスで、式を入力するか、式 ( **[fx]** ) ボタンをクリックして式を作成します。</span><span class="sxs-lookup"><span data-stu-id="af048-115">Type the expression or click the expression (**fx**) button to create the expression in the **Expression** dialog box.</span></span>

        > [!NOTE]
        >  <span data-ttu-id="af048-116">表示/非表示を設定する式を指定する場合、次の図のように、レポート アイテムの Hidden プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="af048-116">When you specify an expression for visibility, you are setting the Hidden property of the report item, as shown in the following image.</span></span> <span data-ttu-id="af048-117">この値が False の場合、式の評価によってレポート アイテムが表示され、値が True の場合、レポート アイテムは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="af048-117">The evaluated expression shows the report item when the value is False, and hides the report item when the value is True.</span></span> 
        > <span data-ttu-id="af048-118">![[プロパティ] の [表示] のダイアログと [非表示] プロパティ](../media/hiddenproperty-propertiesvisibility.png "[プロパティ] の [表示] のダイアログと [非表示] プロパティ")</span><span class="sxs-lookup"><span data-stu-id="af048-118">![Properties_Visibility dialog and Hidden property](../media/hiddenproperty-propertiesvisibility.png "Properties_Visibility dialog and Hidden property")</span></span>

4.  <span data-ttu-id="af048-119">[**OK**] を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="af048-119">Click **OK** twice.</span></span>

### <a name="to-hide-static-rows-in-a-table-matrix-or-list"></a><span data-ttu-id="af048-120">テーブル、マトリックス、または一覧の静的行を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="af048-120">To hide static rows in a table, matrix, or list</span></span>

1.  <span data-ttu-id="af048-121">レポート デザイン ビューで、テーブル、マトリックス、または一覧をクリックし、行ハンドルおよび列ハンドルを表示します。</span><span class="sxs-lookup"><span data-stu-id="af048-121">In report design view, click the table, matrix, or list to display the row and column handles.</span></span>

2.  <span data-ttu-id="af048-122">行ハンドルを右クリックし、 **[行表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af048-122">Right-click the row handle, and then click **Row Visibility**.</span></span> <span data-ttu-id="af048-123">**[行表示]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="af048-123">The **Row Visibility** dialog box opens.</span></span>

3.  <span data-ttu-id="af048-124">表示/非表示を設定するには、最初の手順の 3. ～ 4. に従います。</span><span class="sxs-lookup"><span data-stu-id="af048-124">To set the visibility, follow steps 3 and 4 in the first procedure.</span></span>

### <a name="to-hide-static-columns-in-a-table-matrix-or-list"></a><span data-ttu-id="af048-125">テーブル、マトリックス、または一覧の静的列を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="af048-125">To hide static columns in a table, matrix, or list</span></span>

1.  <span data-ttu-id="af048-126">[デザイン] ビューで、テーブル、マトリックス、または一覧を選択し、行ハンドルおよび列ハンドルを表示します。</span><span class="sxs-lookup"><span data-stu-id="af048-126">In Design view, select the table, matrix, or list to display the row and column handles.</span></span>

2.  <span data-ttu-id="af048-127">列ハンドルを右クリックし、 **[列表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af048-127">Right-click the column handle, and then click **Column Visibility**.</span></span>

3.  <span data-ttu-id="af048-128">**[列表示]** ダイアログ ボックスで、最初の手順の 3 ～ 4 に従います。</span><span class="sxs-lookup"><span data-stu-id="af048-128">In the **Column Visibility** dialog box, follow steps 3 and 4 in the first procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="af048-129">参照</span><span class="sxs-lookup"><span data-stu-id="af048-129">See Also</span></span>
 <span data-ttu-id="af048-130">[ドリルダウンアクション &#40;レポートビルダーと ssrs&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [アイテムへの展開または折りたたみアクションの追加 &#40;レポートビルダーと ssrs&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) [式の例 &#40;レポートビルダーと ssrs&#41;](../report-design/expression-examples-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="af048-130">[Drilldown Action &#40;Report Builder and SSRS&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) [Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md)</span></span>


