---
title: データベース ミラーリング エンドポイントでの証明書の使用 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c159e66e798524c41bf6e653283c299cc8393be5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639641"
---
# <a name="use-certificates-for-a-database-mirroring-endpoint-transact-sql"></a><span data-ttu-id="c9d55-102">データベース ミラーリング エンドポイントでの証明書の使用 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c9d55-102">Use Certificates for a Database Mirroring Endpoint (Transact-SQL)</span></span>
  <span data-ttu-id="c9d55-103">あるサーバー インスタンスのデータベース ミラーリングで証明書による認証を有効にするには、システム管理者は、各サーバー インスタンスが発信接続と着信接続の両方で証明書を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9d55-103">To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span> <span data-ttu-id="c9d55-104">この場合、発信接続を最初に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9d55-104">Outbound connections must be configured first.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9d55-105">1 つのサーバー インスタンス上のすべてのミラーリング接続では、1 つのデータベース ミラーリング エンドポイントが使用されます。そのため、エンドポイントを作成する際にサーバー インスタンスの認証方法を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9d55-105">All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.</span></span> <span data-ttu-id="c9d55-106">したがって、データベース ミラーリング用の認証は、サーバー インスタンスあたりに 1 つしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="c9d55-106">Therefore, you can use only one form of authentication per server instance for database mirroring.</span></span>  
  
## <a name="configuring-outbound-connections"></a><span data-ttu-id="c9d55-107">発信接続の構成</span><span class="sxs-lookup"><span data-stu-id="c9d55-107">Configuring Outbound Connections</span></span>  
 <span data-ttu-id="c9d55-108">データベース ミラーリング用に構成する各サーバー インスタンスで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-108">Follow these steps on each server instance that you are configuring for database mirroring:</span></span>  
  
1.  <span data-ttu-id="c9d55-109">**master** データベースで、データベース マスター キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-109">In the **master** database, create a database master key.</span></span>  
  
2.  <span data-ttu-id="c9d55-110">**master** データベースで、暗号化された証明書をサーバー インスタンスに作成します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-110">In the **master** database, create an encrypted certificate on the server instance.</span></span>  
  
3.  <span data-ttu-id="c9d55-111">作成した証明書を使用して、サーバー インスタンスのエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-111">Create an endpoint for the server instance using its certificate.</span></span>  
  
4.  <span data-ttu-id="c9d55-112">証明書をファイルにバックアップし、そのファイルをセキュリティで保護された状態で他のシステムにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c9d55-112">Back up the certificate to a file and securely copy it to the other system or systems.</span></span>  
  
 <span data-ttu-id="c9d55-113">パートナーおよびミラーリング監視サーバーがある場合は、それぞれで上記の手順を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9d55-113">You must complete these steps for each partner and the witness, if there is one.</span></span>  
  
 <span data-ttu-id="c9d55-114">詳細については、「 [データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-114">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
## <a name="configuring-inbound-connections"></a><span data-ttu-id="c9d55-115">着信接続の構成</span><span class="sxs-lookup"><span data-stu-id="c9d55-115">Configuring Inbound Connections</span></span>  
 <span data-ttu-id="c9d55-116">次に、データベース ミラーリング用に構成する各パートナーで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-116">Next, follow these steps for each partner that you are configuring for database mirroring.</span></span> <span data-ttu-id="c9d55-117">**master** データベースで、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="c9d55-117">In the **master** database:</span></span>  
  
1.  <span data-ttu-id="c9d55-118">他のシステムへのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-118">Create a login for the other system.</span></span>  
  
2.  <span data-ttu-id="c9d55-119">そのログインのユーザー名を作成します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-119">Create a user for that login.</span></span>  
  
3.  <span data-ttu-id="c9d55-120">他のサーバー インスタンスのミラーリング エンドポイント用の証明書を入手します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-120">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
4.  <span data-ttu-id="c9d55-121">手順 2. で作成したユーザーに証明書を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="c9d55-121">Associate the certificate with the user created in step 2.</span></span>  
  
5.  <span data-ttu-id="c9d55-122">ミラーリング エンドポイント用のログインに CONNECT 権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-122">Grant CONNECT permission on the login for that mirroring endpoint.</span></span>  
  
 <span data-ttu-id="c9d55-123">ミラーリング監視サーバーがある場合は、このサーバーでも着信接続の構成を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9d55-123">If there is a witness, you must also set up inbound connections for it.</span></span> <span data-ttu-id="c9d55-124">この場合、どちらのパートナーのミラーリング監視サーバーでも、相手のログイン、ユーザー、証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="c9d55-124">This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.</span></span>  
  
 <span data-ttu-id="c9d55-125">詳細については、「 [データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-125">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="c9d55-126">Security</span><span class="sxs-lookup"><span data-stu-id="c9d55-126">Security</span></span>  
 <span data-ttu-id="c9d55-127">ネットワークがセキュリティで保護されていることを保証できる場合を除いて、データベース ミラーリング接続に対して暗号化を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c9d55-127">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span> <span data-ttu-id="c9d55-128">詳細については、「 [データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9d55-128">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
 <span data-ttu-id="c9d55-129">証明書を別のシステムにコピーする場合は、セキュリティで保護されたコピー方法を使用してください。</span><span class="sxs-lookup"><span data-stu-id="c9d55-129">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="c9d55-130">すべての証明書をセキュリティで保護された状態で保管するよう十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c9d55-130">Be extremely careful to keep all of your certificates secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d55-131">参照</span><span class="sxs-lookup"><span data-stu-id="c9d55-131">See Also</span></span>  
 <span data-ttu-id="c9d55-132">[データベース マスター キーの作成](../../relational-databases/security/encryption/create-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="c9d55-132">[Create a Database Master Key](../../relational-databases/security/encryption/create-a-database-master-key.md) </span></span>  
 <span data-ttu-id="c9d55-133">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9d55-133">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="c9d55-134">[データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="c9d55-134">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="c9d55-135">[SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span><span class="sxs-lookup"><span data-stu-id="c9d55-135">[Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span></span>  
 [<span data-ttu-id="c9d55-136">データベース ミラーリング エンドポイント &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c9d55-136">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
  
  
