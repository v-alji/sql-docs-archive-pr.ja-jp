---
title: SSIS カタログを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6ed56d36-18d9-40c2-b51f-f2a4c71d1e73
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2572cc131f34a21171054a159e3b7968c453a780
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633241"
---
# <a name="create-the-ssis-catalog"></a><span data-ttu-id="4ef4c-102">SSIS カタログの作成</span><span class="sxs-lookup"><span data-stu-id="4ef4c-102">Create the SSIS Catalog</span></span>
  <span data-ttu-id="4ef4c-103">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]でパッケージをデザインしてテストしたら、パッケージを含むプロジェクトを [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置できます。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-103">After you design and test packages in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], you can deploy the projects that contain the packages to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="4ef4c-104">プロジェクトを [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置するには、まずサーバーに `SSISDB` カタログを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-104">Before you can deploy the projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, the server must contain the `SSISDB` catalog.</span></span> <span data-ttu-id="4ef4c-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] のインストール プログラムでは、カタログは自動的に作成されません。次の手順を使用して、カタログを手動で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-105">The installation program for [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] does not automatically create the catalog; you need to manually create the catalog by using the following instructions.</span></span>  
  
 <span data-ttu-id="4ef4c-106">SSISDB カタログは [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で作成できます。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-106">You can create the SSISDB catalog in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4ef4c-107">Windows PowerShell を使用して、カタログをプログラムから作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-107">You also create the catalog programmatically by using Windows PowerShell.</span></span>  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a><span data-ttu-id="4ef4c-108">SQL Server Management Studio で SSISDB カタログを作成するには</span><span class="sxs-lookup"><span data-stu-id="4ef4c-108">To create the SSISDB catalog in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="4ef4c-109">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="4ef4c-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース エンジンに接続します。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-110">Connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Database Engine.</span></span>  
  
3.  <span data-ttu-id="4ef4c-111">オブジェクト エクスプローラーで、サーバー ノードを展開します。次に、 **[Integration Services カタログ]** ノードを右クリックし、 **[カタログの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-111">In Object Explorer, expand the server node, right-click the **Integration Services Catalogs** node, and then click **Create Catalog**.</span></span>  
  
4.  <span data-ttu-id="4ef4c-112">**[CLR 統合を有効にする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-112">Click **Enable CLR Integration**.</span></span>  
  
     <span data-ttu-id="4ef4c-113">カタログは CLR ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-113">The catalog uses CLR stored procedures.</span></span>  
  
5.  <span data-ttu-id="4ef4c-114">**サーバー インスタンスを再起動するたびに** catalog.startup [ストアド プロシージャが実行されるようにするには、](/sql/integration-services/system-stored-procedures/catalog-startup) [SQL Server のスタートアップ時に Integration Services ストアド プロシージャを自動実行できるようにする] [!INCLUDE[ssIS](../includes/ssis-md.md)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-114">Click **Enable automatic execution of Integration Services stored procedure at SQL Server startup** to enable the [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) stored procedure to run each time the [!INCLUDE[ssIS](../includes/ssis-md.md)] server instance is restarted.</span></span>  
  
     <span data-ttu-id="4ef4c-115">このストアド プロシージャは、SSISDB カタログに対する操作の状態のメンテナンスを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-115">The stored procedure performs maintenance of the state of operations for the SSISDB catalog.</span></span> <span data-ttu-id="4ef4c-116">[!INCLUDE[ssIS](../includes/ssis-md.md)] サーバー インスタンスがダウンした場合に、実行されていたパッケージの状態を修正します。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-116">It fixes the status of any packages there were running if and when the [!INCLUDE[ssIS](../includes/ssis-md.md)] server instance goes down.</span></span>  
  
6.  <span data-ttu-id="4ef4c-117">パスワードを入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-117">Enter a password, and then click **Ok**.</span></span>  
  
     <span data-ttu-id="4ef4c-118">カタログ データを暗号化するために使用されるデータベース マスター キーがパスワードで保護されます。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-118">The password protects the database master key that is used for encrypting the catalog data.</span></span> <span data-ttu-id="4ef4c-119">パスワードは安全な場所に保管してください。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-119">Save the password in a secure location.</span></span> <span data-ttu-id="4ef4c-120">データベース マスター キーをバックアップすることもお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-120">It is recommended that you also back up the database master key.</span></span> <span data-ttu-id="4ef4c-121">詳細については、「 [データベース マスター キーのバックアップ](../relational-databases/security/encryption/back-up-a-database-master-key.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-121">For more information, see [Back Up a Database Master Key](../relational-databases/security/encryption/back-up-a-database-master-key.md).</span></span>  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a><span data-ttu-id="4ef4c-122">SSISDB カタログをプログラムから作成するには</span><span class="sxs-lookup"><span data-stu-id="4ef4c-122">To create the SSISDB catalog programmatically</span></span>  
  
1.  <span data-ttu-id="4ef4c-123">次の PowerShell スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-123">Execute the following PowerShell script:</span></span>  
  
    ```powershell
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()
    ```  
  
     <span data-ttu-id="4ef4c-124">Windows PowerShell と <xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間の使用方法を紹介したその他の例については、blogs.msdn.com のブログ エントリ「[SQL Server 2012 での SSIS と PowerShell](https://go.microsoft.com/fwlink/?LinkId=242539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-124">For more examples of how to use Windows PowerShell and the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace, see the blog entry, [SSIS and PowerShell in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539), on blogs.msdn.com.</span></span> <span data-ttu-id="4ef4c-125">名前空間とコード例の概要については、blogs.msdn.com のブログ エントリ「 [SSIS カタログ マネージド オブジェクト モデルの概要](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ef4c-125">For an overview of the namespace and code examples, see the blog entry, [A Glimpse of the SSIS Catalog Managed Object Model](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef4c-126">参照</span><span class="sxs-lookup"><span data-stu-id="4ef4c-126">See Also</span></span>  
 <span data-ttu-id="4ef4c-127">[SSIS カタログ](catalog/ssis-catalog.md) </span><span class="sxs-lookup"><span data-stu-id="4ef4c-127">[SSIS Catalog](catalog/ssis-catalog.md) </span></span>  
 [<span data-ttu-id="4ef4c-128">SSIS カタログのバックアップ、復元、および移動</span><span class="sxs-lookup"><span data-stu-id="4ef4c-128">Backup, Restore, and Move the SSIS Catalog</span></span>](../../2014/integration-services/backup-restore-and-move-the-ssis-catalog.md)  
