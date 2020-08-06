---
title: サーバー ロールの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverrole.members.f1
- SQL12.SWB.SERVERROLE.GENERAL.F1
- sql12.swb.serverrole.memberships.f1
helpviewer_keywords:
- SERVER ROLE, creating
ms.assetid: 74f19992-8082-4ed7-92a1-04fe676ee82d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45c3d5bb9c9c7fdae9abe18ab3cb808cae4c1fa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643747"
---
# <a name="create-a-server-role"></a><span data-ttu-id="ba258-102">サーバー ロールの作成</span><span class="sxs-lookup"><span data-stu-id="ba258-102">Create a Server Role</span></span>
  <span data-ttu-id="ba258-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]で新しいサーバー ロールを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba258-103">This topic describes how to create a new server role in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ba258-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ba258-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ba258-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ba258-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ba258-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ba258-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ba258-107">Security</span><span class="sxs-lookup"><span data-stu-id="ba258-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ba258-108">**新しいサーバー ロールを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="ba258-108">**To create a new server role, using:**</span></span>  
  
     [<span data-ttu-id="ba258-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba258-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ba258-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba258-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ba258-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="ba258-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ba258-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ba258-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ba258-113">データベース レベルのセキュリティ保護可能なリソースに対する権限をサーバー ロールに付与することはできません。</span><span class="sxs-lookup"><span data-stu-id="ba258-113">Server roles cannot be granted permission on database-level securables.</span></span> <span data-ttu-id="ba258-114">データベース ロールを作成するには、「[CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba258-114">To create database roles, see [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ba258-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ba258-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ba258-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="ba258-116">Permissions</span></span>  
  
-   <span data-ttu-id="ba258-117">CREATE SERVER ROLE 権限、または sysadmin 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="ba258-117">Requires CREATE SERVER ROLE permission or membership in the sysadmin fixed server role.</span></span>  
  
-   <span data-ttu-id="ba258-118">さらに、ログインのための *server_principal* に対する IMPERSONATE 権限、 *server_principal*として使用されるサーバー ロールのための ALTER 権限、または server_principal として使用される Windows グループのメンバーシップも必要です。</span><span class="sxs-lookup"><span data-stu-id="ba258-118">Also requires IMPERSONATE on the *server_principal* for logins, ALTER permission for server roles used as the *server_principal*, or membership in a Windows group that is used as the server_principal.</span></span>  
  
-   <span data-ttu-id="ba258-119">AUTHORIZATION オプションを使用してサーバー ロールの所有権を割り当てる場合は、次の権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="ba258-119">When you use the AUTHORIZATION option to assign server role ownership, the following permissions are also required:</span></span>  
  
    -   <span data-ttu-id="ba258-120">サーバー ロールの所有権を別のログインに割り当てるには、そのログインに対する IMPERSONATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ba258-120">To assign ownership of a server role to another login, requires IMPERSONATE permission on that login.</span></span>  
  
    -   <span data-ttu-id="ba258-121">サーバー ロールの所有権を別のサーバー ロールに割り当てるには、割り当て先のサーバー ロールのメンバーシップまたはそのサーバー ロールに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ba258-121">To assign ownership of a server role to another server role, requires membership in the recipient server role or ALTER permission on that server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ba258-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ba258-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-new-server-role"></a><span data-ttu-id="ba258-123">新しいサーバー ロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="ba258-123">To create a new server role</span></span>  
  
1.  <span data-ttu-id="ba258-124">オブジェクト エクスプローラーで、新しいサーバー ロールを作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ba258-124">In Object Explorer, expand the server where you want to create the new server role.</span></span>  
  
2.  <span data-ttu-id="ba258-125">**[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ba258-125">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="ba258-126">**[サーバー ロール]** フォルダーを右クリックし、 **[新しいサーバー ロール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba258-126">Right-click the **Server Roles** folder and select **New Server Role...**.</span></span>  
  
4.  <span data-ttu-id="ba258-127">[**新しいサーバーロール-**_server_role_name_ ] ダイアログボックスの **[全般**] ページで、[**サーバーロール名**] ボックスに新しいサーバーロールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ba258-127">In the **New Server Role -**_server_role_name_ dialog box, on the **General** page, enter a name for the new server role in the **Server role name** box.</span></span>  
  
5.  <span data-ttu-id="ba258-128">**[所有者]** ボックスに、新しいサーバー ロールを所有するサーバー プリンシパルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ba258-128">In the **Owner** box, enter the name of the server principal that will own the new role.</span></span> <span data-ttu-id="ba258-129">または、省略記号 **[...]** をクリックして **[サーバー ログインまたはロールの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba258-129">Alternately, click the ellipsis **(...)** to open the **Select Server Login or Role** dialog box.</span></span>  
  
6.  <span data-ttu-id="ba258-130">**[セキュリティ保護可能なリソース]** で、1 つ以上のサーバーレベルのセキュリティ保護可能なリソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="ba258-130">Under **Securables**, select one or more server-level securables.</span></span> <span data-ttu-id="ba258-131">セキュリティ保護可能なリソースを選択すると、サーバー ロールに、そのセキュリティ保護可能なリソースに対する権限を許可または拒否できます。</span><span class="sxs-lookup"><span data-stu-id="ba258-131">When a securable is selected, this server role can be granted or denied permissions on that securable.</span></span>  
  
7.  <span data-ttu-id="ba258-132">**[権限: 明示的]** ボックスで、選択されたセキュリティ保護可能なリソースに対するこのサーバー ロールの権限について、許可、許可の許可、または拒否を行います。</span><span class="sxs-lookup"><span data-stu-id="ba258-132">In the **Permissions: Explicit** box, select the check box to grant, grant with grant, or deny permission to this server role for the selected securables.</span></span> <span data-ttu-id="ba258-133">選択されたセキュリティ保護可能なリソースすべてに対して権限を許可または拒否できない場合、権限は部分的に選択された形で表されます。</span><span class="sxs-lookup"><span data-stu-id="ba258-133">If a permission cannot be granted or denied to all of the selected securables, the permission is represented as a partial select.</span></span>  
  
8.  <span data-ttu-id="ba258-134">**[メンバー]** ページで **[追加]** ボタンを使用して、新しいサーバー ロールに個人またはグループを表すログインを追加します。</span><span class="sxs-lookup"><span data-stu-id="ba258-134">On the **Members** page, use the **Add** button to add logins that represent individuals or groups to the new server role.</span></span>  
  
9. <span data-ttu-id="ba258-135">ユーザー定義のサーバー ロールを、別のサーバー ロールのメンバーにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ba258-135">A user-defined server role can be a member of another server role.</span></span> <span data-ttu-id="ba258-136">現在のユーザー定義のサーバー ロールを、選択したサーバー ロールのメンバーにする場合は、 **[メンバーシップ]** ページでチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ba258-136">On the **Memberships** page, select a check box to make the current user-defined server role a member of a selected server role.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ba258-137">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ba258-137">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-new-server-role"></a><span data-ttu-id="ba258-138">新しいサーバー ロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="ba258-138">To create a new server role</span></span>  
  
1.  <span data-ttu-id="ba258-139">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ba258-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ba258-140">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba258-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ba258-141">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba258-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Creates the server role auditors that is owned the securityadmin fixed server role.  
    USE master;  
    CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
    GO  
    ```  
  
 <span data-ttu-id="ba258-142">詳細については、「[CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba258-142">For more information, see [CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql).</span></span>  
  
  
