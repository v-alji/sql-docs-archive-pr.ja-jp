---
title: SQL Server エージェント サービスの開始、停止、または一時停止 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2feb6a18c602271b1bec871fbfc9793979b100e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711569"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a><span data-ttu-id="f74c8-102">Start, Stop, or Pause the SQL Server Agent Service</span><span class="sxs-lookup"><span data-stu-id="f74c8-102">Start, Stop, or Pause the SQL Server Agent Service</span></span>
  <span data-ttu-id="f74c8-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の SQL Server エージェント サービスを開始、停止、または一時停止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f74c8-103">This topic describes how to start, stop, or restart the SQL Server Agent Service in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="f74c8-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、オペレーティング システムの起動時に自動的に開始するよう構成したり、ジョブの完了が必要なときに手動で開始できます。</span><span class="sxs-lookup"><span data-stu-id="f74c8-104">You can configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to start automatically when the operating system starts, or you can start it manually when you need to complete jobs.</span></span> <span data-ttu-id="f74c8-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを停止または一時停止して、ジョブ、オペレーターへの通知、および警告を中断できます。</span><span class="sxs-lookup"><span data-stu-id="f74c8-105">You can stop or pause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to suspend jobs, operator notifications, and alerts.</span></span>  
  
 <span data-ttu-id="f74c8-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f74c8-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f74c8-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f74c8-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f74c8-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f74c8-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f74c8-109">Security</span><span class="sxs-lookup"><span data-stu-id="f74c8-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="f74c8-110">SQL Server Management Studio を使用して SQL Server エージェント サービスを開始、停止、または一時停止するには</span><span class="sxs-lookup"><span data-stu-id="f74c8-110">To start, stop, or restart the SQL Server Agent Service using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f74c8-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="f74c8-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f74c8-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f74c8-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="f74c8-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、管理タスクを自動化するためにサービスとして実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f74c8-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running as a service in order to automate administrative tasks.</span></span> <span data-ttu-id="f74c8-114">詳細については、「 [Configure SQL Server Agent](configure-sql-server-agent.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f74c8-114">For more information, see [Configure SQL Server Agent](configure-sql-server-agent.md).</span></span>  
  
-   <span data-ttu-id="f74c8-115">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="f74c8-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f74c8-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f74c8-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f74c8-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="f74c8-117">Permissions</span></span>  
 <span data-ttu-id="f74c8-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f74c8-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f74c8-119">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f74c8-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="f74c8-120">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="f74c8-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="f74c8-121">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="f74c8-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="f74c8-122">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="f74c8-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="f74c8-123">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="f74c8-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="f74c8-124">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f74c8-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f74c8-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f74c8-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a><span data-ttu-id="f74c8-126">SQL Server エージェント サービスを開始、停止、または一時停止するには</span><span class="sxs-lookup"><span data-stu-id="f74c8-126">To start, stop, or restart the SQL Server Agent Service</span></span>  
  
1.  <span data-ttu-id="f74c8-127">**オブジェクト エクスプ ローラー**で、プラス記号をクリックして、管理する SQL Server エージェント サービスを展開します。</span><span class="sxs-lookup"><span data-stu-id="f74c8-127">In **Object Explorer**, click the plus sign to expand the server where you want to manage SQL Server Agent Service.</span></span>  
  
2.  <span data-ttu-id="f74c8-128">**[SQL Server エージェント]** を右クリックし、 **[開始]**、 **[停止]**、または **[再起動]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f74c8-128">Right-click **SQL Server Agent**, and then select either **Start**, **Stop**, or **Restart**.</span></span>  
  
3.  <span data-ttu-id="f74c8-129">**[ユーザー アカウント制御]** ダイアログ ボックスで、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f74c8-129">In the **User Account Control** dialog box, click **Yes**.</span></span>  
  
4.  <span data-ttu-id="f74c8-130">アクションを実行するかどうかを確認するメッセージが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f74c8-130">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
 <span data-ttu-id="f74c8-131">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f74c8-131">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f74c8-132">データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動</span><span class="sxs-lookup"><span data-stu-id="f74c8-132">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
-   [<span data-ttu-id="f74c8-133">SQL Server エージェントの自動起動 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f74c8-133">Autostart SQL Server Agent &#40;SQL Server Management Studio&#41;</span></span>](autostart-sql-server-agent-sql-server-management-studio.md)  
  
  
