---
title: サーバーのスタートアップ オプションの構成 (SQL Server 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 405a96208c774a6326a69cf9826a14ca3552eae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713477"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a><span data-ttu-id="3da24-102">サーバーのスタートアップ オプションの構成 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="3da24-102">Configure Server Startup Options (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="3da24-103">このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、[!INCLUDE[ssDE](../../includes/ssde-md.md)] が起動するたびに使用するスタートアップ オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3da24-103">This topic describes how to configure startup options that will be used every time the [!INCLUDE[ssDE](../../includes/ssde-md.md)] starts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="3da24-104">スタートアップ オプションの一覧は、「 [データベース エンジン サービスのスタートアップ オプション](database-engine-service-startup-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3da24-104">For a list of startup options, see [Database Engine Service Startup Options](database-engine-service-startup-options.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3da24-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="3da24-105">Before You Begin</span></span>  
  
### <a name="limitations-and-restrictions"></a><span data-ttu-id="3da24-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="3da24-106">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3da24-107">構成マネージャーは、スタートアップ パラメーターをレジストリに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="3da24-107">Configuration Manager writes startup parameters to the registry.</span></span> <span data-ttu-id="3da24-108">これらのパラメーターは、次回 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を起動したときに有効になります。</span><span class="sxs-lookup"><span data-stu-id="3da24-108">They take effect upon the next startup of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="3da24-109">クラスターでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がオンラインの間にアクティブ サーバー上で変更を行う必要があり、その変更は [!INCLUDE[ssDE](../../includes/ssde-md.md)] を再起動すると有効になります。</span><span class="sxs-lookup"><span data-stu-id="3da24-109">On a cluster, changes must be made on the active server when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is online, and will take effect when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is restarted.</span></span> <span data-ttu-id="3da24-110">他のノードでは、次回のフェールオーバー時にスタートアップ オプションのレジストリが更新されます。</span><span class="sxs-lookup"><span data-stu-id="3da24-110">The registry update of the startup options on the other node will occur upon the next failover.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3da24-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3da24-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3da24-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="3da24-112">Permissions</span></span>  
 <span data-ttu-id="3da24-113">サーバーのスタートアップ オプションの構成は、レジストリの関連エントリを変更できるユーザーのみが使用できます。</span><span class="sxs-lookup"><span data-stu-id="3da24-113">Configuring server startup options is restricted to users who can change the related entries in the registry.</span></span> <span data-ttu-id="3da24-114">該当するユーザーは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3da24-114">This includes the following users.</span></span>  
  
-   <span data-ttu-id="3da24-115">ローカル管理者グループのメンバー。</span><span class="sxs-lookup"><span data-stu-id="3da24-115">Members of the local administrators group.</span></span>  
  
-   <span data-ttu-id="3da24-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって使用されるドメイン アカウント ( [!INCLUDE[ssDE](../../includes/ssde-md.md)] がドメイン アカウントで実行されるように構成されている場合)。</span><span class="sxs-lookup"><span data-stu-id="3da24-116">The domain account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to run under a domain account.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3da24-117">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="3da24-117">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-configure-startup-options"></a><span data-ttu-id="3da24-118">起動オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="3da24-118">To configure startup options</span></span>  
  
1.  <span data-ttu-id="3da24-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3da24-119">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click **SQL Server Services**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3da24-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。</span><span class="sxs-lookup"><span data-stu-id="3da24-120">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="3da24-121">**Windows 10**:</span><span class="sxs-lookup"><span data-stu-id="3da24-121">**Windows 10**:</span></span>  
    >          <span data-ttu-id="3da24-122">Configuration Manager を開くには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **スタートページ**で「「sqlservermanager12.msc」 (の場合)」と入力 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="3da24-122">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="3da24-123">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、12 をより小さい数値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3da24-123">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="3da24-124">SQLServerManager12.msc をクリックすると、構成マネージャーが開きます。</span><span class="sxs-lookup"><span data-stu-id="3da24-124">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="3da24-125">Configuration Manager をスタートページまたはタスクバーにピン留めするには、「Sqlservermanager12.msc」を右クリックし、[**ファイルの場所を開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3da24-125">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="3da24-126">Windows エクスプローラーで「Sqlservermanager12.msc」を右クリックし、[**スタート画面にピン留めする**] または [**タスクバーにピン留め**する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3da24-126">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="3da24-127">**Windows 8**:</span><span class="sxs-lookup"><span data-stu-id="3da24-127">**Windows 8**:</span></span>  
    >          <span data-ttu-id="3da24-128">Configuration Manager を開くには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、**検索**チャームで、[**アプリ**] の下に「 \*\*SQLServerManager \<version> \*\* 」と入力し、 `SQLServerManager12.msc` **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3da24-128">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="3da24-129">右ペインで、[ **SQL Server (***<instance_name>***)**] を右クリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3da24-129">In the right pane, right-click **SQL Server (***<instance_name>***)**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3da24-130">**[起動時のパラメーター]** タブの **[起動時のパラメーターの指定]** ボックスにパラメーターを入力し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3da24-130">On the **Startup Parameters** tab, in the **Specify a startup parameter** box, type the parameter, and then click **Add**.</span></span>  
  
     <span data-ttu-id="3da24-131">たとえば、シングルユーザーモードで起動するには、[ `-m` 起動時の**パラメーターの指定**] ボックスに「」と入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3da24-131">For example, to start in single-user mode, type `-m` in the **Specify a startup parameter** box and then click **Add**.</span></span> <span data-ttu-id="3da24-132">( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をシングル ユーザー モードで再起動する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを停止してください。</span><span class="sxs-lookup"><span data-stu-id="3da24-132">(When you restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="3da24-133">そうしないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって先に接続が行われ、2 番目のユーザーとして接続できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3da24-133">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent might connect first and prevent you from connecting as a second user.)</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="3da24-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="3da24-134">Restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="3da24-135">シングルユーザーモードの使用が完了したら、[起動時のパラメーター] ボックスで、[ `-m` 既存の**パラメーター** ] ボックスのパラメーターを選択し、[**削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3da24-135">After you are finished using single-user mode, in the Startup Parameters box, select the `-m` parameter in the **Existing Parameters** box, and then click **Remove**.</span></span> <span data-ttu-id="3da24-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)] を再起動すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が通常のマルチユーザー モードに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3da24-136">Restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to restore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the typical multi-user mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da24-137">参照</span><span class="sxs-lookup"><span data-stu-id="3da24-137">See Also</span></span>  
 <span data-ttu-id="3da24-138">[シングル ユーザー モードでの SQL Server の起動](start-sql-server-in-single-user-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3da24-138">[Start SQL Server in Single-User Mode](start-sql-server-in-single-user-mode.md) </span></span>  
 <span data-ttu-id="3da24-139">[システム管理者がロックアウトされた場合の SQL Server への接続](connect-to-sql-server-when-system-administrators-are-locked-out.md) </span><span class="sxs-lookup"><span data-stu-id="3da24-139">[Connect to SQL Server When System Administrators Are Locked Out](connect-to-sql-server-when-system-administrators-are-locked-out.md) </span></span>  
 [<span data-ttu-id="3da24-140">SQL Server エージェント サービスの開始、停止、または一時停止</span><span class="sxs-lookup"><span data-stu-id="3da24-140">Start, Stop, or Pause the SQL Server Agent Service</span></span>](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
