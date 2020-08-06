---
title: '[セキュリティ保護可能なリソース] | Microsoft Docs'
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ff2aaba72e2e5489694d31b35e594622c099acab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714018"
---
# <a name="securables"></a><span data-ttu-id="ec0a9-102">[セキュリティ保護可能なリソース]</span><span class="sxs-lookup"><span data-stu-id="ec0a9-102">Securables</span></span>
  <span data-ttu-id="ec0a9-103">セキュリティ保護可能なリソースは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の承認システムによりアクセスが制限されたリソースです。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-103">Securables are the resources to which the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] authorization system regulates access.</span></span> <span data-ttu-id="ec0a9-104">たとえば、テーブルはセキュリティ保護可能です。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-104">For example, a table is a securable.</span></span> <span data-ttu-id="ec0a9-105">セキュリティ保護可能なリソースの中には他のセキュリティ保護可能なリソースに含まれているものがあります。これらは "スコープ" と呼ばれ、それ自体をセキュリティで保護できる入れ子構造の階層を形成しています。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-105">Some securables can be contained within others, creating nested hierarchies called "scopes" that can themselves be secured.</span></span> <span data-ttu-id="ec0a9-106">セキュリティ保護可能なスコープは、 **サーバー**、 **データベース**、および **スキーマ**です。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-106">The securable scopes are **server**, **database**, and **schema**.</span></span>  
  
## <a name="securable-scope-server"></a><span data-ttu-id="ec0a9-107">セキュリティ保護可能なスコープ:サーバー</span><span class="sxs-lookup"><span data-stu-id="ec0a9-107">Securable scope: Server</span></span>  
 <span data-ttu-id="ec0a9-108">**サーバー** セキュリティ保護可能なスコープには、次のセキュリティ保護可能なリソースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-108">The **server** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="ec0a9-109">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="ec0a9-109">Availability group</span></span>  
  
-   <span data-ttu-id="ec0a9-110">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="ec0a9-110">Endpoint</span></span>  
  
-   <span data-ttu-id="ec0a9-111">ログイン</span><span class="sxs-lookup"><span data-stu-id="ec0a9-111">Login</span></span>  
  
-   <span data-ttu-id="ec0a9-112">サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="ec0a9-112">Server role</span></span>  
  
-   <span data-ttu-id="ec0a9-113">データベース</span><span class="sxs-lookup"><span data-stu-id="ec0a9-113">Database</span></span>  
  
## <a name="securable-scope-database"></a><span data-ttu-id="ec0a9-114">セキュリティ保護可能なスコープ:データベース</span><span class="sxs-lookup"><span data-stu-id="ec0a9-114">Securable scope: Database</span></span>  
 <span data-ttu-id="ec0a9-115">**データベース** セキュリティ保護可能なスコープには、次のセキュリティ保護可能なリソースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-115">The **database** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="ec0a9-116">アプリケーション ロール</span><span class="sxs-lookup"><span data-stu-id="ec0a9-116">Application role</span></span>  
  
-   <span data-ttu-id="ec0a9-117">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="ec0a9-117">Assembly</span></span>  
  
-   <span data-ttu-id="ec0a9-118">非対称キー</span><span class="sxs-lookup"><span data-stu-id="ec0a9-118">Asymmetric key</span></span>  
  
-   <span data-ttu-id="ec0a9-119">Certificate</span><span class="sxs-lookup"><span data-stu-id="ec0a9-119">Certificate</span></span>  
  
-   <span data-ttu-id="ec0a9-120">コントラクト</span><span class="sxs-lookup"><span data-stu-id="ec0a9-120">Contract</span></span>  
  
-   <span data-ttu-id="ec0a9-121">フルテキスト カタログ</span><span class="sxs-lookup"><span data-stu-id="ec0a9-121">Fulltext catalog</span></span>  
  
-   <span data-ttu-id="ec0a9-122">フルテキスト ストップリスト</span><span class="sxs-lookup"><span data-stu-id="ec0a9-122">Fulltext stoplist</span></span>  
  
-   <span data-ttu-id="ec0a9-123">メッセージ型</span><span class="sxs-lookup"><span data-stu-id="ec0a9-123">Message type</span></span>  
  
-   <span data-ttu-id="ec0a9-124">リモート サービス バインド</span><span class="sxs-lookup"><span data-stu-id="ec0a9-124">Remote Service Binding</span></span>  
  
-   <span data-ttu-id="ec0a9-125">(データベース) ロール</span><span class="sxs-lookup"><span data-stu-id="ec0a9-125">(Database) Role</span></span>  
  
-   <span data-ttu-id="ec0a9-126">ルート</span><span class="sxs-lookup"><span data-stu-id="ec0a9-126">Route</span></span>  
  
-   <span data-ttu-id="ec0a9-127">スキーマ</span><span class="sxs-lookup"><span data-stu-id="ec0a9-127">Schema</span></span>  
  
-   <span data-ttu-id="ec0a9-128">検索プロパティ リスト</span><span class="sxs-lookup"><span data-stu-id="ec0a9-128">Search property list</span></span>  
  
-   <span data-ttu-id="ec0a9-129">サービス</span><span class="sxs-lookup"><span data-stu-id="ec0a9-129">Service</span></span>  
  
-   <span data-ttu-id="ec0a9-130">対称キー</span><span class="sxs-lookup"><span data-stu-id="ec0a9-130">Symmetric key</span></span>  
  
-   <span data-ttu-id="ec0a9-131">User</span><span class="sxs-lookup"><span data-stu-id="ec0a9-131">User</span></span>  
  
## <a name="securable-scope-schema"></a><span data-ttu-id="ec0a9-132">セキュリティ保護可能なスコープ:スキーマ</span><span class="sxs-lookup"><span data-stu-id="ec0a9-132">Securable scope: Schema</span></span>  
 <span data-ttu-id="ec0a9-133">**スキーマ** セキュリティ保護可能なスコープには、次のセキュリティ保護可能なリソースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-133">The **schema** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="ec0a9-134">Type</span><span class="sxs-lookup"><span data-stu-id="ec0a9-134">Type</span></span>  
  
-   <span data-ttu-id="ec0a9-135">XML スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="ec0a9-135">XML schema collection</span></span>  
  
-   <span data-ttu-id="ec0a9-136">オブジェクト - オブジェクト クラスのメンバーは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-136">Object - The object class has the following members:</span></span>  
  
    -   <span data-ttu-id="ec0a9-137">Aggregate</span><span class="sxs-lookup"><span data-stu-id="ec0a9-137">Aggregate</span></span>  
  
    -   <span data-ttu-id="ec0a9-138">機能</span><span class="sxs-lookup"><span data-stu-id="ec0a9-138">Function</span></span>  
  
    -   <span data-ttu-id="ec0a9-139">手順</span><span class="sxs-lookup"><span data-stu-id="ec0a9-139">Procedure</span></span>  
  
    -   <span data-ttu-id="ec0a9-140">キュー</span><span class="sxs-lookup"><span data-stu-id="ec0a9-140">Queue</span></span>  
  
    -   <span data-ttu-id="ec0a9-141">シノニム</span><span class="sxs-lookup"><span data-stu-id="ec0a9-141">Synonym</span></span>  
  
    -   <span data-ttu-id="ec0a9-142">テーブル</span><span class="sxs-lookup"><span data-stu-id="ec0a9-142">Table</span></span>  
  
    -   <span data-ttu-id="ec0a9-143">表示</span><span class="sxs-lookup"><span data-stu-id="ec0a9-143">View</span></span>  
  
## <a name="controlling-access-to-a-securable"></a><span data-ttu-id="ec0a9-144">セキュリティ保護可能なものへのアクセスの制御</span><span class="sxs-lookup"><span data-stu-id="ec0a9-144">Controlling Access to a Securable</span></span>  
 <span data-ttu-id="ec0a9-145">セキュリティ保護可能なものに対する権限を受け取るエンティティは、プリンシパルと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-145">The entity that receives permission to a securable is called a principal.</span></span> <span data-ttu-id="ec0a9-146">最も一般的なプリンシパルは、ログインとデータベース ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-146">The most common principals are logins and database users.</span></span> <span data-ttu-id="ec0a9-147">セキュリティ保護可能なものへのアクセスは、権限を許可または拒否することや、アクセスが可能なロールにログインおよびユーザーを追加することによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-147">Access to securables is controlled by granting or denying permissions, or by adding logins and user to roles which have access.</span></span> <span data-ttu-id="ec0a9-148">アクセス許可を制御する方法の詳細については、「[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)」、「[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)」、「[DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql)」、「[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)」および「[sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-148">For information about controlling permissions, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql), [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql), [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql), [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql), and [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ec0a9-149">セットアップ時にシステム オブジェクトに付与された既定のアクセス許可は、発生する可能性のある脅威に対して慎重に評価されているため、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストールの際、セキュリティ強化の一部として変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-149">The default permissions that are granted to system objects at the time of setup are carefully evaluated against possible threats and need not be altered as part of hardening the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="ec0a9-150">システム オブジェクトのアクセス許可の変更はどのようなものであっても、機能を制限または中断する可能性があり、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストールがサポートされていない状態のままになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec0a9-150">Any changes to the permissions on the system objects could limit or break the functionality and could potentially leave your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation in an unsupported state.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="ec0a9-151">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ec0a9-151">Related Content</span></span>  
 [<span data-ttu-id="ec0a9-152">SQL Server の保護</span><span class="sxs-lookup"><span data-stu-id="ec0a9-152">Securing SQL Server</span></span>](securing-sql-server.md)  
  
 [<span data-ttu-id="ec0a9-153">sys.database_principals &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ec0a9-153">sys.database_principals &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)  
  
 [<span data-ttu-id="ec0a9-154">sys.database_role_members &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ec0a9-154">sys.database_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)  
  
 [<span data-ttu-id="ec0a9-155">sys.server_principals &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ec0a9-155">sys.server_principals &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)  
  
 [<span data-ttu-id="ec0a9-156">sys.server_role_members &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ec0a9-156">sys.server_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)  
  
 [<span data-ttu-id="ec0a9-157">sys.sql_logins &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ec0a9-157">sys.sql_logins &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)  
  
  
