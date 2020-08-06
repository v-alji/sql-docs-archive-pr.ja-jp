---
title: Microsoft Azure Virtual Machine の SQL Server データベースの配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploymentwizard.deploymentsettings.f1
- sql12.swb.deploymentwizard.progress.f1
- sql11.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.f1
- sql12.swb.deploymentwizard.azuresignin.f1
- sql11.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.azuresignin.f1
- sql12.swb.deploymentwizard.f1
- sql12.swb.sqlvmdialog.f1
- sql11.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.results.f1
- sql11.swb.deploymentwizard.progress.f1
- sql12.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.sourcesettings.f1
- sql12.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.sourcesettings.f1
- sql11.swb.deploymentwizard.results.f1
- sql12.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.deploymentsettings.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
author: stevestein
ms.author: sstein
ms.openlocfilehash: d48c06db038a775811cba6705fbaf1d97a960f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736385"
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a><span data-ttu-id="9ea46-102">Microsoft Azure Virtual Machine の SQL Server データベースの配置</span><span class="sxs-lookup"><span data-stu-id="9ea46-102">Deploy a SQL Server Database to a Microsoft Azure Virtual Machine</span></span>
  <span data-ttu-id="9ea46-103">Azure 仮想マシン (VM) ののインスタンスからデータベースを配置するには、 **AZURE VM への SQL Server データベースの配置**ウィザードを使用し [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-103">Use the **Deploy a SQL Server Database to an Azure VM** wizard to deploy a database from an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in an Azure Virtual Machine (VM).</span></span> <span data-ttu-id="9ea46-104">このウィザードはデータベースの完全バックアップ操作を活用し、SQL Server のユーザー データベースから常にデータベース スキーマ全体とデータ全体をコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-104">The wizard utilizes a full database backup operation, so it always copies the complete database schema and the data from a SQL Server user database.</span></span> <span data-ttu-id="9ea46-105">また、このウィザードは Azure のすべての仮想マシンを自動的に構成するため、仮想マシンの事前構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9ea46-105">The wizard also does all of the Azure VM configuration for you, so no pre-configuration of the VM is required.</span></span>  
  
 <span data-ttu-id="9ea46-106">このウィザードは同じデータベース名を持つ既存のデータベースを上書きしないため、このウィザードを使用して差分バックアップを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="9ea46-106">You cannot use the wizard for differential backups because the wizard will not overwrite an existing database that has the same database name.</span></span> <span data-ttu-id="9ea46-107">仮想マシン上にある既存のデータベースを置き換えるには、まず既存のデータベースを削除するか、データベース名を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-107">To replace an existing database on the VM, you must first drop the existing database or change the database name.</span></span> <span data-ttu-id="9ea46-108">インフライト配置操作を実行しているときに、複数のデータベース名の間で名前の競合が発生し、既存のデータベースが仮想マシン上に存在している場合は、ウィザードはインフライト データベースに対して付加的なデータベース名を提示し、操作を完了できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-108">If there is a naming conflict between the database name for an in-flight deploy operation and an existing database on the VM, the wizard will suggest an appended database name for the in-flight database to enable you to complete the operation.</span></span>  
  
##  <a name="before-you-begin"></a><a name="before_you_begin"></a> <span data-ttu-id="9ea46-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="9ea46-109">Before You Begin</span></span>  
 <span data-ttu-id="9ea46-110">このウィザードを完了するには、次の情報を用意し、これらの構成設定を整える必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-110">To complete this wizard, you must be able to provide the following information and have these configuration settings in place:</span></span>  
  
-   <span data-ttu-id="9ea46-111">Azure サブスクリプションに関連付けられている Microsoft アカウントの詳細。</span><span class="sxs-lookup"><span data-stu-id="9ea46-111">The Microsoft account details associated with your Azure subscription.</span></span>  
  
-   <span data-ttu-id="9ea46-112">Azure 発行プロファイル。</span><span class="sxs-lookup"><span data-stu-id="9ea46-112">Your Azure publishing profile.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="9ea46-113">SQL Server では現在、公開プロファイルのバージョン 2.0 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9ea46-113">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="9ea46-114">公開プロファイルのサポート対象バージョンをダウンロードするには、「 [公開プロファイルのバージョン 2.0 のダウンロード](https://go.microsoft.com/fwlink/?LinkId=396421)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9ea46-114">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
  
-   <span data-ttu-id="9ea46-115">Azure サブスクリプションにアップロードされた管理証明書。</span><span class="sxs-lookup"><span data-stu-id="9ea46-115">The management certificate uploaded to your Azure subscription.</span></span>  
  
-   <span data-ttu-id="9ea46-116">ウィザードを実行するコンピューターで個人証明書ストアに保存された管理証明書。</span><span class="sxs-lookup"><span data-stu-id="9ea46-116">The management certificate saved into the personal certificate store on the computer where the wizard is running.</span></span>  
  
-   <span data-ttu-id="9ea46-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをホストするコンピューターで使用できる一時格納場所が必要です。</span><span class="sxs-lookup"><span data-stu-id="9ea46-117">You must have a temporary storage location that is available to the computer where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is hosted.</span></span> <span data-ttu-id="9ea46-118">この一時格納場所は、このウィザードを実行するコンピューターでも使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-118">The temporary storage location must also be available to the computer where the wizard is running.</span></span>  
  
-   <span data-ttu-id="9ea46-119">既存の仮想マシンにデータベースを配置する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを TCP/IP ポートでリッスンするように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-119">If you are deploying the database to an existing VM, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured to listen on a TCP/IP port.</span></span>  
  
-   <span data-ttu-id="9ea46-120">VM の作成に使用する予定の Azure VM またはギャラリーイメージには、SQL Server クラウドアダプター構成され、実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-120">Either an Azure VM or Gallery image you plan to use for creation of the VM must have the SQL Server Cloud Adapter configured and running.</span></span>  
  
-   <span data-ttu-id="9ea46-121">プライベートポート11435を使用して、Azure ゲートウェイで SQL Server クラウドアダプターのオープンエンドポイントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-121">You must configure an open endpoint for your SQL Server Cloud Adapter on the Azure gateway with private port 11435.</span></span>  
  
 <span data-ttu-id="9ea46-122">また、データベースを既存の Azure VM にデプロイする予定がある場合は、次の情報も提供できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-122">In addition, if you plan to deploy your database into an existing Azure VM, you must also be able to provide:</span></span>  
  
-   <span data-ttu-id="9ea46-123">仮想マシンをホストするクラウド サービスの DNS 名。</span><span class="sxs-lookup"><span data-stu-id="9ea46-123">The DNS name of the cloud service that hosts your VM.</span></span>  
  
-   <span data-ttu-id="9ea46-124">仮想マシンの管理者資格情報。</span><span class="sxs-lookup"><span data-stu-id="9ea46-124">Administrator credentials for the VM.</span></span>  
  
-   <span data-ttu-id="9ea46-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のソース インスタンスから配置を計画しているデータベースのバックアップ操作の特権資格情報。</span><span class="sxs-lookup"><span data-stu-id="9ea46-125">Credentials with Backup operator privileges on the database you plan to deploy, from the source instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9ea46-126">Azure 仮想マシンでの SQL Server の実行の詳細については、「 [azure Virtual Machines で SQL Server に移行する](https://msdn.microsoft.com/library/dn133142.aspx)ための準備」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ea46-126">For more information about running SQL Server in Azure virtual machines, see [Getting Ready to Migrate to SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx).</span></span>  
  
 <span data-ttu-id="9ea46-127">Windows Server オペレーティング システムを実行しているコンピューターでは、このウィザードを実行するために、次の構成設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-127">On computers running Windows Server operating systems, you must use the following configuration settings to run this wizard:</span></span>  
  
-   <span data-ttu-id="9ea46-128">セキュリティ強化の構成の無効化。[サーバー マネージャー] > [ローカル サーバー] を使用し、[Internet Explorer セキュリティ強化の構成]\(ESC) を **[オフ]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-128">Turn off Enhanced Security Configuration:  Use Server Manager > Local Server to set Internet Explorer Enhanced Security Configuration (ESC) to **OFF**.</span></span>  
  
-   <span data-ttu-id="9ea46-129">JavaScript の有効化。Internet Explorer > [インターネット オプション] > [セキュリティ] > [レベルのカスタマイズ] > [スクリプト] > [アクティブ スクリプト] を選択し、**[有効にする]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-129">Enable JavaScript:  Internet Explorer > Internet Options > Security > Customer Level > Scripting > Active Scripting: **Enable**.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="limitations"></a> <span data-ttu-id="9ea46-130">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9ea46-130">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9ea46-131">この操作に対応するデータベース サイズの上限は 1 TB です。</span><span class="sxs-lookup"><span data-stu-id="9ea46-131">The database size limitation for this operation is 1 TB.</span></span>  
  
 <span data-ttu-id="9ea46-132">この配置機能は、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]用の SQL Server Management Studio で使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-132">This deployment feature is available in SQL Server Management Studio for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="9ea46-133">この配置機能は、ユーザー データベースを使用している場合にのみ有効です。システム データベースの配置はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9ea46-133">This deployment feature is for use only with user databases; deploying system databases is not supported.</span></span>  
  
 <span data-ttu-id="9ea46-134">配置機能はアフィニティ グループに関連付けられているホストされたサービスをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9ea46-134">The deployment feature does not support hosted services that are associated with an Affinity Group.</span></span> <span data-ttu-id="9ea46-135">たとえば、アフィニティ グループに関連付けられたストレージ アカウントはこのウィザードの **配置の設定** ページで使用するためには選択できません。</span><span class="sxs-lookup"><span data-stu-id="9ea46-135">For example, storage accounts associated with an Affinity Group cannot be selected for use on the **Deployment Settings** page of this wizard.</span></span>  
  
 <span data-ttu-id="9ea46-136">VM での SQL Server のバージョンは、配置元の SQL Server のバージョンと同じまたはそれ以降である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-136">The SQL Server version in the VM must be the same or later than the source SQL Server version.</span></span> <span data-ttu-id="9ea46-137">このウィザードを使用して Azure VM にデプロイできるデータベースのバージョン SQL Server:</span><span class="sxs-lookup"><span data-stu-id="9ea46-137">SQL Server database versions that can be deployed to an Azure VM using this wizard:</span></span>  
  
-   <span data-ttu-id="9ea46-138">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="9ea46-138">SQL Server 2008</span></span>  
  
-   <span data-ttu-id="9ea46-139">SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="9ea46-139">SQL Server 2008 R2</span></span>  
  
-   <span data-ttu-id="9ea46-140">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="9ea46-140">SQL Server 2012</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 <span data-ttu-id="9ea46-141">Azure VM データベースで実行されている SQL Server データベースのバージョンは、次のように配置できます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-141">SQL Server database versions running in an Azure VM database can be deployed to:</span></span>  
  
-   <span data-ttu-id="9ea46-142">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="9ea46-142">SQL Server 2012</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 <span data-ttu-id="9ea46-143">インフライト配置操作を実行しているときに、複数のデータベース名の間で名前の競合が発生し、既存のデータベースが仮想マシン上に存在している場合は、ウィザードはインフライト データベースに対して付加的なデータベース名を提示し、操作を完了できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-143">If there is a naming conflict between the database name for an in-flight deploy operation and an existing database on the VM, the wizard will suggest an appended database name for the in-flight database to enable you to complete the operation.</span></span>  
  
###  <a name="considerations-for-deploying-a-filestream-enabled-database-to-an-azure-vm"></a><a name="filestream"></a> <span data-ttu-id="9ea46-144">FILESTREAM が有効なデータベースの Azure 仮想マシンへの配置に関する注意点</span><span class="sxs-lookup"><span data-stu-id="9ea46-144">Considerations for Deploying a FILESTREAM-enabled Database to an Azure VM</span></span>  
 <span data-ttu-id="9ea46-145">FILESTREAM オブジェクトに格納されている BLOBS があるデータベースを配置する場合は、次のガイドラインと制限事項に注意してください:</span><span class="sxs-lookup"><span data-stu-id="9ea46-145">Note the following guidelines and restrictions when deploying databases that have BLOBS stored in FILESTREAM objects:</span></span>  
  
-   <span data-ttu-id="9ea46-146">配置機能は FILESTREAM が有効なデータベースを新しい仮想マシンに配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="9ea46-146">The deployment feature cannot deploy a FILESTREAM-enabled database into a new VM.</span></span> <span data-ttu-id="9ea46-147">ウィザードを実行する前に FILESTREAM が仮想マシンで有効になっていない場合は、データベースの復元操作が失敗し、ウィザードの操作が正常に完了できません。</span><span class="sxs-lookup"><span data-stu-id="9ea46-147">If FILESTREAM is not enabled in the VM before you run the wizard, the database restore operation will fail and the wizard operation will not be able to complete successfully.</span></span> <span data-ttu-id="9ea46-148">FILESTREAM を使用するデータベースを正常に配置するには、ウィザードを起動する前にホスト仮想マシンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで FILESTREAM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-148">To successfully deploy a database that uses FILESTREAM, enable FILESTREAM in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the host VM before launching the wizard.</span></span> <span data-ttu-id="9ea46-149">詳細については、「 [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ea46-149">For more information, see [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx).</span></span>  
  
-   <span data-ttu-id="9ea46-150">データベースがインメモリ OLTP を使用すると、データベースを変更せずに Azure 仮想マシンにデータベースを配置できます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-150">If your database utilizes In-Memory OLTP, you can deploy the database to an Azure VM without any modifications to the database.</span></span> <span data-ttu-id="9ea46-151">詳細については、「 [インメモリ OLTP (インメモリ最適化)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ea46-151">For more information, see [In-Memory OLTP (In-Memory Optimization)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).</span></span>  
  
###  <a name="considerations-for-geographic-distribution-of-assets"></a><a name="geography"></a><span data-ttu-id="9ea46-152">資産の地理的分散に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="9ea46-152">Considerations for Geographic Distribution of Assets</span></span>  
 <span data-ttu-id="9ea46-153">次の資産が同じ地理的領域に存在する必要があることに注意してください:</span><span class="sxs-lookup"><span data-stu-id="9ea46-153">Note that the following assets must be located in the same geographic region:</span></span>  
  
-   <span data-ttu-id="9ea46-154">クラウド サービス</span><span class="sxs-lookup"><span data-stu-id="9ea46-154">Cloud Service</span></span>  
  
-   <span data-ttu-id="9ea46-155">仮想マシンの場所</span><span class="sxs-lookup"><span data-stu-id="9ea46-155">VM Location</span></span>  
  
-   <span data-ttu-id="9ea46-156">データ ディスク ストレージ サービス</span><span class="sxs-lookup"><span data-stu-id="9ea46-156">Data Disk Storage Service</span></span>  
  
 <span data-ttu-id="9ea46-157">上記の資産が同じ場所に配置されていない場合は、正常に完了できません。</span><span class="sxs-lookup"><span data-stu-id="9ea46-157">If the assets listed above are not co-located, the wizard will not be able to complete successfully.</span></span>  
  
###  <a name="wizard-configuration-settings"></a><a name="configuration_settings"></a><span data-ttu-id="9ea46-158">ウィザードの構成設定</span><span class="sxs-lookup"><span data-stu-id="9ea46-158">Wizard Configuration Settings</span></span>  
 <span data-ttu-id="9ea46-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース配置の Azure 仮想マシンへの設定を変更するには、次の構成の詳細を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-159">Use the following configuration details to modify settings for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database deployment to an Azure VM.</span></span>  
  
-   <span data-ttu-id="9ea46-160">**構成ファイルの既定のパス** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml</span><span class="sxs-lookup"><span data-stu-id="9ea46-160">**Default path for the configuration file** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml</span></span>  
  
-   <span data-ttu-id="9ea46-161">**構成ファイルの構造**</span><span class="sxs-lookup"><span data-stu-id="9ea46-161">**Configuration file structure**</span></span>  
  
    -   \<DeploymentSettings>  
  
        -   <span data-ttu-id="9ea46-162"><OtherSettings</span><span class="sxs-lookup"><span data-stu-id="9ea46-162"><OtherSettings</span></span>  
  
            -   <span data-ttu-id="9ea46-163">TraceLevel = "Debug"\<!-- Logging level --></span><span class="sxs-lookup"><span data-stu-id="9ea46-163">TraceLevel="Debug" \<!-- Logging level --></span></span>  
  
            -   <span data-ttu-id="9ea46-164">BackupPath = " \\ \\ [サーバー名] \\ [ボリューム] \\ "\<!-- The last used path for backup. Used as default in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="9ea46-164">BackupPath="\\\\[server name]\\[volume]\\" \<!-- The last used path for backup. Used as default in the wizard. --></span></span>  
  
            -   <span data-ttu-id="9ea46-165">CleanupDisabled = False/>\<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). --></span><span class="sxs-lookup"><span data-stu-id="9ea46-165">CleanupDisabled = False /> \<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). --></span></span>  
  
        -   <span data-ttu-id="9ea46-166"><PublishProfile\<!-- The last used publish profile information. --></span><span class="sxs-lookup"><span data-stu-id="9ea46-166"><PublishProfile \<!-- The last used publish profile information. --></span></span>  
  
            -   <span data-ttu-id="9ea46-167">Certificate = "12A34B5678901234 EF567A8"\<!-- The certificate for use in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="9ea46-167">Certificate="12A34B567890123ABCD4EF567A8" \<!-- The certificate for use in the wizard. --></span></span>  
  
            -   <span data-ttu-id="9ea46-168">Subscription = "1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx"\<!-- The subscription for use in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="9ea46-168">Subscription="1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx" \<!-- The subscription for use in the wizard. --></span></span>  
  
            -   <span data-ttu-id="9ea46-169">Name = "My Subscription"\<!-- The name of the subscription. --></span><span class="sxs-lookup"><span data-stu-id="9ea46-169">Name="My Subscription" \<!-- The name of the subscription. --></span></span>  
  
            -   <span data-ttu-id="9ea46-170">Publisher="" /></span><span class="sxs-lookup"><span data-stu-id="9ea46-170">Publisher="" /></span></span>  
  
    -   \</DeploymentSettings>  
  
 <span data-ttu-id="9ea46-171">**構成ファイルの値**</span><span class="sxs-lookup"><span data-stu-id="9ea46-171">**Configuration file values**</span></span>  
  
###  <a name="permissions"></a><a name="permissions"></a> <span data-ttu-id="9ea46-172">Permissions</span><span class="sxs-lookup"><span data-stu-id="9ea46-172">Permissions</span></span>  
 <span data-ttu-id="9ea46-173">配置されるデータベースは標準状態でなければならず、このデータベースはウィザードを実行するユーザー アカウントからアクセスできる必要があり、ユーザー アカウントにはバックアップ操作を実行する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9ea46-173">The database being deployed must be in a normal state, the database must be accessible to the user account running the wizard, and the user account must have permissions to perform a backup operation.</span></span>  
  
##  <a name="using-the-deploy-database-to-azure-vm-wizard"></a><a name="launch_wizard"></a><span data-ttu-id="9ea46-174">Azure 仮想マシンへのデータベースの配置ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="9ea46-174">Using the Deploy Database to Azure VM Wizard</span></span>  
 <span data-ttu-id="9ea46-175">**ウィザードを起動するには、次の手順を実行します。**</span><span class="sxs-lookup"><span data-stu-id="9ea46-175">**To launch the wizard, use the following steps:**</span></span>  
  
1.  <span data-ttu-id="9ea46-176">SQL Server Management Studio を使用して、配置するデータベースがある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-176">Use SQL Server Management Studio to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the database you want to deploy.</span></span>  
  
2.  <span data-ttu-id="9ea46-177">**オブジェクト エクスプローラー**で、インスタンス名を展開してから、 **データベース** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-177">In **Object Explorer**, expand the instance name, then expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="9ea46-178">配置するデータベースを右クリックし、[**タスク**] をクリックして、[ **Azure VM にデータベースを配置**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-178">Right-click the database you want to deploy, select **Tasks**, and then select **Deploy Database to Azure VM...**</span></span>  
  

  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="9ea46-179">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="9ea46-179">Introduction Page</span></span>  
 <span data-ttu-id="9ea46-180">このページでは、 **AZURE VM への SQL Server データベースのデプロイ**ウィザードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-180">This page describes the **Deploy a SQL Server Database to an Azure VM** wizard.</span></span>  
  
 <span data-ttu-id="9ea46-181">**Options**</span><span class="sxs-lookup"><span data-stu-id="9ea46-181">**Options**</span></span>  
  
-   <span data-ttu-id="9ea46-182">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="9ea46-182">**Do not show this page again.**</span></span> <span data-ttu-id="9ea46-183">- 今後 [説明] ページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-183">- Click this check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="9ea46-184">**[次へ]** - **[ソースの設定]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-184">**Next** - Proceeds to the **Source Settings** page.</span></span>  
  
-   <span data-ttu-id="9ea46-185">**[キャンセル]** : 操作を取り消し、ウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-185">**Cancel** - Cancels the operation and closes the wizard.</span></span>  
  
-   <span data-ttu-id="9ea46-186">[**ヘルプ**]: ウィザードの MSDN ヘルプトピックを起動します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-186">**Help** - Launches the MSDN Help topic for the wizard.</span></span>  
  
##  <a name="source-settings"></a><a name="Source_settings"></a><span data-ttu-id="9ea46-187">ソース設定</span><span class="sxs-lookup"><span data-stu-id="9ea46-187">Source Settings</span></span>  
 <span data-ttu-id="9ea46-188">このページを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AZURE VM に配置するデータベースをホストするのインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-188">Use this page to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the database you want to deploy to the Azure VM.</span></span> <span data-ttu-id="9ea46-189">また、ファイルを Azure に転送する前に、ローカルコンピューターから保存するファイルの一時的な場所も指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-189">You will also specify a temporary location for files to be saved from the local machine before they are transferred to Azure.</span></span> <span data-ttu-id="9ea46-190">共有のネットワークの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-190">This can be a shared, network location.</span></span>  
  
 <span data-ttu-id="9ea46-191">**Options**</span><span class="sxs-lookup"><span data-stu-id="9ea46-191">**Options**</span></span>  
  
-   <span data-ttu-id="9ea46-192">[**接続...** ] をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置するデータベースをホストするのインスタンスの接続詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-192">Click **Connect...** and then specify connection details for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the database to deploy.</span></span>  
  
-   <span data-ttu-id="9ea46-193">**[データベースの選択]** ドロップダウン リストを使用して、展開するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-193">Use the **Select Database** drop-down list to specify the database to deploy.</span></span>  
  
-   <span data-ttu-id="9ea46-194">[**その他の設定**] フィールドで、Azure VM サービスにアクセスできる共有フォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-194">In the **Other Settings** field, specify a shared folder that will be accessible to the Azure VM service.</span></span>  
  
##  <a name="azure-sign-in"></a><a name="Azure_sign-in"></a><span data-ttu-id="9ea46-195">Azure サインイン</span><span class="sxs-lookup"><span data-stu-id="9ea46-195">Azure Sign-in</span></span>  
 <span data-ttu-id="9ea46-196">このページを使用して、Azure に接続し、管理証明書または発行プロファイルの詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-196">Use this page to connect to Azure and provide management certificate or publishing profile details.</span></span>  
  
 <span data-ttu-id="9ea46-197">**Options**</span><span class="sxs-lookup"><span data-stu-id="9ea46-197">**Options**</span></span>  
  
-   <span data-ttu-id="9ea46-198">[**管理証明書**]-このオプションを使用して、Azure の管理証明書に一致するローカル証明書ストアの証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-198">**Management Certificate** - Use this option to specify a certificate from the local certificate store that matches the management certificate from Azure.</span></span>  
  
-   <span data-ttu-id="9ea46-199">[**発行プロファイル**]: コンピューターにダウンロードした発行プロファイルがある場合に、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-199">**Publishing Profile** - Use this option if you already have a publishing profile downloaded to your computer.</span></span>  
  
-   <span data-ttu-id="9ea46-200">**サインイン**-このオプションを使用して、Live ID や Hotmail アカウントなどの Microsoft アカウントを使用して Azure にサインインし、新しい管理証明書を生成してダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-200">**Sign In** - Use this option to sign in to Azure using a Microsoft account - for example, a Live ID or Hotmail account - to generate and download a new management certificate.</span></span> <span data-ttu-id="9ea46-201">サブスクリプションごとの証明書の数は制限されています。</span><span class="sxs-lookup"><span data-stu-id="9ea46-201">Note that the number of certificates per subscription is limited.</span></span>  
  
-   <span data-ttu-id="9ea46-202">[**サブスクリプション**]-ローカルの証明書ストアまたは公開プロファイルと一致する、AZURE サブスクリプション ID を選択、入力、または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-202">**Subscription** - Select, type, or paste your Azure subscription ID that matches the management certificate from the local certificate store or a publishing profile.</span></span>  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a><span data-ttu-id="9ea46-203">[展開設定] ページ</span><span class="sxs-lookup"><span data-stu-id="9ea46-203">Deployment Settings Page</span></span>  
 <span data-ttu-id="9ea46-204">このページを使用して、配置先サーバーと、新しいデータベースの詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-204">Use this page to specify the destination server and to provide details about your new database.</span></span>  
  
 <span data-ttu-id="9ea46-205">**Options**</span><span class="sxs-lookup"><span data-stu-id="9ea46-205">**Options**</span></span>  
  
-   <span data-ttu-id="9ea46-206">**Azure 仮想マシン**-SQL Server データベースをホストする VM の詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-206">**Azure Virtual Machine** - Specify details for the VM that will host the SQL Server database:</span></span>  
  
-   <span data-ttu-id="9ea46-207">**クラウドサービス名**-VM をホストするサービスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-207">**Cloud Service name** - Specify the name of the service that hosts the VM.</span></span> <span data-ttu-id="9ea46-208">新しいクラウド サービスを作成するには、新しいクラウド サービスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-208">To create a new Cloud Service, specify a name for the new Cloud Service.</span></span>  
  
-   <span data-ttu-id="9ea46-209">**仮想マシン名**-SQL Server データベースをホストする VM の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-209">**Virtual Machine name** - Specify the name of the VM that will host the SQL Server database.</span></span> <span data-ttu-id="9ea46-210">新しい Azure VM を作成するには、新しい VM の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-210">To create a new Azure VM, specify a name for the new VM.</span></span>  
  
-   <span data-ttu-id="9ea46-211">**設定**-[設定] ボタンを使用して、SQL Server データベースをホストする新しい VM を作成します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-211">**Settings** - Use the Settings button to create a new VM to host the SQL Server database.</span></span> <span data-ttu-id="9ea46-212">既存の仮想マシンを使用している場合は、指定した情報を使用して資格情報の認証が行われます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-212">If you are using an existing VM, the information you provide will be used to authenticate your credentials.</span></span>  
  
-   <span data-ttu-id="9ea46-213">[**ストレージアカウント**]-ドロップダウンリストからストレージアカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-213">**Storage account** - Select the storage account from the drop-down list.</span></span> <span data-ttu-id="9ea46-214">新しいストレージ アカウントを作成するには、新しいアカウントの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-214">To create a new storage account, specify a name for the new account.</span></span> <span data-ttu-id="9ea46-215">アフィニティ グループに関連付けられたストレージ アカウントは、ドロップダウン リストに使用できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9ea46-215">Note that storage accounts associated with an Affinity Group will not be available in the drop-down list.</span></span>  
  
-   <span data-ttu-id="9ea46-216">**ターゲットデータベース**-ターゲットデータベースの詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-216">**Target Database** - Specify details for the target database.</span></span>  
  
-   <span data-ttu-id="9ea46-217">サーバー**接続**-サーバーの接続の詳細。</span><span class="sxs-lookup"><span data-stu-id="9ea46-217">**Server Connection** - Connection details for the server.</span></span>  
  
-   <span data-ttu-id="9ea46-218">**データベース**-新しいデータベースの名前を指定または確認します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-218">**Database** - Specify or confirm the name of a new database.</span></span> <span data-ttu-id="9ea46-219">対象の SQL Server インスタンスにデータベース名が既にある場合は、変更したデータベース名を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-219">If the database name already exists on the destination SQL Server instance, we suggest that you specify a modified database name.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="9ea46-220">[概要] ページ</span><span class="sxs-lookup"><span data-stu-id="9ea46-220">Summary Page</span></span>  
 <span data-ttu-id="9ea46-221">このページを使用すると、操作について指定した設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-221">Use this page to review the specified settings for the operation.</span></span> <span data-ttu-id="9ea46-222">指定した設定で配置操作を実行するには、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-222">To complete the deploy operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="9ea46-223">配置操作を取り消してウィザードを終了するには、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-223">To cancel the deploy operation and exit the wizard, click **Cancel**.</span></span>  
  
 <span data-ttu-id="9ea46-224">Azure VM の SQL Server データベースにデータベースの詳細をデプロイするには、手動の手順が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ea46-224">There may be manual steps required to deploy database details to the SQL Server database on the Azure VM.</span></span> <span data-ttu-id="9ea46-225">これらの手順については概要を詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-225">These steps will be outlined in detail for you.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="9ea46-226">[結果] ページ</span><span class="sxs-lookup"><span data-stu-id="9ea46-226">Results Page</span></span>  
 <span data-ttu-id="9ea46-227">このページでは、配置操作の成功と失敗が報告され、各アクションの結果が示されます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-227">This page reports the success or failure of the deploy operation, showing the results of each action.</span></span> <span data-ttu-id="9ea46-228">エラーが発生したアクションには、 **[結果]** 列に情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ea46-228">Any action that encountered an error will have an indication in the **Result** column.</span></span> <span data-ttu-id="9ea46-229">そのアクションのエラーのレポートを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ea46-229">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="9ea46-230">**[完了]** をクリックして、ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="9ea46-230">Click **Finish** to close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea46-231">参照</span><span class="sxs-lookup"><span data-stu-id="9ea46-231">See Also</span></span>  
 <span data-ttu-id="9ea46-232">[SQL Server のクラウドアダプター](../../database-engine/cloud-adapter-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9ea46-232">[Cloud Adapter for SQL Server](../../database-engine/cloud-adapter-for-sql-server.md) </span></span>  
 <span data-ttu-id="9ea46-233">[データベースライフサイクル管理](../database-lifecycle-management.md) </span><span class="sxs-lookup"><span data-stu-id="9ea46-233">[Database Lifecycle Management](../database-lifecycle-management.md) </span></span>  
 <span data-ttu-id="9ea46-234">[データ層アプリケーションのエクスポート](../data-tier-applications/export-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="9ea46-234">[Export a Data-tier Application](../data-tier-applications/export-a-data-tier-application.md) </span></span>  
 <span data-ttu-id="9ea46-235">[BACPAC ファイルをインポートして新しいユーザーデータベースを作成する](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md) </span><span class="sxs-lookup"><span data-stu-id="9ea46-235">[Import a BACPAC File to Create a New User Database](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md) </span></span>  
 <span data-ttu-id="9ea46-236">[Azure SQL Database のバックアップと復元](https://msdn.microsoft.com/library/azure/jj650016.aspx) </span><span class="sxs-lookup"><span data-stu-id="9ea46-236">[Azure SQL Database Backup and Restore](https://msdn.microsoft.com/library/azure/jj650016.aspx) </span></span>  
 <span data-ttu-id="9ea46-237">[Azure Virtual Machines での SQL Server デプロイ](https://msdn.microsoft.com/library/dn133141.aspx) </span><span class="sxs-lookup"><span data-stu-id="9ea46-237">[SQL Server Deployment in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133141.aspx) </span></span>  
 [<span data-ttu-id="9ea46-238">Azure の仮想マシンに SQL Server を移行するための準備</span><span class="sxs-lookup"><span data-stu-id="9ea46-238">Getting Ready to Migrate to SQL Server in Azure Virtual Machines</span></span>](https://msdn.microsoft.com/library/dn133142.aspx)  
  
  
