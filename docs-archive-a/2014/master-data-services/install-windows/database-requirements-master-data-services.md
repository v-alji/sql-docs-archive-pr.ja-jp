---
title: データベース要件 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b17c04db6805ea412b70644d2ee2c0b7da93b2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644507"
---
# <a name="database-requirements-master-data-services"></a><span data-ttu-id="69418-102">データベース要件 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="69418-102">Database Requirements (Master Data Services)</span></span>
  <span data-ttu-id="69418-103">マスター データはすべて [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="69418-103">All master data is stored in a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="69418-104">このデータベースをホストするコンピューターでは、のインスタンスを実行する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="69418-104">The computer that hosts this database must run an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="69418-105">ローカル コンピューターまたはリモート コンピューターで [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] データベースを作成および構成するには、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="69418-105">Use [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] to create and configure the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database on either a local or a remote computer.</span></span> <span data-ttu-id="69418-106">環境間でデータベースを移動する場合、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスと [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] を新しい場所のデータベースに関連付けることにより、新しい環境で情報を維持できます。</span><span class="sxs-lookup"><span data-stu-id="69418-106">If you move the database from one environment to another, you can maintain the information in a new environment by associating the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service and [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to the database in its new location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69418-107">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のコンポーネントをインストールするコンピューターはすべてライセンス供与を受けている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69418-107">Any computer on which you install components of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] must be licensed.</span></span> <span data-ttu-id="69418-108">詳細については、使用許諾契約書 (EULA) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69418-108">For more information, refer to the End User License Agreement (EULA).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69418-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="69418-109">Requirements</span></span>  
 <span data-ttu-id="69418-110">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースを作成する前に、次の要件が満たされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="69418-110">Before you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, ensure the following requirements are met.</span></span>  
  
### <a name="sql-server-edition"></a><span data-ttu-id="69418-111">SQL Server のエディション</span><span class="sxs-lookup"><span data-stu-id="69418-111">SQL Server Edition</span></span>  
 <span data-ttu-id="69418-112">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースは、次のエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でホストできます。</span><span class="sxs-lookup"><span data-stu-id="69418-112">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database can be hosted on the following editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="69418-113">Business Intelligence (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="69418-113">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="69418-114">Enterprise (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="69418-114">Enterprise (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="69418-115">Developer (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="69418-115">Developer (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="69418-116">Business Intelligence (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="69418-116">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="69418-117">Enterprise (64 ビット) x64 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise からのアップグレードの場合のみ)</span><span class="sxs-lookup"><span data-stu-id="69418-117">Enterprise (64-bit) x64 - Upgrade from [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise only</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="69418-118">Developer (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="69418-118">Developer (64-bit) x64</span></span>  
  
-   <span data-ttu-id="69418-119">Microsoft SQL Server 2008 R2 Enterprise (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="69418-119">Microsoft SQL Server 2008 R2 Enterprise (64-bit) x64</span></span>  
  
-   <span data-ttu-id="69418-120">Microsoft SQL Server 2008 R2 Developer (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="69418-120">Microsoft SQL Server 2008 R2 Developer (64-bit) x64</span></span>  
  
 <span data-ttu-id="69418-121">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69418-121">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="operating-system"></a><span data-ttu-id="69418-122">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="69418-122">Operating System</span></span>  
 <span data-ttu-id="69418-123">でサポートされている Windows オペレーティングシステムおよびその他の要件の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 、「 [SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69418-123">For information about the supported Windows operating systems and other requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
### <a name="accounts-and-permissions"></a><span data-ttu-id="69418-124">アカウントと権限</span><span class="sxs-lookup"><span data-stu-id="69418-124">Accounts and Permissions</span></span>  
  
|<span data-ttu-id="69418-125">Type</span><span class="sxs-lookup"><span data-stu-id="69418-125">Type</span></span>|<span data-ttu-id="69418-126">説明</span><span class="sxs-lookup"><span data-stu-id="69418-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="69418-127">ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="69418-127">User account</span></span>|<span data-ttu-id="69418-128">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]では、Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続し、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースをホストできます。</span><span class="sxs-lookup"><span data-stu-id="69418-128">In [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], you can use a Windows account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to host the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="69418-129">このユーザー アカウントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスの **sysadmin** サーバー ロールに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="69418-129">The user account must belong to the **sysadmin** server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="69418-130">**Sysadmin**ロールの詳細については、「[サーバーレベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69418-130">For more information about the **sysadmin** role, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="69418-131">管理者アカウント</span><span class="sxs-lookup"><span data-stu-id="69418-131">administrator account</span></span>|<span data-ttu-id="69418-132">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースを作成する場合、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] システム管理者となるドメイン ユーザー アカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69418-132">When you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, you must specify a domain user account to be the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="69418-133">このユーザーは、このデータベースに関連付けられているすべての [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションについて、すべての機能領域のすべてのモデルおよびすべてのデータを更新できます。</span><span class="sxs-lookup"><span data-stu-id="69418-133">For all [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web applications associated with this database, this user can update all models and all data in all functional areas.</span></span> <span data-ttu-id="69418-134">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69418-134">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>|  
  
### <a name="database-backup"></a><span data-ttu-id="69418-135">データベース バックアップ</span><span class="sxs-lookup"><span data-stu-id="69418-135">Database Backup</span></span>  
 <span data-ttu-id="69418-136">システムの使用率が低い時間帯にデータベース全体を毎日バックアップし、使用している環境のニーズに応じて、毎日数回、トランザクション ログをバックアップすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="69418-136">As a best practice, back up the full database daily at a time of low activity and back up transaction logs more frequently depending on the needs of your environment.</span></span> <span data-ttu-id="69418-137">データベース バックアップの詳細については、「[バックアップの概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69418-137">For more information about database backups, see [Backup Overview &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69418-138">参照</span><span class="sxs-lookup"><span data-stu-id="69418-138">See Also</span></span>  
 <span data-ttu-id="69418-139">[マスターデータサービスのインストール](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="69418-139">[Install Master Data Services](install-master-data-services.md) </span></span>  
 <span data-ttu-id="69418-140">[マスターデータサービスデータベースを作成する](create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="69418-140">[Create a Master Data Services Database](create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="69418-141">[マスターデータサービスデータベース](../master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="69418-141">[Master Data Services Database](../master-data-services-database.md) </span></span>  
 <span data-ttu-id="69418-142">[[マスターデータサービスデータベースへの接続] ダイアログボックス](../connect-to-a-master-data-services-database-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="69418-142">[Connect to a Master Data Services Database Dialog Box](../connect-to-a-master-data-services-database-dialog-box.md) </span></span>  
 [<span data-ttu-id="69418-143">データベースの作成ウィザード &#40;マスター データ サービス構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="69418-143">Create Database Wizard &#40;Master Data Services Configuration Manager&#41;</span></span>](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  
