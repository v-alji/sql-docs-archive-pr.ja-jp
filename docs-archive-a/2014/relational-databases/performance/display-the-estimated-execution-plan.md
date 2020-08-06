---
title: 推定実行プランの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- zoom [SQL Server]
- estimated execution plan [SQL Server]
- displaying execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
- customizing execution plan display [SQL Server]
- modifying execution plan display
- custom zoom [SQL Server]
ms.assetid: e94aa576-4c0c-4c54-ad05-6c3432cc615b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79c0972661d40eb9e359cf43f7a1f0b1b2ae4b0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714213"
---
# <a name="display-the-estimated-execution-plan"></a><span data-ttu-id="20422-102">推定実行プランの表示</span><span class="sxs-lookup"><span data-stu-id="20422-102">Display the Estimated Execution Plan</span></span>
  <span data-ttu-id="20422-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、グラフィカルな推定実行プランを生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="20422-103">This topic describes how to generate graphical estimated execution plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="20422-104">推定実行プランを生成するときには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] のクエリやバッチは実行されません。</span><span class="sxs-lookup"><span data-stu-id="20422-104">When estimated execution plans are generated, the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries or batches do not execute.</span></span> <span data-ttu-id="20422-105">代わりに、クエリが実際に実行された場合に [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によって使用される可能性が最も高いクエリ実行プランが、生成された実行プランに表示されます。</span><span class="sxs-lookup"><span data-stu-id="20422-105">Instead, the execution plan that is generated displays the query execution plan that [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] would most probably use if the queries were actually executed.</span></span>  
  
 <span data-ttu-id="20422-106">この機能を使用するには、グラフィカルな実行プランの生成に使用する [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを実行できる適切な権限を持ち、このクエリが参照するすべてのデータベースに SHOWPLAN 権限が与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="20422-106">To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] query for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-display-the-estimated-execution-plan-for-a-query"></a><span data-ttu-id="20422-107">クエリの推定実行プランを表示するには</span><span class="sxs-lookup"><span data-stu-id="20422-107">To display the estimated execution plan for a query</span></span>  
  
1.  <span data-ttu-id="20422-108">ツール バーの **[データベース エンジン クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20422-108">On the toolbar, click **Database Engine Query**.</span></span> <span data-ttu-id="20422-109">また、ツール バーの **[ファイルを開く]** をクリックして既存のクエリを参照することにより、既存のクエリを開き、推定実行プランを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="20422-109">You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.</span></span>  
  
2.  <span data-ttu-id="20422-110">表示する推定実行プランに対するクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="20422-110">Enter the query for which you would like to display the estimated execution plan.</span></span>  
  
3.  <span data-ttu-id="20422-111">**[クエリ]** メニューの **[推定実行プランの表示]** をクリックするか、ツール バーの **[推定実行プランの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20422-111">On the **Query** menu, click **Display Estimated Execution Plan** or click the **Display Estimated Execution Plan** toolbar button.</span></span> <span data-ttu-id="20422-112">推定実行プランが、結果ペインの **[実行プラン]** タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="20422-112">The estimated execution plan is displayed on the **Execution Plan** tab in the results pane.</span></span> <span data-ttu-id="20422-113">追加情報を表示するには、マウス ポインターを論理操作や物理操作のアイコン上にしばらく置き、各操作について、表示されるツールヒント内の説明とプロパティを参照します。</span><span class="sxs-lookup"><span data-stu-id="20422-113">To view additional information, pause the mouse over the logical and physical operator icons and view the description and properties of the operator in the displayed ToolTip.</span></span> <span data-ttu-id="20422-114">また、プロパティ ウィンドウでも操作のプロパティを参照できます。</span><span class="sxs-lookup"><span data-stu-id="20422-114">Alternatively, you can view operator properties in the Properties window.</span></span> <span data-ttu-id="20422-115">プロパティが表示されていない場合は、任意の操作を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20422-115">If Properties is not visible, right-click an operator and click **Properties**.</span></span> <span data-ttu-id="20422-116">特定の操作のプロパティを表示するには、その操作をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20422-116">Select an operator to view its properties.</span></span>  
  
4.  <span data-ttu-id="20422-117">実行プランの表示を変更するには、実行プランを右クリックし、 **[拡大]** 、 **[縮小]** 、 **[ズームの指定]** 、 **[ウィンドウのサイズに合わせて大きさを変更]** のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="20422-117">To alter the display of the execution plan, right-click the execution plan and select **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**.</span></span> <span data-ttu-id="20422-118">**[拡大]** と **[縮小]** では、実行プランを固定比率ずつ拡大または縮小できます。</span><span class="sxs-lookup"><span data-stu-id="20422-118">**Zoom In** and **Zoom Out** allow you to magnify or reduce the execution plan by fixed amounts.</span></span> <span data-ttu-id="20422-119">**[ズームの指定]** を使用すると、表示倍率 (80% など) を定義できます。</span><span class="sxs-lookup"><span data-stu-id="20422-119">**Custom Zoom** allows you to define your own display magnification, such as zooming at 80 percent.</span></span> <span data-ttu-id="20422-120">**[ウィンドウのサイズに合わせて大きさを変更]** では、結果ペインの大きさに合わせて実行プランを拡大できます。</span><span class="sxs-lookup"><span data-stu-id="20422-120">**Zoom to Fit** magnifies the execution plan to fit the result pane.</span></span>  
  
  
