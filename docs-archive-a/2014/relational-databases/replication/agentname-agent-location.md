---
title: '&lt;AgentName&gt; エージェントの場所 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentlocation.f1
ms.assetid: dc664d80-fbe3-4586-aba8-a71fa62d14f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7fc39541915b43abd024e1b02022f8a9e61580b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634416"
---
# <a name="ltagentnamegt-agent-location"></a><span data-ttu-id="8e9c3-102">&lt;AgentName&gt; エージェントの場所</span><span class="sxs-lookup"><span data-stu-id="8e9c3-102">&lt;AgentName&gt; Agent Location</span></span>
  <span data-ttu-id="8e9c3-103">マージ エージェント (マージ サブスクリプション用) とディストリビューション エージェント (トランザクション サブスクリプションおよびスナップショット サブスクリプション用) は、ディストリビューターまたはサブスクライバーで実行します。</span><span class="sxs-lookup"><span data-stu-id="8e9c3-103">The Merge Agent (for merge subscriptions) and the Distribution Agent (for transactional and snapshot subscriptions) run at the Distributor or at the Subscriber.</span></span> <span data-ttu-id="8e9c3-104">エージェントをディストリビューターで実行するとサブスクリプションはプッシュ サブスクリプションとして参照され、サブスクライバーで実行するとプル サブスクリプションとして参照されます。</span><span class="sxs-lookup"><span data-stu-id="8e9c3-104">If the agent runs at the Distributor, the subscription is referred to as a push subscription; if the agent runs at the Subscriber, it is referred to as a pull subscription.</span></span> <span data-ttu-id="8e9c3-105">プッシュ サブスクリプションとプル サブスクリプションの詳細については、「[パブリケーションのサブスクライブ](subscribe-to-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e9c3-105">For more information about push and pull subscriptions, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="8e9c3-106">ウィザードの手順で作成されたすべてのサブスクリプションは、選択した種類になります。</span><span class="sxs-lookup"><span data-stu-id="8e9c3-106">All subscriptions created in this pass through the wizard will be of the selected type.</span></span> <span data-ttu-id="8e9c3-107">両方の種類のサブスクリプションを作成するには、ウィザードを 2 回実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e9c3-107">To create subscriptions of both types, you must run the wizard twice.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e9c3-108">サブスクリプションの種類は、作成後に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="8e9c3-108">Subscription type cannot be changed after a subscription is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e9c3-109">参照</span><span class="sxs-lookup"><span data-stu-id="8e9c3-109">See Also</span></span>  
 <span data-ttu-id="8e9c3-110">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="8e9c3-110">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="8e9c3-111">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="8e9c3-111">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="8e9c3-112">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="8e9c3-112">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
