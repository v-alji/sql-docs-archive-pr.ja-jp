---
title: ブレークポイントの設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8115fcd845ee5ff415d13aa4fe36230234e33ca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738113"
---
# <a name="set-breakpoints"></a><span data-ttu-id="e559c-102">[ブレークポイントの設定]</span><span class="sxs-lookup"><span data-stu-id="e559c-102">Set Breakpoints</span></span>
  <span data-ttu-id="e559c-103">**[ブレークポイントの設定]** ダイアログ ボックスを使用すると、ブレークポイントを有効にしてブレークポイントの動作を制御するためのイベントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e559c-103">Use the **Set Breakpoints** dialog box to specify the events on which to enable breakpoints and to control the behavior of the breakpoint.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e559c-104">Options</span><span class="sxs-lookup"><span data-stu-id="e559c-104">Options</span></span>  
 <span data-ttu-id="e559c-105">**有効**</span><span class="sxs-lookup"><span data-stu-id="e559c-105">**Enabled**</span></span>  
 <span data-ttu-id="e559c-106">選択すると、イベントのブレークポイントが有効になります。</span><span class="sxs-lookup"><span data-stu-id="e559c-106">Select to enable a breakpoint on an event.</span></span>  
  
 <span data-ttu-id="e559c-107">**Break Condition**</span><span class="sxs-lookup"><span data-stu-id="e559c-107">**Break Condition**</span></span>  
 <span data-ttu-id="e559c-108">ブレークポイントの設定に使用できるイベントの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="e559c-108">View a list of available events on which to set breakpoints.</span></span>  
  
 <span data-ttu-id="e559c-109">**Hit Count Type**</span><span class="sxs-lookup"><span data-stu-id="e559c-109">**Hit Count Type**</span></span>  
 <span data-ttu-id="e559c-110">ブレークポイントがいつ有効になるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e559c-110">Specify when the breakpoint takes effect.</span></span>  
  
|<span data-ttu-id="e559c-111">値</span><span class="sxs-lookup"><span data-stu-id="e559c-111">Value</span></span>|<span data-ttu-id="e559c-112">説明</span><span class="sxs-lookup"><span data-stu-id="e559c-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e559c-113">**毎回**</span><span class="sxs-lookup"><span data-stu-id="e559c-113">**Always**</span></span>|<span data-ttu-id="e559c-114">ブレークポイントにヒットすると、常に実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="e559c-114">Execution is always suspended when the breakpoint is hit.</span></span>|  
|<span data-ttu-id="e559c-115">**ヒット カウント (等しい)**</span><span class="sxs-lookup"><span data-stu-id="e559c-115">**Hit count equals**</span></span>|<span data-ttu-id="e559c-116">ブレークポイントの発生回数がヒット カウントと等しくなると実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="e559c-116">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|  
|<span data-ttu-id="e559c-117">**[ヒット カウント (より大きいまたは等しい)]**</span><span class="sxs-lookup"><span data-stu-id="e559c-117">**Hit greater or equal**</span></span>|<span data-ttu-id="e559c-118">ブレークポイントの発生回数がヒット カウント以上になると実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="e559c-118">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|  
|<span data-ttu-id="e559c-119">**ヒット カウント (倍数)**</span><span class="sxs-lookup"><span data-stu-id="e559c-119">**Hit count multiple**</span></span>|<span data-ttu-id="e559c-120">ヒット カウントの倍数だけブレークポイントが発生すると実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="e559c-120">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="e559c-121">たとえば、このオプションを 5 に設定すると、実行は 5 回ごとに中断されます。</span><span class="sxs-lookup"><span data-stu-id="e559c-121">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|  
  
 <span data-ttu-id="e559c-122">**[ヒット カウント]**</span><span class="sxs-lookup"><span data-stu-id="e559c-122">**Hit Count**</span></span>  
 <span data-ttu-id="e559c-123">ブレークをトリガーするヒットの回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e559c-123">Specify the number of hits at which to trigger a break.</span></span> <span data-ttu-id="e559c-124">ブレークポイントが常に有効になっている場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e559c-124">This option is not available if the breakpoint is always in effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e559c-125">参照</span><span class="sxs-lookup"><span data-stu-id="e559c-125">See Also</span></span>  
 [<span data-ttu-id="e559c-126">制御フローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="e559c-126">Debugging Control Flow</span></span>](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
