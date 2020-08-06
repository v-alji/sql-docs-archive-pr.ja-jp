---
title: スケジュールされたポリシーを複数のインスタンスにデプロイする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 30faf94c2033be43ac035517e58d5a18c0c68ab8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712665"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a><span data-ttu-id="6d9fd-102">スケジュールされたポリシーの複数インスタンスへの配置</span><span class="sxs-lookup"><span data-stu-id="6d9fd-102">Deploy Scheduled Policies to Multiple Instances</span></span>
  <span data-ttu-id="6d9fd-103">登録済みサーバーを使用すると、スケジュールされたポリシーを集中管理された場所からマネージド サーバーに配置できます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-103">By using Registered Servers, you can deploy scheduled policies to managed servers from a central location.</span></span> <span data-ttu-id="6d9fd-104">スケジュールされたポリシーは、ローカル サーバー グループまたは中央管理サーバーから配置できます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-104">You can deploy scheduled policies from either a local server group, or from a Central Management Server.</span></span>  
  
 <span data-ttu-id="6d9fd-105">ここでは、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-105">In this task, you will do the following:</span></span>  
  
1.  <span data-ttu-id="6d9fd-106">前の作業でスケジュール設定したポリシーをフォルダーにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-106">Export the policies that you scheduled in the previous task to a folder.</span></span>  
  
2.  <span data-ttu-id="6d9fd-107">登録済みサーバーで管理されている対象インスタンスにスケジュールされたポリシーを配置します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-107">Deploy the scheduled policies to target instances that are managed through Registered Servers.</span></span>  
  
 <span data-ttu-id="6d9fd-108">これらの作業は、このレッスンの前の作業を完了したコンピューターで実行します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-108">You will perform these tasks on the computer where you completed the previous tasks in this lesson.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6d9fd-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="6d9fd-109">Prerequisites</span></span>  
 <span data-ttu-id="6d9fd-110">この作業には、次の前提条件があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-110">This task has the following prerequisites:</span></span>  
  
-   <span data-ttu-id="6d9fd-111">このレッスンの前の作業を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-111">You must have completed the previous tasks in this lesson.</span></span>  
  
-   <span data-ttu-id="6d9fd-112">スケジュールされたポリシーを配置するインスタンスで [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-112">The instances where you want to deploy the scheduled policies must be running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span> <span data-ttu-id="6d9fd-113">オートメーションではポリシーがローカルに格納されている必要がありますが、これは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-113">Automation requires the policies to be stored locally, which is not supported on versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
-   <span data-ttu-id="6d9fd-114">スケジュールされたポリシーを展開するサーバーは、**ローカルサーバーグループ**または**中央管理サーバー**ノードの登録済みサーバーに登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-114">The servers where you want to deploy the scheduled policies must be registered in Registered Servers in either the **Local Server Groups** or the **Central Management Servers** node.</span></span> <span data-ttu-id="6d9fd-115">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-115">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="6d9fd-116">サーバー グループの作成または編集 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6d9fd-116">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="6d9fd-117">[接続されたサーバー &#40;SQL Server Management Studio&#41;に登録](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-117">[Register a Connected Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).</span></span>  
  
    -   [<span data-ttu-id="6d9fd-118">中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6d9fd-118">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a><span data-ttu-id="6d9fd-119">スケジュールされたポリシーを .xml ファイルとしてエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="6d9fd-119">To export the scheduled policies as .xml files</span></span>  
  
1.  <span data-ttu-id="6d9fd-120">前のタスクでスケジュールされたポリシーを構成したサーバーで、[**管理**]、[**ポリシー管理**] の順に展開し、[**ポリシー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-120">On the server where you configured scheduled policies in the previous task, expand **Management**, expand **Policy Management**, and then click **Policies**.</span></span>  
  
2.  <span data-ttu-id="6d9fd-121">**[表示]** メニューの **[オブジェクト エクスプローラーの詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-121">On the **View** menu, click **Object Explorer Details**.</span></span>  
  
3.  <span data-ttu-id="6d9fd-122">[**オブジェクトエクスプローラーの詳細**] ウィンドウで、登録済みサーバーを使用して他のサーバーに展開する、スケジュールされたすべてのベストプラクティスポリシーを選択します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-122">In the **Object Explorer Details** pane, select all the scheduled best practices policies that you want to deploy to other servers through Registered Servers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d9fd-123">**カテゴリの見出しを**クリックすると、ポリシーをカテゴリ別に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-123">You can click the **Category** heading to sort the policies by category.</span></span>  
  
4.  <span data-ttu-id="6d9fd-124">選択範囲を右クリックし、[**ポリシーのエクスポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-124">Right-click the selection, and then click **Export Policy**.</span></span>  
  
5.  <span data-ttu-id="6d9fd-125">エクスポートするポリシーを複数選択した場合は、[**フォルダーの参照**] ダイアログボックスで、インストール先のフォルダーを選択するか、新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-125">If you selected multiple policies to export, in the **Browse For Folder** dialog box, select a destination folder, or create a new folder.</span></span> <span data-ttu-id="6d9fd-126">このレッスンでは、 **c:\ Scheduled_BP_Policies**というパスで新しいフォルダーを作成し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-126">For this lesson, create a new folder with the path **C:\Scheduled_BP_Policies**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="6d9fd-127">エクスポートするポリシーを1つだけ選択した場合は、[**ポリシーのエクスポート**] ダイアログボックスで、 **c:\ Scheduled_BP_Policies**というパスの新しいフォルダーを作成し、[**開く**] をクリックして、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-127">If you only selected one policy to export, in the **Export Policy** dialog box, create a new folder with the path **C:\Scheduled_BP_Policies**, click **Open**, and then click **Save**.</span></span>  
  
     <span data-ttu-id="6d9fd-128">.xml ポリシー ファイルがフォルダーの場所に作成されます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-128">The .xml policy files are created in the folder location.</span></span>  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a><span data-ttu-id="6d9fd-129">登録済みサーバーで管理されているサーバーにスケジュールされたポリシーを配置するには</span><span class="sxs-lookup"><span data-stu-id="6d9fd-129">To deploy the scheduled policies to servers that are managed through Registered Servers</span></span>  
  
1.  <span data-ttu-id="6d9fd-130">**[表示]** メニューの **[登録済みサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-130">On the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="6d9fd-131">[**データベースエンジン**] を展開し、[**ローカルサーバーグループ**] または [**中央管理サーバー**] を展開して、ポリシーの展開先のノードを右クリックし、[**ポリシーのインポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-131">Expand **Database Engine**, expand either **Local Server Groups** or **Central Management Servers**, right-click the node that you want to deploy the policies to, and then click **Import Policies**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d9fd-132">**ローカルサーバーグループ**または中央管理サーバー自体を右クリックすると、すべての管理対象サーバーにポリシーが展開されます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-132">If you right-click **Local Server Groups** or the Central Management Server itself, the policies will be deployed to all managed servers.</span></span> <span data-ttu-id="6d9fd-133">特定のサーバー グループを右クリックした場合、そのグループ内のサーバーだけにポリシーが配置されます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-133">If you right-click a specific server group, the policies will only be deployed to servers in that group.</span></span> <span data-ttu-id="6d9fd-134">特定の登録済みサーバーを右クリックした場合、そのサーバーだけにポリシーが配置されます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-134">If you right-click a specific registered server, the policies will only be deployed to that server.</span></span>  
  
3.  <span data-ttu-id="6d9fd-135">[**インポートするファイル**] の横にある省略記号ボタン ([.**..**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-135">Next to **Files to import**, click the ellipsis button (**...**).</span></span>  
  
4.  <span data-ttu-id="6d9fd-136">**[ポリシーの選択**] ダイアログボックスで、スケジュールされたポリシーを保存したフォルダーの場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-136">In the **Select Policy** dialog box, browse to the folder location where you saved the scheduled policies.</span></span> <span data-ttu-id="6d9fd-137">この例では、場所**c:\ Scheduled_BP_Policies**に移動します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-137">For this example, browse to the location **C:\Scheduled_BP_Policies**.</span></span>  
  
5.  <span data-ttu-id="6d9fd-138">ターゲットインスタンスにインポートするポリシーを選択し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-138">Select the policies that you want to import to the target instances, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="6d9fd-139">[**インポート**] ダイアログボックスの [**ポリシーの状態**] ボックスの一覧で、目的のポリシーの状態を選択します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-139">In the **Import** dialog box, in the **Policy state** list, select the desired policy state.</span></span> <span data-ttu-id="6d9fd-140">ポリシーの状態を保存するか、インポート時にポリシーを有効または無効にするかを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-140">You can choose to preserve the policy state, enable, or disable the policies on import.</span></span> <span data-ttu-id="6d9fd-141">ポリシーは、スケジュールに従って実行されるように有効にしておく必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-141">Be aware that the policies must be enabled to run on a schedule.</span></span>  
  
7.  <span data-ttu-id="6d9fd-142">[ **OK** ] をクリックして、すべてのターゲットインスタンスにポリシーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-142">Click **OK** to import the policies to all the target instances.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d9fd-143">エラーが発生しても、[**インポート**] ダイアログボックスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-143">If there are any errors, the **Import** dialog box does not disappear.</span></span> <span data-ttu-id="6d9fd-144">[**ログ**] ページをクリックして、メッセージを確認します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-144">Click the **Log** page to review the messages.</span></span> <span data-ttu-id="6d9fd-145">[**キャンセル**] をクリックして、ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-145">Click **Cancel** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="6d9fd-146">ターゲットインスタンスからポリシーを表示するには、インスタンスに接続し、オブジェクトエクスプローラーを開き、[**管理**]、[**ポリシー**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-146">To view the policies from a target instance, connect to the instance, open Object Explorer, expand **Management**, and then expand **Policies**.</span></span> <span data-ttu-id="6d9fd-147">インポートされたポリシーが [**ポリシー**ノードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-147">You should see the imported policies in the **Policies** node.</span></span> <span data-ttu-id="6d9fd-148">各ポリシーをダブルクリックすると、スケジュールを表示したり、設定を変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-148">If you double-click each policy, you can view the schedule, or change the settings.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d9fd-149">スケジュールされたポリシーが実行された後に評価結果を表示するには、対象インスタンスのポリシー履歴ログを開きます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-149">To view the evaluation results after a scheduled policy runs, open the Policy History log on the target instance.</span></span> <span data-ttu-id="6d9fd-150">ログを開くには、[**ポリシー管理**] を右クリックし、[**履歴の表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-150">To open the log, right-click **Policy Management**, and then click **View History**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6d9fd-151">まとめ</span><span class="sxs-lookup"><span data-stu-id="6d9fd-151">Summary</span></span>  
 <span data-ttu-id="6d9fd-152">このチュートリアルでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスに対して、ベスト プラクティス ポリシーの評価を要求時および定期的に実行する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-152">This tutorial has shown you how to perform both on-demand and scheduled evaluations of the best practices policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="next"></a><span data-ttu-id="6d9fd-153">次へ</span><span class="sxs-lookup"><span data-stu-id="6d9fd-153">Next</span></span>  
 <span data-ttu-id="6d9fd-154">このチュートリアルはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-154">This tutorial is finished.</span></span> <span data-ttu-id="6d9fd-155">開始に戻るには、「[チュートリアル: ポリシーベースの管理を使用したベストプラクティスの評価](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-155">To return to the start, see [Tutorial: Evaluating Best Practices by Using Policy-Based Management](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="6d9fd-156">チュートリアルの一覧を表示するには [!INCLUDE[ssDE](../includes/ssde-md.md)] 、[[データベースエンジンチュートリアル](../relational-databases/database-engine-tutorials.md)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-156">To see a list of [!INCLUDE[ssDE](../includes/ssde-md.md)] tutorials, click [Database Engine Tutorials](../relational-databases/database-engine-tutorials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9fd-157">参照</span><span class="sxs-lookup"><span data-stu-id="6d9fd-157">See Also</span></span>  
 [<span data-ttu-id="6d9fd-158">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="6d9fd-158">Administer Servers by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
