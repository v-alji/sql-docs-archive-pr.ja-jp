---
title: 管理者以外のユーザーがレプリケーション モニターを使用できるようにする | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4a7699c555086d627e4c3a52ea70acf931ea1af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634398"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a><span data-ttu-id="cc363-102">管理者以外のユーザーがレプリケーション モニターを使用できるようにする</span><span class="sxs-lookup"><span data-stu-id="cc363-102">Allow Non-Administrators to Use Replication Monitor</span></span>
  <span data-ttu-id="cc363-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、管理者以外のユーザーがレプリケーション モニターを使用できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc363-103">This topic describes how to allow non-administrators to use Replication Monitor in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cc363-104">レプリケーション モニターは、次のロールのメンバーになっているユーザーが使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc363-104">Replication Monitor can be used by users who are members of the following roles:</span></span>  
  
-   <span data-ttu-id="cc363-105">**sysadmin** 固定サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="cc363-105">The **sysadmin** fixed server role.</span></span>  
  
     <span data-ttu-id="cc363-106">これらのユーザーはレプリケーションを監視することができ、また、エージェント スケジュール、エージェント プロファイルなどのレプリケーション プロパティの変更に対するフル コントロール権限を持っています。</span><span class="sxs-lookup"><span data-stu-id="cc363-106">These users can monitor replication and have full control over changing replication properties such as agent schedules, agent profiles, and so on.</span></span>  
  
-   <span data-ttu-id="cc363-107">`replmonitor`ディストリビューションデータベースのデータベースロールです。</span><span class="sxs-lookup"><span data-stu-id="cc363-107">The `replmonitor` database role in the distribution database.</span></span>  
  
     <span data-ttu-id="cc363-108">これらのユーザーはレプリケーションを監視できますが、レプリケーション プロパティは変更できません。</span><span class="sxs-lookup"><span data-stu-id="cc363-108">These users can monitor replication, but cannot change any replication properties.</span></span>  
  
 <span data-ttu-id="cc363-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="cc363-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cc363-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="cc363-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cc363-111">Security</span><span class="sxs-lookup"><span data-stu-id="cc363-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cc363-112">**管理者以外のユーザーがレプリケーション モニターを使用できるようにするために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="cc363-112">**To allow non-administrators to use Replication Monitor, using:**</span></span>  
  
     [<span data-ttu-id="cc363-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cc363-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cc363-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc363-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cc363-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="cc363-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cc363-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cc363-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cc363-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="cc363-117">Permissions</span></span>  
 <span data-ttu-id="cc363-118">管理者以外のユーザーがレプリケーションモニターを使用できるようにするには、 **sysadmin**固定サーバーロールのメンバーが、ディストリビューションデータベースにユーザーを追加し、そのユーザーをロールに割り当てる必要があり `replmonitor` ます。</span><span class="sxs-lookup"><span data-stu-id="cc363-118">To allow non-administrators to use Replication Monitor, a member of the **sysadmin** fixed server role must add the user to the distribution database and assign that user to the `replmonitor` role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cc363-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="cc363-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a><span data-ttu-id="cc363-120">管理者以外のユーザーがレプリケーション モニターを使用できるようにするには</span><span class="sxs-lookup"><span data-stu-id="cc363-120">To allow non-administrators to use Replication Monitor</span></span>  
  
1.  <span data-ttu-id="cc363-121">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、ディストリビューターに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cc363-121">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the Distributor, and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="cc363-122">**[データベース]**、 **[システム データベース]** の順に展開してから、ディストリビューション データベース (既定の名前は **distribution** ) を展開します。</span><span class="sxs-lookup"><span data-stu-id="cc363-122">Expand **Databases**, expand **System Databases**, and then expand the distribution database (named **distribution** by default).</span></span>  
  
3.  <span data-ttu-id="cc363-123">**[セキュリティ]** を展開し、 **[ユーザー]** を右クリックしてから、 **[新しいユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc363-123">Expand **Security**, right-click **Users**, and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="cc363-124">ユーザー名とユーザーのログインを入力します。</span><span class="sxs-lookup"><span data-stu-id="cc363-124">Enter a user name and login for the user.</span></span>  
  
5.  <span data-ttu-id="cc363-125">の既定のスキーマを選択し `replmonitor` ます。</span><span class="sxs-lookup"><span data-stu-id="cc363-125">Select a default schema of `replmonitor`.</span></span>  
  
6.  <span data-ttu-id="cc363-126">[ `replmonitor` **データベースロールのメンバーシップ**] グリッドで、このチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="cc363-126">Select the `replmonitor` check box in the **Database role membership** grid.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cc363-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="cc363-127">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a><span data-ttu-id="cc363-128">固定データベース ロール replmonitor にユーザーを追加するには</span><span class="sxs-lookup"><span data-stu-id="cc363-128">To add a user to the replmonitor fixed database role</span></span>  
  
1.  <span data-ttu-id="cc363-129">ディストリビューターのディストリビューション データベースで [sp_helpuser (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc363-129">At the Distributor on the distribution database, execute [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql).</span></span> <span data-ttu-id="cc363-130">ユーザーが結果セットのに一覧表示されていない場合は、 `UserName` [CREATE User &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)ステートメントを使用して、ディストリビューションデータベースへのアクセス権をユーザーに付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc363-130">If the user is not listed in `UserName` in the result set, the user must be granted access to the distribution database using the [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) statement.</span></span>  
  
2.  <span data-ttu-id="cc363-131">ディストリビューター側のディストリビューションデータベースに対して、パラメーターに値を指定して[sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)を実行し `replmonitor` **@rolename** ます。</span><span class="sxs-lookup"><span data-stu-id="cc363-131">At the Distributor on the distribution database, execute [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql), specifying a value of `replmonitor` for the **@rolename** parameter.</span></span> <span data-ttu-id="cc363-132">ユーザーが結果セットのに一覧表示されている場合 `MemberName` 、そのユーザーは既にこのロールに属しています。</span><span class="sxs-lookup"><span data-stu-id="cc363-132">If the user is listed in `MemberName` in the result set, the user already belongs to this role.</span></span>  
  
3.  <span data-ttu-id="cc363-133">ユーザーがロールに属していない場合は `replmonitor` 、ディストリビューター側のディストリビューションデータベースに対して[Sp_addrolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc363-133">If the user does not belong to the `replmonitor` role, execute [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="cc363-134">に値を、 `replmonitor` **@rolename** にを追加するデータベースユーザーまたは Windows ログインの名前を指定し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] **@membername** ます。</span><span class="sxs-lookup"><span data-stu-id="cc363-134">Specify a value of `replmonitor` for **@rolename** and the name of the database user or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows login being added for **@membername**.</span></span>  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a><span data-ttu-id="cc363-135">固定データベース ロール replmonitor からユーザーを削除するには</span><span class="sxs-lookup"><span data-stu-id="cc363-135">To remove a user from the replmonitor fixed database role</span></span>  
  
1.  <span data-ttu-id="cc363-136">ユーザーがロールに属していることを確認するには `replmonitor` 、ディストリビューター側のディストリビューションデータベースに対して[Sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)を実行し、の値をに指定し `replmonitor` **@rolename** ます。</span><span class="sxs-lookup"><span data-stu-id="cc363-136">To verify that the user belongs to the `replmonitor` role, execute [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) at the Distributor on the distribution database, and specify a value of `replmonitor` for **@rolename**.</span></span> <span data-ttu-id="cc363-137">対象のユーザーが結果セットの `MemberName` に含まれていなかった場合、そのユーザーは現在、このロールに所属していません。</span><span class="sxs-lookup"><span data-stu-id="cc363-137">If the user is not listed in `MemberName` in the result set, the user does not currently belong to this role.</span></span>  
  
2.  <span data-ttu-id="cc363-138">ユーザーがロールに属している場合は `replmonitor` 、ディストリビューター側のディストリビューションデータベースに対して[Sp_droprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc363-138">If the user does belong to the `replmonitor` role, execute [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="cc363-139">に値を、には `replmonitor` **@rolename** 削除するデータベースユーザーまたは Windows ログインの名前を指定し **@membername** ます。</span><span class="sxs-lookup"><span data-stu-id="cc363-139">Specify a value of `replmonitor` for **@rolename** and the name of the database user or the Windows login being removed for **@membername**.</span></span>  
  
  
