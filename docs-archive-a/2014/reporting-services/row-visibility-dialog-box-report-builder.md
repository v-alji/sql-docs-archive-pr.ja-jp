---
title: '[行表示] ダイアログボックス (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 748cf1612f04e02a90a5d8579b56d3856dea0388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633737"
---
# <a name="row-visibility-dialog-box-report-builder"></a><span data-ttu-id="2bab2-102">[行表示] ダイアログ ボックス (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="2bab2-102">Row Visibility Dialog Box (Report Builder)</span></span>
  <span data-ttu-id="2bab2-103">**[行表示]** ダイアログ ボックスを使用すると、選択した行をレポートの初回実行時に表示または非表示にすることも、別のレポート アイテムを使用して行の表示を切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="2bab2-103">Use the **Row Visibility** dialog box to show or hide the selected row when the report is first run or to use another report item to toggle the visibility of the row.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2bab2-104">Options</span><span class="sxs-lookup"><span data-stu-id="2bab2-104">Options</span></span>  
 <span data-ttu-id="2bab2-105">**[レポートの初期実行時]**</span><span class="sxs-lookup"><span data-stu-id="2bab2-105">**When the report is initially run**</span></span>  
 <span data-ttu-id="2bab2-106">レポートに行を表示する際の初期設定を示すオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bab2-106">Select an option to indicate how the row is initially displayed in the report.</span></span>  
  
 <span data-ttu-id="2bab2-107">**表示**</span><span class="sxs-lookup"><span data-stu-id="2bab2-107">**Show**</span></span>  
 <span data-ttu-id="2bab2-108">行を表示します。</span><span class="sxs-lookup"><span data-stu-id="2bab2-108">Select this option to show the row.</span></span>  
  
 <span data-ttu-id="2bab2-109">**Hide**</span><span class="sxs-lookup"><span data-stu-id="2bab2-109">**Hide**</span></span>  
 <span data-ttu-id="2bab2-110">行を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="2bab2-110">Select this option to hide the row.</span></span>  
  
 <span data-ttu-id="2bab2-111">**[式を基に表示/非表示を切り替える]**</span><span class="sxs-lookup"><span data-stu-id="2bab2-111">**Show or hide based on an expression**</span></span>  
 <span data-ttu-id="2bab2-112">式を使用して初期表示を変化させます。</span><span class="sxs-lookup"><span data-stu-id="2bab2-112">Select this option to vary the initial visibility using an expression.</span></span>  
  
 <span data-ttu-id="2bab2-113">アイテムを非表示にする場合は `Boolean`、アイテムを表示する場合は `True` と評価される `False` 値の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="2bab2-113">Type an expression that evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span> <span data-ttu-id="2bab2-114">式を編集するには、**式**([*fx*]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2bab2-114">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="2bab2-115">**[次のレポート アイテムでの表示の切り替えを可能にする]**</span><span class="sxs-lookup"><span data-stu-id="2bab2-115">**Display can be toggled by this report item**</span></span>  
 <span data-ttu-id="2bab2-116">ユーザーが HTML レポート ビューアーでこの行の表示/非表示を切り替えられるようにする切り替えイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="2bab2-116">Choose this option to display a toggle image that enables the user to show or hide this row in an HTML report viewer.</span></span>  
  
 <span data-ttu-id="2bab2-117">切り替えイメージを表示するレポートのテキスト ボックスの名前 (「Textbox1」など) を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="2bab2-117">Type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span> <span data-ttu-id="2bab2-118">選択するテキスト ボックスは、このレポート アイテムの現在のスコープまたはコンテナー スコープに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bab2-118">The text box that you choose must be in the current or containing scope for this report item.</span></span> <span data-ttu-id="2bab2-119">たとえば、子グループに関連付けられている行の表示を切り替えるには、親グループに関連付けられている行のテキスト ボックスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bab2-119">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span> <span data-ttu-id="2bab2-120">グラフの表示を切り替えるには、レポート本文や四角形など、グラフと同じコンテナー スコープにあるテキスト ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bab2-120">To toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bab2-121">参照</span><span class="sxs-lookup"><span data-stu-id="2bab2-121">See Also</span></span>  
 <span data-ttu-id="2bab2-122">[式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2bab2-122">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2bab2-123">[アイテムへの展開または折りたたみアクションの追加 &#40;レポートビルダーと SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2bab2-123">[Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2bab2-124">[&#40;レポートビルダーと SSRS&#41;の画像](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2bab2-124">[Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2bab2-125">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="2bab2-125">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="2bab2-126">[[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="2bab2-126">[Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)</span></span>  
  
  
