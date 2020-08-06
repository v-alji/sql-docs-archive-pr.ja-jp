---
title: '[新しいエージェント プロファイル] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1d7848e44585fd35a5b5a33cf431e15de96c9375
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721344"
---
# <a name="new-agent-profile"></a><span data-ttu-id="9d47f-102">[新しいエージェント プロファイル]</span><span class="sxs-lookup"><span data-stu-id="9d47f-102">New Agent Profile</span></span>
  <span data-ttu-id="9d47f-103">**[新しいエージェント プロファイル]** ダイアログ ボックスを使用すると、新しいプロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9d47f-103">Use the **New Agent Profile** dialog box to create a new profile.</span></span> <span data-ttu-id="9d47f-104">新しいプロファイルは常に既存のプロファイルに基づきますが、アプリケーション要件に一致するように変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="9d47f-104">New profiles are always based on existing profiles, but they can be modified to meet application requirements.</span></span> <span data-ttu-id="9d47f-105">プロファイルを作成したら、 **[エージェント プロファイル]** ダイアログ ボックスで、既存のエージェントおよび今後のエージェントのジョブに適用できます。</span><span class="sxs-lookup"><span data-stu-id="9d47f-105">After a profile has been created, it can be applied to existing and future agent jobs in the **Agent Profiles** dialog box.</span></span> <span data-ttu-id="9d47f-106">エージェントのパラメーター値は、[\<**AgentProfileName> のプロパティ]\*\* ダイアログ ボックスで編集できます。</span><span class="sxs-lookup"><span data-stu-id="9d47f-106">Agent parameter values can be edited in the \<**AgentProfileName> Properties\*\* dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9d47f-107">Options</span><span class="sxs-lookup"><span data-stu-id="9d47f-107">Options</span></span>  
 <span data-ttu-id="9d47f-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="9d47f-108">**Name**</span></span>  
 <span data-ttu-id="9d47f-109">プロファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="9d47f-109">Enter a name for the profile.</span></span>  
  
 <span data-ttu-id="9d47f-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="9d47f-110">**Description**</span></span>  
 <span data-ttu-id="9d47f-111">プロファイルの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="9d47f-111">Enter a description for the profile.</span></span>  
  
 <span data-ttu-id="9d47f-112">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="9d47f-112">**Parameter**</span></span>  
 <span data-ttu-id="9d47f-113">プロファイルに含まれるエージェント パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="9d47f-113">The agent parameters included in the profile.</span></span> <span data-ttu-id="9d47f-114">新しいプロファイルが基づくプロファイルは、必ずしもパラメーターごとの値を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9d47f-114">The profile on which the new profile is based does not necessarily specify a value for each parameter.</span></span> <span data-ttu-id="9d47f-115">指定されたエージェントで有効なパラメーターをすべて表示するには、 **[このプロファイルに使用されているパラメーターのみ表示する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="9d47f-115">To see all parameters that are valid for a given agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="9d47f-116">各パラメーターの詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d47f-116">For descriptions of each parameter, see:</span></span>  
  
-   [<span data-ttu-id="9d47f-117">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="9d47f-117">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
-   [<span data-ttu-id="9d47f-118">レプリケーション ログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="9d47f-118">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="9d47f-119">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="9d47f-119">Replication Distribution Agent</span></span>](agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="9d47f-120">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="9d47f-120">Replication Merge Agent</span></span>](agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="9d47f-121">レプリケーション キュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="9d47f-121">Replication Queue Reader Agent</span></span>](agents/replication-queue-reader-agent.md)  
  
 <span data-ttu-id="9d47f-122">**既定値**</span><span class="sxs-lookup"><span data-stu-id="9d47f-122">**Default Value**</span></span>  
 <span data-ttu-id="9d47f-123">各エージェント パラメーターの既定値です。</span><span class="sxs-lookup"><span data-stu-id="9d47f-123">The default value for each agent parameter.</span></span>  
  
 <span data-ttu-id="9d47f-124">**Value**</span><span class="sxs-lookup"><span data-stu-id="9d47f-124">**Value**</span></span>  
 <span data-ttu-id="9d47f-125">新しいプロファイルが基づくプロファイル内のパラメーターに対して指定された値です。</span><span class="sxs-lookup"><span data-stu-id="9d47f-125">The value specified for the parameter in the profile on which the new profile is based.</span></span> <span data-ttu-id="9d47f-126">パラメーター値を変更するには、このフィールドを編集します。</span><span class="sxs-lookup"><span data-stu-id="9d47f-126">Edit this field for any parameter values you want to change.</span></span>  
  
 <span data-ttu-id="9d47f-127">**[このプロファイルに使用されているパラメーターのみ表示する]**</span><span class="sxs-lookup"><span data-stu-id="9d47f-127">**Show only parameters used in this profile**</span></span>  
 <span data-ttu-id="9d47f-128">指定されたエージェントに有効なパラメーターをすべて表示するにはオフにします。</span><span class="sxs-lookup"><span data-stu-id="9d47f-128">Clear to show all valid parameters for a given agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d47f-129">参照</span><span class="sxs-lookup"><span data-stu-id="9d47f-129">See Also</span></span>  
 <span data-ttu-id="9d47f-130">[レプリケーション エージェント プロファイルの操作](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="9d47f-130">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="9d47f-131">[レプリケーション エージェントの概要](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="9d47f-131">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="9d47f-132">レプリケーション エージェント プロファイル</span><span class="sxs-lookup"><span data-stu-id="9d47f-132">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
