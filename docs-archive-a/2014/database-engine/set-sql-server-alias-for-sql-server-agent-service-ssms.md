---
title: SQL Server エージェントサービスの SQL Server エイリアスを設定します (SQL Server Management Studio)。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b178d91a47d907b182ef7962b98c7f22d4454094
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632076"
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a><span data-ttu-id="a2020-102">Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a2020-102">Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)</span></span>
  <span data-ttu-id="a2020-103">このトピックで [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に接続するために使用するエージェントの別名を設定する方法について説明し [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a2020-103">This topic describes how to set a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] alias for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent to use to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a2020-104">既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービスは、追加のクライアント構成を必要としない動的サーバー名を使用することによって、名前付きパイプを経由して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a2020-104">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] over named pipes by using dynamic server names that require no additional client configuration.</span></span> <span data-ttu-id="a2020-105">既定のネットワーク転送を使用しない場合、または、代替の名前付きパイプを使用して受信待ちする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続する場合は、サーバー接続の別名を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2020-105">You need to configure a server connection alias only if you are not using the default network transport or if you are connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that listens on an alternate named pipe.</span></span>  
  
 <span data-ttu-id="a2020-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a2020-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a2020-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a2020-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a2020-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2020-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a2020-109">Security</span><span class="sxs-lookup"><span data-stu-id="a2020-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="a2020-110">SQL Server Management Studio を使用して SQL Server エージェント サービスの SQL Server 別名を設定する方法</span><span class="sxs-lookup"><span data-stu-id="a2020-110">To set a SQL Server Alias for the SQL Server Agent Service using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a2020-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="a2020-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a2020-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2020-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="a2020-113">のローカル インスタンスを参照する別名を選択しないと、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]エージェントは正常に機能しません。</span><span class="sxs-lookup"><span data-stu-id="a2020-113">Agent will not work correctly unless you select an alias that refers to the local instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a2020-114">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="a2020-114">Object Explorer only displays the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a2020-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a2020-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a2020-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="a2020-116">Permissions</span></span>  
 <span data-ttu-id="a2020-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2020-117">To perform its functions, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a2020-118">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a2020-118">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="a2020-119">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="a2020-119">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="a2020-120">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="a2020-120">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="a2020-121">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="a2020-121">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="a2020-122">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="a2020-122">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="a2020-123">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2020-123">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a2020-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a2020-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a><span data-ttu-id="a2020-125">SQL Server エージェント サービスの SQL Server 別名を設定する方法</span><span class="sxs-lookup"><span data-stu-id="a2020-125">To set a SQL Server Alias for the SQL Server Agent Service</span></span>  
  
1.  <span data-ttu-id="a2020-126">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスに接続して、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2020-126">In the **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a2020-127">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2020-127">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a2020-128">[ **SQL Server エージェントのプロパティ**_server_name_ ] ダイアログボックスの [**ページの選択**] で、[**接続**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2020-128">In the **SQL Server Agent Properties**_server_name_ dialog box, under **Select a page**, select **Connection**, and</span></span>  
  
4.  <span data-ttu-id="a2020-129">**[別名ローカル ホスト サーバー]** ボックスに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントが接続するサーバーの別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="a2020-129">In the **Alias local host server** box, type the alias of the server to which [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should connect.</span></span>  
  
5.  <span data-ttu-id="a2020-130">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2020-130">Click **OK**.</span></span>  
  
  
