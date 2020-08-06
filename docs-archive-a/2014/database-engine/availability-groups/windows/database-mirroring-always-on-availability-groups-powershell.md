---
title: AlwaysOn 可用性グループ (SQL Server PowerShell) のデータベースミラーリングエンドポイントを作成します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56058ff8aa72d2471381dd87fb25a3b68356ed36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743433"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a><span data-ttu-id="74ba5-102">AlwaysOn 可用性グループのデータベース ミラーリング エンドポイントの作成 (SQLServer PowerShell)</span><span class="sxs-lookup"><span data-stu-id="74ba5-102">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups (SQL Server PowerShell)</span></span>
  <span data-ttu-id="74ba5-103">このトピックでは、PowerShell を使用して、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で使用するデータベース ミラーリング エンドポイントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74ba5-103">This topic describes how to create a database mirroring endpoint for use by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using PowerShell.</span></span>  
  
 <span data-ttu-id="74ba5-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="74ba5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="74ba5-105">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="74ba5-105">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="74ba5-106">**データベース ミラーリング エンドポイントを作成するために使用するもの:**  [PowerShell](#PowerShellProcedure)</span><span class="sxs-lookup"><span data-stu-id="74ba5-106">**To create a database mirroring endpoint, using:**  [PowerShell](#PowerShellProcedure)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="74ba5-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="74ba5-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="74ba5-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="74ba5-108">Security</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="74ba5-109">RC4 アルゴリズムは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="74ba5-109">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="74ba5-110">AES を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="74ba5-110">We recommend that you use AES.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="74ba5-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="74ba5-111">Permissions</span></span>  
 <span data-ttu-id="74ba5-112">CREATE ENDPOINT 権限、または sysadmin 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="74ba5-112">Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role.</span></span> <span data-ttu-id="74ba5-113">詳細については、「 [GRANT (エンドポイントの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74ba5-113">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="74ba5-114">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="74ba5-114">Using PowerShell</span></span>  
 <span data-ttu-id="74ba5-115">**データベース ミラーリング エンドポイントを作成するには**</span><span class="sxs-lookup"><span data-stu-id="74ba5-115">**To create a database mirroring endpoint**</span></span>  
  
1.  <span data-ttu-id="74ba5-116">ディレクトリ変更コマンド (`cd`) を使用して、データベース ミラーリング エンドポイントを作成するサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="74ba5-116">Change directory (`cd`) to the server instance for which you want to create the database mirroring endpoint.</span></span>  
  
2.  <span data-ttu-id="74ba5-117">`New-SqlHadrEndpoint` コマンドレットを使用してエンドポイントを作成し、その後 `Set-SqlHadrEndpoint` を使用してエンドポイントを開始します。</span><span class="sxs-lookup"><span data-stu-id="74ba5-117">Use the `New-SqlHadrEndpoint` cmdlet to create the endpoint and then use the `Set-SqlHadrEndpoint` to start the endpoint.</span></span>  
  
###  <a name="example-powershell"></a><a name="PShellExample"></a> <span data-ttu-id="74ba5-118">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="74ba5-118">Example (PowerShell)</span></span>  
 <span data-ttu-id="74ba5-119">次の PowerShell コマンドでは、SQL Server (*マシン*インスタンス) のインスタンスにデータベースミラーリングエンドポイントを作成し \\ *Instance*ます。</span><span class="sxs-lookup"><span data-stu-id="74ba5-119">The following PowerShell commands create a database mirroring endpoint on an instance of SQL Server (*Machine*\\*Instance*).</span></span> <span data-ttu-id="74ba5-120">このエンドポイントはポート 5022 を使用します。</span><span class="sxs-lookup"><span data-stu-id="74ba5-120">The endpoint uses port 5022.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="74ba5-121">この例を使用できるのは、現在データベース ミラーリング エンドポイントが存在しないサーバー インスタンスのみです。</span><span class="sxs-lookup"><span data-stu-id="74ba5-121">This example works only on a server instance that currently lack a database mirroring endpoint.</span></span>  
  
```powershell
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="74ba5-122">関連タスク</span><span class="sxs-lookup"><span data-stu-id="74ba5-122">Related Tasks</span></span>  
 <span data-ttu-id="74ba5-123">**データベース ミラーリング エンドポイントを構成するには**</span><span class="sxs-lookup"><span data-stu-id="74ba5-123">**To Configure a Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="74ba5-124">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74ba5-124">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="74ba5-125">データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74ba5-125">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="74ba5-126">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74ba5-126">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="74ba5-127">データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74ba5-127">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="74ba5-128">サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="74ba5-128">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="74ba5-129">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="74ba5-129">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="74ba5-130">**データベース ミラーリング エンドポイントに関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="74ba5-130">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="74ba5-131">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74ba5-131">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="74ba5-132">参照</span><span class="sxs-lookup"><span data-stu-id="74ba5-132">See Also</span></span>  
 <span data-ttu-id="74ba5-133">[Transact-sql&#41;&#40;可用性グループを作成する](create-an-availability-group-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="74ba5-133">[Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) </span></span>  
 [<span data-ttu-id="74ba5-134">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="74ba5-134">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
