---
title: 孤立ユーザーのトラブルシューティング (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5df714d818949b921ff2236e50d58913eab0e0db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640541"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a><span data-ttu-id="952d1-102">孤立ユーザーのトラブルシューティング (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="952d1-102">Troubleshoot Orphaned Users (SQL Server)</span></span>
  <span data-ttu-id="952d1-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにログインするには、有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインがプリンシパルに提供されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="952d1-103">To log into an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a principal must have a valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="952d1-104">このログインは、プリンシパルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続できるかどうかを確認する認証プロセスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="952d1-104">This login is used in the authentication process that verifies whether the principal is allowed to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="952d1-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーインスタンス上のログインは、 **server_principals**カタログビューおよび**sys.sysログイン**互換性ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="952d1-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins on a server instance are visible in the **sys.server_principals** catalog view and the **sys.syslogins** compatibility view.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="952d1-106">ログインは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップされているデータベース ユーザーを使用して個々のデータベースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="952d1-106">logins access individual databases using a database user that is mapped to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="952d1-107">このルールには次の 2 つの例外があります。</span><span class="sxs-lookup"><span data-stu-id="952d1-107">There are two exceptions to this rule:</span></span>  
  
-   <span data-ttu-id="952d1-108">guest アカウント</span><span class="sxs-lookup"><span data-stu-id="952d1-108">The guest account.</span></span>  
  
     <span data-ttu-id="952d1-109">このアカウントがデータベースで有効になっていると、データベース ユーザーにマップされていない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインはゲスト ユーザーとしてデータベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="952d1-109">This is an account that, when enabled in the database, enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins that are not mapped to a database user to enter the database as the guest user.</span></span>  
  
-   <span data-ttu-id="952d1-110">Microsoft Windows グループのメンバー</span><span class="sxs-lookup"><span data-stu-id="952d1-110">Microsoft Windows group memberships.</span></span>  
  
     <span data-ttu-id="952d1-111">Windows ユーザーから作成した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは、Windows ユーザーが属しているグループがデータベースのユーザーである場合にデータベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="952d1-111">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login created from a Windows user can enter a database if the Windows user is a member of a Windows group that is also a user in the database.</span></span>  
  
 <span data-ttu-id="952d1-112">データベース ユーザーへの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのマップに関する情報は、データベース内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="952d1-112">Information about the mapping of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to a database user is stored within the database.</span></span> <span data-ttu-id="952d1-113">これには、データベース ユーザーの名前および対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの SID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="952d1-113">It includes the name of the database user and the SID of the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="952d1-114">データベース内での承認には、このデータベース ユーザーの権限を使用します。</span><span class="sxs-lookup"><span data-stu-id="952d1-114">The permissions of this database user are used for authorization in the database.</span></span>  
  
 <span data-ttu-id="952d1-115">対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが未定義のデータベース ユーザー、またはサーバー インスタンスで適切に定義されていないデータベース ユーザーは、インスタンスにログインできません。</span><span class="sxs-lookup"><span data-stu-id="952d1-115">A database user for which the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is undefined or is incorrectly defined on a server instance cannot log in to the instance.</span></span> <span data-ttu-id="952d1-116">このようなユーザーは、そのサーバー インスタンスのデータベースの *孤立ユーザー* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="952d1-116">Such a user is said to be an *orphaned user* of the database on that server instance.</span></span> <span data-ttu-id="952d1-117">データベース ユーザーは、対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが削除された場合に孤立状態になることがあります。</span><span class="sxs-lookup"><span data-stu-id="952d1-117">A database user can become orphaned if the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is dropped.</span></span> <span data-ttu-id="952d1-118">また、データベースを復元したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスにアタッチした場合も、孤立状態になることがあります。</span><span class="sxs-lookup"><span data-stu-id="952d1-118">Also, a database user can become orphaned after a database is restored or attached to a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="952d1-119">孤立状態は、データベース ユーザーが新しいサーバー インスタンスに存在しない SID にマップされると発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="952d1-119">Orphaning can happen if the database user is mapped to a SID that is not present in the new server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="952d1-120">ログインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] そのデータベースで**guest**が有効になっていない限り、対応するデータベースユーザーがないデータベースにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="952d1-120">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login cannot access a database in which it lacks a corresponding database user unless **guest** is enabled in that database.</span></span> <span data-ttu-id="952d1-121">データベースユーザーアカウントの作成の詳細については、「 [CREATE user &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="952d1-121">For information about creating a database user account, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
## <a name="to-detect-orphaned-users"></a><span data-ttu-id="952d1-122">孤立ユーザーを検出するには</span><span class="sxs-lookup"><span data-stu-id="952d1-122">To Detect Orphaned Users</span></span>  
 <span data-ttu-id="952d1-123">孤立ユーザーを検出するには、次の Transact-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="952d1-123">To detect orphaned users, execute the following Transact-SQL statements:</span></span>  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 <span data-ttu-id="952d1-124">現在のデータベース内で、どの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにもリンクされていないユーザーとそのセキュリティ識別子 (SID) が出力されます。</span><span class="sxs-lookup"><span data-stu-id="952d1-124">The output lists the users and corresponding security identifiers (SID) in the current database that are not linked to any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="952d1-125">詳細については、「 [sp_change_users_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="952d1-125">For more information, see [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="952d1-126">**sp_change_users_login**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows から作成されたログインでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="952d1-126">**sp_change_users_login** cannot be used with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins that are created from Windows.</span></span>  
  
## <a name="to-resolve-an-orphaned-user"></a><span data-ttu-id="952d1-127">孤立ユーザーを解決するには</span><span class="sxs-lookup"><span data-stu-id="952d1-127">To Resolve an Orphaned User</span></span>  
 <span data-ttu-id="952d1-128">孤立ユーザーを解決するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="952d1-128">To resolve an orphaned user, use the following procedure:</span></span>  
  
1.  <span data-ttu-id="952d1-129">次のコマンドは、 *<login_name>* で指定されたサーバーログインアカウントを、 *<database_user>* で指定されたデータベースユーザーとエディットコンティニュします。</span><span class="sxs-lookup"><span data-stu-id="952d1-129">The following command relinks the server login account specified by *<login_name>* with the database user specified by *<database_user>*.</span></span>  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     <span data-ttu-id="952d1-130">詳細については、「 [sp_change_users_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="952d1-130">For more information, see [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).</span></span>  
  
2.  <span data-ttu-id="952d1-131">前の手順のコードを実行すると、ユーザーがデータベースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="952d1-131">After you run the code in the preceding step, the user can access the database.</span></span> <span data-ttu-id="952d1-132">次のように、ユーザーは**sp_password**ストアドプロシージャを使用して、 *<login_name>* ログインアカウントのパスワードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="952d1-132">The user then can alter the password of the *<login_name>* login account by using the **sp_password** stored procedure, as follows:</span></span>  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="952d1-133">ALTER ANY LOGIN 権限を持つログインだけが、他のユーザーのログイン パスワードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="952d1-133">Only logins with the ALTER ANY LOGIN permission can change the password of another user's login.</span></span> <span data-ttu-id="952d1-134">ただし、 **sysadmin** ロール メンバーのパスワードを変更できるのは、 **sysadmin** ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="952d1-134">However, only members of the **sysadmin** role can modify passwords of **sysadmin** role members.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="952d1-135">**sp_password**は、Windows アカウントには使用できません [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="952d1-135">**sp_password** cannot be used for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows accounts.</span></span> <span data-ttu-id="952d1-136">Windows ネットワーク アカウントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するユーザーは Windows によって認証されるので、このようなユーザーのパスワードは Windows でしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="952d1-136">Users connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through their Windows network account are authenticated by Windows; therefore, their passwords can only be changed in Windows.</span></span>  
  
     <span data-ttu-id="952d1-137">詳細については、「 [sp_password &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="952d1-137">For more information, see [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952d1-138">参照</span><span class="sxs-lookup"><span data-stu-id="952d1-138">See Also</span></span>  
 <span data-ttu-id="952d1-139">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="952d1-139">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="952d1-140">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="952d1-140">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="952d1-141">[sp_change_users_login &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="952d1-141">[sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql) </span></span>  
 <span data-ttu-id="952d1-142">[sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="952d1-142">[sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql) </span></span>  
 <span data-ttu-id="952d1-143">[sp_grantlogin &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="952d1-143">[sp_grantlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql) </span></span>  
 <span data-ttu-id="952d1-144">[sp_password &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="952d1-144">[sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql) </span></span>  
 <span data-ttu-id="952d1-145">[sys.sysユーザー &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="952d1-145">[sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql) </span></span>  
 [<span data-ttu-id="952d1-146">Transact-sql&#41;&#40;のログインのsys.sys</span><span class="sxs-lookup"><span data-stu-id="952d1-146">sys.syslogins &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
