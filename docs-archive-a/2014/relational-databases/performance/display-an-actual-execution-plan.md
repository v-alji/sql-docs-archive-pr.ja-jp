---
title: 実際の実行プランの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f384e2d2752b7601fbb46b8ee7f7b56a2615651c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714225"
---
# <a name="display-an-actual-execution-plan"></a><span data-ttu-id="63028-102">実際の実行プランの表示</span><span class="sxs-lookup"><span data-stu-id="63028-102">Display an Actual Execution Plan</span></span>
  <span data-ttu-id="63028-103">このトピックでは、実際のグラフィカルな実行プランを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="63028-103">This topic describes how to generate actual graphical execution plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="63028-104">実際の実行プランの生成時には、 [!INCLUDE[tsql](../../includes/tsql-md.md)] のクエリまたはバッチが実行されます。</span><span class="sxs-lookup"><span data-stu-id="63028-104">When actual execution plans are generated, the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries or batches execute.</span></span> <span data-ttu-id="63028-105">生成される実行プランには、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によりクエリの実行に使用される実際のクエリ実行プランが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63028-105">The execution plan that is generated displays the actual query execution plan that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses to execute the queries.</span></span>  
  
 <span data-ttu-id="63028-106">この機能を使用するユーザーには、グラフィカルな実行プランの生成に対応した [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリの実行に必要な権限があり、このクエリが参照するすべてのデータベースに対する SHOWPLAN 権限が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="63028-106">To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-include-an-execution-plan-for-a-query-during-execution"></a><span data-ttu-id="63028-107">クエリの実行に実行プランを含めるには</span><span class="sxs-lookup"><span data-stu-id="63028-107">To include an execution plan for a query during execution</span></span>  
  
1.  <span data-ttu-id="63028-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のツール バーの **[データベース エンジン クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63028-108">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar, click **Database Engine Query**.</span></span> <span data-ttu-id="63028-109">また、ツール バーの **[ファイルを開く]** をクリックして既存のクエリを参照することにより、既存のクエリを開き、推定実行プランを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="63028-109">You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.</span></span>  
  
2.  <span data-ttu-id="63028-110">表示する実際の実行プランに対するクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="63028-110">Enter the query for which you would like to display the actual execution plan.</span></span>  
  
3.  <span data-ttu-id="63028-111">[**クエリ**] メニューの [**実際の実行プランを含める**] をクリックするか、[**実際の実行プランを含める**] ツールバーボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="63028-111">On the **Query** menu, click **Include Actual Execution Plan** or click the **Include Actual Execution Plan** toolbar button</span></span>  
  
4.  <span data-ttu-id="63028-112">ツール バーの **[実行]** をクリックしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="63028-112">Execute the query by clicking the **Execute** toolbar button.</span></span> <span data-ttu-id="63028-113">クエリ オプティマイザーで使用されるプランが、結果ペインの **[実行プラン]** タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="63028-113">The plan used by the query optimizer is displayed on the **Execution Plan** tab in the results pane.</span></span> <span data-ttu-id="63028-114">マウス ポインターを論理操作や物理操作の上に置くと、各操作について、表示されるツールヒント内の説明とプロパティを確認できます。</span><span class="sxs-lookup"><span data-stu-id="63028-114">Pause the mouse over the logical and physical operators to view the description and properties of the operators in the displayed ToolTip.</span></span>  
  
     <span data-ttu-id="63028-115">また、プロパティ ウィンドウでも操作のプロパティを参照できます。</span><span class="sxs-lookup"><span data-stu-id="63028-115">Alternatively, you can view operator properties in the Properties window.</span></span> <span data-ttu-id="63028-116">プロパティが表示されていない場合は、任意の操作を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63028-116">If Properties is not visible, right-click an operator and select **Properties**.</span></span> <span data-ttu-id="63028-117">特定の操作のプロパティを表示するには、その操作をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63028-117">Select an operator to view its properties.</span></span>  
  
5.  <span data-ttu-id="63028-118">実行プランを右クリックし、 **[拡大]** 、 **[縮小]** 、 **[ズームの指定]** 、 **[ウィンドウのサイズに合わせて大きさを変更]** のいずれかをクリックして、実行プランの表示を変更できます。</span><span class="sxs-lookup"><span data-stu-id="63028-118">You can alter the display of the execution plan by right-clicking the execution plan and selecting **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**.</span></span> <span data-ttu-id="63028-119">**[拡大]** と **[縮小]** では、実行プランを拡大したり縮小したりできます。 **[ズームの指定]** では、80% で表示するなど、独自の縮尺を指定できます。</span><span class="sxs-lookup"><span data-stu-id="63028-119">**Zoom In** and **Zoom Out** allow you to zoom in or out on the execution plan, while **Custom Zoom** allows you to define your own zoom, such as zooming at 80 percent.</span></span> <span data-ttu-id="63028-120">**[ウィンドウのサイズに合わせて大きさを変更]** では、結果ペインの大きさに合わせて実行プランを拡大できます。</span><span class="sxs-lookup"><span data-stu-id="63028-120">**Zoom to Fit** magnifies the execution plan to fit the result pane.</span></span>  
  
  
