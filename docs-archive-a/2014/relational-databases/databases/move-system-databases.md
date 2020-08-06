---
title: システム データベースの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- moving system databases
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- tempdb database [SQL Server], moving
- system databases [SQL Server], moving
- scheduled disk maintenace [SQL Server]
- moving databases
- msdb database [SQL Server], moving
- moving database files
- relocating database files
- planned database relocations [SQL Server]
- master database [SQL Server], moving
- model database [SQL Server], moving
- Resource database [SQL Server]
- databases [SQL Server], moving
ms.assetid: 72bb62ee-9602-4f71-be51-c466c1670878
author: stevestein
ms.author: sstein
ms.openlocfilehash: 748d781d6bbefb0dc710427a34ebd71ec7037fdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743329"
---
# <a name="move-system-databases"></a><span data-ttu-id="b5746-102">システム データベースの移動</span><span class="sxs-lookup"><span data-stu-id="b5746-102">Move System Databases</span></span>
  <span data-ttu-id="b5746-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のシステム データベースを移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b5746-103">This topic describes how to move system databases in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b5746-104">システム データベースの移動は、次の状況で便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="b5746-104">Moving system databases may be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="b5746-105">障害復旧。</span><span class="sxs-lookup"><span data-stu-id="b5746-105">Failure recovery.</span></span> <span data-ttu-id="b5746-106">たとえば、ハードウェア障害により、データベースが問題のあるモードになっている場合や、シャットダウンされた場合など。</span><span class="sxs-lookup"><span data-stu-id="b5746-106">For example, the database is in suspect mode or has shut down because of a hardware failure.</span></span>  
  
-   <span data-ttu-id="b5746-107">計画に従った再配置。</span><span class="sxs-lookup"><span data-stu-id="b5746-107">Planned relocation.</span></span>  
  
-   <span data-ttu-id="b5746-108">スケジュールされたディスク メンテナンスとしての再配置。</span><span class="sxs-lookup"><span data-stu-id="b5746-108">Relocation for scheduled disk maintenance.</span></span>  
  
 <span data-ttu-id="b5746-109">次の手順は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の同じインスタンス内でデータベース ファイルを移動する場合に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b5746-109">The following procedures apply to moving database files within the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b5746-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスにデータベースを移動する場合や、別のサーバーに移動する場合は、 [バックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md) 操作か [デタッチとアタッチ](move-a-database-using-detach-and-attach-transact-sql.md) 操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5746-110">To move a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to another server, use the [backup and restore](../backup-restore/back-up-and-restore-of-sql-server-databases.md) or [detach and attach](move-a-database-using-detach-and-attach-transact-sql.md) operations.</span></span>  
  
 <span data-ttu-id="b5746-111">このトピックの手順では、データベース ファイルの論理名が必要です。</span><span class="sxs-lookup"><span data-stu-id="b5746-111">The procedures in this topic require the logical name of the database files.</span></span> <span data-ttu-id="b5746-112">論理名を取得するには、 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) カタログ ビューで name 列に対するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-112">To obtain the name, query the name column in the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b5746-113">システム データベースを移動した後に master データベースを再構築すると、すべてのシステム データベースがそれぞれ既定の場所にインストールされるため、システム データベースを再度移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5746-113">If you move a system database and later rebuild the master database, you must move the system database again because the rebuild operation installs all system databases to their default location.</span></span>  
  
##  <a name="in-this-topic"></a><a name="Intro"></a><span data-ttu-id="b5746-114">**このトピックの**内容</span><span class="sxs-lookup"><span data-stu-id="b5746-114">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="b5746-115">計画された再配置とスケジュールされたディスクメンテナンスの手順</span><span class="sxs-lookup"><span data-stu-id="b5746-115">Planned Relocation and Scheduled Disk Maintenance Procedure</span></span>](#Planned)  
  
-   [<span data-ttu-id="b5746-116">障害復旧手順</span><span class="sxs-lookup"><span data-stu-id="b5746-116">Failure Recovery Procedure</span></span>](#Failure)  
  
-   [<span data-ttu-id="b5746-117">Master データベースの移動</span><span class="sxs-lookup"><span data-stu-id="b5746-117">Moving the master Database</span></span>](#master)  
  
-   [<span data-ttu-id="b5746-118">Resource データベースの移動</span><span class="sxs-lookup"><span data-stu-id="b5746-118">Moving the Resource Database</span></span>](#Resource)  
  
-   [<span data-ttu-id="b5746-119">補足情報: すべてのシステムデータベースを移動した後</span><span class="sxs-lookup"><span data-stu-id="b5746-119">Follow-up: After Moving All System Databases</span></span>](#Follow)  
  
-   [<span data-ttu-id="b5746-120">使用例</span><span class="sxs-lookup"><span data-stu-id="b5746-120">Examples</span></span>](#Examples)  
  
##  <a name="planned-relocation-and-scheduled-disk-maintenance-procedure"></a><a name="Planned"></a> <span data-ttu-id="b5746-121">計画に従った再配置とスケジュールされたディスク メンテナンスの手順</span><span class="sxs-lookup"><span data-stu-id="b5746-121">Planned Relocation and Scheduled Disk Maintenance Procedure</span></span>  
 <span data-ttu-id="b5746-122">計画に従った再配置やスケジュールされたメンテナンス操作の中でシステム データベースのデータ ファイルやログ ファイルを移動するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-122">To move a system database data or log file as part of a planned relocation or scheduled maintenance operation, follow these steps.</span></span> <span data-ttu-id="b5746-123">この手順は、master データベースと Resource データベース以外のすべてのシステム データベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b5746-123">This procedure applies to all system databases except the master and Resource databases.</span></span>  
  
1.  <span data-ttu-id="b5746-124">移動対象のそれぞれのファイルに対して、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-124">For each file to be moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
2.  <span data-ttu-id="b5746-125">メンテナンスを行うため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを停止するか、システムをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="b5746-125">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or shut down the system to perform maintenance.</span></span> <span data-ttu-id="b5746-126">詳細については、「 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5746-126">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="b5746-127">ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-127">Move the file or files to the new location.</span></span>  
  
4.  <span data-ttu-id="b5746-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスまたはサーバーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-128">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the server.</span></span> <span data-ttu-id="b5746-129">詳細については、「 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5746-129">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
5.  <span data-ttu-id="b5746-130">次のクエリを実行して、ファイルが変更されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b5746-130">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
 <span data-ttu-id="b5746-131">msdb データベースが移動され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで [データベース メール](../database-mail/database-mail.md)が構成されている場合は、次の追加の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-131">If the msdb database is moved and the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured for [Database Mail](../database-mail/database-mail.md), complete these additional steps.</span></span>  
  
1.  <span data-ttu-id="b5746-132">次のクエリを実行して、msdb データベースで [!INCLUDE[ssSB](../../../includes/sssb-md.md)] が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b5746-132">Verify that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] is enabled for the msdb database by running the following query.</span></span>  
  
    ```  
    SELECT is_broker_enabled   
    FROM sys.databases  
    WHERE name = N'msdb';  
    ```  
  
     <span data-ttu-id="b5746-133">[!INCLUDE[ssSB](../../../includes/sssb-md.md)] を有効にする方法の詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5746-133">For more information about enabling [!INCLUDE[ssSB](../../../includes/sssb-md.md)], see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
2.  <span data-ttu-id="b5746-134">テスト メールを送信して、データベース メールが動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b5746-134">Verify that Database Mail is working by sending a test mail.</span></span>  
  
##  <a name="failure-recovery-procedure"></a><a name="Failure"></a> <span data-ttu-id="b5746-135">障害復旧の手順</span><span class="sxs-lookup"><span data-stu-id="b5746-135">Failure Recovery Procedure</span></span>  
 <span data-ttu-id="b5746-136">ハードウェア障害が原因でファイルを移動する必要がある場合、次の手順に従って別の場所にファイルを再配置します。</span><span class="sxs-lookup"><span data-stu-id="b5746-136">If a file must be moved because of a hardware failure, follow these steps to relocate the file to a new location.</span></span> <span data-ttu-id="b5746-137">この手順は、master データベースと Resource データベース以外のすべてのシステム データベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b5746-137">This procedure applies to all system databases except the master and Resource databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b5746-138">データベースを起動できないとき、つまり、データベースが問題のあるモードか復旧できない状態にある場合、ファイルを移動できるのは、sysadmin 固定ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="b5746-138">If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.</span></span>  
  
1.  <span data-ttu-id="b5746-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動していたら停止します。</span><span class="sxs-lookup"><span data-stu-id="b5746-139">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if it is started.</span></span>  
  
2.  <span data-ttu-id="b5746-140">コマンド プロンプトで次のいずれかのコマンドを入力し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを master のみを復旧するモードで開始します。</span><span class="sxs-lookup"><span data-stu-id="b5746-140">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in master-only recovery mode by entering one of the following commands at the command prompt.</span></span> <span data-ttu-id="b5746-141">これらのコマンドで指定されるパラメーターでは、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="b5746-141">The parameters specified in these commands are case sensitive.</span></span> <span data-ttu-id="b5746-142">パラメーターが次のように指定されていない場合、コマンドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="b5746-142">The commands fail when the parameters are not specified as shown.</span></span>  
  
    -   <span data-ttu-id="b5746-143">既定 (MSSQLSERVER) のインスタンスの場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-143">For the default (MSSQLSERVER) instance, run the following command:</span></span>  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   <span data-ttu-id="b5746-144">名前付きインスタンスの場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-144">For a named instance, run the following command:</span></span>  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     <span data-ttu-id="b5746-145">詳細については、「 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5746-145">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="b5746-146">移動対象の各ファイルに対して、 **sqlcmd** コマンドか [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-146">For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
     <span data-ttu-id="b5746-147">**sqlcmd** ユーティリティの使用方法については、「 [sqlcmd ユーティリティの使用](../scripting/sqlcmd-use-the-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5746-147">For more information about using the **sqlcmd** utility, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
4.  <span data-ttu-id="b5746-148">**sqlcmd** ユーティリティまたは [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を終了します。</span><span class="sxs-lookup"><span data-stu-id="b5746-148">Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
5.  <span data-ttu-id="b5746-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="b5746-149">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b5746-150">たとえば、 `NET STOP MSSQLSERVER`を実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-150">For example, run `NET STOP MSSQLSERVER`.</span></span>  
  
6.  <span data-ttu-id="b5746-151">ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-151">Move the file or files to the new location.</span></span>  
  
7.  <span data-ttu-id="b5746-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-152">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b5746-153">たとえば、 `NET START MSSQLSERVER`を実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-153">For example, run `NET START MSSQLSERVER`.</span></span>  
  
8.  <span data-ttu-id="b5746-154">次のクエリを実行して、ファイルが変更されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b5746-154">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
##  <a name="moving-the-master-database"></a><a name="master"></a> <span data-ttu-id="b5746-155">master データベースの移動</span><span class="sxs-lookup"><span data-stu-id="b5746-155">Moving the master Database</span></span>  
 <span data-ttu-id="b5746-156">master データベースを移動するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-156">To move the master database, follow these steps.</span></span>  
  
1.  <span data-ttu-id="b5746-157">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** 、 **[構成ツール]** の順にポイントし、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5746-157">From the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="b5746-158">**[SQL Server のサービス]** ノードで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス (たとえば、 **[SQL Server (MSSQLSERVER)]** ) を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5746-158">In the **SQL Server Services** node, right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (for example, **SQL Server (MSSQLSERVER)**) and choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="b5746-159">\*\*[SQL Server ( \*\*\*instance_name \***) のプロパティ]** ダイアログ ボックスで、 **[起動時のパラメーター]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5746-159">In the **SQL Server (***instance_name***) Properties** dialog box, click the **Startup Parameters** tab.</span></span>  
  
4.  <span data-ttu-id="b5746-160">**[既存のパラメーター]** ボックスで -d パラメーターを選択して、マスター データ ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-160">In the **Existing parameters** box, select the -d parameter to move the master data file.</span></span> <span data-ttu-id="b5746-161">**[更新]** をクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="b5746-161">Click **Update** to save the change.</span></span>  
  
     <span data-ttu-id="b5746-162">**[起動時のパラメーターの指定]** ボックスで、パラメーターを master データベースの新しいパスに変更します。</span><span class="sxs-lookup"><span data-stu-id="b5746-162">In the **Specify a startup parameter** box, change the parameter to the new path of the master database.</span></span>  
  
5.  <span data-ttu-id="b5746-163">**[既存のパラメーター]** ボックスで -l パラメーターを選択して、マスター ログ ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-163">In the **Existing parameters** box, select the -l parameter to move the master log file.</span></span> <span data-ttu-id="b5746-164">**[更新]** をクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="b5746-164">Click **Update** to save the change.</span></span>  
  
     <span data-ttu-id="b5746-165">**[起動時のパラメーターの指定]** ボックスで、パラメーターを master データベースの新しいパスに変更します。</span><span class="sxs-lookup"><span data-stu-id="b5746-165">In the **Specify a startup parameter** box, change the parameter to the new path of the master database.</span></span>  
  
     <span data-ttu-id="b5746-166">`-d` パラメーターの後にデータ ファイルのパラメーター値を指定し、 `-l` パラメーターの後にログ ファイルのパラメーター値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5746-166">The parameter value for the data file must follow the `-d` parameter and the value for the log file must follow the `-l` parameter.</span></span> <span data-ttu-id="b5746-167">次の例は、マスター データ ファイルの既定の場所のパラメーター値を示します。</span><span class="sxs-lookup"><span data-stu-id="b5746-167">The following example shows the parameter values for the default location of the master data file.</span></span>  
  
     `-dC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\master.mdf`  
  
     `-lC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\mastlog.ldf`  
  
     <span data-ttu-id="b5746-168">マスター データ ファイルの計画に従った再配置場所が `E:\SQLData`の場合、パラメーター値を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="b5746-168">If the planned relocation for the master data file is `E:\SQLData`, the parameter values would be changed as follows:</span></span>  
  
     `-dE:\SQLData\master.mdf`  
  
     `-lE:\SQLData\mastlog.ldf`  
  
6.  <span data-ttu-id="b5746-169">インスタンス名を右クリックして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [停止] **をクリックし、** のインスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="b5746-169">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by right-clicking the instance name and choosing **Stop**.</span></span>  
  
7.  <span data-ttu-id="b5746-170">master.mdf ファイルおよび mastlog.ldf ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-170">Move the master.mdf and mastlog.ldf files to the new location.</span></span>  
  
8.  <span data-ttu-id="b5746-171">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-171">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
9. <span data-ttu-id="b5746-172">master データベースのファイルが変更されたことを確認するため、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5746-172">Verify the file change for the master database by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID('master');  
    GO  
    ```  
  
##  <a name="moving-the-resource-database"></a><a name="Resource"></a> <span data-ttu-id="b5746-173">Resource データベースの移動</span><span class="sxs-lookup"><span data-stu-id="b5746-173">Moving the Resource Database</span></span>  
 <span data-ttu-id="b5746-174">Resource データベースの既定の場所は、\<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\ です。</span><span class="sxs-lookup"><span data-stu-id="b5746-174">The location of the Resource database is \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\.</span></span> <span data-ttu-id="b5746-175">データベースを移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="b5746-175">The database cannot be moved.</span></span>  
  
##  <a name="follow-up-after-moving-all-system-databases"></a><a name="Follow"></a> <span data-ttu-id="b5746-176">補足情報:すべてのシステム データベースを移動した後</span><span class="sxs-lookup"><span data-stu-id="b5746-176">Follow-up: After Moving All System Databases</span></span>  
 <span data-ttu-id="b5746-177">すべてのシステム データベースを、新しいドライブやボリューム、または別のドライブ文字を使用した別のサーバーに移動した場合は、次の更新を行います。</span><span class="sxs-lookup"><span data-stu-id="b5746-177">If you have moved all of the system databases to a new drive or volume or to another server with a different drive letter, make the following updates.</span></span>  
  
-   <span data-ttu-id="b5746-178">SQL Server エージェントのログ パスを変更します。</span><span class="sxs-lookup"><span data-stu-id="b5746-178">Change the SQL Server Agent log path.</span></span> <span data-ttu-id="b5746-179">このパスを更新しないと、SQL Server エージェントは起動しません。</span><span class="sxs-lookup"><span data-stu-id="b5746-179">If you do not update this path, SQL Server Agent will fail to start.</span></span>  
  
-   <span data-ttu-id="b5746-180">データベースの既定の場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="b5746-180">Change the database default location.</span></span> <span data-ttu-id="b5746-181">既定の場所として指定したドライブ文字やパスが存在しない場合、新しいデータベースが作成されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b5746-181">Creating a new database may fail if the drive letter and path specified as the default location do not exist.</span></span>  
  
#### <a name="change-the-sql-server-agent-log-path"></a><span data-ttu-id="b5746-182">SQL Server エージェントのログ パスの変更</span><span class="sxs-lookup"><span data-stu-id="b5746-182">Change the SQL Server Agent Log Path</span></span>  
  
1.  <span data-ttu-id="b5746-183">SQL Server Management Studio のオブジェクト エクスプローラーで、 **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b5746-183">From SQL Server Management Studio, in Object Explorer, expand **SQL Server Agent**.</span></span>  
  
2.  <span data-ttu-id="b5746-184">**[エラー ログ]** を右クリックし、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5746-184">Right-click **Error Logs** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="b5746-185">**SQL Server エージェント エラー ログの構成］** ダイアログ ボックスで、SQLAGENT.OUT ファイルの新しい場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5746-185">In the **Configure SQL Server Agent Error Logs** dialog box, specify the new location of the SQLAGENT.OUT file.</span></span> <span data-ttu-id="b5746-186">既定の場所は、C:\Program Server\MSSQL12. SQL <instance_name> \MSSQL\Log \\ です。</span><span class="sxs-lookup"><span data-stu-id="b5746-186">The default location is C:\Program Files\Microsoft SQL Server\MSSQL12.<instance_name>\MSSQL\Log\\.</span></span>  
  
#### <a name="change-the-database-default-location"></a><span data-ttu-id="b5746-187">データベースの既定の場所の変更</span><span class="sxs-lookup"><span data-stu-id="b5746-187">Change the database default location</span></span>  
  
1.  <span data-ttu-id="b5746-188">SQL Server Management Studio のオブジェクト エクスプローラーで、SQL Server のサーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5746-188">From SQL Server Management Studio, in Object Explorer, right-click the SQL Server server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b5746-189">**[サーバーのプロパティ]** ダイアログ ボックスで、 **[データベースの設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5746-189">In the **Server Properties** dialog box, select **Database Settings**.</span></span>  
  
3.  <span data-ttu-id="b5746-190">**[データベースの既定の場所]** で、データ ファイルとログ ファイルの両方の新しい場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="b5746-190">Under **Database Default Locations**, browse to the new location for both the data and log files.</span></span>  
  
4.  <span data-ttu-id="b5746-191">変更を完了するため、SQL Server サービスをいったん停止してから開始します。</span><span class="sxs-lookup"><span data-stu-id="b5746-191">Stop and start the SQL Server service to complete the change.</span></span>  
  
##  <a name="examples"></a><a name="Examples"></a> <span data-ttu-id="b5746-192">使用例</span><span class="sxs-lookup"><span data-stu-id="b5746-192">Examples</span></span>  
  
### <a name="a-moving-the-tempdb-database"></a><span data-ttu-id="b5746-193">A.</span><span class="sxs-lookup"><span data-stu-id="b5746-193">A.</span></span> <span data-ttu-id="b5746-194">tempdb データベースを移動する</span><span class="sxs-lookup"><span data-stu-id="b5746-194">Moving the tempdb database</span></span>  
 <span data-ttu-id="b5746-195">次の例では、計画に従った再配置の一環として、 `tempdb` データ ファイルとログ ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-195">The following example moves the `tempdb` data and log files to a new location as part of a planned relocation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5746-196">tempdb は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが開始されるたびに再作成されるので、データ ファイルとログ ファイルを物理的に移動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b5746-196">Because tempdb is re-created each time the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started, you do not have to physically move the data and log files.</span></span> <span data-ttu-id="b5746-197">手順 3. でサービスを再起動すると、新しい場所にファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b5746-197">The files are created in the new location when the service is restarted in step 3.</span></span> <span data-ttu-id="b5746-198">サービスを再起動するまでは、tempdb は既存の場所のデータ ファイルとログ ファイルを使用し続けます。</span><span class="sxs-lookup"><span data-stu-id="b5746-198">Until the service is restarted, tempdb continues to use the data and log files in existing location.</span></span>  
  
1.  <span data-ttu-id="b5746-199">`tempdb` データベースの論理ファイル名と、ディスク上での現在の場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="b5746-199">Determine the logical file names of the `tempdb` database and their current location on the disk.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    GO  
    ```  
  
2.  <span data-ttu-id="b5746-200">`ALTER DATABASE`を使用して、各ファイルの場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="b5746-200">Change the location of each file by using `ALTER DATABASE`.</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'F:\SQLLog\templog.ldf');  
    GO  
    ```  
  
3.  <span data-ttu-id="b5746-201">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスをいったん停止してから再起動します。</span><span class="sxs-lookup"><span data-stu-id="b5746-201">Stop and restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="b5746-202">ファイルの変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="b5746-202">Verify the file change.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    ```  
  
5.  <span data-ttu-id="b5746-203">`tempdb.mdf` ファイルおよび `templog.ldf` ファイルを元の場所から削除します。</span><span class="sxs-lookup"><span data-stu-id="b5746-203">Delete the `tempdb.mdf` and `templog.ldf` files from the original location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5746-204">参照</span><span class="sxs-lookup"><span data-stu-id="b5746-204">See Also</span></span>  
 <span data-ttu-id="b5746-205">[Resource データベース](resource-database.md) </span><span class="sxs-lookup"><span data-stu-id="b5746-205">[Resource Database](resource-database.md) </span></span>  
 <span data-ttu-id="b5746-206">[tempdb データベース](tempdb-database.md) </span><span class="sxs-lookup"><span data-stu-id="b5746-206">[tempdb Database](tempdb-database.md) </span></span>  
 <span data-ttu-id="b5746-207">[master データベース](master-database.md) </span><span class="sxs-lookup"><span data-stu-id="b5746-207">[master Database](master-database.md) </span></span>  
 <span data-ttu-id="b5746-208">[msdb データベース](msdb-database.md) </span><span class="sxs-lookup"><span data-stu-id="b5746-208">[msdb Database](msdb-database.md) </span></span>  
 <span data-ttu-id="b5746-209">[model データベース](model-database.md) </span><span class="sxs-lookup"><span data-stu-id="b5746-209">[model Database](model-database.md) </span></span>  
 <span data-ttu-id="b5746-210">[ユーザー データベースの移動](move-user-databases.md) </span><span class="sxs-lookup"><span data-stu-id="b5746-210">[Move User Databases](move-user-databases.md) </span></span>  
 <span data-ttu-id="b5746-211">[データベース ファイルの移動](move-database-files.md) </span><span class="sxs-lookup"><span data-stu-id="b5746-211">[Move Database Files](move-database-files.md) </span></span>  
 <span data-ttu-id="b5746-212">[データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="b5746-212">[Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) </span></span>  
 <span data-ttu-id="b5746-213">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5746-213">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="b5746-214">システム データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="b5746-214">Rebuild System Databases</span></span>](system-databases.md)  
  
  
