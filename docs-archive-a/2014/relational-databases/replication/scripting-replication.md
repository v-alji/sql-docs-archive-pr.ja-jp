---
title: レプリケーションのスクリプト作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server replication], replication objects
- merge replication scripting [SQL Server replication]
- replication [SQL Server], scripting
- snapshot replication [SQL Server], scripting
- scripts [SQL Server replication]
- transactional replication, scripting
ms.assetid: e50fac44-54c0-470c-a4ea-9c111fa4322b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e865e2664a399bca4738c1fc157bef176f35e96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631772"
---
# <a name="scripting-replication"></a><span data-ttu-id="62e6e-102">レプリケーションのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="62e6e-102">Scripting Replication</span></span>
  <span data-ttu-id="62e6e-103">トポロジ内のすべてのレプリケーション コンポーンネントは、ディザスター リカバリー計画の一部としてスクリプト化され、スクリプトはタスクの繰り返しの自動化にも使用することができます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-103">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="62e6e-104">スクリプトには、パブリケーションやサブスクリプションなどスクリプト化されたレプリケーション コンポーネントを実装するために必要な Transact-SQL システム ストアド プロシージャが格納されます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-104">A script contains the Transact-SQL system stored procedures necessary to implement the replication component(s) scripted, such as a publication or subscription.</span></span> <span data-ttu-id="62e6e-105">スクリプトはウィザード (パブリケーションの新規作成ウィザードなど) で作成することができ、コンポーネントの作成後、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-105">Scripts can be created in a wizard (such as the New Publication Wizard) or in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] after you create a component.</span></span> <span data-ttu-id="62e6e-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または **sqlcmd**を使用すると、スクリプトの表示、変更、および実行を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-106">You can view, modify, and run the script using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or **sqlcmd**.</span></span> <span data-ttu-id="62e6e-107">スクリプトをバックアップ ファイルと共に保存して、レプリケーション トポロジの再構成が必要な場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-107">Scripts can be stored with backup files to be used in case a replication topology must be reconfigured.</span></span>  
  
 <span data-ttu-id="62e6e-108">プロパティが変更された場合は、コンポーネントのスクリプトを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62e6e-108">A component should be re-scripted if any property changes are made.</span></span> <span data-ttu-id="62e6e-109">トランザクション レプリケーションでカスタム ストアド プロシージャを使用している場合は、各プロシージャのコピーをスクリプトと共に保存しておく必要があります。プロシージャが変更された場合は、プロシージャのコピーも更新する必要があります (スキーマやアプリケーション要件が変更されると、通常、プロシージャが更新されます)。</span><span class="sxs-lookup"><span data-stu-id="62e6e-109">If you use custom stored procedures with transactional replication, a copy of each procedure should be stored with the scripts; the copy should be updated if the procedure changes (procedures are typically updated due to schema changes or changing application requirements).</span></span> <span data-ttu-id="62e6e-110">カスタム プロシージャの詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62e6e-110">For more information about custom procedures, see [Specify How Changes Are Propagated for Transactional Articles](transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
 <span data-ttu-id="62e6e-111">パラメーター化されたフィルターを使用するマージ パブリケーションの場合、パブリケーション スクリプトには、データ パーティションを作成するためのストアド プロシージャの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-111">For merge publications that use parameterized filters, publication scripts contain the stored procedure calls to create data partitions.</span></span> <span data-ttu-id="62e6e-112">このスクリプトによって、作成されたパーティションの参照、および必要に応じて 1 つ以上のパーティションを再作成する方法を利用できます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-112">The script provides a reference for the partitions created and a way in which to re-create one or more partitions if necessary.</span></span>  
  
## <a name="example-of-automating-a-task-with-scripts"></a><span data-ttu-id="62e6e-113">スクリプトによるタスクの自動化の例</span><span class="sxs-lookup"><span data-stu-id="62e6e-113">Example of Automating a Task with Scripts</span></span>  
 <span data-ttu-id="62e6e-114">たとえば、 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]では、リモートの営業部門にデータを配信するマージ レプリケーションを実装しているとします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-114">Consider [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], which implements merge replication to distribute data to its remote sales force.</span></span> <span data-ttu-id="62e6e-115">営業担当者は、プル サブスクリプションを使用して自分の販売区域内の顧客に関連するすべてのデータをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-115">A sales representative downloads all the data that pertains to the customers in her territory using pull subscriptions.</span></span> <span data-ttu-id="62e6e-116">オフラインで作業しているときには、データを更新したり、新しい顧客や受注を入力することができます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-116">When working offline, the sales representative updates data and enters new customers and orders.</span></span> <span data-ttu-id="62e6e-117">[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] には、さまざまな区域に 50 人を超える営業担当者がいるため、サブスクリプションの新規作成ウィザードを使用してサブスクライバーごとにさまざまなサブスクリプションを作成するには時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="62e6e-117">Because [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] has more than fifty sales representatives in different territories, it would be time-consuming to create the different subscriptions at each Subscriber with the New Subscription Wizard.</span></span> <span data-ttu-id="62e6e-118">代わりに、レプリケーション管理者は次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-118">Instead, the replication administrator can follow these steps:</span></span>  
  
1.  <span data-ttu-id="62e6e-119">営業担当者または販売区域に基づいたパーティションで必要なマージ パブリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-119">Set up the necessary merge publications with partitions based on the sales representative or their territory.</span></span>  
  
2.  <span data-ttu-id="62e6e-120">1 つのサブスクライバーに対して 1 つのプル サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-120">Create a pull subscription for one Subscriber.</span></span>  
  
3.  <span data-ttu-id="62e6e-121">作成したプル サブスクリプションに基づいてスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-121">Generate a script based on that pull subscription.</span></span>  
  
4.  <span data-ttu-id="62e6e-122">スクリプトを変更し、サブスクライバーの名前などの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-122">Modify the script, changing such values as the name of the Subscriber.</span></span>  
  
5.  <span data-ttu-id="62e6e-123">複数のサブスクライバーでスクリプトを実行し、必要なプル サブスクリプションを生成します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-123">Run the script at multiple Subscribers to generate the required pull subscriptions.</span></span>  
  
## <a name="script-replication-objects"></a><span data-ttu-id="62e6e-124">レプリケーション オブジェクトのスクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="62e6e-124">Script Replication Objects</span></span>  
 <span data-ttu-id="62e6e-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のレプリケーション ウィザード、または **[レプリケーション]** フォルダーからレプリケーション オブジェクトのスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-125">Script replication objects from the replication wizards or from the **Replication** folder in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="62e6e-126">ウィザードからスクリプトを作成する場合は、オブジェクトの作成後にスクリプトを作成するか、スクリプトの作成のみを行うかを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-126">If you script from the wizards, you can choose to create objects and script them, or you can choose only to script them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="62e6e-127">すべてのパスワードは NULL としてスクリプトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-127">All passwords are scripted as NULL.</span></span> <span data-ttu-id="62e6e-128">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-128">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="62e6e-129">スクリプト ファイルに資格情報を格納する場合は、不正アクセスを防ぐために、そのファイルをセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62e6e-129">If you store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="62e6e-130">レプリケーション ウィザードの使用方法の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62e6e-130">For more information about using the replication wizards, see:</span></span>  
  
-   [<span data-ttu-id="62e6e-131">パブリッシングおよびディストリビューションの構成</span><span class="sxs-lookup"><span data-stu-id="62e6e-131">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
-   [<span data-ttu-id="62e6e-132">パブリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="62e6e-132">Create a Publication</span></span>](publish/create-a-publication.md)  
  
-   [<span data-ttu-id="62e6e-133">プッシュ サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="62e6e-133">Create a Push Subscription</span></span>](create-a-push-subscription.md)  
  
-   [<span data-ttu-id="62e6e-134">Create a Pull Subscription</span><span class="sxs-lookup"><span data-stu-id="62e6e-134">Create a Pull Subscription</span></span>](create-a-pull-subscription.md)  
  
#### <a name="to-script-an-object-from-a-replication-wizard"></a><span data-ttu-id="62e6e-135">レプリケーション ウィザードからオブジェクトのスクリプトを作成するには</span><span class="sxs-lookup"><span data-stu-id="62e6e-135">To script an object from a replication wizard</span></span>  
  
1.  <span data-ttu-id="62e6e-136">ウィザードの **[ウィザードのアクション]** ページで、ウィザードに対して適切なチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-136">On the **Wizard Actions** page of a wizard, select the check box appropriate for the wizard:</span></span>  
  
    -   <span data-ttu-id="62e6e-137">**[パブリケーションを作成するためのステップを含むスクリプト ファイルを生成する]**</span><span class="sxs-lookup"><span data-stu-id="62e6e-137">**Generate a script file with steps to create a publication**</span></span>  
  
    -   <span data-ttu-id="62e6e-138">**[サブスクリプションを作成するためのステップを含むスクリプト ファイルを生成する]**</span><span class="sxs-lookup"><span data-stu-id="62e6e-138">**Generate a script file with steps to create the subscription(s)**</span></span>  
  
    -   <span data-ttu-id="62e6e-139">**[ディストリビューションを構成するためのステップを含むスクリプトを生成する]**</span><span class="sxs-lookup"><span data-stu-id="62e6e-139">**Generate a script file with steps to configure distribution**</span></span>  
  
2.  <span data-ttu-id="62e6e-140">**[スクリプト ファイルのプロパティ]** ページでオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-140">Specify options on the **Script File Properties** page.</span></span>  
  
3.  <span data-ttu-id="62e6e-141">ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-141">Complete the wizard.</span></span>  
  
#### <a name="to-script-an-object-from-management-studio"></a><span data-ttu-id="62e6e-142">Management Studio からオブジェクトのスクリプトを作成するには</span><span class="sxs-lookup"><span data-stu-id="62e6e-142">To script an object from Management Studio</span></span>  
  
1.  <span data-ttu-id="62e6e-143">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でディストリビューター、パブリッシャー、またはサブスクライバーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-143">Connect to the Distributor, Publisher, or Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="62e6e-144">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーまたは **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-144">Expand the **Replication** folder, and then expand the **Local Publications** folder or the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="62e6e-145">パブリケーションまたはサブスクリプションを右クリックし、 **[スクリプトの生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-145">Right-click a publication or subscription, and then click **Generate Scripts**.</span></span>  
  
4.  <span data-ttu-id="62e6e-146">**[SQL スクリプトの生成 - \<ReplicationObject>]** ダイアログ ボックスでオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-146">Specify options in the **Generate SQL Script - \<ReplicationObject>** dialog box.</span></span>  
  
5.  <span data-ttu-id="62e6e-147">**[スクリプトをファイルに保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-147">Click **Script to File**.</span></span>  
  
6.  <span data-ttu-id="62e6e-148">**[スクリプト ファイルの場所]** ダイアログ ボックスでファイル名を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-148">Enter a file name in the **Script File Location** dialog box, and then click **Save**.</span></span> <span data-ttu-id="62e6e-149">状態メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-149">A status message is displayed.</span></span>  
  
7.  <span data-ttu-id="62e6e-150">**[OK]** をクリックし、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-150">Click **OK**, and then click **Close**.</span></span>  
  
#### <a name="to-script-multiple-objects-from-management-studio"></a><span data-ttu-id="62e6e-151">Management Studio から複数のオブジェクトのスクリプトを作成するには</span><span class="sxs-lookup"><span data-stu-id="62e6e-151">To script multiple objects from Management Studio</span></span>  
  
1.  <span data-ttu-id="62e6e-152">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でディストリビューター、パブリッシャー、またはサブスクライバーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-152">Connect to the Distributor, Publisher, or Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="62e6e-153">**[レプリケーション]** フォルダーを右クリックし、 **[スクリプトの生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-153">Right-click the **Replication** folder, and then click **Generate Scripts**.</span></span>  
  
3.  <span data-ttu-id="62e6e-154">**[SQL スクリプトの生成]** ダイアログ ボックスでオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="62e6e-154">Specify options in the **Generate SQL Script** dialog box.</span></span>  
  
4.  <span data-ttu-id="62e6e-155">**[スクリプトをファイルに保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-155">Click **Script to File**.</span></span>  
  
5.  <span data-ttu-id="62e6e-156">**[スクリプト ファイルの場所]** ダイアログ ボックスでファイル名を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-156">Enter a file name in the **Script File Location** dialog box, and then click **Save**.</span></span> <span data-ttu-id="62e6e-157">状態メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="62e6e-157">A status message is displayed.</span></span>  
  
6.  <span data-ttu-id="62e6e-158">**[OK]** をクリックし、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62e6e-158">Click **OK, and then** click **Close**.</span></span>  
  
  
