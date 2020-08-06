---
title: プリンシパル (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectroll.f1
- sql12.swb.databaseuser.permissions.user.f1--May use common.permissions
helpviewer_keywords:
- certificates [SQL Server], principals
- roles [SQL Server], principals
- permissions [SQL Server], principals
- '##MS_SQLAuthenticatorCertificate##'
- principals [SQL Server]
- '##MS_SQLResourceSigningCertificate##'
- groups [SQL Server], principals
- '##MS_AgentSigningCertificate##'
- authentication [SQL Server], principals
- schemas [SQL Server], principals
- principals [SQL Server], about principals
- security [SQL Server], principals
- users [SQL Server], principals
- '##MS_SQLReplicationSigningCertificate##'
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 808c8516b3ed9e95ea4c724736461cb00923a7fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645473"
---
# <a name="principals-database-engine"></a><span data-ttu-id="cbe04-102">プリンシパル (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="cbe04-102">Principals (Database Engine)</span></span>
  <span data-ttu-id="cbe04-103">*プリンシパル* は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースを要求できるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="cbe04-103">*Principals* are entities that can request [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resources.</span></span> <span data-ttu-id="cbe04-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の承認モデルの他のコンポーネントと同様に、プリンシパルは階層内に配置できます。</span><span class="sxs-lookup"><span data-stu-id="cbe04-104">Like other components of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authorization model, principals can be arranged in a hierarchy.</span></span> <span data-ttu-id="cbe04-105">プリンシパルの効力のスコープは、プリンシパルの定義のスコープ (Windows、サーバー、データベース) と、プリンシパルが分割不可能かコレクションであるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="cbe04-105">The scope of influence of a principal depends on the scope of the definition of the principal: Windows, server, database; and whether the principal is indivisible or a collection.</span></span> <span data-ttu-id="cbe04-106">分割できないプリンシパルの例には Windows ログインがあり、コレクションであるプリンシパルの例には Windows グループがあります。</span><span class="sxs-lookup"><span data-stu-id="cbe04-106">A Windows Login is an example of an indivisible principal, and a Windows Group is an example of a principal that is a collection.</span></span> <span data-ttu-id="cbe04-107">各プリンシパルには、1 つのセキュリティ識別子 (SID) があります。</span><span class="sxs-lookup"><span data-stu-id="cbe04-107">Every principal has a security identifier (SID).</span></span>  
  
 <span data-ttu-id="cbe04-108">**Windows レベルのプリンシパル**</span><span class="sxs-lookup"><span data-stu-id="cbe04-108">**Windows-level principals**</span></span>  
  
-   <span data-ttu-id="cbe04-109">Windows ドメイン ログイン</span><span class="sxs-lookup"><span data-stu-id="cbe04-109">Windows Domain Login</span></span>  
  
-   <span data-ttu-id="cbe04-110">Windows ローカル ログイン</span><span class="sxs-lookup"><span data-stu-id="cbe04-110">Windows Local Login</span></span>  
  
 <span data-ttu-id="cbe04-111">**SQL Server** -**レベル\*\*\*\*プリンシパル**</span><span class="sxs-lookup"><span data-stu-id="cbe04-111">**SQL Server**-**level** **principals**</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="cbe04-112">ログイン</span><span class="sxs-lookup"><span data-stu-id="cbe04-112">Login</span></span>  
  
-   <span data-ttu-id="cbe04-113">サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="cbe04-113">Server Role</span></span>  
  
 <span data-ttu-id="cbe04-114">**データベースレベルのプリンシパル**</span><span class="sxs-lookup"><span data-stu-id="cbe04-114">**Database-level principals**</span></span>  
  
-   <span data-ttu-id="cbe04-115">データベース ユーザー</span><span class="sxs-lookup"><span data-stu-id="cbe04-115">Database User</span></span>  
  
-   <span data-ttu-id="cbe04-116">データベース ロール</span><span class="sxs-lookup"><span data-stu-id="cbe04-116">Database Role</span></span>  
  
-   <span data-ttu-id="cbe04-117">アプリケーション ロール</span><span class="sxs-lookup"><span data-stu-id="cbe04-117">Application Role</span></span>  
  
## <a name="the-sql-server-sa-login"></a><span data-ttu-id="cbe04-118">SQL Server sa ログイン</span><span class="sxs-lookup"><span data-stu-id="cbe04-118">The SQL Server sa Login</span></span>  
 <span data-ttu-id="cbe04-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa ログインはサーバー レベルのプリンシパルです。</span><span class="sxs-lookup"><span data-stu-id="cbe04-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa log in is a server-level principal.</span></span> <span data-ttu-id="cbe04-120">このログインは、インスタンスのインストール時に既定で作成されます。</span><span class="sxs-lookup"><span data-stu-id="cbe04-120">By default, it is created when an instance is installed.</span></span> <span data-ttu-id="cbe04-121">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]より、sa の既定のデータベースは master です。</span><span class="sxs-lookup"><span data-stu-id="cbe04-121">Beginning in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the default database of sa is master.</span></span> <span data-ttu-id="cbe04-122">これは、以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の動作から変更されています。</span><span class="sxs-lookup"><span data-stu-id="cbe04-122">This is a change of behavior from earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="public-database-role"></a><span data-ttu-id="cbe04-123">public データベース ロール</span><span class="sxs-lookup"><span data-stu-id="cbe04-123">public Database Role</span></span>  
 <span data-ttu-id="cbe04-124">データベース ユーザーはすべて、public データベース ロールに属しています。</span><span class="sxs-lookup"><span data-stu-id="cbe04-124">Every database user belongs to the public database role.</span></span> <span data-ttu-id="cbe04-125">セキュリティ保護可能なリソースに対する特定の権限が与えられていないか権限が拒否されたユーザーは、public がそのリソースに対して許可されている権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="cbe04-125">When a user has not been granted or denied specific permissions on a securable, the user inherits the permissions granted to public on that securable.</span></span>  
  
## <a name="information_schema-and-sys"></a><span data-ttu-id="cbe04-126">INFORMATION_SCHEMA と sys</span><span class="sxs-lookup"><span data-stu-id="cbe04-126">INFORMATION_SCHEMA and sys</span></span>  
 <span data-ttu-id="cbe04-127">各データベースには、カタログ ビューにユーザーとして表示される 2 つのエンティティ INFORMATION_SCHEMA および sys が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cbe04-127">Every database includes two entities that appear as users in catalog views: INFORMATION_SCHEMA and sys.</span></span> <span data-ttu-id="cbe04-128">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]はこれらを必要とします。</span><span class="sxs-lookup"><span data-stu-id="cbe04-128">These entities are required by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cbe04-129">これらのエンティティはプリンシパルではなく、変更も削除もできません。</span><span class="sxs-lookup"><span data-stu-id="cbe04-129">They are not principals, and they cannot be modified or dropped.</span></span>  
  
## <a name="certificate-based-sql-server-logins"></a><span data-ttu-id="cbe04-130">証明書ベースの SQL Server ログイン</span><span class="sxs-lookup"><span data-stu-id="cbe04-130">Certificate-based SQL Server Logins</span></span>  
 <span data-ttu-id="cbe04-131">名前が 2 つの番号記号 (##) で囲まれたサーバー プリンシパルは、内部システムでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="cbe04-131">Server principals with names enclosed by double hash marks (##) are for internal system use only.</span></span> <span data-ttu-id="cbe04-132">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストール時に証明書から作成される以下のプリンシパルは、削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="cbe04-132">The following principals are created from certificates when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is installed, and should not be deleted.</span></span>  
  
-   <span data-ttu-id="cbe04-133">\##MS_SQLResourceSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="cbe04-133">\##MS_SQLResourceSigningCertificate##</span></span>  
  
-   <span data-ttu-id="cbe04-134">\##MS_SQLReplicationSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="cbe04-134">\##MS_SQLReplicationSigningCertificate##</span></span>  
  
-   <span data-ttu-id="cbe04-135">\##MS_SQLAuthenticatorCertificate##</span><span class="sxs-lookup"><span data-stu-id="cbe04-135">\##MS_SQLAuthenticatorCertificate##</span></span>  
  
-   <span data-ttu-id="cbe04-136">\##MS_AgentSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="cbe04-136">\##MS_AgentSigningCertificate##</span></span>  
  
-   <span data-ttu-id="cbe04-137">\##MS_PolicyEventProcessingLogin##</span><span class="sxs-lookup"><span data-stu-id="cbe04-137">\##MS_PolicyEventProcessingLogin##</span></span>  
  
-   <span data-ttu-id="cbe04-138">\##MS_PolicySigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="cbe04-138">\##MS_PolicySigningCertificate##</span></span>  
  
-   <span data-ttu-id="cbe04-139">\##MS_PolicyTsqlExecutionLogin##</span><span class="sxs-lookup"><span data-stu-id="cbe04-139">\##MS_PolicyTsqlExecutionLogin##</span></span>  
  
## <a name="the-guest-user"></a><span data-ttu-id="cbe04-140">guest ユーザー</span><span class="sxs-lookup"><span data-stu-id="cbe04-140">The guest User</span></span>  
 <span data-ttu-id="cbe04-141">各データベースには、 **guest**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cbe04-141">Each database includes a **guest**.</span></span> <span data-ttu-id="cbe04-142">データベースにはアクセスできるが、データベース内のユーザー アカウントは持っていないユーザーは、 **guest** ユーザーに許可された権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="cbe04-142">Permissions granted to the **guest** user are inherited by users who have access to the database, but who do not have a user account in the database.</span></span> <span data-ttu-id="cbe04-143">**Guest**ユーザーを削除することはできませんが、アクセス許可を取り消すことによって無効にすることができ `CONNECT` ます。</span><span class="sxs-lookup"><span data-stu-id="cbe04-143">The **guest** user cannot be dropped, but it can be disabled by revoking it's `CONNECT` permission.</span></span> <span data-ttu-id="cbe04-144">権限は、 `CONNECT` `REVOKE CONNECT FROM GUEST` master または tempdb 以外のデータベース内で実行することで取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="cbe04-144">The `CONNECT` permission can be revoked by executing `REVOKE CONNECT FROM GUEST` within any database other than master or tempdb.</span></span>  
  
## <a name="client-and-database-server"></a><span data-ttu-id="cbe04-145">クライアントとデータベース サーバー</span><span class="sxs-lookup"><span data-stu-id="cbe04-145">Client and Database Server</span></span>  
 <span data-ttu-id="cbe04-146">定義上、クライアントとデータベース サーバーはセキュリティ プリンシパルであり、セキュリティで保護できます。</span><span class="sxs-lookup"><span data-stu-id="cbe04-146">By definition, a client and a database server are security principals and can be secured.</span></span> <span data-ttu-id="cbe04-147">これらのエンティティは、安全なネットワーク接続が確立される前に相互に認証できます。</span><span class="sxs-lookup"><span data-stu-id="cbe04-147">These entities can be mutually authenticated before a secure network connection is established.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="cbe04-148">では、クライアントがネットワーク認証サービスと対話する方法を定義する[Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758)認証プロトコルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cbe04-148">supports the [Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758) authentication protocol, which defines how clients interact with a network authentication service.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="cbe04-149">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="cbe04-149">Related Tasks</span></span>  
 <span data-ttu-id="cbe04-150">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックのこのセクションの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cbe04-150">The following topics are included in this section of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   [<span data-ttu-id="cbe04-151">ログイン、ユーザー、およびスキーマの管理方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="cbe04-151">Managing Logins, Users, and Schemas How-to Topics</span></span>](managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [<span data-ttu-id="cbe04-152">サーバーレベルのロール</span><span class="sxs-lookup"><span data-stu-id="cbe04-152">Server-Level Roles</span></span>](server-level-roles.md)  
  
-   [<span data-ttu-id="cbe04-153">データベース レベルのロール</span><span class="sxs-lookup"><span data-stu-id="cbe04-153">Database-Level Roles</span></span>](database-level-roles.md)  
  
-   [<span data-ttu-id="cbe04-154">アプリケーション ロール</span><span class="sxs-lookup"><span data-stu-id="cbe04-154">Application Roles</span></span>](application-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="cbe04-155">参照</span><span class="sxs-lookup"><span data-stu-id="cbe04-155">See Also</span></span>  
 <span data-ttu-id="cbe04-156">[SQL Server の保護](../securing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cbe04-156">[Securing SQL Server](../securing-sql-server.md) </span></span>  
 <span data-ttu-id="cbe04-157">[sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cbe04-157">[sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql) </span></span>  
 <span data-ttu-id="cbe04-158">[sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cbe04-158">[sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) </span></span>  
 <span data-ttu-id="cbe04-159">[sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cbe04-159">[sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) </span></span>  
 <span data-ttu-id="cbe04-160">[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cbe04-160">[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql) </span></span>  
 <span data-ttu-id="cbe04-161">[サーバー レベルのロール](server-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="cbe04-161">[Server-Level Roles](server-level-roles.md) </span></span>  
 [<span data-ttu-id="cbe04-162">データベース レベルのロール</span><span class="sxs-lookup"><span data-stu-id="cbe04-162">Database-Level Roles</span></span>](database-level-roles.md)  
  
  
