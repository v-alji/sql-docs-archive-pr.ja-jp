---
title: '[列表示] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.columnvisibility.f1
- "10127"
ms.assetid: ca59d1cd-d782-4298-aa61-4f312c32eb50
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c2e5f4124f987b87f02968282367817d61c3211
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641515"
---
# <a name="column-visibility-dialog-box"></a><span data-ttu-id="e0535-102">[列表示] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="e0535-102">Column Visibility Dialog Box</span></span>
  <span data-ttu-id="e0535-103">**[列表示]** ダイアログ ボックスでは、選択した列をレポートの初期実行時に表示または非表示にする操作や、別のレポート アイテムを使用して列の表示を切り替える操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e0535-103">Use the **Column Visibility** dialog box to show or hide the selected column when the report is first run or to use another report item to toggle the visibility of the column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e0535-104">Options</span><span class="sxs-lookup"><span data-stu-id="e0535-104">Options</span></span>  
 <span data-ttu-id="e0535-105">**[レポートの初期実行時]**</span><span class="sxs-lookup"><span data-stu-id="e0535-105">**When the report is initially run**</span></span>  
 <span data-ttu-id="e0535-106">レポートにレポート アイテムを表示する際の初期設定を示すオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e0535-106">Select an option to indicate how the report item is initially displayed in the report.</span></span>  
  
 <span data-ttu-id="e0535-107">**表示**</span><span class="sxs-lookup"><span data-stu-id="e0535-107">**Show**</span></span>  
 <span data-ttu-id="e0535-108">レポート アイテムを表示します。</span><span class="sxs-lookup"><span data-stu-id="e0535-108">Choose this option to show the report item.</span></span>  
  
 <span data-ttu-id="e0535-109">**Hide**</span><span class="sxs-lookup"><span data-stu-id="e0535-109">**Hide**</span></span>  
 <span data-ttu-id="e0535-110">レポート アイテムを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="e0535-110">Choose this option to hide the report item.</span></span>  
  
 <span data-ttu-id="e0535-111">**[式を基に表示/非表示を切り替える]**</span><span class="sxs-lookup"><span data-stu-id="e0535-111">**Show or hide based on an expression**</span></span>  
 <span data-ttu-id="e0535-112">式を使用して初期表示を変化させます。</span><span class="sxs-lookup"><span data-stu-id="e0535-112">Choose this option to vary the initial visibility using an expression.</span></span>  
  
 <span data-ttu-id="e0535-113">アイテムを非表示にする場合は `Boolean`、アイテムを表示する場合は `True` と評価される `False` 値の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="e0535-113">Type an expression that evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span> <span data-ttu-id="e0535-114">式を編集するには、式 ([*fx*]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0535-114">Click the Expression (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="e0535-115">**[次のレポート アイテムでの表示の切り替えを可能にする]**</span><span class="sxs-lookup"><span data-stu-id="e0535-115">**Display can be toggled by this report item**</span></span>  
 <span data-ttu-id="e0535-116">ユーザーが HTML レポート ビューアーでこのレポート アイテムの表示/非表示を切り替えられるようにする切り替えイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="e0535-116">Choose this option to display a toggle image that enables the user to show or hide this report item in an HTML report viewer.</span></span>  
  
 <span data-ttu-id="e0535-117">切り替えイメージを表示するレポートのテキスト ボックスの名前 (「Textbox1」など) を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="e0535-117">Type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span> <span data-ttu-id="e0535-118">選択するテキスト ボックスは、このレポート アイテムの現在のスコープまたはコンテナー スコープに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0535-118">The text box that you choose must be in the current or containing scope for this report item.</span></span> <span data-ttu-id="e0535-119">たとえば、子グループに関連付けられている行の表示を切り替えるには、親グループに関連付けられている行のテキスト ボックスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0535-119">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span> <span data-ttu-id="e0535-120">グラフの表示を切り替えるには、レポート本文や四角形など、グラフと同じコンテナー スコープにあるテキスト ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="e0535-120">To toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0535-121">参照</span><span class="sxs-lookup"><span data-stu-id="e0535-121">See Also</span></span>  
 <span data-ttu-id="e0535-122">[式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0535-122">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e0535-123">[アイテムへの展開または折りたたみアクションの追加 &#40;レポートビルダーと SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0535-123">[Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e0535-124">[&#40;レポートビルダーと SSRS&#41;の画像](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0535-124">[Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e0535-125">レポート デザイナーの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="e0535-125">Report Designer F1 Help</span></span>](tools/report-designer-f1-help.md)  
  
  