---
title: アプリケーション ロール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- application roles [SQL Server], about application roles
- principals [SQL Server], application roles
- credentials [SQL Server], roles
- application roles [SQL Server]
- roles [SQL Server], application
- permissions [SQL Server], roles
- users [SQL Server], application roles
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f2fcc7b1e333bb42a00675da5bb9fd559d1c34f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633027"
---
# <a name="application-roles"></a><span data-ttu-id="20dd7-102">アプリケーション ロール</span><span class="sxs-lookup"><span data-stu-id="20dd7-102">Application Roles</span></span>
  <span data-ttu-id="20dd7-103">アプリケーション ロールは、ユーザーのような独自の権限でアプリケーションを実行できるようにするデータベース プリンシパルです。</span><span class="sxs-lookup"><span data-stu-id="20dd7-103">An application role is a database principal that enables an application to run with its own, user-like permissions.</span></span> <span data-ttu-id="20dd7-104">アプリケーション ロールを使用すると、特定のアプリケーションから接続しているユーザーに対してのみ、特定のデータへのアクセスを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="20dd7-104">You can use application roles to enable access to specific data to only those users who connect through a particular application.</span></span> <span data-ttu-id="20dd7-105">アプリケーション ロールは、データベース ロールとは異なり、既定ではメンバーが含まれておらず、アクティブではありません。</span><span class="sxs-lookup"><span data-stu-id="20dd7-105">Unlike database roles, application roles contain no members and are inactive by default.</span></span> <span data-ttu-id="20dd7-106">アプリケーション ロールは、両方の認証モードで機能します。</span><span class="sxs-lookup"><span data-stu-id="20dd7-106">Application roles work with both authentication modes.</span></span> <span data-ttu-id="20dd7-107">アプリケーション ロールは **sp_setapprole**を使用して有効化され、これにはパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="20dd7-107">Application roles are enabled by using **sp_setapprole**, which requires a password.</span></span> <span data-ttu-id="20dd7-108">アプリケーション ロールはデータベース レベルのプリンシパルであるため、他のデータベースへのアクセスは、そのデータベースの **guest**に許可された権限を介してのみ可能になります。</span><span class="sxs-lookup"><span data-stu-id="20dd7-108">Because application roles are a database-level principal, they can access other databases only through permissions granted in those databases to **guest**.</span></span> <span data-ttu-id="20dd7-109">したがって、 **guest** が無効になったデータベースには、他のデータベースのアプリケーション ロールからアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="20dd7-109">Therefore, any database in which **guest** has been disabled will be inaccessible to application roles in other databases.</span></span>  
  
 <span data-ttu-id="20dd7-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、アプリケーション ロールは、サーバー レベルのプリンシパルと関連付けられていないため、サーバー レベルのメタデータにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="20dd7-110">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], application roles cannot access server-level metadata because they are not associated with a server-level principal.</span></span> <span data-ttu-id="20dd7-111">この制限を無効にして、アプリケーション ロールがサーバー レベルのメタデータにアクセスできるようにするには、グローバル フラグ 4616 を設定します。</span><span class="sxs-lookup"><span data-stu-id="20dd7-111">To disable this restriction and thereby allow application roles to access server-level metadata, set the global flag 4616.</span></span> <span data-ttu-id="20dd7-112">詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)」および「[DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20dd7-112">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) and [DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql).</span></span>  
  
## <a name="connecting-with-an-application-role"></a><span data-ttu-id="20dd7-113">アプリケーション ロールを使用した接続</span><span class="sxs-lookup"><span data-stu-id="20dd7-113">Connecting with an Application Role</span></span>  
 <span data-ttu-id="20dd7-114">アプリケーション ロールがセキュリティ コンテキストを切り替える処理を行う手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="20dd7-114">The following steps make up the process by which an application role switches security contexts:</span></span>  
  
1.  <span data-ttu-id="20dd7-115">ユーザーがクライアント アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="20dd7-115">A user executes a client application.</span></span>  
  
2.  <span data-ttu-id="20dd7-116">クライアント アプリケーションが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにユーザーとして接続します。</span><span class="sxs-lookup"><span data-stu-id="20dd7-116">The client application connects to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the user.</span></span>  
  
3.  <span data-ttu-id="20dd7-117">アプリケーションが、このアプリケーションのみに対して既知であるパスワードを使用して、 **sp_setapprole** ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="20dd7-117">The application then executes the **sp_setapprole** stored procedure with a password known only to the application.</span></span>  
  
4.  <span data-ttu-id="20dd7-118">アプリケーション ロール名およびパスワードが有効であれば、アプリケーション ロールが有効になります。</span><span class="sxs-lookup"><span data-stu-id="20dd7-118">If the application role name and password are valid, the application role is enabled.</span></span>  
  
5.  <span data-ttu-id="20dd7-119">この時点で、接続はユーザーの権限を失い、アプリケーション ロールの権限を取得します。</span><span class="sxs-lookup"><span data-stu-id="20dd7-119">At this point the connection loses the permissions of the user and assumes the permissions of the application role.</span></span>  
  
 <span data-ttu-id="20dd7-120">アプリケーション ロールを使用して取得した権限は、接続している間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="20dd7-120">The permissions acquired through the application role remain in effect for the duration of the connection.</span></span>  
  
 <span data-ttu-id="20dd7-121">前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、アプリケーション ロールの開始後にユーザーが元のセキュリティ コンテキストを再取得するには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を切断して再接続する以外にありませんでした。</span><span class="sxs-lookup"><span data-stu-id="20dd7-121">In earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the only way for a user to reacquire its original security context after starting an application role is to disconnect and reconnect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="20dd7-122">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]以降の **sp_setapprole** には、クッキーを作成するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="20dd7-122">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **sp_setapprole** has an option that creates a cookie.</span></span> <span data-ttu-id="20dd7-123">クッキーには、アプリケーション ロールが有効になる前のコンテキスト情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="20dd7-123">The cookie contains context information before the application role is enabled.</span></span> <span data-ttu-id="20dd7-124">**sp_unsetapprole** でクッキーを使用すると、元のコンテキストにセッションを戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="20dd7-124">The cookie can be used by **sp_unsetapprole** to revert the session to its original context.</span></span> <span data-ttu-id="20dd7-125">この新しいオプションの詳細と例については、「 [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)に許可された権限を介してのみ可能になります。</span><span class="sxs-lookup"><span data-stu-id="20dd7-125">For information about this new option and an example, see [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="20dd7-126">**SqlClient** では、ODBC **encrypt**オプションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="20dd7-126">The ODBC **encrypt** option is not supported by **SqlClient**.</span></span> <span data-ttu-id="20dd7-127">機密情報をネットワーク経由で送信する場合、SSL (Secure Sockets Layer) または IPsec を使用してチャネルを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="20dd7-127">When you are transmitting confidential information over a network, use Secure Sockets Layer (SSL) or IPsec to encrypt the channel.</span></span> <span data-ttu-id="20dd7-128">クライアント アプリケーション内に資格情報を保持しておく必要がある場合、暗号化 API (Crypto API) 関数を使用して資格情報を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="20dd7-128">If you must persist credentials in the client application, encrypt the credentials by using the crypto API functions.</span></span> <span data-ttu-id="20dd7-129">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンでは、パラメーター *password* は一方向のハッシュとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="20dd7-129">In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions, the parameter *password* is stored as a one-way hash.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="20dd7-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="20dd7-130">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="20dd7-131">アプリケーション ロールを作成する。</span><span class="sxs-lookup"><span data-stu-id="20dd7-131">Create an application role.</span></span>|<span data-ttu-id="20dd7-132">[アプリケーション ロールの作成](create-an-application-role.md)および [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="20dd7-132">[Create an Application Role](create-an-application-role.md) and [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)</span></span>|  
|<span data-ttu-id="20dd7-133">アプリケーション ロールを変更する。</span><span class="sxs-lookup"><span data-stu-id="20dd7-133">Alter an application role.</span></span>|[<span data-ttu-id="20dd7-134">ALTER APPLICATION ROLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="20dd7-134">ALTER APPLICATION ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-application-role-transact-sql)|  
|<span data-ttu-id="20dd7-135">アプリケーション ロールを削除する。</span><span class="sxs-lookup"><span data-stu-id="20dd7-135">Delete an application role.</span></span>|[<span data-ttu-id="20dd7-136">DROP APPLICATION ROLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="20dd7-136">DROP APPLICATION ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-application-role-transact-sql)|  
|<span data-ttu-id="20dd7-137">アプリケーション ロールを使用する。</span><span class="sxs-lookup"><span data-stu-id="20dd7-137">Using an application role.</span></span>|[<span data-ttu-id="20dd7-138">sp_setapprole &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="20dd7-138">sp_setapprole &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)|  
  
## <a name="see-also"></a><span data-ttu-id="20dd7-139">参照</span><span class="sxs-lookup"><span data-stu-id="20dd7-139">See Also</span></span>  
 [<span data-ttu-id="20dd7-140">SQL Server の保護</span><span class="sxs-lookup"><span data-stu-id="20dd7-140">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
  
