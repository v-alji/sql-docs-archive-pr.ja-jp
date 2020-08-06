---
title: SQL Server エージェントの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81c78faf733fac5ffb9a6e74dbf03f8caaff03d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640326"
---
# <a name="configure-sql-server-agent"></a><span data-ttu-id="c8c7a-102">SQL Server エージェントの構成</span><span class="sxs-lookup"><span data-stu-id="c8c7a-102">Configure SQL Server Agent</span></span>
  <span data-ttu-id="c8c7a-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール中に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントのいくつかの構成オプションを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-103">This topic describes how to specify some configuration options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent during installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c8c7a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの構成オプションの完全なセットは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO)、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ストアド プロシージャでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-104">The full set of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent configuration options is only available within [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO), or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stored procedures.</span></span>  
  
 <span data-ttu-id="c8c7a-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c8c7a-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c8c7a-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c8c7a-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c8c7a-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c8c7a-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c8c7a-108">Security</span><span class="sxs-lookup"><span data-stu-id="c8c7a-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="c8c7a-109">SQL Server エージェントを構成するには</span><span class="sxs-lookup"><span data-stu-id="c8c7a-109">To configure SQL Server Agent</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c8c7a-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="c8c7a-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c8c7a-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c8c7a-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c8c7a-112">ジョブ、オペレーター、警告、および **エージェント サービスを管理するには、** のオブジェクト エクスプローラーで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [SQL Server エージェント] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-112">Click **SQL Server Agent** in Object Explorer of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to administer jobs, operators, alerts, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="c8c7a-113">ただし、オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-113">However, Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="c8c7a-114">フェールオーバー クラスター インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスでは自動再起動を有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-114">Auto-restart should not be enabled for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on failover cluster instances.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c8c7a-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c8c7a-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c8c7a-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="c8c7a-116">Permissions</span></span>  
 <span data-ttu-id="c8c7a-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-117">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c8c7a-118">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-118">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="c8c7a-119">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="c8c7a-119">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="c8c7a-120">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="c8c7a-120">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="c8c7a-121">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="c8c7a-121">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="c8c7a-122">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="c8c7a-122">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="c8c7a-123">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-123">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c8c7a-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c8c7a-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-sql-server-agent"></a><span data-ttu-id="c8c7a-125">SQL Server エージェントを構成するには</span><span class="sxs-lookup"><span data-stu-id="c8c7a-125">To configure SQL Server Agent</span></span>  
  
1.  <span data-ttu-id="c8c7a-126">**[スタート]** をクリックします。 **[スタート]**  メニューの **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-126">Click the **Start** button, and then, on the **Start**  menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="c8c7a-127">[コントロール パネル] で、 **[システムとセキュリティ]** をクリックします。次に、 **[管理ツール]** をクリックし、 **[ローカル セキュリティ ポリシー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-127">In Control Panel, click **System and Security**, click **Administrative Tools**, and then select **Local Security Policy**.</span></span>  
  
3.  <span data-ttu-id="c8c7a-128">[ローカル セキュリティ ポリシー] で、シェブロンをクリックして **[ローカル ポリシー]** フォルダーを展開し、 **[ユーザー権利の割り当て]** フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-128">In Local Security Policy, click the chevron to expand the **Local Policies** folder, and then click the **User Rights Assignment** folder.</span></span>  
  
4.  <span data-ttu-id="c8c7a-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での使用のために構成する権限を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-129">Right-click a permission that you want to configure for use with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="c8c7a-130">権限のプロパティ ダイアログ ボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの実行に使用するアカウントが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-130">In the permission's properties dialog box, verify that the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs is listed.</span></span> <span data-ttu-id="c8c7a-131">表示されていない場合は、 **[ユーザーまたはグループの追加]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの実行に使用するアカウントを **[ユーザー、コンピューター、サービス アカウント、またはグループの選択]** ダイアログ ボックスに入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-131">If not, click **Add User or Group**, enter the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs in the **Select Users, Computers, Service Accounts, or Groups** dialog box, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="c8c7a-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行するために追加するそれぞれの権限に対して、この操作を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-132">Repeat for each permission that you want to add to run with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="c8c7a-133">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8c7a-133">When finished, click **OK**.</span></span>  
  
  
