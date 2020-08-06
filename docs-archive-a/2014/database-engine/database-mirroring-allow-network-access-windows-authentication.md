---
title: データベースミラーリングエンドポイントへのネットワークアクセス
description: SQL Server のデータベースミラーリングエンドポイントへの windows 認証のネットワークアクセスを許可する方法について説明します。
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0d1d8786d128ef2cc99fe571e33f89c4c4e7699c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643474"
---
# <a name="allow-network-access-to-a-database-mirroring-endpoint-using-windows-authentication-sql-server"></a><span data-ttu-id="95385-103">Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="95385-103">Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication (SQL Server)</span></span>
  <span data-ttu-id="95385-104">次のような条件下で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 2 つのインスタンスのデータベース ミラーリング エンドポイントに接続するために Windows 認証を使用するときは、ログイン アカウントを手動で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95385-104">Using Windows Authentication for connecting the database mirroring endpoints of two instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requires manual configuration of login accounts under the following conditions:</span></span>  
  
-   <span data-ttu-id="95385-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスが (同じドメインまたは信頼関係のあるドメインの) 異なるドメイン アカウントでサービスとして実行される場合、各リモート サーバー インスタンス上の **master** に各アカウントのログインを作成する必要があります。また、そのログインには、エンドポイントに対する CONNECT 権限を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="95385-105">If the instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] run as services under different domain accounts (in the same or trusted domains), the login of each account must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.</span></span>  
  
-   <span data-ttu-id="95385-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスがネットワーク サービス アカウントとして実行される場合、各リモート サーバー インスタンス上の **master** に各ホスト コンピューター アカウント (*DomainName***\\***ComputerName$* ) のログインを作成する必要があります。また、そのログインには、エンドポイントに対する CONNECT アクセス許可を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="95385-106">If the instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] run as the Network Service account, the login of the each host computer account (*DomainName***\\***ComputerName$*) must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="95385-107">これは、ネットワーク サービス アカウントで実行されているサーバー インスタンスではホスト コンピューターのドメイン アカウントを使用して認証を行うためです。</span><span class="sxs-lookup"><span data-stu-id="95385-107">This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95385-108">各サーバー インスタンスのエンドポイントが存在することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="95385-108">Ensure that an endpoint exists for each of the server instances.</span></span> <span data-ttu-id="95385-109">詳細については、「[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95385-109">For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
### <a name="to-configure-logins-for-windows-authentication"></a><span data-ttu-id="95385-110">Windows 認証のログインを構成するには</span><span class="sxs-lookup"><span data-stu-id="95385-110">To configure logins for Windows Authentication</span></span>  
  
1.  <span data-ttu-id="95385-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の各インスタンスのユーザー アカウントについて、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の別のインスタンスでログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="95385-111">For the user account of each instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], create a login on the other instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="95385-112">[CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) ステートメントと FROM WINDOWS 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="95385-112">Use a [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) statement with the FROM WINDOWS clause.</span></span>  
  
     <span data-ttu-id="95385-113">詳細については、「 [ログインの作成](../relational-databases/security/authentication-access/create-a-login.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95385-113">For more information, see [Create a Login](../relational-databases/security/authentication-access/create-a-login.md).</span></span>  
  
2.  <span data-ttu-id="95385-114">ログイン ユーザーがエンドポイントにアクセスできるように、 [GRANT](/sql/t-sql/statements/grant-transact-sql) ステートメントを使用して、エンドポイントへの接続権限をそのログインに許可します。</span><span class="sxs-lookup"><span data-stu-id="95385-114">Also, to ensure that the login user has access to the endpoint, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement to grant connect permissions on the endpoint to the login.</span></span> <span data-ttu-id="95385-115">エンドポイントへの接続権限の許可は、管理者には不要なので注意してください。</span><span class="sxs-lookup"><span data-stu-id="95385-115">Note that granting connect permissions to the endpoint is unnecessary if the user is an Administrator.</span></span>  
  
     <span data-ttu-id="95385-116">詳細については、「 [プリンシパルに対する権限の許可](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95385-116">For more information, see [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95385-117">例</span><span class="sxs-lookup"><span data-stu-id="95385-117">Example</span></span>  
 <span data-ttu-id="95385-118">次の [!INCLUDE[tsql](../includes/tsql-md.md)] の例では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] というドメインに所属するユーザー アカウント `Otheruser` の `Adomain`ログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="95385-118">The following [!INCLUDE[tsql](../includes/tsql-md.md)] example creates a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login for a user account named `Otheruser` that belongs to a domain called `Adomain`.</span></span> <span data-ttu-id="95385-119">このユーザーには、 `Mirroring_Endpoint`という既存のデータベース ミラーリング エンドポイントへの接続権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="95385-119">The example then grants this user connect permissions to a pre-existing database mirroring endpoint named `Mirroring_Endpoint`.</span></span>  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="95385-120">参照</span><span class="sxs-lookup"><span data-stu-id="95385-120">See Also</span></span>  
 <span data-ttu-id="95385-121">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="95385-121">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="95385-122">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="95385-122">[Database Mirroring &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="95385-123">[データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="95385-123">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md) </span></span>  
 [<span data-ttu-id="95385-124">データベース ミラーリング エンドポイント &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95385-124">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
