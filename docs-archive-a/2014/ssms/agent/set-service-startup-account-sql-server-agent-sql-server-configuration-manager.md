---
title: SQL Server エージェントのサービス開始アカウントを設定する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: stevestein
ms.author: sstein
ms.openlocfilehash: 63e5ba7c24f1aa1a3f79f80e5ca28c02a0cd5812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715002"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a><span data-ttu-id="7b794-102">Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)</span><span class="sxs-lookup"><span data-stu-id="7b794-102">Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="7b794-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス開始アカウントでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを実行する Windows アカウントとそのネットワーク権限を定義します。</span><span class="sxs-lookup"><span data-stu-id="7b794-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service startup account defines the Windows account that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs as, as well as its network permissions.</span></span> <span data-ttu-id="7b794-104">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 構成マネージャーを使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]エージェント サービス アカウントを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b794-104">This topic describes how to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="7b794-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="7b794-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7b794-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="7b794-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7b794-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7b794-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7b794-108">Security</span><span class="sxs-lookup"><span data-stu-id="7b794-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="7b794-109">SQL Server Management Studio を使用して SQL Server エージェントのサービス開始アカウントを設定するには</span><span class="sxs-lookup"><span data-stu-id="7b794-109">To set the Service Startup Account for SQL Server Agent using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7b794-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="7b794-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7b794-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7b794-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7b794-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを操作する場合、サービス開始アカウントが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators グループのメンバーである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7b794-112">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer requires that the service startup account be a member of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators group.</span></span> <span data-ttu-id="7b794-113">ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス開始アカウントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b794-113">However, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service startup account must be a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin fixed server role.</span></span> <span data-ttu-id="7b794-114">マルチサーバー ジョブの処理を使用する場合は、アカウントはマスター サーバーの msdb データベースの TargetServersRole ロールのメンバーでもなければなりません。</span><span class="sxs-lookup"><span data-stu-id="7b794-114">The account must also be a member of the msdb database role TargetServersRole on the master server if multiserver job processing is used.</span></span>  
  
-   <span data-ttu-id="7b794-115">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="7b794-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7b794-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7b794-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7b794-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="7b794-117">Permissions</span></span>  
 <span data-ttu-id="7b794-118">この機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の固定サーバーロールのメンバーであるアカウントの資格情報を使用するようにエージェントを構成する必要があり `sysadmin` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7b794-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the `sysadmin` fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b794-119">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7b794-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="7b794-120">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="7b794-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="7b794-121">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="7b794-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="7b794-122">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="7b794-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="7b794-123">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="7b794-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="7b794-124">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b794-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7b794-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7b794-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a><span data-ttu-id="7b794-126">SQL Server エージェントのサービス開始アカウントを設定するには</span><span class="sxs-lookup"><span data-stu-id="7b794-126">To set the Service Startup Account for SQL Server Agent</span></span>  
  
1.  <span data-ttu-id="7b794-127">**[登録済みサーバー]** で、プラス記号をクリックして **[データベース エンジン]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="7b794-127">In **Registered Servers**, click the plus sign to expand **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="7b794-128">プラス記号をクリックして、 **[ローカル サーバー グループ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7b794-128">Click the plus sign to expand the **Local Server Groups** folder.</span></span>  
  
3.  <span data-ttu-id="7b794-129">サービス開始カウントを設定するサーバー インスタンスを右クリックし、**[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b794-129">Right-click the server instance where you want set up the Service Startup Account, and select **SQL Server Configuration Manager...**.</span></span>  
  
4.  <span data-ttu-id="7b794-130">**[ユーザー アカウント制御]** ダイアログ ボックスで、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b794-130">In the **User Account Control** dialog box, click **Yes**.</span></span>  
  
5.  <span data-ttu-id="7b794-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのコンソール ペインで、 **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b794-131">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the console pane, select **SQL Server Services**.</span></span>  
  
6.  <span data-ttu-id="7b794-132">詳細ペインで、サービス開始アカウントを変更する **(server_name)**_]_( *server_name* は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント インスタンスの名前) を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b794-132">In the details pane, right-click **SQL Server Agent**_(server_name)_, where *server_name* is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent instance for which you want to change the service startup account, and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="7b794-133">[ **SQL Server エージェント**_(server_name)_ **のプロパティ**] ダイアログボックスの [**ログオン**] タブで、[次のアカウントで**ログオン**] で次のオプションのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="7b794-133">In the **SQL Server Agent**_(server_name)_ **Properties** dialog box, in the **Log On** tab, select one of the following options under **Log on as**:</span></span>  
  
    -   <span data-ttu-id="7b794-134">**[ビルトイン アカウント]**: ジョブがローカル サーバーのリソースだけを必要とする場合はこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7b794-134">**Built-in account**: select this option if your jobs require resources from the local server only.</span></span> <span data-ttu-id="7b794-135">Windows ビルトイン アカウントの選択方法については、「 [SQL Server エージェント サービスのアカウントの選択](https://msdn.microsoft.com/library/ms191543.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7b794-135">For information about how to choose a Windows built-in account type, see [Selecting an Account for SQL Server Agent Service.](https://msdn.microsoft.com/library/ms191543.aspx)</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="7b794-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、 **では** Local Service [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]アカウントはサポートしません。</span><span class="sxs-lookup"><span data-stu-id="7b794-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service does not support the **Local Service** account in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
    -   <span data-ttu-id="7b794-137">**[このアカウント]**: ジョブがネットワーク経由のリソース (アプリケーション リソースを含む) を必要とする場合、他の Windows アプリケーション ログにイベントを転送する場合、またはメールやポケットベルを使用してオペレーターに通知する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7b794-137">**This account**: select this option if your jobs require resources across the network, including application resources; if you want to forward events to other Windows application logs; or if you want to notify operators through e-mail or pagers.</span></span>  
  
         <span data-ttu-id="7b794-138">このオプションを選択する場合:</span><span class="sxs-lookup"><span data-stu-id="7b794-138">If you select this option:</span></span>  
  
        1.  <span data-ttu-id="7b794-139">**[アカウント名]** ボックスに、SQL Server エージェントを実行するために使用するアカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b794-139">In the **Account Name** box, enter the account that will be used to run SQL Server Agent.</span></span> <span data-ttu-id="7b794-140">または、 **[参照]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを開き、使用するアカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="7b794-140">Alternately, click **Browse** to open the **Select User or Group** dialog box and select the account to use.</span></span>  
  
        2.  <span data-ttu-id="7b794-141">**[パスワード]** ボックスに、アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b794-141">In the **Password** box, enter the password for the account.</span></span> <span data-ttu-id="7b794-142">**[パスワードの確認入力]** ボックスに、パスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="7b794-142">Re-enter the password in the **Confirm password** box.</span></span>  
  
8.  <span data-ttu-id="7b794-143">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b794-143">Click **OK**.</span></span>  
  
9. <span data-ttu-id="7b794-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[閉じる]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b794-144">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click the **Close** button.</span></span>  
  
  
