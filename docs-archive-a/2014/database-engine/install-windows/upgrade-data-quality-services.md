---
title: Data Quality Services のアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: f396666b-7754-4efc-9507-0fd114cc32d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9d2544df341a831f2f676ec58150ed64a800fb96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634620"
---
# <a name="upgrade-data-quality-services"></a><span data-ttu-id="c7261-102">Data Quality Services のアップグレード</span><span class="sxs-lookup"><span data-stu-id="c7261-102">Upgrade Data Quality Services</span></span>
  <span data-ttu-id="c7261-103">このトピックでは、Data Quality Services (DQS) の既存のインストールを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 にアップグレードする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="c7261-103">This topic provides information on how to upgrade your existing installation of Data Quality Services (DQS) to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="c7261-104">DQS 内の Data Quality サーバーを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードする作業の一環として、DQS データベース スキーマもアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7261-104">As part of upgrading your Data Quality Server in DQS to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must also upgrade the DQS databases schema.</span></span>  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="c7261-105">スキーマのアップグレード中に誤ってデータが削除されることを防ぐため、DQS をアップグレードする前に DQS データベースをバックアップしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7261-105">You must back up your DQS databases before upgrading DQS to prevent any accidental data loss during the schema upgrade.</span></span> <span data-ttu-id="c7261-106">DQS データベースのバックアップの詳細については、「 [DQS データベースのバックアップと復元](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7261-106">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).</span></span>  
> -   <span data-ttu-id="c7261-107">データ品質タスクを実行するために、現在または以前のバージョンの Data Quality クライアントか、Integration Services 内の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] DQS クレンジング変換 [を使用して、Data Quality サーバーの](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) バージョンに接続できます。</span><span class="sxs-lookup"><span data-stu-id="c7261-107">You can connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Data Quality Server by using the current or an earlier version of Data Quality Client or the [DQS Cleansing Transformation](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) in Integration Services to perform your data quality tasks.</span></span>  
> -   <span data-ttu-id="c7261-108">Data Quality Services およびマスター データ サービスを [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] CTP2 にアップグレードした後も、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 バージョンの Excel 用マスター データ サービス アドインを使用し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="c7261-108">You can continue using the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel after upgrading Data Quality Services and Master Data Services to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="c7261-109">ただし、SQL Server 2014 CTP2 にアップグレードした後、以前のバージョンの Excel 用マスター データ サービス アドインは機能しません。</span><span class="sxs-lookup"><span data-stu-id="c7261-109">However, any earlier version of the Master Data Services Add-In for Excel will not work after upgrading to SQL Server 2014 CTP2.</span></span> <span data-ttu-id="c7261-110">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]SP1 バージョンの Excel 用マスターデータサービスアドインは、[こちら](https://go.microsoft.com/fwlink/?LinkId=328664)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="c7261-110">You can download the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel from [here](https://go.microsoft.com/fwlink/?LinkId=328664).</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c7261-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="c7261-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="c7261-112">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コンピューターの Administrators グループのメンバーとしてログオンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7261-112">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="c7261-113">Windows ユーザー アカウントが、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] がインストールされている SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c7261-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
##  <a name="upgrading-dqs"></a><a name="Upgrade"></a> <span data-ttu-id="c7261-114">DQS のアップグレード</span><span class="sxs-lookup"><span data-stu-id="c7261-114">Upgrading DQS</span></span>  
 <span data-ttu-id="c7261-115">DQS をアップグレードするには:</span><span class="sxs-lookup"><span data-stu-id="c7261-115">To upgrade DQS:</span></span>  
  
1.  <span data-ttu-id="c7261-116">スキーマのアップグレードを開始する前に、DQS データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="c7261-116">Back up your DQS databases before you start the upgrade process.</span></span> <span data-ttu-id="c7261-117">DQS データベースのバックアップの詳細については、「 [DQS データベースのバックアップと復元](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7261-117">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).</span></span>  
  
2.  <span data-ttu-id="c7261-118">DQS のインストール先である SQL Server インスタンスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="c7261-118">Upgrade the SQL Server instance where DQS is installed to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    1.  <span data-ttu-id="c7261-119">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="c7261-119">Run the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="c7261-120">左ペインで、 **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7261-120">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="c7261-121">右ペインで、[ **SQL Server 2005、SQL Server 2008、SQL Server 2008 R2 または SQL Server 2012 からのアップグレード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7261-121">In the right pane, click **Upgrade from SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 or SQL Server 2012**.</span></span>  
  
    4.  <span data-ttu-id="c7261-122">セットアップ ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="c7261-122">Complete the Setup wizard.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c7261-123">この結果、SQL Server インスタンスが [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードされ、また、このコンピューターに以前に Data Quality クライアントがインストールされていた場合は、最新の Data Quality クライアントがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c7261-123">This will upgrade your SQL Server instance to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and also install the latest Data Quality Client, if Data Quality Client was previously installed on this computer.</span></span> <span data-ttu-id="c7261-124">他のコンピューターに Data Quality クライアントをインストールしていた場合は、それらのコンピューターに対して手順 2. の下位の手順を実行して、現在のバージョンの Data Quality クライアントをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7261-124">If you have Data Quality Client installed on other computers, you must run the sub steps in Step 2 on those computers to install the current version of Data Quality Client.</span></span> <span data-ttu-id="c7261-125">セットアップ ウィザードは、Data Quality クライアントの既存のバージョンと並行して、Data Quality クライアントの現在のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c7261-125">The Setup wizard installs the current version of Data Quality Client alongside the existing version of Data Quality Client.</span></span> <span data-ttu-id="c7261-126">DQS データベース スキーマをアップグレードした後、現在または以前のバージョンの Data Quality クライアントを使用して、Data Quality サーバーの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンに接続できます。</span><span class="sxs-lookup"><span data-stu-id="c7261-126">After you upgrade the DQS databases schema, you can connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Data Quality Server by using the current or an earlier version of Data Quality Client.</span></span>  
  
3.  <span data-ttu-id="c7261-127">DQS データベース スキーマをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="c7261-127">Upgrade the DQS databases schema.</span></span>  
  
    1.  <span data-ttu-id="c7261-128">管理者としてコマンド プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="c7261-128">Start Command Prompt as an administrator.</span></span>  
  
    2.  <span data-ttu-id="c7261-129">コマンド プロンプトで、DQSInstaller.exe が格納されている場所にディレクトリを変更します。</span><span class="sxs-lookup"><span data-stu-id="c7261-129">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="c7261-130">SQL Server の既定のインスタンスの場合は、DQSInstaller.exe ファイルは C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn に格納されます。</span><span class="sxs-lookup"><span data-stu-id="c7261-130">For the default instance of SQL Server, the DQSInstaller.exe file is available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
        ```  
        cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
        ```  
  
    3.  <span data-ttu-id="c7261-131">コマンド プロンプトに次のコマンドを入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c7261-131">At the command prompt, type the following command, and press ENTER:</span></span>  
  
        ```  
        dqsinstaller.exe -upgrade  
        ```  
  
    4.  <span data-ttu-id="c7261-132">処理を続ける前に DQS データベースをバックアップするように求められます。</span><span class="sxs-lookup"><span data-stu-id="c7261-132">The installer prompts you for backing up the DQS databases before proceeding.</span></span> <span data-ttu-id="c7261-133">既に DQS データベースをバックアップしている場合 `Y` は、またはを入力し、enter `Yes` キーを押してアップグレードを続行します。</span><span class="sxs-lookup"><span data-stu-id="c7261-133">If you have already backed up your DQS databases, type `Y` or `Yes`, and then press ENTER to continue with the upgrade.</span></span>  
  
    5.  <span data-ttu-id="c7261-134">DQS データベース スキーマのアップグレードが正常に完了すると、完了のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7261-134">A completion message is displayed after successful upgrade of the DQS databases schema.</span></span>  
  
##  <a name="verifying-the-dqs-databases-schema-upgrade"></a><a name="Verify"></a> <span data-ttu-id="c7261-135">DQS データベース スキーマのアップグレードの確認</span><span class="sxs-lookup"><span data-stu-id="c7261-135">Verifying the DQS Databases Schema Upgrade</span></span>  
 <span data-ttu-id="c7261-136">DQS データベース スキーマが正常にアップグレードされたことを確認するために、各データベース内の A_DB_VERSION テーブルに対してクエリを実行し、DQS_MAIN データベースと DQS_PROJECTS データベースの現在のバージョンを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="c7261-136">To verify that DQS databases schema have successfully upgraded, you can check the current version in the DQS_MAIN and DQS_PROJECTS databases by querying the A_DB_VERSION table in each database.</span></span> <span data-ttu-id="c7261-137">そのためには次を行います。</span><span class="sxs-lookup"><span data-stu-id="c7261-137">To do so:</span></span>  
  
1.  <span data-ttu-id="c7261-138">SQL Server Management Studio を起動し、アップグレード後の DQS データベース スキーマを含む SQL Server インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c7261-138">Start SQL Server Management Studio, and connect to the SQL Server instance that contains the upgraded DQS databases schema.</span></span>  
  
2.  <span data-ttu-id="c7261-139">次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c7261-139">Run the following query:</span></span>  
  
    ```  
    SELECT * FROM DQS_MAIN.dbo.A_DB_VERSION WHERE STATUS=2;  
    SELECT * FROM DQS_PROJECTS.dbo.A_DB_VERSION WHERE STATUS=2;  
    ```  
  
3.  <span data-ttu-id="c7261-140">出力で、アップグレードの日付と共に、各アップグレードのエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7261-140">The output will display an entry for each upgrade along with the date of the upgrade.</span></span> <span data-ttu-id="c7261-141">最新の日付になっていて、値が最も大きい VERSION_ID と ASSEMBLY_VERSION が、現在のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="c7261-141">The maximum VERSION_ID and ASSEMBLY_VERSION on the latest date is the current version.</span></span> <span data-ttu-id="c7261-142">STATUS 列に値 2 が表示されている場合は、成功を示しています。</span><span class="sxs-lookup"><span data-stu-id="c7261-142">A value of 2 in the STATUS column indicates success.</span></span> <span data-ttu-id="c7261-143">エラーが発生した場合は、ERROR 列にそのエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7261-143">If an error has occurred, the error will be listed in the ERROR column.</span></span> <span data-ttu-id="c7261-144">サンプル出力を示します。</span><span class="sxs-lookup"><span data-stu-id="c7261-144">A sample output:</span></span>  
  
    |<span data-ttu-id="c7261-145">id</span><span class="sxs-lookup"><span data-stu-id="c7261-145">ID</span></span>|<span data-ttu-id="c7261-146">UPGRADE_DATE</span><span class="sxs-lookup"><span data-stu-id="c7261-146">UPGRADE_DATE</span></span>|<span data-ttu-id="c7261-147">VERSION_ID</span><span class="sxs-lookup"><span data-stu-id="c7261-147">VERSION_ID</span></span>|<span data-ttu-id="c7261-148">ASSEMBLY_VERSION</span><span class="sxs-lookup"><span data-stu-id="c7261-148">ASSEMBLY_VERSION</span></span>|<span data-ttu-id="c7261-149">USER_NAME</span><span class="sxs-lookup"><span data-stu-id="c7261-149">USER_NAME</span></span>|<span data-ttu-id="c7261-150">状態</span><span class="sxs-lookup"><span data-stu-id="c7261-150">STATUS</span></span>|<span data-ttu-id="c7261-151">ERROR</span><span class="sxs-lookup"><span data-stu-id="c7261-151">ERROR</span></span>|  
    |--------|-------------------|-----------------|-----------------------|----------------|------------|-----------|  
    |<span data-ttu-id="c7261-152">1000</span><span class="sxs-lookup"><span data-stu-id="c7261-152">1000</span></span>|<span data-ttu-id="c7261-153">2013-08-11 05:26:39.567</span><span class="sxs-lookup"><span data-stu-id="c7261-153">2013-08-11 05:26:39.567</span></span>|<span data-ttu-id="c7261-154">1200</span><span class="sxs-lookup"><span data-stu-id="c7261-154">1200</span></span>|<span data-ttu-id="c7261-155">11.0.3000.0</span><span class="sxs-lookup"><span data-stu-id="c7261-155">11.0.3000.0</span></span>|\<DOMAIN\UserName>|<span data-ttu-id="c7261-156">2</span><span class="sxs-lookup"><span data-stu-id="c7261-156">2</span></span>||  
    |<span data-ttu-id="c7261-157">1001</span><span class="sxs-lookup"><span data-stu-id="c7261-157">1001</span></span>|<span data-ttu-id="c7261-158">2013-09-19 15:09:37.750</span><span class="sxs-lookup"><span data-stu-id="c7261-158">2013-09-19 15:09:37.750</span></span>|<span data-ttu-id="c7261-159">1600</span><span class="sxs-lookup"><span data-stu-id="c7261-159">1600</span></span>|<span data-ttu-id="c7261-160">12.0.xxxx.0</span><span class="sxs-lookup"><span data-stu-id="c7261-160">12.0.xxxx.0</span></span>|\<DOMAIN\UserName>|<span data-ttu-id="c7261-161">2</span><span class="sxs-lookup"><span data-stu-id="c7261-161">2</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="c7261-162">参照</span><span class="sxs-lookup"><span data-stu-id="c7261-162">See Also</span></span>  
 <span data-ttu-id="c7261-163">[Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="c7261-163">[Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md) </span></span>  
 <span data-ttu-id="c7261-164">[Data Quality Server オブジェクトの削除](../../sql-server/install/remove-data-quality-server-objects.md) </span><span class="sxs-lookup"><span data-stu-id="c7261-164">[Remove Data Quality Server Objects](../../sql-server/install/remove-data-quality-server-objects.md) </span></span>  
 [<span data-ttu-id="c7261-165">SQL Server 2014 へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="c7261-165">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
  
  
