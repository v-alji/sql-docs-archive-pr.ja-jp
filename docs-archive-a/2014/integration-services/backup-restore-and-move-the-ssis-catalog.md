---
title: SSIS カタログをバックアップ、復元、移動する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9de552ddd54168f516f42d9988302561616fd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639624"
---
# <a name="backup-restore-and-move-the-ssis-catalog"></a><span data-ttu-id="30d41-102">SSIS カタログのバックアップ、復元、および移動</span><span class="sxs-lookup"><span data-stu-id="30d41-102">Backup, Restore, and Move the SSIS Catalog</span></span>
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] <span data-ttu-id="30d41-103">には SSISDB データベースが用意されています。</span><span class="sxs-lookup"><span data-stu-id="30d41-103">includes the SSISDB database.</span></span> <span data-ttu-id="30d41-104">**SSISDB** カタログに格納されているオブジェクト、設定、および業務データを検査するには、SSISDB データベースのビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d41-104">You query views in the SSISDB database to inspect objects, settings, and operational data that are stored in the **SSISDB** catalog.</span></span> <span data-ttu-id="30d41-105">このトピックでは、データベースのバックアップと復元の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="30d41-105">This topic provides instructions for backing up and restoring the database.</span></span>  
  
 <span data-ttu-id="30d41-106">**SSISDB** カタログは、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置したパッケージを格納します。</span><span class="sxs-lookup"><span data-stu-id="30d41-106">The **SSISDB** catalog stores the packages that you've deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="30d41-107">カタログの詳細については、「 [SSIS カタログ](catalog/ssis-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-107">For more information about the catalog, see [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
##  <a name="to-back-up-the-ssis-database"></a><a name="backup"></a> <span data-ttu-id="30d41-108">SSIS データベースをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="30d41-108">To Back up the SSIS Database</span></span>  
  
1.  <span data-ttu-id="30d41-109">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="30d41-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="30d41-110">BACKUP MASTER KEY Transact-SQL ステートメントを使用して、SSISDB データベースのマスター キーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="30d41-110">Back up the master key for the SSISDB database, by using the BACKUP MASTER KEY Transact-SQL statement.</span></span> <span data-ttu-id="30d41-111">このキーは指定したファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="30d41-111">The key is stored in a file that you specify.</span></span> <span data-ttu-id="30d41-112">ファイル内のマスター キーを暗号化するには、パスワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="30d41-112">Use a password to encrypt the master key in the file.</span></span>  
  
     <span data-ttu-id="30d41-113">ステートメントの詳細については、「[BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-113">For more information about the statement, see [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
     <span data-ttu-id="30d41-114">次の例では、マスター キーが `c:\temp directory\RCTestInstKey` ファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="30d41-114">In the following example, the master key is exported to the `c:\temp directory\RCTestInstKey` file.</span></span> <span data-ttu-id="30d41-115">マスター キーの暗号化には、 `LS2Setup!` というパスワードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="30d41-115">The `LS2Setup!` password is used to encrypt the master key.</span></span>  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  <span data-ttu-id="30d41-116">**の** [データベースのバックアップ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用して SSISDB データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="30d41-116">Back up the SSISDB database by using the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="30d41-117">詳細については、「[データベースをバックアップする方法 (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812) に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30d41-117">For more information, see [How to: Back Up a Database (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812).</span></span>  
  
4.  <span data-ttu-id="30d41-118">次の手順を実行して、##MS_SSISServerCleanupJobLogin## の CREATE LOGIN スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="30d41-118">Generate the CREATE LOGIN script for ##MS_SSISServerCleanupJobLogin##, by doing the following.</span></span> <span data-ttu-id="30d41-119">詳細については、「[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-119">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
    1.  <span data-ttu-id="30d41-120">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、 **[セキュリティ]** ノードを展開し、 **[ログイン]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="30d41-120">In Object Explorer in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Security** node and then expand the **Logins** node.</span></span>  
  
    2.  <span data-ttu-id="30d41-121">**[##MS_SSISServerCleanupJobLogin##]** を右クリックし、 **[ログインをスクリプト化]**  >  **[CREATE]**  >  **[新しいクエリ エディター ウィンドウ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d41-121">Right-click **##MS_SSISServerCleanupJobLogin##**, and then click **Script Login as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
5.  <span data-ttu-id="30d41-122">SSISDB カタログが作成されていない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに SSISDB データベースを復元する場合は、次の操作を行って、sp_ssis_startup の CREATE PROCEDURE スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="30d41-122">If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, generate the CREATE PROCEDURE script for sp_ssis_startup, by doing the following.</span></span> <span data-ttu-id="30d41-123">詳細については、「[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-123">For more information, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
    1.  <span data-ttu-id="30d41-124">オブジェクトエクスプローラーで、[**データベース**] ノードを展開し、[**システムデータベース**] [master] [プログラミング] [  >  **master**  >  **Programmability**  >  **ストアドプロシージャ**] ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="30d41-124">In Object Explorer, expand the **Databases** node and then expand the **System Databases** > **master** > **Programmability** > **Stored Procedures** node.</span></span>  
  
    2.  <span data-ttu-id="30d41-125">**[dbo.sp_ssis_startup]** を右クリックし、 **[ストアド プロシージャをスクリプト化]** > **[CREATE]** > **[新しいクエリ エディター ウィンドウ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="30d41-125">Right click **dbo.sp_ssis_startup**, and then click **Script Stored Procedure as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
6.  <span data-ttu-id="30d41-126">SQL Server エージェントが起動したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="30d41-126">Confirm that SQL Server Agent has been started</span></span>  
  
7.  <span data-ttu-id="30d41-127">SSISDB カタログが作成されていない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに SSISDB データベースを復元する場合は、次の操作を行って、SSIS サーバー メンテナンス ジョブのスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="30d41-127">If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, generate a script for the SSIS Server Maintenance Job by doing the following.</span></span> <span data-ttu-id="30d41-128">SSISDB カタログが作成されると、スクリプトは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントで自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="30d41-128">The script is created in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent automatically when the SSISDB catalog is created.</span></span> <span data-ttu-id="30d41-129">このジョブは、保有期間外の操作ログのクリーンアップおよび古いバージョンのプロジェクトの削除に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="30d41-129">The job helps clean up cleanup operation logs outside the retention window and remove older versions of projects.</span></span>  
  
    1.  <span data-ttu-id="30d41-130">オブジェクト エクスプローラーで、 **[SQL Server エージェント]** ノードを展開し、 **[ジョブ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="30d41-130">In Object Explorer, expand the **SQL Server Agent** node and then expand the **Jobs** node.</span></span>  
  
    2.  <span data-ttu-id="30d41-131">[SSIS サーバーメンテナンスジョブ] を右クリックし、[ジョブをスクリプト化] をクリックし**て**  >  **CREATE To**  >  **新しいクエリエディターウィンドウ**を作成します。</span><span class="sxs-lookup"><span data-stu-id="30d41-131">Right click SSIS Server Maintenance Job, and then click **Script Job as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
### <a name="to-restore-the-ssis-database"></a><span data-ttu-id="30d41-132">SSIS データベースを復元するには</span><span class="sxs-lookup"><span data-stu-id="30d41-132">To Restore the SSIS Database</span></span>  
  
1.  <span data-ttu-id="30d41-133">SSISDB カタログが作成されていない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに SSISDB データベースを復元する場合は、sp_configure ストアド プロシージャを実行して、共通言語ランタイム (CLR) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="30d41-133">If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, enable common language runtime (clr) by running the sp_configure stored procedure.</span></span> <span data-ttu-id="30d41-134">詳細については、「[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)」と「[clr enabled サーバー構成オプション](https://go.microsoft.com/fwlink/?LinkId=231855)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-134">For more information, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) and [clr enabled Option](https://go.microsoft.com/fwlink/?LinkId=231855).</span></span>  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  <span data-ttu-id="30d41-135">SSISDB カタログが作成されていない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに SSISDB データベースを復元する場合は、非対称キーと非対称キーからのログインを作成し、UNSAFE 権限をログインに付与します。</span><span class="sxs-lookup"><span data-stu-id="30d41-135">If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, create the asymmetric key and the login from the asymmetric key, and grant UNSAFE permission to the login.</span></span>  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="30d41-136">ログインを行うには Microsoft Win32 API などの制限付きのリソースへの追加アクセスが必要であるため、CLR ストアド プロシージャでは、UNSAFE 権限をログインに付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30d41-136">CLR stored procedures require UNSAFE permissions to be granted to the login because the login requires additional access to restricted resources, such as the Microsoft Win32 API.</span></span> <span data-ttu-id="30d41-137">UNSAFE コード権限の要件の詳細については、「 [アセンブリの作成](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-137">For more information about the UNSAFE code permission, see [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).</span></span>  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  <span data-ttu-id="30d41-138">**の** [データベースの復元] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用して、バックアップから SSISDB データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="30d41-138">Restore the SSISDB database from the backup by using the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="30d41-139">詳細については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-139">For more information, see the following topics.</span></span>  
  
    -   <span data-ttu-id="30d41-140">[[データベースの復元] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="30d41-140">[Restore Database &#40;General Page&#41;](general-page-of-integration-services-designers-options.md)</span></span>  
  
    -   <span data-ttu-id="30d41-141">[[データベースの復元] &#40;[ファイル] ページ&#41;](../relational-databases/backup-restore/restore-database-files-page.md)</span><span class="sxs-lookup"><span data-stu-id="30d41-141">[Restore Database &#40;Files Page&#41;](../relational-databases/backup-restore/restore-database-files-page.md)</span></span>  
  
    -   <span data-ttu-id="30d41-142">[[データベースの復元] &#40;[オプション] ページ&#41;](../relational-databases/backup-restore/restore-database-options-page.md)</span><span class="sxs-lookup"><span data-stu-id="30d41-142">[Restore Database &#40;Options Page&#41;](../relational-databases/backup-restore/restore-database-options-page.md)</span></span>  
  
4.  <span data-ttu-id="30d41-143">##MS_SSISServerCleanupJobLogin##、sp_ssis_startup、および SSIS サーバー メンテナンス ジョブの「 [SSIS をバックアップするには](#backup) 」で作成したスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="30d41-143">Execute the scripts that you created in the [To Back up the SSIS Database](#backup) for ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup, and SSIS Server Maintenance Job.</span></span> <span data-ttu-id="30d41-144">SQL Server エージェントが起動したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="30d41-144">Confirm that SQL Server Agent has been started.</span></span>  
  
5.  <span data-ttu-id="30d41-145">次のステートメントを実行して、sp_ssis_startup プロシージャの自動実行を設定します。</span><span class="sxs-lookup"><span data-stu-id="30d41-145">Run the following statement to set the sp_ssis_startup prodecure for autoexecution.</span></span> <span data-ttu-id="30d41-146">詳細については、「[sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-146">For more information, see [sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql).</span></span>  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  <span data-ttu-id="30d41-147">**の** [ログインのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用して、SSISDB ユーザーの ##MS_SSISServerCleanupJobUser## (SSISDB database) を ##MS_SSISServerCleanupJobLogin## にマップします。</span><span class="sxs-lookup"><span data-stu-id="30d41-147">Map the SSISDB user ##MS_SSISServerCleanupJobUser## (SSISDB database) to ##MS_SSISServerCleanupJobLogin##, by using the **Login Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
7.  <span data-ttu-id="30d41-148">次のいずれかの方法を使用して、マスター キーを復元します。</span><span class="sxs-lookup"><span data-stu-id="30d41-148">Restore the master key by using one of the following methods.</span></span> <span data-ttu-id="30d41-149">暗号化の詳細については、「 [暗号化階層](../relational-databases/security/encryption/encryption-hierarchy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-149">For more information about encryption, see [Encryption Hierarchy](../relational-databases/security/encryption/encryption-hierarchy.md).</span></span>  
  
    -   <span data-ttu-id="30d41-150">**方法 1**</span><span class="sxs-lookup"><span data-stu-id="30d41-150">**Method 1**</span></span>  
  
         <span data-ttu-id="30d41-151">この方法は、データベース マスター キーのバックアップが実行済みで、マスター キーの暗号化に使用するパスワードがある場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="30d41-151">Use this method if you've already performed a backup of the database master key, and you have the password used to encrypt the master key.</span></span>  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="30d41-152">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス アカウントにバックアップ キー ファイルの読み取り権限があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-152">Confirm that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service account has permissions to read the backup key file.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="30d41-153">データベース マスター キーがサービス マスター キーによって暗号化されていない場合、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] には次の警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30d41-153">You will see the following warning message displayed in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] if the database master key has not yet been encrypted by the service master key.</span></span> <span data-ttu-id="30d41-154">この警告メッセージは無視してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-154">Ignore the warning message.</span></span>  
        >   
        >  <span data-ttu-id="30d41-155">**現在のマスター キーは暗号化解除できません。FORCE オプションが指定されたので、エラーは無視されました。**</span><span class="sxs-lookup"><span data-stu-id="30d41-155">**The current master key cannot be decrypted. The error was ignored because the FORCE option was specified.**</span></span>  
        >   
        >  <span data-ttu-id="30d41-156">FORCE 引数は、現在のデータベース マスター キーが開いていない場合でも復元プロセスを続行するように指定します。</span><span class="sxs-lookup"><span data-stu-id="30d41-156">The FORCE argument specifies that the restore process should continue even if the current database master key is not open.</span></span> <span data-ttu-id="30d41-157">SSISDB カタログについては、データベースを復元するインスタンスでデータベース マスター キーが開いていないため、このメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30d41-157">For the SSISDB catalog, because the database master key has not been opened on the instance where you are restoring the database, you will see this message.</span></span>  
  
    -   <span data-ttu-id="30d41-158">**方法 2**</span><span class="sxs-lookup"><span data-stu-id="30d41-158">**Method 2**</span></span>  
  
         <span data-ttu-id="30d41-159">この方法は、SSISDB の作成に使用した元のパスワードがある場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="30d41-159">Use this method if you have the original password that was used to create SSISDB.</span></span>  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  <span data-ttu-id="30d41-160">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.check_schema_version [を実行して、SSISDB カタログ スキーマと](/sql/integration-services/system-stored-procedures/catalog-check-schema-version)バイナリ (ISServerExec および SQLCLR アセンブリ) に互換性があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="30d41-160">Determine whether the SSISDB catalog schema and the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] binaries (ISServerExec and SQLCLR assembly) are compatible, by running [catalog.check_schema_version](/sql/integration-services/system-stored-procedures/catalog-check-schema-version).</span></span>  
  
9. <span data-ttu-id="30d41-161">SSISDB データベースが正常に復元されたことを確認するには、SSISDB カタログに対して、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置したパッケージの実行などの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="30d41-161">To confirm that the SSISDB database has been restored successfully, perform operations against the SSISDB catalog such as running packages that have been deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="30d41-162">詳細については、「 [SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-162">For more information, see [Run a Package on the SSIS Server Using SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md).</span></span>  
  
### <a name="to-move-the-ssis-database"></a><span data-ttu-id="30d41-163">SSIS データベースを移動するには</span><span class="sxs-lookup"><span data-stu-id="30d41-163">To Move the SSIS Database</span></span>  
  
-   <span data-ttu-id="30d41-164">ユーザー データベースの移動の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="30d41-164">Follow the instructions for moving user databases.</span></span> <span data-ttu-id="30d41-165">詳細については、「 [ユーザー データベースの移動](../relational-databases/databases/move-user-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-165">For more information, see [Move User Databases](../relational-databases/databases/move-user-databases.md).</span></span>  
  
     <span data-ttu-id="30d41-166">SSISDB データベースのマスター キーをバックアップしてバックアップ ファイルを保護していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="30d41-166">Ensure that you back up the master key for the SSISDB database and protect the backup file.</span></span> <span data-ttu-id="30d41-167">詳細については、「 [SSIS データベースをバックアップするには](#backup)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d41-167">For more information, see [To Back up the SSIS Database](#backup).</span></span>  
  
     <span data-ttu-id="30d41-168">Integration Services (SSIS) 関連のオブジェクトが、SSISDB カタログが作成されていない新しい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="30d41-168">Ensure that the Integration Services (SSIS) relevant objects are created in the new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog has not yet been created.</span></span>  
  
  
