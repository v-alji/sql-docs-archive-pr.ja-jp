---
title: '&lt;AgentProfileName&gt; プロパティ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofileprops.f1
helpviewer_keywords:
- Agent Profile Properties dialog box
ms.assetid: 01a992d2-e4ff-417c-93f0-dc43ab2d1624
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 561f55353b7e40d168266cf5ba531519c8225053
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645563"
---
# <a name="ltagentprofilenamegt-properties"></a><span data-ttu-id="a7dc5-102">&lt;AgentProfileName&gt; プロパティ</span><span class="sxs-lookup"><span data-stu-id="a7dc5-102">&lt;AgentProfileName&gt; Properties</span></span>
  <span data-ttu-id="a7dc5-103">**[&lt;AgentProfileName&gt; のプロパティ]** ダイアログ ボックスを使用すると、プロファイル内の各エージェント パラメーターに対して指定された値を表示したり、ユーザー定義のプロファイルの値を変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-103">Use the **Agent Profiles Properties** dialog box to view the values specified for each agent parameter in a profile and to modify the values for user-defined profiles.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7dc5-104">オプション</span><span class="sxs-lookup"><span data-stu-id="a7dc5-104">Options</span></span>  
 <span data-ttu-id="a7dc5-105">**Name**</span><span class="sxs-lookup"><span data-stu-id="a7dc5-105">**Name**</span></span>  
 <span data-ttu-id="a7dc5-106">プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-106">The name of the profile.</span></span>  
  
 <span data-ttu-id="a7dc5-107">**説明**</span><span class="sxs-lookup"><span data-stu-id="a7dc5-107">**Description**</span></span>  
 <span data-ttu-id="a7dc5-108">プロファイルの説明です。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-108">A description of the profile.</span></span>  
  
 <span data-ttu-id="a7dc5-109">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="a7dc5-109">**Parameter**</span></span>  
 <span data-ttu-id="a7dc5-110">プロファイルに含まれるエージェント パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-110">The agent parameters included in the profile.</span></span> <span data-ttu-id="a7dc5-111">各パラメーターに対する値は、プロファイルで指定されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-111">Profiles do not necessarily specify a value for each parameter.</span></span> <span data-ttu-id="a7dc5-112">指定されたエージェントで有効なパラメーターをすべて表示するには、 **[このプロファイルに使用されているパラメーターのみ表示する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-112">To see all parameters that are valid for a given agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="a7dc5-113">各パラメーターの詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-113">For descriptions of each parameter, see:</span></span>  
  
-   [<span data-ttu-id="a7dc5-114">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="a7dc5-114">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
-   [<span data-ttu-id="a7dc5-115">レプリケーション ログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="a7dc5-115">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="a7dc5-116">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="a7dc5-116">Replication Distribution Agent</span></span>](agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="a7dc5-117">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="a7dc5-117">Replication Merge Agent</span></span>](agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="a7dc5-118">レプリケーション キュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="a7dc5-118">Replication Queue Reader Agent</span></span>](agents/replication-queue-reader-agent.md)  
  
 <span data-ttu-id="a7dc5-119">**既定値**</span><span class="sxs-lookup"><span data-stu-id="a7dc5-119">**Default Value**</span></span>  
 <span data-ttu-id="a7dc5-120">各エージェント パラメーターの既定値です。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-120">The default value for each agent parameter.</span></span>  
  
 <span data-ttu-id="a7dc5-121">**Value**</span><span class="sxs-lookup"><span data-stu-id="a7dc5-121">**Value**</span></span>  
 <span data-ttu-id="a7dc5-122">プロファイル内のパラメーターに対して指定された値です。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-122">The value specified for the parameter in the profile.</span></span> <span data-ttu-id="a7dc5-123">このフィールドは、ユーザー定義のプロファイルに対して編集可能です。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-123">This field is editable for user-defined profiles.</span></span>  
  
 <span data-ttu-id="a7dc5-124">**[このプロファイルに使用されているパラメーターのみ表示する]**</span><span class="sxs-lookup"><span data-stu-id="a7dc5-124">**Show only parameters used in this profile**</span></span>  
 <span data-ttu-id="a7dc5-125">指定されたエージェントに有効なパラメーターをすべて表示するにはオフにします。</span><span class="sxs-lookup"><span data-stu-id="a7dc5-125">Clear to show all valid parameters for a given agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7dc5-126">参照</span><span class="sxs-lookup"><span data-stu-id="a7dc5-126">See Also</span></span>  
 <span data-ttu-id="a7dc5-127">[レプリケーション エージェント プロファイルの操作](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="a7dc5-127">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="a7dc5-128">[レプリケーション エージェントの概要](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="a7dc5-128">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="a7dc5-129">レプリケーション エージェント プロファイル</span><span class="sxs-lookup"><span data-stu-id="a7dc5-129">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
