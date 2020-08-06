---
title: データベースミラーリングまたは AlwaysOn 可用性グループ (SQL Server) のログインアカウントを設定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- logins [SQL Server], database mirroring
ms.assetid: e9f5287b-1325-4cda-88a6-19eaaa52a652
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d149016dabd0239bd76eadc8655b6752afd916d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716733"
---
# <a name="set-up-login-accounts-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a><span data-ttu-id="8b994-102">データベース ミラーリングまたは AlwaysOn 可用性グループのログイン アカウントの設定 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8b994-102">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="8b994-103">2 つのサーバー インスタンスが互いにもう一方の [データベース ミラーリング エンドポイント](the-database-mirroring-endpoint-sql-server.md) であるポイントに接続するには、各インスタンスのログイン アカウントがもう一方のインスタンスにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b994-103">For two server instances to connect to each other's [database mirroring endpoint](the-database-mirroring-endpoint-sql-server.md) point, the login account of each instance requires access to the other instance.</span></span> <span data-ttu-id="8b994-104">また、各ログイン アカウントには、他方のインスタンスのデータベース ミラーリング エンドポイントへの接続権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="8b994-104">Also, each login account requires connect permission to the Database Mirroring endpoint of the other instance.</span></span>  
  
 <span data-ttu-id="8b994-105">この要件による影響は、サーバー インスタンスを同じドメイン ユーザー アカウントとして実行しているかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="8b994-105">The impact of this requirement depends on whether the server instances run as the same domain user account:</span></span>  
  
-   <span data-ttu-id="8b994-106">同じドメイン ユーザー アカウントでサーバー インスタンスを実行した場合は、自動的に両方の **マスター** データベースに正しいユーザー ログインが存在します。</span><span class="sxs-lookup"><span data-stu-id="8b994-106">If the server instances run as the same domain user account, the correct user logins exist automatically in both **master** databases.</span></span> <span data-ttu-id="8b994-107">このため、データベース ミラーリングと AlwaysOn 可用性グループのセキュリティ構成が単純化されます。</span><span class="sxs-lookup"><span data-stu-id="8b994-107">This simplifies the security configuration for Database Mirroring and AlwaysOn Availability Groups.</span></span>  
  
-   <span data-ttu-id="8b994-108">異なるユーザー アカウントとしてサーバー インスタンスを実行している場合は、プリンシパル サーバーまたはプライマリ レプリカをホストするサーバー インスタンスに対するユーザー ログインを、ミラー サーバーをホストするサーバー インスタンスまたはセカンダリ レプリカをホストするすべてのサーバー インスタンスに手動で再現する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b994-108">If the server instances run as different user accounts, user logins on the server instance that hosts the principal server or primary replica must be manually reproduced on the server instance that hosts the mirror server or on every server instance that hosts a secondary replica.</span></span> <span data-ttu-id="8b994-109">詳細については、この後の「 [異なるアカウントのログインの作成](#CreateLogin) 」および「 [接続権限の許可](#GrantConnect)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b994-109">For more information, see [Create a Login for a Different Account](#CreateLogin) and [Grant Connect Permission](#GrantConnect), later in this topic.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8b994-110">より安全な環境を作成するには、各サーバー インスタンスに対して個別のドメイン アカウントを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="8b994-110">To create a more secure environment, consider using separate domain accounts for each server instance.</span></span>  
  
##  <a name="create-a-login-for-a-different-account"></a><a name="CreateLogin"></a> <span data-ttu-id="8b994-111">異なるアカウントのログインの作成</span><span class="sxs-lookup"><span data-stu-id="8b994-111">Create a Login for a Different Account</span></span>  
 <span data-ttu-id="8b994-112">2 つのサーバー インスタンスが異なるアカウントで実行される場合、システム管理者は CREATE LOGIN [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して、リモート インスタンスのスタートアップ サービス アカウント用にログインを作成する必要があります。このログインは、各サーバー インスタンスに作成します。</span><span class="sxs-lookup"><span data-stu-id="8b994-112">If two server instances run as different accounts, the system administrator must use the CREATE LOGIN [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to create a login for the startup service account of the remote instance for each server instance.</span></span> <span data-ttu-id="8b994-113">詳細については、「[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b994-113">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8b994-114">ドメイン アカウント以外で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行する場合、証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b994-114">If you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] under a non-domain account, you must use certificates.</span></span> <span data-ttu-id="8b994-115">詳細については、この後の「 [データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b994-115">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
 <span data-ttu-id="8b994-116">たとえば、loginA で実行されるサーバー インスタンス sqlA の場合、loginB で実行されるサーバー インスタンス sqlB に接続するには、loginA が sqlB に存在し、かつ loginB が sqlA に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b994-116">For example, for the server instance sqlA, which runs under loginA, to connect to the server instance sqlB, which runs under loginB, loginA must exist on sqlB, and loginB must exist on sqlA.</span></span> <span data-ttu-id="8b994-117">また、データベース ミラーリング セッションにミラーリング監視サーバー インスタンス (sqlC) が含まれ、3 つのサーバー インスタンスがそれぞれ異なるドメイン アカウントで実行される場合は、以下のログインを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b994-117">In addition, for a database mirroring session that includes a witness server instance (sqlC) and in which the three server instances run under different domain accounts, the following logins must be created:</span></span>  
  
|<span data-ttu-id="8b994-118">インスタンス</span><span class="sxs-lookup"><span data-stu-id="8b994-118">On instance...</span></span>|<span data-ttu-id="8b994-119">ログインを作成し接続権限を許可する対象</span><span class="sxs-lookup"><span data-stu-id="8b994-119">Create logins for and grant connection permission to ...</span></span>|  
|--------------------|--------------------------------------------------------------|  
|<span data-ttu-id="8b994-120">sqlA</span><span class="sxs-lookup"><span data-stu-id="8b994-120">sqlA</span></span>|<span data-ttu-id="8b994-121">sqlB と sqlC</span><span class="sxs-lookup"><span data-stu-id="8b994-121">sqlB and sqlC</span></span>|  
|<span data-ttu-id="8b994-122">sqlB</span><span class="sxs-lookup"><span data-stu-id="8b994-122">sqlB</span></span>|<span data-ttu-id="8b994-123">sqlA と sqlC</span><span class="sxs-lookup"><span data-stu-id="8b994-123">sqlA and sqlC</span></span>|  
|<span data-ttu-id="8b994-124">sqlC</span><span class="sxs-lookup"><span data-stu-id="8b994-124">sqlC</span></span>|<span data-ttu-id="8b994-125">sqlA と sqlB</span><span class="sxs-lookup"><span data-stu-id="8b994-125">sqlA and sqlB</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="8b994-126">ドメイン ユーザーではなくコンピューター アカウントを使用することにより、ネットワーク サービス アカウントで接続できます。</span><span class="sxs-lookup"><span data-stu-id="8b994-126">It is possible to connect with the network service account by using the machine account instead of a domain user.</span></span> <span data-ttu-id="8b994-127">コンピューター アカウントを使用する場合は、そのアカウントを他方のサーバー インスタンスにユーザーとして追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b994-127">If the machine account is used, it must be added as a user on the other server instance.</span></span>  
  
##  <a name="grant-connect-permission"></a><a name="GrantConnect"></a> <span data-ttu-id="8b994-128">接続権限の許可</span><span class="sxs-lookup"><span data-stu-id="8b994-128">Grant Connect Permission</span></span>  
 <span data-ttu-id="8b994-129">サーバー インスタンスでログインを作成した後、サーバー インスタンスのデータベース ミラーリング エンドポイントに接続するための権限をそのログインに許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b994-129">Once a login has been created on a server instance, the login must be granted permission to connect to the database mirroring endpoint of the server instance.</span></span> <span data-ttu-id="8b994-130">システム管理者は、GRANT [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して接続権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="8b994-130">The system administrator grants the connect permission using a GRANT [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="8b994-131">詳細については、「 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)と共に使用できるように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8b994-131">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8b994-132">関連タスク</span><span class="sxs-lookup"><span data-stu-id="8b994-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="8b994-133">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="8b994-133">Create a Login</span></span>](../../relational-databases/security/authentication-access/create-a-login.md)  
  
-   <span data-ttu-id="8b994-134">[Windows 認証を使用してデータベースミラーリングエンドポイントへのネットワークアクセスを許可する &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="8b994-134">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
-   [<span data-ttu-id="8b994-135">データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b994-135">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b994-136">参照</span><span class="sxs-lookup"><span data-stu-id="8b994-136">See Also</span></span>  
 <span data-ttu-id="8b994-137">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8b994-137">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="8b994-138">[データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8b994-138">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="8b994-139">AlwaysOn 可用性グループ構成 &#40;SQL Server のトラブルシューティング&#41;</span><span class="sxs-lookup"><span data-stu-id="8b994-139">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;</span></span>](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
