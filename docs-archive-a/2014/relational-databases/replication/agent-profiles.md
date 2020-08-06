---
title: '[エージェント プロファイル] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofiles.f1
helpviewer_keywords:
- Agent Profiles dialog box
ms.assetid: 0422e99c-e688-419b-bb4c-c7bebeef1d8d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7584670088da1ac7a9c81f1f8f0cbdce8b040c7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634418"
---
# <a name="agent-profiles"></a><span data-ttu-id="eca0f-102">[エージェント プロファイル]</span><span class="sxs-lookup"><span data-stu-id="eca0f-102">Agent Profiles</span></span>
  <span data-ttu-id="eca0f-103">**[エージェント プロファイル]** ダイアログ ボックスを使用すると、エージェント プロファイルを管理できます。</span><span class="sxs-lookup"><span data-stu-id="eca0f-103">Use the **Agent Profiles** dialog box to manage agent profiles.</span></span> <span data-ttu-id="eca0f-104">エージェント プロファイルを利用すると、各エージェントの実行時パラメーターを容易に管理できます。</span><span class="sxs-lookup"><span data-stu-id="eca0f-104">Agent profiles provide a convenient way to manage the runtime parameters for each agent.</span></span> <span data-ttu-id="eca0f-105">それぞれのエージェントは既定のプロファイルを持ちます。一部のエージェントには、追加の定義済みプロファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eca0f-105">Each agent has a default profile, and some agents have additional predefined profiles.</span></span> <span data-ttu-id="eca0f-106">たとえば、マージ エージェントには、低帯域幅接続の "低速リンク" プロファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eca0f-106">For example, the Merge Agent has a "slow link" profile designed for low bandwidth connections.</span></span> <span data-ttu-id="eca0f-107">ほとんどのアプリケーションでは定義済みのプロファイルで十分ですが、ユーザー定義プロファイルを作成して、エージェントの動作をカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="eca0f-107">Predefined profiles are sufficient for most applications, but you can also create user-defined profiles, allowing you to customize agent behavior.</span></span>  
  
## <a name="options"></a><span data-ttu-id="eca0f-108">オプション</span><span class="sxs-lookup"><span data-stu-id="eca0f-108">Options</span></span>  
 <span data-ttu-id="eca0f-109">**[ページの選択]**</span><span class="sxs-lookup"><span data-stu-id="eca0f-109">**Select a page**</span></span>  
 <span data-ttu-id="eca0f-110">左側のペインでエージェントを選択すると、エージェントのプロファイルが右側のペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="eca0f-110">Select an agent in the left pane, and the profiles for the agent are displayed in the right pane.</span></span>  
  
 <span data-ttu-id="eca0f-111">**[新規の既定]**</span><span class="sxs-lookup"><span data-stu-id="eca0f-111">**Default for New**</span></span>  
 <span data-ttu-id="eca0f-112">特定の種類のエージェントに対してジョブを作成するときに使用するプロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="eca0f-112">Select the profile that will be used when jobs are created for an agent of a given type.</span></span> <span data-ttu-id="eca0f-113">たとえば、マージ パブリケーションに対していくつかのサブスクリプションを作成する場合、選択されたプロファイルが各サブスクリプションのマージ エージェント ジョブで使用されます。</span><span class="sxs-lookup"><span data-stu-id="eca0f-113">For example, if you create a number of subscriptions to a merge publication, the Merge Agent job for each subscription will use the profile selected.</span></span> <span data-ttu-id="eca0f-114">既存のジョブのプロファイルを変更するには、プロファイルを選択し、 **[既存のエージェントの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca0f-114">If you want to change the profile for existing jobs, select a profile, and then click **Change Existing Agents**.</span></span>  
  
 <span data-ttu-id="eca0f-115">**Name**</span><span class="sxs-lookup"><span data-stu-id="eca0f-115">**Name**</span></span>  
 <span data-ttu-id="eca0f-116">プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="eca0f-116">The name of the profile.</span></span>  
  
 <span data-ttu-id="eca0f-117">**Type**</span><span class="sxs-lookup"><span data-stu-id="eca0f-117">**Type**</span></span>  
 <span data-ttu-id="eca0f-118">プロファイルの種類です。 **[ユーザー]** \(ユーザー定義) または **[システム]** (定義済み) を選択します。</span><span class="sxs-lookup"><span data-stu-id="eca0f-118">The type of profile: **User** (user-defined) or **System** (predefined).</span></span>  
  
 <span data-ttu-id="eca0f-119">**[プロパティ] (...)**</span><span class="sxs-lookup"><span data-stu-id="eca0f-119">**Properties (...)**</span></span>  
 <span data-ttu-id="eca0f-120">クリックすると、エージェント プロファイルの各パラメーターに使用されている値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eca0f-120">Click to view the values used for each parameter in the agent profile.</span></span>  
  
 <span data-ttu-id="eca0f-121">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="eca0f-121">**New**</span></span>  
 <span data-ttu-id="eca0f-122">クリックすると、新しいプロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="eca0f-122">Click to create a new profile.</span></span>  
  
 <span data-ttu-id="eca0f-123">**削除**</span><span class="sxs-lookup"><span data-stu-id="eca0f-123">**Delete**</span></span>  
 <span data-ttu-id="eca0f-124">ユーザー定義プロファイルを削除するには、プロファイルを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca0f-124">Select a user-defined profile, and then click **Delete** to delete that profile.</span></span> <span data-ttu-id="eca0f-125">定義済みのプロファイルは削除できません。</span><span class="sxs-lookup"><span data-stu-id="eca0f-125">Predefined profiles cannot be deleted.</span></span>  
  
 <span data-ttu-id="eca0f-126">**[既存のエージェントの変更]**</span><span class="sxs-lookup"><span data-stu-id="eca0f-126">**Change Existing Agents**</span></span>  
 <span data-ttu-id="eca0f-127">特定の種類のエージェントのすべての既存のジョブで、選択したプロファイルを使用する場合は、プロファイルを選択して **[既存のエージェントの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca0f-127">Select a profile, and then click **Change Existing Agents** to specify that all existing jobs for an agent of a given type should use the selected profile.</span></span> <span data-ttu-id="eca0f-128">たとえば、マージ パブリケーションに対して作成したサブスクリプションがいくつかあり、これらの各サブスクリプションのマージ エージェント ジョブで **低速リンク エージェント プロファイル**を使用するようにプロファイルを変更するには、目的のプロファイルを選択し、 **[既存のエージェントの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca0f-128">For example, if you have created a number of subscriptions to a merge publication, and you want to change the profile to specify that the Merge Agent job for each of these subscriptions should use the **Slow link agent profile**, select that profile, and then click **Change Existing Agents**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca0f-129">参照</span><span class="sxs-lookup"><span data-stu-id="eca0f-129">See Also</span></span>  
 <span data-ttu-id="eca0f-130">[レプリケーション エージェント プロファイルの操作](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="eca0f-130">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="eca0f-131">[レプリケーション エージェントの概要](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="eca0f-131">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="eca0f-132">レプリケーション エージェント プロファイル</span><span class="sxs-lookup"><span data-stu-id="eca0f-132">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
