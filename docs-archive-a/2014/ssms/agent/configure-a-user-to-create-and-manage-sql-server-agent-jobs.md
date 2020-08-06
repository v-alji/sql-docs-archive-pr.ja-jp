---
title: SQL Server エージェント ジョブ ステップを作成および管理するユーザーの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83313389b3b872004fb23b0babdad19cfb5b8e7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645336"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a><span data-ttu-id="8d188-102">Configure a User to Create and Manage SQL Server Agent Jobs</span><span class="sxs-lookup"><span data-stu-id="8d188-102">Configure a User to Create and Manage SQL Server Agent Jobs</span></span>
  <span data-ttu-id="8d188-103">このトピックでは、エージェントジョブを作成または実行するユーザーを構成する方法について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8d188-103">This topic describes how to configure a user to create or execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
-   <span data-ttu-id="8d188-104">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="8d188-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="8d188-105">**SQL Server エージェント ジョブを作成または管理するユーザーを構成するために使用するもの:**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="8d188-105">**To configure a user to create and manage SQL Server Agent jobs, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8d188-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="8d188-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8d188-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8d188-107">Security</span></span>  
 <span data-ttu-id="8d188-108">エージェントジョブを作成または実行するユーザーを構成するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Msdb データベースの SQLAgentUserRole、SQLAgentReaderRole、または SQLAgentOperatorRole のいずれかのエージェント固定データベースロールに、既存の SQL Server ログインまたは msdb ロールを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d188-108">To configure a user to create or execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, you must first add an existing SQL Server login or msdb role to one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the msdb database: SQLAgentUserRole, SQLAgentReaderRole, or SQLAgentOperatorRole.</span></span>  
  
 <span data-ttu-id="8d188-109">既定では、これらのデータベース ロールのメンバーは、メンバー自身が実行する独自のジョブ ステップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8d188-109">By default, members of these database roles can create their own job steps that run as themselves.</span></span> <span data-ttu-id="8d188-110">このような管理者権限のないユーザーが他の種類のジョブ ステップ ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージなど) を実行するには、プロキシ アカウントへのアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="8d188-110">If these non-administrative users want to run jobs that execute other job step types (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages), they will need to have access to a proxy account.</span></span> <span data-ttu-id="8d188-111">sysadmin 固定サーバー ロールのすべてのメンバーには、プロキシ アカウントを作成、変更、および削除する権限があります。</span><span class="sxs-lookup"><span data-stu-id="8d188-111">All members of the sysadmin fixed server role have permission to create, modify, and delete proxy accounts.</span></span> <span data-ttu-id="8d188-112">これら [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定のデータベース ロールに関連付けられている権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d188-112">For more information about the permissions that are associated with these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8d188-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="8d188-113">Permissions</span></span>  
 <span data-ttu-id="8d188-114">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d188-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="8d188-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="8d188-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8d188-116">**SQL ログインまたは msdb ロールを SQL Server エージェント固定データベース ロールに追加するには**</span><span class="sxs-lookup"><span data-stu-id="8d188-116">**To add a SQL login or msdb role to a SQL Server Agent fixed database role**</span></span>  
  
1.  <span data-ttu-id="8d188-117">**オブジェクト エクスプローラー**で、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8d188-117">In **Object Explorer**, expand a server.</span></span>  
  
2.  <span data-ttu-id="8d188-118">**[セキュリティ]** を展開し、 **[ログイン]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="8d188-118">Expand **Security**, and then expand **Logins**.</span></span>  
  
3.  <span data-ttu-id="8d188-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールに追加するログインを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d188-119">Right-click the login you wish to add to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database role, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="8d188-120">[**ログインのプロパティ**] ダイアログボックスの [**ユーザーマッピング**] ページで、を含む行を選択し `msdb` ます。</span><span class="sxs-lookup"><span data-stu-id="8d188-120">On the **User Mapping** page of the **Login Properties** dialog box, select the row containing `msdb`.</span></span>  
  
5.  <span data-ttu-id="8d188-121">**[データベース ロールのメンバーシップ: msdb]** で、該当する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8d188-121">Under **Database role membership for: msdb**, check the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database role.</span></span>  
  
 <span data-ttu-id="8d188-122">**SQL Server エージェント ジョブ ステップを作成および管理できるようにプロキシ アカウントを構成するには**</span><span class="sxs-lookup"><span data-stu-id="8d188-122">**To configure a proxy account to create and manage SQL Server Agent job steps**</span></span>  
  
1.  <span data-ttu-id="8d188-123">**オブジェクト エクスプローラー**で、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8d188-123">In **Object Explorer**, expand a server.</span></span>  
  
2.  <span data-ttu-id="8d188-124">**[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="8d188-124">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="8d188-125">**[プロキシ]** を右クリックして **[新しいプロキシ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d188-125">Right-click **Proxies** and select **New Proxy**.</span></span>  
  
4.  <span data-ttu-id="8d188-126">**[新しいプロキシ アカウント]** ダイアログの **[全般]** ページで、新しいプロキシのプロキシ名、資格情報名、および説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="8d188-126">On the **General** page of the **New Proxy Account** dialog, specify the proxy name, credential name, and description for the new proxy.</span></span> <span data-ttu-id="8d188-127">SQL Server エージェントのプロキシを作成する前に、まず資格情報を作成する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8d188-127">Note that you must create a credential first before creating a SQL Server Agent proxy.</span></span> <span data-ttu-id="8d188-128">資格情報の作成の詳細については、「 [create a credential](../../relational-databases/security/authentication-access/create-a-credential.md) 」と「 [Create credential &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d188-128">For more information about creating a credential, see [Create a Credential](../../relational-databases/security/authentication-access/create-a-credential.md) and [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>  
  
5.  <span data-ttu-id="8d188-129">このプロキシに適したサブシステムを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d188-129">Check the appropriate subsystems for this proxy.</span></span>  
  
6.  <span data-ttu-id="8d188-130">**[プリンシパル]** ページで、プロキシ アカウントへのアクセスを許可するログインまたはロールを追加するか、あるいは拒否するログインまたはロールを削除します。</span><span class="sxs-lookup"><span data-stu-id="8d188-130">On the **Principals** page, add or remove logins or roles to grant or remove access to the proxy account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d188-131">参照</span><span class="sxs-lookup"><span data-stu-id="8d188-131">See Also</span></span>  
 [<span data-ttu-id="8d188-132">SQL Server エージェントのセキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="8d188-132">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
