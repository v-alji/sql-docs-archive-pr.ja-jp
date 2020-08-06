---
title: 登録済みサーバーを使用して要求時評価を実行する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a3a06efaabff7e94e5b560744f0e1c739831042a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631416"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a><span data-ttu-id="4006a-102">登録済みサーバーを使用した要求時評価の実行</span><span class="sxs-lookup"><span data-stu-id="4006a-102">Perform an On-Demand Evaluation by Using Registered Servers</span></span>

  <span data-ttu-id="4006a-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスに対して登録済みサーバーを使用して、ベスト プラクティス ポリシーの要求時評価を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4006a-103">You can perform an on-demand evaluation of best practices policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using Registered Servers.</span></span> <span data-ttu-id="4006a-104">使用できるのは、ローカル サーバー グループまたは中央管理サーバーのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="4006a-104">You can use either local server groups or a central management server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4006a-105">[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 以降のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行しているサーバー グループ メンバーに対して、ベスト プラクティス ポリシーの要求時評価を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4006a-105">You can perform an on-demand evaluation of best practices policies against server group members that are running [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] or a later version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4006a-106">ただし、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] または [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] でサポートされていない一部のプロパティがポリシーによって参照される場合は、例外エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="4006a-106">However, you may receive an exception error if there are some properties that are referred to by a policy that are not supported in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] or [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4006a-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="4006a-107">Prerequisites</span></span>  
 <span data-ttu-id="4006a-108">この作業を実行するには、登録済みサーバーでサーバー登録を 1 つ以上構成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4006a-108">To perform this task, you must have configured one or more server registrations in Registered Servers.</span></span> <span data-ttu-id="4006a-109">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4006a-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="4006a-110">サーバー グループの作成または編集 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4006a-110">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   <span data-ttu-id="4006a-111">[接続されたサーバー &#40;SQL Server Management Studio&#41;に登録](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)します。</span><span class="sxs-lookup"><span data-stu-id="4006a-111">[Register a Connected Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).</span></span>  
  
-   [<span data-ttu-id="4006a-112">中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4006a-112">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a><span data-ttu-id="4006a-113">サーバー グループに対してベスト プラクティス ポリシーを評価するには</span><span class="sxs-lookup"><span data-stu-id="4006a-113">To evaluate best practices policies against a server group</span></span>  
  
1.  <span data-ttu-id="4006a-114">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[登録済みサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-114">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="4006a-115">構成に応じて [**データベースエンジン**] を展開し、[**ローカルサーバーグループ**] または [**中央管理サーバー**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="4006a-115">Expand **Database Engine**, and then expand either **Local Server Groups**, or **Central Management Servers**, depending on your configuration.</span></span>  
  
3.  <span data-ttu-id="4006a-116">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="4006a-116">Do either of the following:</span></span>  
  
    -   <span data-ttu-id="4006a-117">ローカルサーバーグループまたは中央管理サーバーで管理されているすべてのサーバーに対してポリシーを評価するには、ローカルサーバーグループ名または中央管理サーバー名を右クリックし、[**ポリシーの評価**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-117">To evaluate the policies against all servers that are managed by the local server group or the central management server, right-click the local server group name or the central management server name, and then click **Evaluate Policies**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4006a-118">中央管理サーバーを通じてポリシーを評価する場合、ポリシーは中央管理サーバー自体に対しては評価されません。</span><span class="sxs-lookup"><span data-stu-id="4006a-118">When you evaluate policies through a central management server, the policies are not evaluated against the central management server itself.</span></span>  
  
    -   <span data-ttu-id="4006a-119">特定のサーバーまたはサーバーグループに対してポリシーを評価するには、[**ローカルサーバーグループ**] または [中央管理サーバー名] を展開し、ポリシーを評価するサーバーまたはサーバーグループを右クリックして、[**ポリシーの評価**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-119">To evaluate the policies against a specific server or server group, expand **Local Server Groups** or the central management server name, right-click the server or server group that you want to evaluate policies against, and then click **Evaluate Policies**.</span></span>  
  
4.  <span data-ttu-id="4006a-120">[**ポリシーの評価**] ダイアログボックスの [**ソース**] ボックスの横にある省略記号ボタン ([**...**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-120">In the **Evaluate Policies** dialog box, next to the **Source** box, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="4006a-121">[**ソースの選択**] ダイアログボックスで、評価するポリシーファイルのソースとして [**ファイル**] または [**サーバー** ] を選択できます。</span><span class="sxs-lookup"><span data-stu-id="4006a-121">In the **Select Source** dialog box, you can select either **Files** or **Server** as the source of the policy files to evaluate.</span></span> <span data-ttu-id="4006a-122">[**サーバー**] をクリックすると、以前にローカルサーバーまたはリモートサーバー上のポリシーベースの管理にインポートされたベストプラクティスポリシーの要求時評価を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4006a-122">If you click **Server**, you can perform an on-demand evaluation of any best practices policies that were previously imported into Policy-Based Management on a local or remote server.</span></span> <span data-ttu-id="4006a-123">このチュートリアルでは、[**ファイル**] をクリックし、評価する個々のポリシーファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4006a-123">In this tutorial, you will click **Files**, and then select the individual policy files that you want to evaluate.</span></span> <span data-ttu-id="4006a-124">そのためには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4006a-124">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="4006a-125">[**ファイル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-125">Click **Files**.</span></span>  
  
    2.  <span data-ttu-id="4006a-126">[**ファイル**] の横にある省略記号ボタン ([.**..**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-126">Next to **Files**, click the ellipsis (**...**) button.</span></span>  
  
    3.  <span data-ttu-id="4006a-127">評価する1つまたは複数の .xml ポリシーファイルを選択し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-127">Select one or more .xml policy files to evaluate, and then click **Open**.</span></span>  
  
         <span data-ttu-id="4006a-128">選択したファイルの一覧が [**ファイル**] ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4006a-128">The list of selected files appears in the **Files** box.</span></span>  
  
    4.  <span data-ttu-id="4006a-129">[**ソースの選択**] ダイアログボックスで、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-129">In the **Select Source** dialog box, click **OK**.</span></span>  
  
    5.  <span data-ttu-id="4006a-130">[**ポリシーの読み込み**] ダイアログボックスが表示されたら、[**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-130">If the **Loading Policies** dialog box appears, click **Close**.</span></span>  
  
     <span data-ttu-id="4006a-131">選択したポリシーは、[ポリシーの**選択**] ページに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="4006a-131">The policies that you selected are listed on the **Policy Selection** page.</span></span> <span data-ttu-id="4006a-132">ポリシーの横に警告アイコンが表示された場合、そのポリシーにスクリプトが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="4006a-132">Be aware that a warning icon next to a policy indicates that the policy contains scripts.</span></span>  
  
6.  <span data-ttu-id="4006a-133">[**評価**] をクリックしてポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="4006a-133">Click **Evaluate** to evaluate the policies.</span></span>  
  
7.  <span data-ttu-id="4006a-134">一部のポリシー エラーでは、ポリシー ベースの管理機能によってポリシーへの準拠を対象に直ちに適用できます。</span><span class="sxs-lookup"><span data-stu-id="4006a-134">For some policy failures, Policy-Based Management enables you to immediately enforce policy compliance on the target.</span></span> <span data-ttu-id="4006a-135">このようなエラーの場合、エラーが発生したポリシーの横にチェック ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4006a-135">For such failures, a check box will appear next to the failed policy.</span></span> <span data-ttu-id="4006a-136">チェックボックスをオンにした場合、または失敗したポリシーが含まれている行をクリックすると、評価に失敗したターゲットインスタンスの横にある [**対象の詳細**] ペインにチェックボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4006a-136">If you select the check box, or click the row with the failed policy, check boxes appear in the **Target details** pane next to the target instances that failed the evaluation.</span></span> <span data-ttu-id="4006a-137">いずれかのチェックボックスをオンにすると、[**適用**] ボタンが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4006a-137">If any of the check boxes are selected, the **Apply** button becomes available.</span></span> <span data-ttu-id="4006a-138">[**適用**] をクリックすると、選択したターゲットインスタンスの準拠していない設定が自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="4006a-138">When you click **Apply**, the noncompliant setting will be automatically updated on the target instances that you selected.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="4006a-139">ポリシー設定を十分に理解してから、対象インスタンスを自動更新してください。</span><span class="sxs-lookup"><span data-stu-id="4006a-139">Make sure that you fully understand the policy setting before automatically updating a target instance.</span></span> <span data-ttu-id="4006a-140">1つ以上のチェックボックスをオンにした後、[**スクリプト**] をクリックし、出力場所を選択して、変更を適用する前に基になるコードを確認できるようにすることをお勧めし [!INCLUDE[tsql](../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="4006a-140">We recommend that after you select one or more check boxes, you click **Script**, and choose an output location so that you can review the underlying [!INCLUDE[tsql](../includes/tsql-md.md)] code before you apply the changes.</span></span>  
  
8.  <span data-ttu-id="4006a-141">ポリシーの詳細な結果を表示するには、[**結果**] テーブルでポリシーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4006a-141">To view detailed results for a policy, click the policy in the **Results** table.</span></span> <span data-ttu-id="4006a-142">[**対象の詳細**テーブルには、各インスタンスの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4006a-142">The **Target details** table shows the details for each instance.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="4006a-143">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="4006a-143">Next Lesson</span></span>  
 [<span data-ttu-id="4006a-144">レッスン 2: スケジュールに基づくベスト プラクティス ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="4006a-144">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a><span data-ttu-id="4006a-145">参照</span><span class="sxs-lookup"><span data-stu-id="4006a-145">See Also</span></span>  
 <span data-ttu-id="4006a-146">[ポリシーベースの管理を使用したベストプラクティスの監視と実施](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="4006a-146">[Monitor and Enforce Best Practices by Using Policy-Based Management](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md) </span></span>  
 [<span data-ttu-id="4006a-147">中央管理サーバーを使用して複数のサーバーを管理する</span><span class="sxs-lookup"><span data-stu-id="4006a-147">Administer Multiple Servers Using Central Management Servers</span></span>](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
