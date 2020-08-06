---
title: パッケージ オブジェクトをコピーする | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], copying objects
- copying package objects [Integration Services]
- data flow [Integration Services], copying objects
- connection managers [Integration Services], copying
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3219f0023c9a28ed270adeb6fd2b795e3459c3e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633957"
---
# <a name="copy-package-objects"></a><span data-ttu-id="cc4a5-102">パッケージ オブジェクトをコピーする</span><span class="sxs-lookup"><span data-stu-id="cc4a5-102">Copy Package Objects</span></span>
  <span data-ttu-id="cc4a5-103">このトピックでは、制御フロー アイテム、データ フロー アイテム、および接続マネージャーをパッケージ内またはパッケージ間でコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-103">This topic describes how to copy control flow items, data flow items, and connection managers within a package or between packages.</span></span>  
  
### <a name="to-copy-control-and-data-flow-items"></a><span data-ttu-id="cc4a5-104">制御フロー アイテムおよびデータ フロー アイテムをコピーするには</span><span class="sxs-lookup"><span data-stu-id="cc4a5-104">To copy control and data flow items</span></span>  
  
1.  <span data-ttu-id="cc4a5-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、作業対象とするパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the packages that you want work with.</span></span>  
  
2.  <span data-ttu-id="cc4a5-106">ソリューション エクスプローラーで、コピー元とコピー先のパッケージをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-106">In Solution Explorer, double-click the packages that you want to copy between.</span></span>  
  
3.  <span data-ttu-id="cc4a5-107">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、コピーするアイテムを含むパッケージのタブをクリックし、 **[制御フロー]** タブ、 **[データ フロー]** タブ、または **[イベント ハンドラー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-107">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the tab for the package that contains the items to copy and click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="cc4a5-108">コピーする制御フロー アイテムまたはデータ フロー アイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-108">Select the control flow or data flow items to copy.</span></span> <span data-ttu-id="cc4a5-109">アイテムは、Shift キーを押しながらアイテムをクリックして 1 つずつ選択することも、選択する複数のアイテムをポインターでドラッグしてグループとして選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-109">You can either select items one at a time by pressing the Shift key and clicking the item or select items as a group by dragging the pointer across the items you want to select.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="cc4a5-110">アイテムを連結する優先順位制約およびパスは、連結する 2 つのアイテムを選択しても自動的には選択されません。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-110">The precedence constraints and paths that connect items are not selected automatically when you select the two items that they connect.</span></span> <span data-ttu-id="cc4a5-111">順序付けられたワークフロー (制御フローやデータ フローの一部) をコピーするには、必ず優先順位制約およびパスもコピーします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-111">To copy an ordered workflow-a segment of control flow or data flow-make sure to also copy the precedence constrains and the paths.</span></span>  
  
5.  <span data-ttu-id="cc4a5-112">選択したアイテムを右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-112">Right-click a selected item and click **Copy**.</span></span>  
  
6.  <span data-ttu-id="cc4a5-113">アイテムを別のパッケージにコピーする場合は、コピー先のパッケージをクリックし、アイテムの種類に適したタブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-113">If copying items to a different package, click the package that you want to copy to, and then click the appropriate tab for the item type.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="cc4a5-114">データ フロー タスクが 1 つもパッケージに含まれていない場合は、データ フローをパッケージにコピーできません。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-114">You cannot copy a data flow to a package unless the package contains at least one Data Flow task.</span></span>  
  
7.  <span data-ttu-id="cc4a5-115">右クリックして **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-115">Right-click and click **Paste**.</span></span>  
  
### <a name="to-copy-connection-managers"></a><span data-ttu-id="cc4a5-116">接続マネージャーをコピーするには</span><span class="sxs-lookup"><span data-stu-id="cc4a5-116">To copy connection managers</span></span>  
  
1.  <span data-ttu-id="cc4a5-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、作業対象とするパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package that you want to work with.</span></span>  
  
2.  <span data-ttu-id="cc4a5-118">ソリューション エクスプローラーで、パッケージをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-118">In Solution Explorer, double-click the package.</span></span>  
  
3.  <span data-ttu-id="cc4a5-119">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[制御フロー]** タブ、 **[データ フロー]** タブ、または **[イベント ハンドラー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-119">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow**, **Data Flow**, or **Event Handler** tab.</span></span>  
  
4.  <span data-ttu-id="cc4a5-120">**[接続マネージャー]** 領域で、接続マネージャーを右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-120">In the **Connection Managers** area, right-click the connection manager, and then click **Copy**.</span></span> <span data-ttu-id="cc4a5-121">接続マネージャーは、一度に 1 つしかコピーできません。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-121">You can copy only one connection manager at a time.</span></span>  
  
5.  <span data-ttu-id="cc4a5-122">アイテムを別のパッケージにコピーしている場合は、コピー先のパッケージをクリックし、 **[制御フロー]** タブ、 **[データ フロー]** タブ、または **[イベント ハンドラー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-122">If you are copying items to a different package, click the package that you want to copy to and then click the **Control Flow**, **Data Flow**, or **Event Handler** tab.</span></span>  
  
6.  <span data-ttu-id="cc4a5-123">**[接続マネージャー]** 領域を右クリックして、 **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc4a5-123">Right-click in the **Connection Managers** area and click **Paste**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4a5-124">参照</span><span class="sxs-lookup"><span data-stu-id="cc4a5-124">See Also</span></span>  
 <span data-ttu-id="cc4a5-125">[制御フロー](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="cc4a5-125">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="cc4a5-126">[データ フロー](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="cc4a5-126">[Data Flow](data-flow/data-flow.md) </span></span>  
 <span data-ttu-id="cc4a5-127">[Integration Services &#40;SSIS&#41; の接続](connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="cc4a5-127">[Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="cc4a5-128">プロジェクト アイテムをコピーする</span><span class="sxs-lookup"><span data-stu-id="cc4a5-128">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)  
  
  
