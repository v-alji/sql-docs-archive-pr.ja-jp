---
title: MSSQLSERVER_17883 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46488fb6f7adac2c1109871f2aad4c79352829ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713202"
---
# <a name="mssqlserver_17883"></a><span data-ttu-id="16c80-102">MSSQLSERVER_17883</span><span class="sxs-lookup"><span data-stu-id="16c80-102">MSSQLSERVER_17883</span></span>
    
## <a name="details"></a><span data-ttu-id="16c80-103">詳細</span><span class="sxs-lookup"><span data-stu-id="16c80-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16c80-104">製品名</span><span class="sxs-lookup"><span data-stu-id="16c80-104">Product Name</span></span>|<span data-ttu-id="16c80-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="16c80-105">SQL Server</span></span>|  
|<span data-ttu-id="16c80-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="16c80-106">Event ID</span></span>|<span data-ttu-id="16c80-107">17883</span><span class="sxs-lookup"><span data-stu-id="16c80-107">17883</span></span>|  
|<span data-ttu-id="16c80-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="16c80-108">Event Source</span></span>|<span data-ttu-id="16c80-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="16c80-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="16c80-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="16c80-110">Component</span></span>|<span data-ttu-id="16c80-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="16c80-111">SQLEngine</span></span>|  
|<span data-ttu-id="16c80-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="16c80-112">Symbolic Name</span></span>|<span data-ttu-id="16c80-113">SRV_SCHEDULER_NONYIELDING</span><span class="sxs-lookup"><span data-stu-id="16c80-113">SRV_SCHEDULER_NONYIELDING</span></span>|  
|<span data-ttu-id="16c80-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="16c80-114">Message Text</span></span>|<span data-ttu-id="16c80-115">プロセス %ld:%ld:%ld (0x%lx) ワーカー 0x%p が、スケジューラ %ld で応答を停止している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16c80-115">Process %ld:%ld:%ld (0x%lx) Worker 0x%p appears to be non-yielding on Scheduler %ld.</span></span> <span data-ttu-id="16c80-116">Thread creation time: %I64d.</span><span class="sxs-lookup"><span data-stu-id="16c80-116">Thread creation time: %I64d.</span></span> <span data-ttu-id="16c80-117">スレッド CPU 概算使用時間: カーネル %I64d ミリ秒、ユーザー %I64d ミリ秒。</span><span class="sxs-lookup"><span data-stu-id="16c80-117">Approx Thread CPU Used: kernel %I64d ms, user %I64d ms.</span></span> <span data-ttu-id="16c80-118">プロセスの使用率 %d%%。</span><span class="sxs-lookup"><span data-stu-id="16c80-118">Process Utilization %d%%.</span></span> <span data-ttu-id="16c80-119">システムのアイドル状態 %d%%。</span><span class="sxs-lookup"><span data-stu-id="16c80-119">System Idle %d%%.</span></span> <span data-ttu-id="16c80-120">間隔: %I64d ミリ秒。</span><span class="sxs-lookup"><span data-stu-id="16c80-120">Interval: %I64d ms.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="16c80-121">説明</span><span class="sxs-lookup"><span data-stu-id="16c80-121">Explanation</span></span>  
 <span data-ttu-id="16c80-122">スケジューラで応答を停止しているスレッドに問題が発生している可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="16c80-122">Indicates that there is a possible problem with a thread not yielding on a scheduler.</span></span>  <span data-ttu-id="16c80-123">これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のバグが原因で発生するか、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行に必要なサイクルを十分に取得していない場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16c80-123">This could be caused by a bug in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not getting enough cycles to execute.</span></span>  <span data-ttu-id="16c80-124">スレッドが最終的に応答すると、このエラーは解決します。</span><span class="sxs-lookup"><span data-stu-id="16c80-124">This error could go away if the thread eventually yields.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="16c80-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="16c80-125">User Action</span></span>  
 <span data-ttu-id="16c80-126">システムの負荷が高すぎる場合は、負荷を軽減してください。それ以外の場合は、マイクロソフト カスタマー サポート サービスに連絡してください。</span><span class="sxs-lookup"><span data-stu-id="16c80-126">If excessive load on system reduce load otherwise contact Microsoft Customer Support Services.</span></span>  
  
  
