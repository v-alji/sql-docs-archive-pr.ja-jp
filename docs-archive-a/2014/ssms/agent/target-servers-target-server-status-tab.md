---
title: '[ターゲット サーバー] ([ターゲット サーバーの状態] タブ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.target.status.f1
ms.assetid: 010a4cab-d878-4889-8ac8-7d91db6345d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: be51648a4642d25c59e52be65e43037844ec0909
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714994"
---
# <a name="target-servers-target-server-status-tab"></a><span data-ttu-id="b021c-102">[ターゲット サーバー] ([ターゲット サーバーの状態] タブ)</span><span class="sxs-lookup"><span data-stu-id="b021c-102">Target Servers (Target Server Status Tab)</span></span>
  <span data-ttu-id="b021c-103">このページを使用すると、このマスター サーバーのターゲット サーバーの状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="b021c-103">Use this page to view the status of the target servers for this master server.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b021c-104">Options</span><span class="sxs-lookup"><span data-stu-id="b021c-104">Options</span></span>  
 <span data-ttu-id="b021c-105">**対象サーバー**</span><span class="sxs-lookup"><span data-stu-id="b021c-105">**Target Server**</span></span>  
 <span data-ttu-id="b021c-106">ターゲット サーバーの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="b021c-106">View the name of the target server.</span></span>  
  
 <span data-ttu-id="b021c-107">**[ローカル時刻]**</span><span class="sxs-lookup"><span data-stu-id="b021c-107">**Local time**</span></span>  
 <span data-ttu-id="b021c-108">ターゲット サーバーのローカル タイム ゾーンにおける日付と時刻を表示します。</span><span class="sxs-lookup"><span data-stu-id="b021c-108">View the date and time of the target server in the local time zone for that server.</span></span>  
  
 <span data-ttu-id="b021c-109">**[最終呼び出し]**</span><span class="sxs-lookup"><span data-stu-id="b021c-109">**Last polled**</span></span>  
 <span data-ttu-id="b021c-110">ターゲット サーバーがマスターの呼び出しを行った最新の日時を、そのサーバーのローカル時刻で表示します。</span><span class="sxs-lookup"><span data-stu-id="b021c-110">View the local date and time that the target server last polled the master.</span></span>  
  
 <span data-ttu-id="b021c-111">**[未読の命令]**</span><span class="sxs-lookup"><span data-stu-id="b021c-111">**Unread instructions**</span></span>  
 <span data-ttu-id="b021c-112">ターゲット サーバーが受け取っていない命令の数を表示します。</span><span class="sxs-lookup"><span data-stu-id="b021c-112">View the number of instructions that the target server has not yet received.</span></span>  
  
 <span data-ttu-id="b021c-113">**状態**</span><span class="sxs-lookup"><span data-stu-id="b021c-113">**Status**</span></span>  
 <span data-ttu-id="b021c-114">ターゲット サーバーの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="b021c-114">View the status of the target server.</span></span>  
  
 <span data-ttu-id="b021c-115">**[強制的にポーリング]**</span><span class="sxs-lookup"><span data-stu-id="b021c-115">**Force Poll**</span></span>  
 <span data-ttu-id="b021c-116">このボタンをクリックすると、選択されているターゲット サーバーがマスター サーバーをポーリングします。</span><span class="sxs-lookup"><span data-stu-id="b021c-116">Click this button to force the selected target servers to poll the master server.</span></span>  
  
 <span data-ttu-id="b021c-117">**[強制的に参加解除]**</span><span class="sxs-lookup"><span data-stu-id="b021c-117">**Force Defection**</span></span>  
 <span data-ttu-id="b021c-118">このボタンをクリックすると、選択されているターゲット サーバーがマスター サーバーを登録解除します。</span><span class="sxs-lookup"><span data-stu-id="b021c-118">Click this button to force the selected target servers to defect from the master server.</span></span>  
  
 <span data-ttu-id="b021c-119">**[命令を通知]**</span><span class="sxs-lookup"><span data-stu-id="b021c-119">**Post Instructions**</span></span>  
 <span data-ttu-id="b021c-120">選択されているターゲット サーバーに命令を通知します。</span><span class="sxs-lookup"><span data-stu-id="b021c-120">Post instructions to the selected target servers.</span></span>  
  
 <span data-ttu-id="b021c-121">**[自動更新を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="b021c-121">**Enable Auto Refresh**</span></span>  
 <span data-ttu-id="b021c-122">このオプションをオンにすると、表示されている情報が自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="b021c-122">Select this option to automatically refresh the information shown.</span></span>  
  
 <span data-ttu-id="b021c-123">**[更新間隔]**</span><span class="sxs-lookup"><span data-stu-id="b021c-123">**Refresh every**</span></span>  
 <span data-ttu-id="b021c-124">このページの情報を更新する間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="b021c-124">Specify how often the information on this page is refreshed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b021c-125">参照</span><span class="sxs-lookup"><span data-stu-id="b021c-125">See Also</span></span>  
 [<span data-ttu-id="b021c-126">エンタープライズ全体の管理の自動化</span><span class="sxs-lookup"><span data-stu-id="b021c-126">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
