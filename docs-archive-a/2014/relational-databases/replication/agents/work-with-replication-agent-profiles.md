---
title: レプリケーション エージェント プロファイルを操作する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], agents and profiles
- replication agent profiles [SQL Server]
- agents [SQL Server replication], profiles
- profiles [SQL Server], replication agents
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc20451edfb1096fca7e468effb14df78b51f758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632401"
---
# <a name="work-with-replication-agent-profiles"></a><span data-ttu-id="1528e-102">レプリケーション エージェント プロファイルを操作する</span><span class="sxs-lookup"><span data-stu-id="1528e-102">Work with Replication Agent Profiles</span></span>
  <span data-ttu-id="1528e-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、レプリケーション エージェント プロファイルを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1528e-103">This topic describes how to work with Replication Agent Profiles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="1528e-104">各レプリケーション エージェントの動作は、エージェント プロファイルで設定できる一連のパラメーターによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-104">The behavior of each replication agent is controlled by a set of parameters that can be set through agent profiles.</span></span> <span data-ttu-id="1528e-105">各エージェントには既定のプロファイルがあり、その一部には事前に定義された追加のプロファイルがあります。1 つのエージェントに対しては、1 つのプロファイルのみがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="1528e-105">Each agent has a default profile, and some have additional predefined profiles; at a given time, only one profile is active for an agent.</span></span>  
  
 <span data-ttu-id="1528e-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1528e-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1528e-107">**レプリケーション エージェント プロファイルを操作するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="1528e-107">**To work with Replication Agent Profiles, using:**</span></span>  
  
     [<span data-ttu-id="1528e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1528e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
    -   <span data-ttu-id="1528e-109">[エージェント プロファイル] ダイアログ ボックスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="1528e-109">Access the Agent Profiles dialog box</span></span>  
  
    -   <span data-ttu-id="1528e-110">エージェントのプロファイルの指定</span><span class="sxs-lookup"><span data-stu-id="1528e-110">Specify a profile for an agent</span></span>  
  
    -   <span data-ttu-id="1528e-111">プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="1528e-111">Create a profile</span></span>  
  
    -   <span data-ttu-id="1528e-112">プロファイルの変更</span><span class="sxs-lookup"><span data-stu-id="1528e-112">Modify a profile</span></span>  
  
    -   <span data-ttu-id="1528e-113">プロファイルの削除</span><span class="sxs-lookup"><span data-stu-id="1528e-113">Delete a profile</span></span>  
  
     [<span data-ttu-id="1528e-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1528e-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
    -   <span data-ttu-id="1528e-115">プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="1528e-115">Create a profile</span></span>  
  
    -   <span data-ttu-id="1528e-116">プロファイルの変更</span><span class="sxs-lookup"><span data-stu-id="1528e-116">Modify a profile</span></span>  
  
    -   <span data-ttu-id="1528e-117">プロファイルの削除</span><span class="sxs-lookup"><span data-stu-id="1528e-117">Delete a profile</span></span>  
  
    -   <span data-ttu-id="1528e-118">同期時のエージェント プロファイルの使用</span><span class="sxs-lookup"><span data-stu-id="1528e-118">Use agent profiles during synchronization</span></span>  
  
    -   <span data-ttu-id="1528e-119">Transact-SQL の例</span><span class="sxs-lookup"><span data-stu-id="1528e-119">Transact-SQL example</span></span>  
  
     [<span data-ttu-id="1528e-120">レプリケーション管理オブジェクト (Replication Management Objects)</span><span class="sxs-lookup"><span data-stu-id="1528e-120">Replication Management Objects</span></span>](#RMOProcedure)  
  
    -   <span data-ttu-id="1528e-121">プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="1528e-121">Create a profile</span></span>  
  
    -   <span data-ttu-id="1528e-122">プロファイルの変更</span><span class="sxs-lookup"><span data-stu-id="1528e-122">Modify a profile</span></span>  
  
    -   <span data-ttu-id="1528e-123">プロファイルの削除</span><span class="sxs-lookup"><span data-stu-id="1528e-123">Delete a profile</span></span>  
  
-   <span data-ttu-id="1528e-124">**補足情報:** [エージェント パラメーターを変更した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1528e-124">**Follow Up:**  [After Changing Agent Parameters](#FollowUp)</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1528e-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1528e-125">Using SQL Server Management Studio</span></span>  
  
###  <a name="to-access-the-agent-profiles-dialog-box-from-sql-server-management-studio"></a><a name="Access_SSMS"></a> <span data-ttu-id="1528e-126">SQL Server Management Studio から [エージェント プロファイル] ダイアログ ボックスにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="1528e-126">To access the Agent Profiles dialog box from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="1528e-127">**[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページで、 **[プロファイルの既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-127">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click **Profile Defaults**.</span></span>  
  
#### <a name="to-access-the-agent-profiles-dialog-box-from-replication-monitor"></a><span data-ttu-id="1528e-128">レプリケーション モニターから [エージェント プロファイル] ダイアログ ボックスにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="1528e-128">To access the Agent Profiles dialog box from Replication Monitor</span></span>  
  
-   <span data-ttu-id="1528e-129">すべてのエージェントに対するダイアログ ボックスを開くには、パブリッシャーを右クリックし、 **[エージェント プロファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-129">To open the dialog box for all agents, right-click a Publisher, and then click **Agent Profiles**.</span></span>  
  
-   <span data-ttu-id="1528e-130">単一のエージェントに対するダイアログ ボックスを開くには</span><span class="sxs-lookup"><span data-stu-id="1528e-130">To open the dialog box for a single agent:</span></span>  
  
    1.  <span data-ttu-id="1528e-131">レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-131">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
    2.  <span data-ttu-id="1528e-132">ディストリビューション エージェントとマージ エージェントのプロファイルの場合は、 **[すべてのサブスクリプション]** タブでサブスクリプションを右クリックし、 **[エージェント プロファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-132">For Distribution Agent and Merge Agent profiles, right-click a subscription on the **All Subscriptions** tab, and then click **Agent Profile**.</span></span> <span data-ttu-id="1528e-133">その他のエージェントの場合は、 **[エージェント]** タブでエージェントを右クリックし、 **[エージェント プロファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-133">For other agents, right-click the agent on the **Agents** tab, and then click **Agent Profile**.</span></span>  
  
###  <a name="to-specify-a-profile-for-an-agent"></a><a name="Specify_SSMS"></a> <span data-ttu-id="1528e-134">エージェントのプロファイルを指定するには</span><span class="sxs-lookup"><span data-stu-id="1528e-134">To specify a profile for an agent</span></span>  
  
1.  <span data-ttu-id="1528e-135">**[エージェント プロファイル]** ダイアログ ボックスにエージェントのプロファイルが複数表示されている場合は、エージェントを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="1528e-135">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="1528e-136">**[エージェント プロファイル]** グリッドの **[新規の既定]** 列でプロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="1528e-136">Select a profile in the **Default for new** column of the **Agent profiles** grid.</span></span> <span data-ttu-id="1528e-137">既定では、プロファイルは、新しいパブリケーションとサブスクリプションに対するエージェントにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-137">By default, the profile is only applied to agents for new publications and subscriptions.</span></span>  
  
3.  <span data-ttu-id="1528e-138">既存のパブリケーションまたはサブスクリプションに対して選択された種類のすべてのエージェントがこのプロファイルを使用するように指定するには、 **[既存のエージェントの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-138">To specify that all agents of the selected type for existing publications or subscriptions should use this profile, click **Change existing agents**.</span></span>  
  
###  <a name="to-view-and-edit-the-parameters-associated-with-a-profile"></a><a name="Modify_SSMS"></a> <span data-ttu-id="1528e-139">プロファイルに関連付けられたパラメーターを表示および編集するには</span><span class="sxs-lookup"><span data-stu-id="1528e-139">To view and edit the parameters associated with a profile</span></span>  
  
1.  <span data-ttu-id="1528e-140">**[エージェント プロファイル]** ダイアログ ボックスにエージェントのプロファイルが複数表示されている場合は、エージェントを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="1528e-140">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="1528e-141">プロファイルの横にあるプロパティ ボタン **[...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-141">Click the properties button (**...**) next to a profile.</span></span>  
  
3.  <span data-ttu-id="1528e-142">**[\<ProfileName> プロファイルのプロパティ]** ダイアログ ボックスにパラメーターと値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-142">View the parameters and values in the **\<ProfileName> Profile Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="1528e-143">ユーザー定義プロファイルのパラメーターは編集できます。事前に定義されているシステム プロファイルのパラメーターは編集できません。</span><span class="sxs-lookup"><span data-stu-id="1528e-143">Parameters in user-defined profiles can be edited; parameters in predefined system profiles cannot.</span></span>  
  
    -   <span data-ttu-id="1528e-144">1 つのエージェントに対するすべてのパラメーターを表示するには、 **[このプロファイルに使用されているパラメーターのみ表示する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="1528e-144">To view all parameters for an agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="1528e-145">エージェント パラメーターの詳細については、このトピックの末尾のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1528e-145">For information about agent parameters, see the links at the end of this topic.</span></span>  
  
4.  <span data-ttu-id="1528e-146">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-146">Click **Close**.</span></span>  
  
###  <a name="to-create-a-user-defined-profile"></a><a name="Create_SSMS"></a> <span data-ttu-id="1528e-147">ユーザー定義プロファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="1528e-147">To create a user-defined profile</span></span>  
  
1.  <span data-ttu-id="1528e-148">**[エージェント プロファイル]** ダイアログ ボックスにエージェントのプロファイルが複数表示されている場合は、エージェントを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="1528e-148">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="1528e-149">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-149">Click **New**.</span></span>  
  
3.  <span data-ttu-id="1528e-150">**[新しいエージェント プロファイル]** 初期化ダイアログ ボックスで、新しいプロファイルの基となる既存のプロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="1528e-150">In the **New Agent Profile** initialization dialog box, select an existing profile on which to base the new profile.</span></span>  
  
4.  <span data-ttu-id="1528e-151">**[新しいエージェント プロファイル]** ダイアログ ボックスで、 **[名前]** と **[説明]** ボックスに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="1528e-151">In the **New Agent Profile** dialog box, enter values in the **Name** and **Description** text boxes.</span></span>  
  
5.  <span data-ttu-id="1528e-152">パラメーターを変更してプロファイルを調整します。</span><span class="sxs-lookup"><span data-stu-id="1528e-152">Modify parameters to tailor the profile.</span></span> <span data-ttu-id="1528e-153">1 つのエージェントに対するすべてのパラメーターを表示するには、 **[このプロファイルに使用されているパラメーターのみ表示する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="1528e-153">To view all parameters for an agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="1528e-154">エージェント パラメーターの詳細については、このトピックの末尾のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1528e-154">For information about agent parameters, see the links at the end of this topic.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="to-delete-a-user-defined-profile"></a><a name="Delete_SSMS"></a> <span data-ttu-id="1528e-155">ユーザー定義プロファイルを削除するには</span><span class="sxs-lookup"><span data-stu-id="1528e-155">To delete a user-defined profile</span></span>  
  
1.  <span data-ttu-id="1528e-156">**[エージェント プロファイル]** ダイアログ ボックスにエージェントのプロファイルが複数表示されている場合は、エージェントを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="1528e-156">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="1528e-157">1 つのプロファイルが 1 つ以上のエージェントに関連付けられている場合は、これらのエージェントに対するプロファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="1528e-157">If a profile is associated with one or more agents, change the profile for those agents:</span></span>  
  
    1.  <span data-ttu-id="1528e-158">**[エージェント プロファイル]** グリッドで別のプロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="1528e-158">Select a different profile in the **Agent profiles** grid.</span></span>  
  
    2.  <span data-ttu-id="1528e-159">**[既存のエージェントの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-159">Click **Change existing agents**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="1528e-160">これによって、削除したいプロファイルを使用しているエージェントだけではなく、既存のパブリケーションまたはサブスクリプションに対して選択された種類のすべてのエージェントに対するプロファイルが変更されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-160">This will change the profile for all agents of the selected type for existing publications or subscriptions, not only the ones using the profile you want to delete.</span></span>  
  
3.  <span data-ttu-id="1528e-161">削除するプロファイルを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-161">Select the profile you want to delete, and then click **Delete**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1528e-162">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1528e-162">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_tsql"></a> <span data-ttu-id="1528e-163">新しいエージェント プロファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="1528e-163">To create a new agent profile</span></span>  
  
1.  <span data-ttu-id="1528e-164">ディストリビューターで、[sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-164">At the Distributor, execute [sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql).</span></span> <span data-ttu-id="1528e-165">を指定し、には1を、には次のいずれかの値を指定し **@name** **1** **@profile_type** **@agent_type** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-165">Specify **@name**, a value of **1** for **@profile_type**, and one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="1528e-166">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-166">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-167">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-167">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-168">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-168">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-169">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-169">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-170">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-170">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="1528e-171">このプロファイルがこの種類のレプリケーション エージェントの新しい既定のプロファイルになる場合、 **@profile_type** に **@default**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1528e-171">If this profile will become the new default profile for its type of replication agent, specify a value of **1** for **@default**.</span></span> <span data-ttu-id="1528e-172">新しいプロファイルの識別子は、output パラメーターを使用して返され **@profile_id** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-172">The identifier for the new profile is returned using the **@profile_id** output parameter.</span></span> <span data-ttu-id="1528e-173">これにより、特定の種類のエージェントの既定のプロファイルに基づいたプロファイル パラメーターのセットを備えた、新しいプロファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-173">This creates a new profile with a set of profile parameters based on the default profile for the given agent type.</span></span>  
  
2.  <span data-ttu-id="1528e-174">新しいプロファイルを作成したら、既定のパラメーターを追加、削除、変更してプロファイルをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="1528e-174">After the new profile has been created, add, remove, or modify the default parameters to customize the profile.</span></span>  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_tsql"></a> <span data-ttu-id="1528e-175">既存のエージェント プロファイルを変更するには</span><span class="sxs-lookup"><span data-stu-id="1528e-175">To modify an existing agent profile</span></span>  
  
1.  <span data-ttu-id="1528e-176">ディストリビューターで、[sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-176">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="1528e-177">に次のいずれかの値を指定し **@agent_type** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-177">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="1528e-178">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-178">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-179">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-179">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-180">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-180">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-181">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-181">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-182">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-182">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="1528e-183">これにより、指定された種類のエージェントのプロファイルがすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-183">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="1528e-184">変更するプロファイルの結果セットで **profile_id** の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="1528e-184">Note the value of **profile_id** in the result set for the profile to change.</span></span>  
  
2.  <span data-ttu-id="1528e-185">ディストリビューターで、[sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-185">At the Distributor, execute [sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql).</span></span> <span data-ttu-id="1528e-186">手順 1. で指定したプロファイル id を指定し **@profile_id** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-186">Specify the profile identifier from step 1 for **@profile_id**.</span></span> <span data-ttu-id="1528e-187">これにより、プロファイルのすべてのパラメーターが返されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-187">This returns all parameters for the profile.</span></span> <span data-ttu-id="1528e-188">変更するパラメーター、またはプロファイルから削除するパラメーターの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="1528e-188">Note the name of any parameters to modify or remove from the profile.</span></span>  
  
3.  <span data-ttu-id="1528e-189">プロファイル内のパラメーターの値を変更するには、[sp_change_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-189">To change the value of a parameter in a profile, execute [sp_change_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql).</span></span> <span data-ttu-id="1528e-190">手順 1. で指定したプロファイル id をに指定し、 **@profile_id** 変更するパラメーターの名前をに指定し **@property** ます。また、のパラメーターに新しい値を指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-190">Specify the profile identifier from step 1 for **@profile_id**, the name of the parameter to change for **@property**, and a new value for the parameter for **@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1528e-191">既存のエージェント プロファイルを変更して、エージェントの既定のプロファイルにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1528e-191">You cannot change an existing agent profile to become the default profile for an agent.</span></span> <span data-ttu-id="1528e-192">代わりに、前の手順に示すように、新しいプロファイルを既定のプロファイルとして作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1528e-192">You must instead create a new profile as the default profile, as shown in the previous procedure.</span></span>  
  
4.  <span data-ttu-id="1528e-193">プロファイルからパラメーターを削除するには、[sp_drop_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-193">To remove a parameter from a profile, execute [sp_drop_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql).</span></span> <span data-ttu-id="1528e-194">手順 1. で指定したプロファイル id をに指定し、を **@profile_id** 削除するパラメーターの名前を指定し **@parameter_name** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-194">Specify the profile identifier from step 1 for **@profile_id** and the name of the parameter to remove for **@parameter_name**.</span></span>  
  
5.  <span data-ttu-id="1528e-195">プロファイルに新しいパラメーターを追加するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1528e-195">To add a new parameter to a profile, you must do the following:</span></span>  
  
    -   <span data-ttu-id="1528e-196">ディストリビューターで [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) テーブルに対してクエリを実行して、各種類のエージェントに設定できるプロファイル パラメーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="1528e-196">Query the [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) table at the Distributor to determine which profile parameters can be set for each agent type.</span></span>  
  
    -   <span data-ttu-id="1528e-197">ディストリビューターで、[sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-197">At the Distributor, execute [sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql).</span></span> <span data-ttu-id="1528e-198">手順 1. で指定したプロファイル識別子、に **@profile_id** 追加する有効なパラメーターの名前、 **@parameter_name** およびのパラメーターの値を指定し **@parameter_value** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-198">Specify the profile identifier from step 1 for **@profile_id**, the name of a valid parameter to add for **@parameter_name**, and the value of the parameter for **@parameter_value**.</span></span>  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_tsql"></a> <span data-ttu-id="1528e-199">エージェント プロファイルを削除するには</span><span class="sxs-lookup"><span data-stu-id="1528e-199">To delete an agent profile</span></span>  
  
1.  <span data-ttu-id="1528e-200">ディストリビューターで、[sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-200">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="1528e-201">に次のいずれかの値を指定し **@agent_type** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-201">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="1528e-202">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-202">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-203">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-203">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-204">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-204">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-205">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-205">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-206">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-206">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="1528e-207">これにより、指定された種類のエージェントのプロファイルがすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-207">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="1528e-208">削除するプロファイルの結果セットで **profile_id** の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="1528e-208">Note the value of **profile_id** in the result set for the profile to remove.</span></span>  
  
2.  <span data-ttu-id="1528e-209">ディストリビューターで、[sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-209">At the Distributor, execute [sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql).</span></span> <span data-ttu-id="1528e-210">手順 1. で指定したプロファイル id を指定し **@profile_id** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-210">Specify the profile identifier from step 1 for **@profile_id**.</span></span>  
  
###  <a name="to-use-agent-profiles-during-synchronization"></a><a name="Synch_tsql"></a> <span data-ttu-id="1528e-211">同期の際にエージェント プロファイルを使用するには</span><span class="sxs-lookup"><span data-stu-id="1528e-211">To use agent profiles during synchronization</span></span>  
  
1.  <span data-ttu-id="1528e-212">ディストリビューターで、[sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1528e-212">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="1528e-213">に次のいずれかの値を指定し **@agent_type** ます。</span><span class="sxs-lookup"><span data-stu-id="1528e-213">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="1528e-214">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-214">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-215">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-215">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-216">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-216">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-217">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-217">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="1528e-218">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1528e-218">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="1528e-219">これにより、指定された種類のエージェントのプロファイルがすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-219">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="1528e-220">`profile_name`使用するプロファイルの結果セットのの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="1528e-220">Note the value of `profile_name` in the result set for the profile to use.</span></span>  
  
2.  <span data-ttu-id="1528e-221">エージェントがエージェントジョブから起動された場合は、エージェントを起動するジョブステップを編集して、 `profile_name` 手順 1. で取得したの値を **-ProfileName**コマンドラインパラメーターの後に指定します。</span><span class="sxs-lookup"><span data-stu-id="1528e-221">If the agent is started from an agent job, edit the job step that starts the agent to specify the value of `profile_name` obtained in step 1 after the **-ProfileName** command-line parameter.</span></span> <span data-ttu-id="1528e-222">詳細については、「[View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md)」(レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する &#40;SQL Server Management Studio&#41;) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1528e-222">For more information, see [View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md).</span></span>  
  
3.  <span data-ttu-id="1528e-223">コマンドプロンプトからエージェントを起動する場合は、 `profile_name` 手順 1. で取得したの値を **-ProfileName**コマンドラインパラメーターの後に指定します。</span><span class="sxs-lookup"><span data-stu-id="1528e-223">When starting the agent from the command prompt, specify the value of `profile_name` obtained in step 1 after the **-ProfileName** command-line parameter.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1528e-224">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1528e-224">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1528e-225">次の例では、 **custom_merge**という名前のマージ エージェント用のカスタム プロファイルを作成して、 **-UploadReadChangesPerBatch** パラメーターの値を変更し、 **-ExchangeType** パラメーターを新しく追加して、作成されたプロファイルに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="1528e-225">This example creates a custom profile for the Merge Agent named **custom_merge**, changes the value of the **-UploadReadChangesPerBatch** parameter, adds a new **-ExchangeType** parameter, and returns information on the profile that is created.</span></span>  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../snippets/tsql/SQL15/replication/howto/tsql/createperfparammerge.sql#sp_addagentprofileparam)]  
  
##  <a name="using-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="1528e-226">RMO の使用</span><span class="sxs-lookup"><span data-stu-id="1528e-226">Using RMO</span></span>  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_RMO"></a> <span data-ttu-id="1528e-227">新しいエージェント プロファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="1528e-227">To create a new agent profile</span></span>  
  
1.  <span data-ttu-id="1528e-228"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスのインスタンスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1528e-228">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1528e-229"><xref:Microsoft.SqlServer.Replication.AgentProfile> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1528e-229">Create an instance of the <xref:Microsoft.SqlServer.Replication.AgentProfile> class.</span></span>  
  
3.  <span data-ttu-id="1528e-230">オブジェクトの次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1528e-230">Set the following properties on the object:</span></span>  
  
    -   <span data-ttu-id="1528e-231"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="1528e-231"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - the name for the profile.</span></span>  
  
    -   <span data-ttu-id="1528e-232"><xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - プロファイルを作成するレプリケーション エージェントの種類を指定する <xref:Microsoft.SqlServer.Replication.AgentType> 値。</span><span class="sxs-lookup"><span data-stu-id="1528e-232"><xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - an <xref:Microsoft.SqlServer.Replication.AgentType> value that specifies the type of replication agent for which the profile is being created.</span></span>  
  
    -   <span data-ttu-id="1528e-233"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - 手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="1528e-233"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
    -   <span data-ttu-id="1528e-234">(省略可) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - プロファイルの説明。</span><span class="sxs-lookup"><span data-stu-id="1528e-234">(Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - a description of the profile.</span></span>  
  
    -   <span data-ttu-id="1528e-235">(省略可) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> - この <xref:Microsoft.SqlServer.Replication.AgentType> の新しいエージェント ジョブすべてが、既定でこのプロファイルを使用する場合、このプロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1528e-235">(Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> - set this property to `true` if all new agent jobs for this <xref:Microsoft.SqlServer.Replication.AgentType> will use this profile by default.</span></span>  
  
4.  <span data-ttu-id="1528e-236"><xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> メソッドを呼び出し、サーバーにプロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1528e-236">Call the <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> method to create the profile on the server.</span></span>  
  
5.  <span data-ttu-id="1528e-237">サーバーにプロファイルが作成されたら、レプリケーション エージェントのパラメーター値を追加、削除、変更することで、プロファイルをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="1528e-237">Once the profile exists on the server, you can customize it by adding, removing, or changing the values of replication agent parameters.</span></span>  
  
6.  <span data-ttu-id="1528e-238">既存のレプリケーション エージェント ジョブにプロファイルを割り当てるには、 <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1528e-238">To assign the profile to an existing replication agent job, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> method.</span></span> <span data-ttu-id="1528e-239">ディストリビューション データベースの名前を *distributionDBName* に渡し、ジョブの ID を *agentID*に渡します。</span><span class="sxs-lookup"><span data-stu-id="1528e-239">Pass the name of the distribution database for *distributionDBName* and the ID of the job for *agentID*.</span></span>  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_RMO"></a> <span data-ttu-id="1528e-240">既存のエージェント プロファイルを変更するには</span><span class="sxs-lookup"><span data-stu-id="1528e-240">To modify an existing agent profile</span></span>  
  
1.  <span data-ttu-id="1528e-241"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスのインスタンスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1528e-241">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1528e-242"><xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1528e-242">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="1528e-243">手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="1528e-243">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object created in step 1.</span></span>  
  
3.  <span data-ttu-id="1528e-244"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1528e-244">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="1528e-245">このメソッドが `false` を返す場合、ディストリビューターが存在するかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1528e-245">If this method returns `false`, verify that the Distributor exists.</span></span>  
  
4.  <span data-ttu-id="1528e-246"><xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1528e-246">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> method.</span></span> <span data-ttu-id="1528e-247">特定の種類のレプリケーション エージェントのプロファイルが返されるように、 <xref:Microsoft.SqlServer.Replication.AgentType> 値を渡します。</span><span class="sxs-lookup"><span data-stu-id="1528e-247">Pass an <xref:Microsoft.SqlServer.Replication.AgentType> value to narrow down the returned profiles to a specific type of replication agent.</span></span>  
  
5.  <span data-ttu-id="1528e-248">返された <xref:Microsoft.SqlServer.Replication.AgentProfile> から目的の <xref:System.Collections.ArrayList>オブジェクトを取得します。オブジェクトの <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> プロパティはプロファイル名と同じです。</span><span class="sxs-lookup"><span data-stu-id="1528e-248">Get the desired <xref:Microsoft.SqlServer.Replication.AgentProfile> object from the returned <xref:System.Collections.ArrayList>, where the <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> property of the object matches the profile name.</span></span>  
  
6.  <span data-ttu-id="1528e-249"><xref:Microsoft.SqlServer.Replication.AgentProfile> の次のメソッドの 1 つを呼び出して、プロファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="1528e-249">Call one of the following methods of <xref:Microsoft.SqlServer.Replication.AgentProfile> to change the profile:</span></span>  
  
    -   <span data-ttu-id="1528e-250"><xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - サポートされるパラメーターをプロファイルに追加します。ここで、 *name* はレプリケーション エージェント パラメーターの名前、 *value* は指定する値です。</span><span class="sxs-lookup"><span data-stu-id="1528e-250"><xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - adds a supported parameter to the profile, where *name* is the name of the replication agent parameter and *value* is the specified value.</span></span> <span data-ttu-id="1528e-251">指定されたエージェントの種類でサポートされるエージェント パラメーターをすべて列挙するには、 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1528e-251">To enumerate all supported agent parameters for a given agent type, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> method.</span></span> <span data-ttu-id="1528e-252">このメソッドは、サポートされるすべてのパラメーターを表す <xref:System.Collections.ArrayList> オブジェクトの <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> を返します。</span><span class="sxs-lookup"><span data-stu-id="1528e-252">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> objects that represent all supported parameters.</span></span>  
  
    -   <span data-ttu-id="1528e-253"><xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - プロファイルから既存のパラメーターを削除します。ここで、 *name* はレプリケーション エージェント パラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="1528e-253"><xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - removes an existing parameter from the profile, where *name* is the name of the replication agent parameter.</span></span> <span data-ttu-id="1528e-254">プロファイルに定義されている現在のエージェント パラメーターをすべて列挙するには、 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1528e-254">To enumerate all current agent parameters defined for the profile, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> method.</span></span> <span data-ttu-id="1528e-255">このメソッドは、このプロファイルの既存のパラメーターを表す <xref:System.Collections.ArrayList> オブジェクトの <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> を返します。</span><span class="sxs-lookup"><span data-stu-id="1528e-255">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objects that represent the existing parameter for this profile.</span></span>  
  
    -   <span data-ttu-id="1528e-256"><xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - プロファイルの既存のパラメーターの設定を変更します。ここで、 *name* はエージェント パラメーターの名前、 *newValue* はパラメーターの変更後の値です。</span><span class="sxs-lookup"><span data-stu-id="1528e-256"><xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - changes the setting of an existing parameter in the profile, where *name* is the name of the agent parameter and *newValue* is the value to which the parameter is being changed.</span></span> <span data-ttu-id="1528e-257">プロファイルに定義されている現在のエージェント パラメーターをすべて列挙するには、 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1528e-257">To enumerate all current agent parameters defined for the profile, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> method.</span></span> <span data-ttu-id="1528e-258">このメソッドは、このプロファイルの既存のパラメーターを表す <xref:System.Collections.ArrayList> オブジェクトの <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> を返します。</span><span class="sxs-lookup"><span data-stu-id="1528e-258">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objects that represent the existing parameter for this profile.</span></span> <span data-ttu-id="1528e-259">サポートされるエージェント パラメーターの設定をすべて列挙するには、 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1528e-259">To enumerate all supported agent parameter settings, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> method.</span></span> <span data-ttu-id="1528e-260">このメソッドは、すべてのパラメーターでサポートされる値を表す <xref:System.Collections.ArrayList> オブジェクトの <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> を返します。</span><span class="sxs-lookup"><span data-stu-id="1528e-260">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> objects that represent the supported values for all parameters.</span></span>  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_RMO"></a> <span data-ttu-id="1528e-261">エージェント プロファイルを削除するには</span><span class="sxs-lookup"><span data-stu-id="1528e-261">To delete an agent profile</span></span>  
  
1.  <span data-ttu-id="1528e-262"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスのインスタンスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1528e-262">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1528e-263"><xref:Microsoft.SqlServer.Replication.AgentProfile> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1528e-263">Create an instance of the <xref:Microsoft.SqlServer.Replication.AgentProfile> class.</span></span> <span data-ttu-id="1528e-264">プロファイルの名前を <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> に設定し、手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に設定します。</span><span class="sxs-lookup"><span data-stu-id="1528e-264">Set the name of the profile for <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> and the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="1528e-265"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1528e-265">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="1528e-266">このメソッドが `false` を返す場合、指定された名前が誤っているか、プロファイルがサーバーに存在していません。</span><span class="sxs-lookup"><span data-stu-id="1528e-266">If this method returns `false`, either the specified name was incorrect or the profile does not exist on the server.</span></span>  
  
4.  <span data-ttu-id="1528e-267"><xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> プロパティが <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>に設定されていることを確認します。これは、顧客のプロファイルを表します。</span><span class="sxs-lookup"><span data-stu-id="1528e-267">Verify that the <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> property is set to <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, which indicates a customer profile.</span></span> <span data-ttu-id="1528e-268"><xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> の値が <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>であるプロファイルは削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="1528e-268">You should not remove a profile that has a value of <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> for <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>.</span></span>  
  
5.  <span data-ttu-id="1528e-269"><xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> メソッドを呼び出して、このオブジェクトで表されるユーザー定義プロファイルをサーバーから削除します。</span><span class="sxs-lookup"><span data-stu-id="1528e-269">Call the <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> method to remove the user-defined profile represented by this object from the server.</span></span>  
  
##  <a name="follow-up-after-changing-agent-parameters"></a><a name="FollowUp"></a><span data-ttu-id="1528e-270">補足情報: エージェント パラメーターを変更した後</span><span class="sxs-lookup"><span data-stu-id="1528e-270">Follow Up: After Changing Agent Parameters</span></span>  
 <span data-ttu-id="1528e-271">エージェント パラメーターの変更は、エージェントの次回起動時に反映されます。</span><span class="sxs-lookup"><span data-stu-id="1528e-271">Agent parameter changes take effect the next time the agent is started.</span></span> <span data-ttu-id="1528e-272">エージェントを継続して実行している場合は、そのエージェントを停止して再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1528e-272">If the agent runs continuously, you must stop and restart the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1528e-273">参照</span><span class="sxs-lookup"><span data-stu-id="1528e-273">See Also</span></span>  
 <span data-ttu-id="1528e-274">[レプリケーション エージェント プロファイル](replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="1528e-274">[Replication Agent Profiles](replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="1528e-275">[Replication Snapshot Agent](replication-snapshot-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1528e-275">[Replication Snapshot Agent](replication-snapshot-agent.md) </span></span>  
 <span data-ttu-id="1528e-276">[Replication Log Reader Agent](replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1528e-276">[Replication Log Reader Agent](replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="1528e-277">[Replication Distribution Agent](replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1528e-277">[Replication Distribution Agent](replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="1528e-278">[Replication Merge Agent](replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1528e-278">[Replication Merge Agent](replication-merge-agent.md) </span></span>  
 [<span data-ttu-id="1528e-279">レプリケーション キュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="1528e-279">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)  
  
  
