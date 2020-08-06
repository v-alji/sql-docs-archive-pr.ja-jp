---
title: ロールの追加 | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.MEMBERSHIP.F1
helpviewer_keywords:
- adding a member to a role
- join a role
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 58e8c071672c8c3afba8d6c424488899dcf76be7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633023"
---
# <a name="join-a-role"></a><span data-ttu-id="05ca0-102">ロールの追加</span><span class="sxs-lookup"><span data-stu-id="05ca0-102">Join a Role</span></span>
  <span data-ttu-id="05ca0-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、ログインおよびデータベース ユーザーにロールを割り当てる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-103">This topic describes how to assign roles to logins and database users in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="05ca0-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で権限を効率的に管理するには、ロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-104">Use roles in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to efficiently manage permissions.</span></span> <span data-ttu-id="05ca0-105">ロールに権限を割り当て、そのロールに対してユーザーとログインの追加および削除を行います。</span><span class="sxs-lookup"><span data-stu-id="05ca0-105">Assign permissions to roles, and then add and remove users and logins to the roles.</span></span> <span data-ttu-id="05ca0-106">ロールを使用すると、権限をユーザーごとに個別に管理する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="05ca0-106">By using roles, permissions do not have to be individually maintained for each user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="05ca0-107">では、4 種類のロールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="05ca0-107">supports four types of roles.</span></span>  
  
-   <span data-ttu-id="05ca0-108">固定サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="05ca0-108">Fixed server roles</span></span>  
  
-   <span data-ttu-id="05ca0-109">ユーザー定義サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="05ca0-109">User-defined server roles</span></span>  
  
-   <span data-ttu-id="05ca0-110">固定データベース ロール</span><span class="sxs-lookup"><span data-stu-id="05ca0-110">Fixed database roles</span></span>  
  
-   <span data-ttu-id="05ca0-111">ユーザー定義データベース ロール</span><span class="sxs-lookup"><span data-stu-id="05ca0-111">User-defined database roles</span></span>  
  
 <span data-ttu-id="05ca0-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、固定ロールは自動的に使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="05ca0-112">The fixed roles are automatically available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05ca0-113">固定ロールには、一般的なタスクを実行するのに必要な権限があります。</span><span class="sxs-lookup"><span data-stu-id="05ca0-113">Fixed roles have the necessary permissions to accomplish common tasks.</span></span> <span data-ttu-id="05ca0-114">固定ロールの詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="05ca0-114">For more information about fixed roles, see the following links.</span></span> <span data-ttu-id="05ca0-115">ユーザー定義ロールはユーザーが作成するもので、権限を選択してカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="05ca0-115">User-defined roles are created by you, and can be customized with the permissions that you select.</span></span> <span data-ttu-id="05ca0-116">ユーザー定義ロールの詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="05ca0-116">For more information about user-defined roles, see the following links.</span></span>  
  
 <span data-ttu-id="05ca0-117">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="05ca0-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="05ca0-118">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="05ca0-118">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="05ca0-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="05ca0-119">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="05ca0-120">Security</span><span class="sxs-lookup"><span data-stu-id="05ca0-120">Security</span></span>](#Security)  
  
-   <span data-ttu-id="05ca0-121">**ログインおよびデータベース ユーザーにロールを割り当てるために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="05ca0-121">**To assign roles to logins and database users, using:**</span></span>  
  
     [<span data-ttu-id="05ca0-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="05ca0-122">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="05ca0-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="05ca0-123">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="05ca0-124">はじめに</span><span class="sxs-lookup"><span data-stu-id="05ca0-124">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="05ca0-125">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="05ca0-125">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="05ca0-126">データベース ロールの名前を変更しても、ロールの ID 番号、所有者、権限は変わりません。</span><span class="sxs-lookup"><span data-stu-id="05ca0-126">Changing the name of a database role does not change ID number, owner, or permissions of the role.</span></span>  
  
-   <span data-ttu-id="05ca0-127">データベース ロールは、sys.database_role_members および sys.database_principals カタログ ビューで確認できます。</span><span class="sxs-lookup"><span data-stu-id="05ca0-127">Database roles are visible in the sys.database_role_members and sys.database_principals catalog views.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="05ca0-128">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="05ca0-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="05ca0-129">Permissions</span><span class="sxs-lookup"><span data-stu-id="05ca0-129">Permissions</span></span>  
 <span data-ttu-id="05ca0-130">`ALTER ANY ROLE`データベースに対する権限、 `ALTER` ロールに対する権限、または**db_securityadmin**のメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="05ca0-130">Requires `ALTER ANY ROLE` permission on the database, `ALTER` permission on the role, or membership in **db_securityadmin**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="05ca0-131">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="05ca0-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a><span data-ttu-id="05ca0-132">固定サーバー ロールにメンバーを追加するには</span><span class="sxs-lookup"><span data-stu-id="05ca0-132">To add a member to a fixed server role</span></span>  
  
1.  <span data-ttu-id="05ca0-133">オブジェクト エクスプローラーで、固定サーバー ロールを編集するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-133">In Object Explorer, expand the server in which you want to edit a fixed server role.</span></span>  
  
2.  <span data-ttu-id="05ca0-134">**[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-134">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="05ca0-135">**[サーバー ロール]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-135">Expand the **Server Roles** folder</span></span>  
  
4.  <span data-ttu-id="05ca0-136">編集するロールを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05ca0-136">Right-click the role you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="05ca0-137">[**サーバーロールのプロパティ-**_server_role_name_ ] ダイアログボックスの [**メンバー** ] ページで、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05ca0-137">In the **Server Role Properties -**_server_role_name_ dialog box, on the **Members** page, click **Add**.</span></span>  
  
6.  <span data-ttu-id="05ca0-138">**[サーバー ログインまたはロールの選択]** ダイアログ ボックスで、 **[選択するオブジェクト名を入力してください (例)]** に、このサーバー ロールに追加するログインまたはサーバー ロールを入力します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-138">In the **Select Server Login or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or server role to add to this server role.</span></span> <span data-ttu-id="05ca0-139">または、 **[参照...]** をクリックし、 **[オブジェクトの参照]** ダイアログ ボックスに表示されるいずれかのオブジェクトまたはすべてのオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-139">Alternately, click **Browse...** and select any or all of the available objects in the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="05ca0-140">[ **OK** ] をクリックして、[**サーバーロールのプロパティ-**_server_role_name_ ] ダイアログボックスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="05ca0-140">Click **OK** to return to the **Server Role Properties -**_server_role_name_ dialog box.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a><span data-ttu-id="05ca0-141">ユーザー定義データベース ロールにメンバーを追加するには</span><span class="sxs-lookup"><span data-stu-id="05ca0-141">To add a member to a user-defined database role</span></span>  
  
1.  <span data-ttu-id="05ca0-142">オブジェクト エクスプローラーで、ユーザー定義のデータベース ロールを編集するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-142">In Object Explorer, expand the server in which you want to edit a user-defined database role.</span></span>  
  
2.  <span data-ttu-id="05ca0-143">**[データベース]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-143">Expand the **Databases** folder.</span></span>  
  
3.  <span data-ttu-id="05ca0-144">ユーザー定義のデータベース ロールを編集するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-144">Expand the database in which you want to edit a user-defined database role.</span></span>  
  
4.  <span data-ttu-id="05ca0-145">**[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-145">Expand the **Security** folder.</span></span>  
  
5.  <span data-ttu-id="05ca0-146">**[ロール]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-146">Expand the **Roles** folder.</span></span>  
  
6.  <span data-ttu-id="05ca0-147">**[サーバー ロール]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-147">Expand the **Server Roles** folder.</span></span>  
  
7.  <span data-ttu-id="05ca0-148">編集するロールを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05ca0-148">Right-click the role you want to edit and select **Properties**.</span></span>  
  
8.  <span data-ttu-id="05ca0-149">[**データベースロールのプロパティ-**_database_role_name_ ] ダイアログボックスの [**全般**] ページで、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05ca0-149">In the **Database Role Properties -**_database_role_name_ dialog box, in the **General** page, click **Add**.</span></span>  
  
9. <span data-ttu-id="05ca0-150">**[データベース ユーザーまたはロールの選択]** ダイアログ ボックスで、 **[選択するオブジェクト名を入力してください (例)]** に、このデータベース ロールに追加するログインまたはデータベース ロールを入力します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-150">In the **Select Database User or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or database role to add to this database role.</span></span> <span data-ttu-id="05ca0-151">または、 **[参照...]** をクリックし、 **[オブジェクトの参照]** ダイアログ ボックスに表示されるいずれかのオブジェクトまたはすべてのオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-151">Alternately, click **Browse...** and select any or all of the available objects in the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="05ca0-152">[ **OK** ] をクリックして、[**データベースロールのプロパティ-**_database_role_name_ ] ダイアログボックスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="05ca0-152">Click **OK** to return to the **Database Role Properties -**_database_role_name_ dialog box.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="05ca0-153">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="05ca0-153">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a><span data-ttu-id="05ca0-154">固定サーバー ロールにメンバーを追加するには</span><span class="sxs-lookup"><span data-stu-id="05ca0-154">To add a member to a fixed server role</span></span>  
  
1.  <span data-ttu-id="05ca0-155">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="05ca0-156">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05ca0-156">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="05ca0-157">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05ca0-157">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 <span data-ttu-id="05ca0-158">詳細については、「[ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05ca0-158">For more information, see [ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql).</span></span>  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a><span data-ttu-id="05ca0-159">ユーザー定義データベース ロールにメンバーを追加するには</span><span class="sxs-lookup"><span data-stu-id="05ca0-159">To add a member to a user-defined database role</span></span>  
  
1.  <span data-ttu-id="05ca0-160">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="05ca0-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="05ca0-161">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05ca0-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="05ca0-162">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05ca0-162">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 <span data-ttu-id="05ca0-163">詳細については、「[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05ca0-163">For more information, see [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ca0-164">参照</span><span class="sxs-lookup"><span data-stu-id="05ca0-164">See Also</span></span>  
 <span data-ttu-id="05ca0-165">[サーバー レベルのロール](server-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="05ca0-165">[Server-Level Roles](server-level-roles.md) </span></span>  
 <span data-ttu-id="05ca0-166">[データベース レベルのロール](../authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="05ca0-166">[Database-Level Roles](../authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="05ca0-167">アプリケーション ロール</span><span class="sxs-lookup"><span data-stu-id="05ca0-167">Application Roles</span></span>](../authentication-access/application-roles.md)  
  
  
