---
title: メンテナンス プランの作成 (メンテナンス プラン デザイン画面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77e347720824198ba7d6abaddedd7a581ace98a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643322"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a><span data-ttu-id="fcf79-102">メンテナンス プランの作成 (メンテナンス プラン デザイン画面)</span><span class="sxs-lookup"><span data-stu-id="fcf79-102">Create a Maintenance Plan (Maintenance Plan Design Surface)</span></span>
  <span data-ttu-id="fcf79-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でメンテナンス プラン デザイン画面を使用して、単一サーバーまたはマルチサーバーのメンテナンス プランを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-103">This topic describes how to create a single server or multiserver maintenance plan using the Maintenance Plan Design Surface in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="fcf79-104">基本的なメンテナンス プランを作成する場合は、 **メンテナンス プラン ウィザード** が最適です。それに対して、デザイン画面を使用してプランを作成すると、高度なワークフローを利用できます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-104">While the **Maintenance Plan Wizard** is best for creating basic maintenance plans, creating a plan using the design surface allows you to utilize enhanced workflow.</span></span>  
  
 <span data-ttu-id="fcf79-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="fcf79-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fcf79-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="fcf79-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fcf79-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fcf79-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fcf79-108">Security</span><span class="sxs-lookup"><span data-stu-id="fcf79-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="fcf79-109">メンテナンス プラン デザイン画面を使用したメンテナンス プランの作成</span><span class="sxs-lookup"><span data-stu-id="fcf79-109">Creating a maintenance plan using the Maintenance Plan Design Surface</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fcf79-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="fcf79-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fcf79-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fcf79-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fcf79-112">マルチサーバー メンテナンス プランを作成するには、1 台のマスター サーバーと 1 台以上のターゲット サーバーを含むマルチサーバー環境を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-112">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="fcf79-113">マルチサーバー メンテナンス プランは、マスター サーバー上で作成および管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-113">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="fcf79-114">このプランはターゲット サーバー上でも表示できますが、ターゲット サーバーでは管理できません。</span><span class="sxs-lookup"><span data-stu-id="fcf79-114">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
-   <span data-ttu-id="fcf79-115">**db_ssisadmin** ロールおよび **dc_admin** ロールのメンバーは、特権を **sysadmin**に昇格できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-115">Members of the **db_ssisadmin** and **dc_admin** roles may be able to elevate their privileges to **sysadmin**.</span></span> <span data-ttu-id="fcf79-116">このような特権の昇格が発生するのは、それらのロールが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを変更でき、これらのパッケージを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **sysadmin** セキュリティ コンテキストを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行できるためです。</span><span class="sxs-lookup"><span data-stu-id="fcf79-116">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages; these packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **sysadmin** security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="fcf79-117">メンテナンス プラン、データ コレクション セット、およびその他の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行時にこの特権の昇格を防ぐには、特権が制限されたプロキシ アカウントを使用するようにパッケージを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを構成するか、 **db_ssisadmin** ロールおよび **dc_admin** ロールには **sysadmin** メンバーのみを追加するようにします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-117">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add **sysadmin** members to the **db_ssisadmin** and **dc_admin** roles.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fcf79-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fcf79-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fcf79-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="fcf79-119">Permissions</span></span>  
 <span data-ttu-id="fcf79-120">メンテナンス プランを作成または管理するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-120">To create or manage maintenance plans, you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="fcf79-121">ユーザーが **sysadmin** 固定サーバー ロールのメンバーである場合のみ、オブジェクト エクスプローラーに **[メンテナンス プラン]** ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-121">Object Explorer only displays the **Maintenance Plans** node for users who are members of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-maintenance-plan-design-surface"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fcf79-122">メンテナンス プラン デザイン画面の使用</span><span class="sxs-lookup"><span data-stu-id="fcf79-122">Using Maintenance Plan Design Surface</span></span>  
  
#### <a name="to-create-a-maintenance-plan"></a><span data-ttu-id="fcf79-123">メンテナンス プランを作成するには</span><span class="sxs-lookup"><span data-stu-id="fcf79-123">To create a maintenance plan</span></span>  
  
1.  <span data-ttu-id="fcf79-124">オブジェクト エクスプローラーで、プラス記号をクリックして、メンテナンス プランを作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-124">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="fcf79-125">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-125">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="fcf79-126">**[メンテナンス プラン]** フォルダーを右クリックし、 **[新しいメンテナンス プラン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-126">Right-click the **Maintenance Plans** folder and select **New Maintenance Plan**.</span></span>  
  
4.  <span data-ttu-id="fcf79-127">**[新しいメンテナンス プラン]** ダイアログ ボックスで、 **[名前]** ボックスにプランの名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-127">In the **New Maintenance Plan** dialog box, in the **Name** box, type a name for the plan and click **OK**.</span></span> <span data-ttu-id="fcf79-128">ツールボックスと _[maintenance_plan_name_ **[デザイン]]** 画面が開き、**Subplan_1** サブプランがメイン グリッドに作成されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-128">This opens the  Toolbox and the _maintenance_plan_name_ **[Design]** surface with the **Subplan_1** subplan created in the main grid.</span></span>  
  
     <span data-ttu-id="fcf79-129">デザイン領域のヘッダーには、次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-129">The following options are available in the design space's header.</span></span>  
  
     <span data-ttu-id="fcf79-130">**[サブプランの追加]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-130">**Add Subplan**</span></span>  
     <span data-ttu-id="fcf79-131">構成できるサブプランを追加します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-131">Adds a subplan that you can configure.</span></span>  
  
     <span data-ttu-id="fcf79-132">**[サブプランのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-132">**Subplan Properties**</span></span>  
     <span data-ttu-id="fcf79-133">メイン グリッドで選択されたサブプランについて、 **[サブプランのプロパティ]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-133">Displays the **Subplan Properties** dialog box for the selected subplan in the main grid.</span></span> <span data-ttu-id="fcf79-134">グリッドでサブプランをダブルクリックして、 **[サブプランのプロパティ]** ダイアログ ボックスを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-134">Alternately, double-click a subplan in the grid to display the **Subplan Properties** dialog box.</span></span> <span data-ttu-id="fcf79-135">このダイアログ ボックスの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcf79-135">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="fcf79-136">**[選択したサブプランの削除]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-136">**Delete Selected Subplan**</span></span>  
     <span data-ttu-id="fcf79-137">選択されているサブプランを削除します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-137">Deletes the selected subplan.</span></span>  
  
     <span data-ttu-id="fcf79-138">**[サブプランのスケジュール]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-138">**Subplan Schedule**</span></span>  
     <span data-ttu-id="fcf79-139">選択されているサブプランの **[新しいジョブ スケジュール]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-139">Displays the **New Job Schedule** dialog box for the selected subplan.</span></span>  
  
     <span data-ttu-id="fcf79-140">**[スケジュールの削除]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-140">**Remove Schedule**</span></span>  
     <span data-ttu-id="fcf79-141">選択されているサブプランからスケジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-141">Removes a schedule from the selected subplan.</span></span>  
  
     <span data-ttu-id="fcf79-142">**接続の管理**</span><span class="sxs-lookup"><span data-stu-id="fcf79-142">**Manage Connections**</span></span>  
     <span data-ttu-id="fcf79-143">**[接続の管理]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-143">Displays the **Manage Connections** dialog box.</span></span> <span data-ttu-id="fcf79-144">メンテナンス プランに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス接続を追加する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-144">Used to add additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance connections to the maintenance plan.</span></span> <span data-ttu-id="fcf79-145">このダイアログ ボックスの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcf79-145">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="fcf79-146">**[レポートとログ記録]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-146">**Reporting and Logging**</span></span>  
     <span data-ttu-id="fcf79-147">**[レポートとログ記録]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-147">Displays the **Reporting and Logging** dialog box.</span></span> <span data-ttu-id="fcf79-148">このダイアログ ボックスの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcf79-148">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="fcf79-149">**サーバー**</span><span class="sxs-lookup"><span data-stu-id="fcf79-149">**Servers**</span></span>  
     <span data-ttu-id="fcf79-150">**[サーバー]** ダイアログ ボックスが表示されます。このダイアログ ボックスで、サブプラン タスクを実行するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-150">Display the **Servers** dialog box, which is used to select the servers where the subplan tasks will be run.</span></span> <span data-ttu-id="fcf79-151">このオプションは、マルチサーバー環境のマスター サーバーのみで有効になります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-151">This option is enabled only on master servers in multiserver environments.</span></span> <span data-ttu-id="fcf79-152">詳細については、「[マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)」と「[メンテナンス プラン &#40;Servers&#41;](maintenance-plan-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcf79-152">For more information, see [Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md) and [Maintenance Plan &#40;Servers&#41;](maintenance-plan-servers.md).</span></span>  
  
     <span data-ttu-id="fcf79-153">**名前**</span><span class="sxs-lookup"><span data-stu-id="fcf79-153">**Name**</span></span>  
     <span data-ttu-id="fcf79-154">メンテナンス プランの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-154">Display the maintenance plan name.</span></span> <span data-ttu-id="fcf79-155">新しいメンテナンス プランの名前は、メンテナンス プラン デザイナーを開く前にダイアログ ボックスで指定します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-155">For new maintenance plans, the name is specified in a dialog box before the maintenance plan designer opens.</span></span> <span data-ttu-id="fcf79-156">メンテナンス プランの名前を変更するには、オブジェクト エクスプローラーでプランを右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-156">To rename a maintenance plan, right-click the plan in Object Explorer, and then click **Rename**.</span></span>  
  
     <span data-ttu-id="fcf79-157">**説明**</span><span class="sxs-lookup"><span data-stu-id="fcf79-157">**Description**</span></span>  
     <span data-ttu-id="fcf79-158">メンテナンス プランの説明を表示または指定します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-158">View or specify a description for the maintenance plan.</span></span> <span data-ttu-id="fcf79-159">説明の長さは最大 512 文字です。</span><span class="sxs-lookup"><span data-stu-id="fcf79-159">The maximum length for a description is 512 characters.</span></span>  
  
     <span data-ttu-id="fcf79-160">**デザイナー画面**</span><span class="sxs-lookup"><span data-stu-id="fcf79-160">**Designer Surface**</span></span>  
     <span data-ttu-id="fcf79-161">メンテナンスプランのデザインとメンテナンスを行います。</span><span class="sxs-lookup"><span data-stu-id="fcf79-161">Design and maintain maintenance plans.</span></span> <span data-ttu-id="fcf79-162">デザイナー画面を使用して、プランへのメンテナンス タスクの追加、プランからのタスクの削除、タスク間の優先順位制約の指定、タスクの分岐および並列処理の指定を行います。</span><span class="sxs-lookup"><span data-stu-id="fcf79-162">Use the designer surface to add maintenance tasks to a plan, remove tasks from a plan, specify precedence links between the tasks, and indicate task branching and parallelism.</span></span>  
  
     <span data-ttu-id="fcf79-163">2 つのタスクの間にある優先順位制約により、タスク間の関係が確立されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-163">A precedence link between two tasks establishes a relationship between the tasks.</span></span> <span data-ttu-id="fcf79-164">1 番目のタスク ( *先行タスク*) の実行結果が指定の条件を満たした場合のみ、2 番目のタスク ( *依存タスク*) が実行されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-164">The second task (the *dependent task*) executes only if the execution result of the first task (the *precedent task*) matches specified criteria.</span></span> <span data-ttu-id="fcf79-165">一般的に指定される実行結果は、 **[成功]** 、 **[失敗]** 、 **[完了]** のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="fcf79-165">Typically the execution result specified is **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="fcf79-166">詳細については、下記の「手順 **8** 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcf79-166">For more information, see step **8** below.</span></span>  
  
5.  <span data-ttu-id="fcf79-167">デザイン領域のヘッダーで、 **[Subplan_1]** をダブルクリックし、 **[サブプランのプロパティ]** ダイアログ ボックスにサブプランの名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-167">In the design space's header, double-click **Subplan_1** and enter a name and description for the subplan in the **Subplan Properties** dialog box.</span></span>  
  
     <span data-ttu-id="fcf79-168">**[サブプランのプロパティ]** ダイアログ ボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-168">The following options are available in the **Subplan Properties** dialog box.</span></span>  
  
     <span data-ttu-id="fcf79-169">**名前**</span><span class="sxs-lookup"><span data-stu-id="fcf79-169">**Name**</span></span>  
     <span data-ttu-id="fcf79-170">サブプランの名前です。</span><span class="sxs-lookup"><span data-stu-id="fcf79-170">The name of the subplan.</span></span>  
  
     <span data-ttu-id="fcf79-171">**説明**</span><span class="sxs-lookup"><span data-stu-id="fcf79-171">**Description**</span></span>  
     <span data-ttu-id="fcf79-172">サブプランの簡潔な説明です。</span><span class="sxs-lookup"><span data-stu-id="fcf79-172">A brief description of the subplan.</span></span>  
  
     <span data-ttu-id="fcf79-173">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-173">**Schedule**</span></span>  
     <span data-ttu-id="fcf79-174">どのようなスケジュールでサブプランが実行されるかを示します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-174">Indicates on what schedule the subplan will be run.</span></span> <span data-ttu-id="fcf79-175">**[サブプランのスケジュール]** をクリックして、 **[新しいジョブ スケジュール]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-175">Click **Subplan Schedule** to open the **New Job Schedule** dialog box.</span></span> <span data-ttu-id="fcf79-176">サブプランからスケジュールを削除するには、 **[スケジュールの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-176">Click **Remove Schedule** to delete the schedule from the subplan.</span></span>  
  
     <span data-ttu-id="fcf79-177">**[実行するアカウント名]** 一覧</span><span class="sxs-lookup"><span data-stu-id="fcf79-177">**Run as** list</span></span>  
     <span data-ttu-id="fcf79-178">このサブタスクを実行するために使用するアカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-178">Select the account to use to run this subtask.</span></span>  
  
6.  <span data-ttu-id="fcf79-179">**[サブプランのスケジュール]** をクリックし、 **[新しいジョブ スケジュール]** ダイアログ ボックスでスケジュールの詳細を入力します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-179">Click **Subplan Schedule** to enter schedule details in the **New Job Schedule** dialog box.</span></span>  
  
7.  <span data-ttu-id="fcf79-180">サブプランを作成するには、 **ツールボックス** からデザイン画面にタスク フロー要素をドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-180">To build the subplan, drag and drop task flow elements from the **Toolbox** to the plan design surface.</span></span> <span data-ttu-id="fcf79-181">タスクをダブルクリックしてダイアログ ボックスを開き、タスクのオプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-181">Double-click tasks to open dialog boxes to configure the task options.</span></span>  
  
     <span data-ttu-id="fcf79-182">**[ツールボックス]** では、次のメンテナンス プランのタスクを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-182">The following maintenance plan tasks are available in the **Toolbox**:</span></span>  
  
    -   <span data-ttu-id="fcf79-183">**データベースのバックアップ タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-183">**Back up Database Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-184">**データベースの整合性確認タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-184">**Check Database Integrity Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-185">**SQL Server エージェント ジョブの実行タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-185">**Execute SQL Server Agent Job Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-186">**T-SQL ステートメントの実行タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-186">**Execute T-SQL Statement Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-187">**履歴クリーンアップ タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-187">**History Cleanup Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-188">**メンテナンス クリーンアップ タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-188">**Maintenance Cleanup Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-189">**オペレーターへの通知タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-189">**Notify Operator Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-190">**インデックスの再構築タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-190">**Rebuild Index Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-191">**インデックスの再編成タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-191">**Reorganize Index Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-192">**データベースの圧縮タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-192">**Shrink Database Task**</span></span>  
  
    -   <span data-ttu-id="fcf79-193">**統計の更新タスク**</span><span class="sxs-lookup"><span data-stu-id="fcf79-193">**Update Statistics Task**</span></span>  
  
     <span data-ttu-id="fcf79-194">タスクを **[ツールボックス]** に追加するには:</span><span class="sxs-lookup"><span data-stu-id="fcf79-194">To add tasks to the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="fcf79-195">**[ツール]** メニューで **[ツールボックス アイテムの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-195">On the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
    2.  <span data-ttu-id="fcf79-196">**[ツールボックス]** に表示するツールを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-196">Select the tools you want to appear in the **Toolbox**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="fcf79-197">メンテナンス プランのタスクを **[ツールボックス]** に追加すると、 **メンテナンス プラン ウィザード**で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-197">Adding maintenance plan tasks to the **Toolbox** also makes them available in the **Maintenance Plan Wizard**.</span></span> <span data-ttu-id="fcf79-198">上記の個々のタスクの詳細については、「 [メンテナンス プラン ウィザードの起動](use-the-maintenance-plan-wizard.md#SSMSProcedure) 」の「 **メンテナンス プラン ウィザードの使用**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcf79-198">For more information on the individual tasks above, see [Using Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md#SSMSProcedure) under **Start the Maintenance Plan Wizard**.</span></span>  
  
8.  <span data-ttu-id="fcf79-199">タスク間のワークフローを定義するには:</span><span class="sxs-lookup"><span data-stu-id="fcf79-199">To define a workflow between tasks:</span></span>  
  
    1.  <span data-ttu-id="fcf79-200">先行タスクを右クリックし、 **[優先順位制約の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-200">Right-click the precedent task and select **Add Precedence Constraint**.</span></span>  
  
    2.  <span data-ttu-id="fcf79-201">**[制御フロー]** ダイアログ ボックスで、 **[対象]** 一覧から依存タスクを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-201">In the **Control Flow** dialog box, in the **To** list, select the dependent task and click **OK**.</span></span>  
  
    3.  <span data-ttu-id="fcf79-202">2 つのタスク間のコネクタをダブルクリックすると、 **[優先順位制約エディター]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-202">Double click the connector between the two tasks to open the **Precedence Constraint Editor** dialog box.</span></span>  
  
         <span data-ttu-id="fcf79-203">**[優先順位制約エディター]** ダイアログ ボックスでは次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-203">The following options are available in the **Precedence Constraint Editor** dialog box.</span></span>  
  
         <span data-ttu-id="fcf79-204">**[制約オプション]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-204">**Constraint option**</span></span>  
         <span data-ttu-id="fcf79-205">2 つのタスク間の制約の動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-205">Defines how a constraint works between two tasks.</span></span>  
  
         <span data-ttu-id="fcf79-206">**[評価操作]**  一覧</span><span class="sxs-lookup"><span data-stu-id="fcf79-206">**Evaluation operation**  list</span></span>  
         <span data-ttu-id="fcf79-207">優先順位制約で使用する評価操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-207">Specify the evaluation operation that the precedence constraint uses.</span></span> <span data-ttu-id="fcf79-208">操作は次のとおりです: **[制約]** 、 **[式]** 、 **[式と制約]** 、 **[式または制約]** 。</span><span class="sxs-lookup"><span data-stu-id="fcf79-208">The operations are: **Constraint**, **Expression**, **Expression and Constraint**, and **Expression or Constraint**.</span></span>  
  
         <span data-ttu-id="fcf79-209">**[値]** 一覧</span><span class="sxs-lookup"><span data-stu-id="fcf79-209">**Value** list</span></span>  
         <span data-ttu-id="fcf79-210">制約値として次の値を指定します: **[成功]** 、 **[失敗]** 、 **[完了]** 。</span><span class="sxs-lookup"><span data-stu-id="fcf79-210">Specify the constraint value: **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="fcf79-211">デフォルト値は **[成功]** です。</span><span class="sxs-lookup"><span data-stu-id="fcf79-211">**Success** is the default.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="fcf79-212">優先順位制約を表す線は、 **[成功]** の場合は緑色、 **[失敗]** の場合は赤色、 **[完了]** の場合は青色です。</span><span class="sxs-lookup"><span data-stu-id="fcf79-212">The precedence constraint line is green for **Success**, red for **Failure**, and blue for **Completion**.</span></span>  
  
         <span data-ttu-id="fcf79-213">**[式]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-213">**Expression**</span></span>  
         <span data-ttu-id="fcf79-214">操作として **[式]** 、 **[式と制約]** 、または **[式または制約]** を使用する場合は、式を入力します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-214">If using the operations **Expression**, **Expression and Constraint**, or **Expression or Constraint**, type an expression.</span></span> <span data-ttu-id="fcf79-215">式はブール値に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-215">The expression must evaluate to a Boolean.</span></span>  
  
         <span data-ttu-id="fcf79-216">**テスト**</span><span class="sxs-lookup"><span data-stu-id="fcf79-216">**Test**</span></span>  
         <span data-ttu-id="fcf79-217">式を検証します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-217">Validate the expression.</span></span>  
  
         <span data-ttu-id="fcf79-218">**[複数の制約]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-218">**Multiple constraints**</span></span>  
         <span data-ttu-id="fcf79-219">複数の制約がどのように相互運用して制約付きタスクの実行を制御するかを定義します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-219">Define how multiple constraints interoperate to control the execution of the constrained task.</span></span>  
  
         <span data-ttu-id="fcf79-220">**論理積**</span><span class="sxs-lookup"><span data-stu-id="fcf79-220">**Logical AND**</span></span>  
         <span data-ttu-id="fcf79-221">同一の実行可能ファイルに対して、複数の優先順位制約を同時に評価することを指定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-221">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="fcf79-222">すべての制約が True に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-222">All constraints must evaluate to True.</span></span> <span data-ttu-id="fcf79-223">これは既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="fcf79-223">This option is the default.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="fcf79-224">この種類の優先順位制約は、緑色、赤色、または青色の実線で示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-224">This type of precedence constraint appears as a solid green, red, or blue line.</span></span>  
  
         <span data-ttu-id="fcf79-225">**論理和**</span><span class="sxs-lookup"><span data-stu-id="fcf79-225">**Logical OR**</span></span>  
         <span data-ttu-id="fcf79-226">同一の実行可能ファイルに対して、複数の優先順位制約を同時に評価することを指定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-226">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="fcf79-227">少なくとも 1 つの制約が True に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-227">At least one constraint must evaluate to True.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="fcf79-228">この種類の優先順位制約は、緑色、赤色、または青色の点線で示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-228">This type of precedence constraint appears as a dotted green, red, or blue line.</span></span>  
  
9. <span data-ttu-id="fcf79-229">別のスケジュールで実行されるタスクを制約する別のサブプランを追加するには、ツール バーの **[サブプランの追加]** をクリックし、 **[サブプランのプロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-229">To add another subplan that contains tasks run on a different schedule, click **Add Subplan** on the toolbar to open the **Subplan Properties** dialog box.</span></span>  
  
10. <span data-ttu-id="fcf79-230">別のサーバーに接続を追加するには:</span><span class="sxs-lookup"><span data-stu-id="fcf79-230">To add connections to different servers:</span></span>  
  
    1.  <span data-ttu-id="fcf79-231">デザイン画面のツール バーで、 **[接続の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-231">In the design space's toolbar, click **Manage Connections**.</span></span>  
  
    2.  <span data-ttu-id="fcf79-232">**[接続の管理]** ダイアログ ボックスで **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-232">In the **Manage Connections** dialog box, click **Add**.</span></span>  
  
    3.  <span data-ttu-id="fcf79-233">**[接続プロパティ]** ダイアログ ボックスの **[接続名]** ボックスに、作成する接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-233">In the **Connection Properties** dialog box, in the **Connection name** box, enter the name of the connection you are creating.</span></span>  
  
    4.  <span data-ttu-id="fcf79-234">**[SQL Server データに接続するための情報を指定してください]** の **[サーバー名の選択または入力]** ボックスで、使用する SQL Server 名を入力するか、参照ボタン **([...])** をクリックして **[SQL Server]** ダイアログ ボックスでサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-234">Under **Specify the following to connect to SQL Server data**, in the **Select or enter a server name** box, either enter the name of the SQL server you want to use or click the ellipsis **(...)** and select a server in the **SQL Server** dialog box.</span></span> <span data-ttu-id="fcf79-235">**[SQL Server]** ダイアログ ボックスでサーバーを選択した場合は、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-235">If you select a server from the **SQL Server** dialog box, click **OK**.</span></span>  
  
    5.  <span data-ttu-id="fcf79-236">**[サーバーにログオンするための情報の入力]** で、 **[Windows NT の統合セキュリティを使用する]** または **[特定のユーザー名とパスワードを使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-236">Under **Enter information to log on to the server**, select either **Use Windows NT Integrated security** or **Use a specific user name and password**.</span></span> <span data-ttu-id="fcf79-237">特定のユーザー名とパスワードを使用するように選択した場合は、 **[ユーザー名]** および **[パスワード]** ボックスにそれぞれ情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-237">If you elect to use a specific user name and password, enter that information in the **User name** and **Password** boxes, respectively.</span></span>  
  
    6.  <span data-ttu-id="fcf79-238">**[接続プロパティ]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-238">In the **Connection Properties** dialog box, click **OK**.</span></span>  
  
    7.  <span data-ttu-id="fcf79-239">**[接続の管理]** ダイアログ ボックスで、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-239">In the **Manage Connections** dialog box, click **Close**.</span></span>  
  
11. <span data-ttu-id="fcf79-240">レポート オプションを指定するには:</span><span class="sxs-lookup"><span data-stu-id="fcf79-240">To specify reporting options:</span></span>  
  
    1.  <span data-ttu-id="fcf79-241">デザイン画面のツール バーで **[レポートとログ記録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-241">In the design space's toolbar, click **Reporting and Logging**.</span></span>  
  
    2.  <span data-ttu-id="fcf79-242">**[レポートとログ記録]** ダイアログ ボックスの **[レポート]** で、 **[テキスト ファイルのレポートを生成する]** または **[電子メール受信者にレポートを送信する]** 、あるいはその両方を選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-242">In the **Reporting and Logging** dialog box, under **Reporting**, select **Generate a text file report** or **Send report to an email recipient** or both.</span></span>  
  
        1.  <span data-ttu-id="fcf79-243">**[テキスト ファイルのレポートを生成する]** で、 **[新しいファイルの作成]** または **[ファイルに追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-243">If you select **Generate a text file report**, select either **Create a new file** or **Append to file**.</span></span>  
  
        2.  <span data-ttu-id="fcf79-244">上記の選択内容に応じて、 **[フォルダー]** または **[ファイル名]** ボックスに情報を入力することにより、新しいファイルまたは追加されるファイルの名前および完全なパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-244">Depending on the selection above, enter the name and full path of the new file or file to be appended by entering the information in the **Folder** or **File name** boxes.</span></span> <span data-ttu-id="fcf79-245">または、省略記号 **(...)** をクリックし、[**フォルダーの検索-**_server_name_ ] ダイアログボックスまたは [**データベースファイルの検索-**_server_name_ ] ダイアログボックスで、フォルダーまたはファイル名のパスを選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-245">Alternately, click on the ellipsis **(...)** and select the path to the folder or file name from the **Locate Folder -**_server_name_ or **Locate Database Files -**_server_name_ dialog boxes.</span></span>  
  
        3.  <span data-ttu-id="fcf79-246">**[エージェント オペレーター]** 一覧で **[電子メール受信者にレポートを送信する]** を選択した場合は、電子メール レポートの受信者を選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-246">If you select **Send report to an email recipient**, on the **Agent operator** list, select the recipient of the emailed report.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="fcf79-247">メールを送信するためには、データベース メールを使用するように SQL Server エージェントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcf79-247">SQL Server Agent must be configured to use Database Mail in order to send mail.</span></span> <span data-ttu-id="fcf79-248">詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fcf79-248">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)</span></span>  
  
    3.  <span data-ttu-id="fcf79-249">より詳細な情報を保存するには、 **[ログ記録]** で、 **[拡張情報をログに記録する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-249">To save more detailed information, under **Logging**, select **Log extended information**.</span></span>  
  
    4.  <span data-ttu-id="fcf79-250">メンテナンス プランの結果情報を別のサーバーに書き込むには、 **[リモート サーバーにログを記録する]** をオンにし、 **[接続]** 一覧からサーバー接続を選択するか、または **[新規]** をクリックして **[接続プロパティ]** ダイアログ ボックスに接続情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-250">To write maintenance plan results information to another server, select **Log to remote server** and either select a server connection from the **Connection** list or click **New** and enter the connection information in the **Connection Properties** dialog box.</span></span>  
  
    5.  <span data-ttu-id="fcf79-251">**[レポートとログ記録]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-251">In the **Reporting and Logging** dialog box, click **OK**.</span></span>  
  
12. <span data-ttu-id="fcf79-252">ログ ファイル ビューアーで結果を参照するには、 **オブジェクト エクスプローラー**で **[メンテナンス プラン]** フォルダーを右クリックするか、特定のメンテナンス プランを右クリックして **[履歴の表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-252">To view the results in the log file viewer, in **Object Explorer**, right-click either the **Maintenance Plans** folder or the specific maintenance plan and select **View History**.</span></span>  
  
     <span data-ttu-id="fcf79-253">[**ログファイルの表示-**_server_name_ ] ダイアログボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-253">The following options are available on the **Log File Viewer -**_server_name_ dialog box.</span></span>  
  
     <span data-ttu-id="fcf79-254">**[ログの読み込み]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-254">**Load Log**</span></span>  
     <span data-ttu-id="fcf79-255">読み込むログ ファイルを指定できるダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-255">Open a dialog box where you can specify a log file to load.</span></span>  
  
     <span data-ttu-id="fcf79-256">**エクスポート**</span><span class="sxs-lookup"><span data-stu-id="fcf79-256">**Export**</span></span>  
     <span data-ttu-id="fcf79-257">**[ログ ファイルの概要]** グリッドに表示されている情報をテキスト ファイルとしてエクスポートするためのダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-257">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
     <span data-ttu-id="fcf79-258">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-258">**Refresh**</span></span>  
     <span data-ttu-id="fcf79-259">選択されたログの表示を更新します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-259">Refresh the view of the selected logs.</span></span> <span data-ttu-id="fcf79-260">**[更新]** ボタンをクリックすると、選択したログがターゲット サーバーから再度読み込まれ、それと同時にすべてのフィルター設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-260">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
     <span data-ttu-id="fcf79-261">**Assert**</span><span class="sxs-lookup"><span data-stu-id="fcf79-261">**Filter**</span></span>  
     <span data-ttu-id="fcf79-262">**[接続]** や **[日付]** などの **[全般]** フィルター基準を含め、ログ ファイルのフィルター選択に使用する設定を指定できるダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-262">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
     <span data-ttu-id="fcf79-263">**Search**</span><span class="sxs-lookup"><span data-stu-id="fcf79-263">**Search**</span></span>  
     <span data-ttu-id="fcf79-264">ログ ファイル内で特定のテキストを検索します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-264">Search the log file for specific text.</span></span> <span data-ttu-id="fcf79-265">ワイルドカード文字を使用した検索はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="fcf79-265">Searching with wildcard characters is not supported.</span></span>  
  
     <span data-ttu-id="fcf79-266">**Stop**</span><span class="sxs-lookup"><span data-stu-id="fcf79-266">**Stop**</span></span>  
     <span data-ttu-id="fcf79-267">ログ ファイル エントリの読み込みを停止します。</span><span class="sxs-lookup"><span data-stu-id="fcf79-267">Stops loading the log file entries.</span></span> <span data-ttu-id="fcf79-268">たとえば、最新のエントリのみを表示したい場合に、リモートまたはオフラインのログ ファイルの読み込みに長い時間がかかるときは、このオプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fcf79-268">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
     <span data-ttu-id="fcf79-269">**[ログ ファイルの概要]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-269">**Log file summary**</span></span>  
     <span data-ttu-id="fcf79-270">この情報パネルには、ログ ファイルのフィルター選択の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-270">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="fcf79-271">ファイルがフィルター選択されない場合、 **"フィルターが適用されていません"** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-271">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="fcf79-272">ログにフィルターが適用されている場合、"**ログ エントリのフィルター条件:** \<filter criteria>" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-272">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
     <span data-ttu-id="fcf79-273">**Date**</span><span class="sxs-lookup"><span data-stu-id="fcf79-273">**Date**</span></span>  
     <span data-ttu-id="fcf79-274">イベントの日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-274">Displays the date of the event.</span></span>  
  
     <span data-ttu-id="fcf79-275">**ソース**</span><span class="sxs-lookup"><span data-stu-id="fcf79-275">**Source**</span></span>  
     <span data-ttu-id="fcf79-276">サービスの名前 (たとえば MSSQLSERVER) など、イベントの作成元のソース機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-276">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="fcf79-277">ログの種類によっては表示されません。</span><span class="sxs-lookup"><span data-stu-id="fcf79-277">This does not appear for all log types.</span></span>  
  
     <span data-ttu-id="fcf79-278">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="fcf79-278">**Message**</span></span>  
     <span data-ttu-id="fcf79-279">イベントに関連付けられているメッセージがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-279">Displays any messages associated with the event.</span></span>  
  
     <span data-ttu-id="fcf79-280">**[ログの種類]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-280">**Log Type**</span></span>  
     <span data-ttu-id="fcf79-281">イベントが属するログの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-281">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="fcf79-282">[ログ ファイルの概要] ウィンドウには、選択したログがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-282">All selected logs appear in the log file summary window.</span></span>  
  
     <span data-ttu-id="fcf79-283">**[ログ ソース]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-283">**Log Source**</span></span>  
     <span data-ttu-id="fcf79-284">イベントがキャプチャされているソース ログの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-284">Displays a description of the source log in which the event is captured.</span></span>  
  
     <span data-ttu-id="fcf79-285">**[選択した行の詳細]**</span><span class="sxs-lookup"><span data-stu-id="fcf79-285">**Selected row details**</span></span>  
     <span data-ttu-id="fcf79-286">行を選択すると、選択されたイベント行の詳細情報がページの下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-286">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="fcf79-287">列をグリッド内の別の場所にドラッグすることで、列を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-287">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="fcf79-288">グリッドのヘッダーで列のセパレーター バーを左右にドラッグすると、列の幅を変更できます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-288">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="fcf79-289">グリッドのヘッダーで列のセパレーター バーをダブルクリックすると、内容の長さに合わせて自動的に列の幅が調整されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-289">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
     <span data-ttu-id="fcf79-290">**インスタンス**</span><span class="sxs-lookup"><span data-stu-id="fcf79-290">**Instance**</span></span>  
     <span data-ttu-id="fcf79-291">イベントが発生したインスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="fcf79-291">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="fcf79-292">これは、 *computer name*\\*instance name*と表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcf79-292">This is displayed as *computer name*\\*instance name*.</span></span>  
  
  
