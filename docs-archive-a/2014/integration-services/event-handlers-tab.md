---
title: '[イベントハンドラー] タブ |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.eventhandlerwindow.f1
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5f25a9b0d602a3189feab797b7ef9c333decabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641772"
---
# <a name="event-handlers-tab"></a><span data-ttu-id="a1109-102">[イベント ハンドラー] タブ</span><span class="sxs-lookup"><span data-stu-id="a1109-102">Event Handlers Tab</span></span>
  <span data-ttu-id="a1109-103">**デザイナーの** [イベント ハンドラー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージの制御フローを構築できます。</span><span class="sxs-lookup"><span data-stu-id="a1109-103">Use the **Event Handlers** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to build a control flow in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="a1109-104">イベント ハンドラーは、パッケージによって生成されたイベントまたはパッケージ内のタスクまたはコンテナーによって生成されたイベントに応答して実行されます。</span><span class="sxs-lookup"><span data-stu-id="a1109-104">An event handler runs in response to an event raised by the package or by a task or container in the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a1109-105">Options</span><span class="sxs-lookup"><span data-stu-id="a1109-105">Options</span></span>  
 <span data-ttu-id="a1109-106">**[実行可能ファイル]**</span><span class="sxs-lookup"><span data-stu-id="a1109-106">**Executable**</span></span>  
 <span data-ttu-id="a1109-107">イベント ハンドラーを作成する実行可能ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a1109-107">Select the executable for which you want to build an event handler.</span></span> <span data-ttu-id="a1109-108">実行可能ファイルとは、パッケージか、パッケージ内のタスクまたはコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="a1109-108">The executable can be the package, or a task or containers in the package.</span></span>  
  
 <span data-ttu-id="a1109-109">**イベント ハンドラー**</span><span class="sxs-lookup"><span data-stu-id="a1109-109">**Event handler**</span></span>  
 <span data-ttu-id="a1109-110">イベント ハンドラーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="a1109-110">Select a type of event handler.</span></span> <span data-ttu-id="a1109-111">**ツールボックス**からアイテムをドラッグしてイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a1109-111">Create the event handler by dragging items from the **Toolbox**.</span></span>  
  
 <span data-ttu-id="a1109-112">**削除**</span><span class="sxs-lookup"><span data-stu-id="a1109-112">**Delete**</span></span>  
 <span data-ttu-id="a1109-113">イベント ハンドラーを選択し、 **[削除]** をクリックすると、パッケージからイベント ハンドラーを削除できます。</span><span class="sxs-lookup"><span data-stu-id="a1109-113">Select an event handler, and remove it from the package by clicking **Delete**.</span></span>  
  
 <span data-ttu-id="a1109-114">**実行可能ファイル \<executable name> の \<event handler name> を作成するにはここをクリックします**</span><span class="sxs-lookup"><span data-stu-id="a1109-114">**Click here to create an \<event handler name> for the executable \<executable name>**</span></span>  
 <span data-ttu-id="a1109-115">イベント ハンドラーを作成する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1109-115">Click to create the event handler.</span></span>  
  
 <span data-ttu-id="a1109-116">制御フローを作成するには、 [!INCLUDE[ssIS](../includes/ssis-md.md)] タスクおよびコンテナーを表すグラフィカル オブジェクトを、 **ツールボックス** から **[イベント ハンドラー]** タブのデザイン画面にドラッグします。次に、優先順位制約を使用してオブジェクトどうしを接続して、その実行の順序を定義します。</span><span class="sxs-lookup"><span data-stu-id="a1109-116">Create the control flow by dragging graphical objects that represent [!INCLUDE[ssIS](../includes/ssis-md.md)] tasks and containers from the **Toolbox** to the design surface of the **Event Handlers** tab, and then connecting the objects by using precedence constraints to define the sequence in which they run.</span></span>  
  
 <span data-ttu-id="a1109-117">また、注釈を追加するには、デザイン画面を右クリックし、メニューの **[注釈の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1109-117">Additionally, to add annotations, right-click the design surface, and then on the menu, click **Add Annotation**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1109-118">参照</span><span class="sxs-lookup"><span data-stu-id="a1109-118">See Also</span></span>  
 <span data-ttu-id="a1109-119">[Integration Services &#40;SSIS&#41; のイベント ハンドラー](integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="a1109-119">[Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md) </span></span>  
 <span data-ttu-id="a1109-120">[制御フロー](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="a1109-120">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="a1109-121">[SSIS デザイナー](ssis-designer.md) </span><span class="sxs-lookup"><span data-stu-id="a1109-121">[SSIS Designer](ssis-designer.md) </span></span>  
 [<span data-ttu-id="a1109-122">Integration Services &#40;SSIS&#41; のイベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="a1109-122">Integration Services &#40;SSIS&#41; Event Handlers</span></span>](integration-services-ssis-event-handlers.md)  
  
  
