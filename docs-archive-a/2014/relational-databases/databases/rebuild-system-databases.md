---
title: システム データベースの再構築 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], rebuilding
- REBUILDDATABASE parameter
- rebuilding databases, master
- system databases [SQL Server], rebuilding
ms.assetid: af457ecd-523e-4809-9652-bdf2e81bd876
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f695589fa0fc1b86d4433d36afa1bc6357aabd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640059"
---
# <a name="rebuild-system-databases"></a><span data-ttu-id="a4c28-102">システム データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="a4c28-102">Rebuild System Databases</span></span>
  <span data-ttu-id="a4c28-103">[master](master-database.md)、 [model](model-database.md)、 [msdb](msdb-database.md)、または [resource](resource-database.md) の各システム データベースの損傷による問題を解決するか、既定のサーバー レベルの照合順序を変更するには、システム データベースを再構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-103">System databases must be rebuilt to fix corruption problems in the [master](master-database.md), [model](model-database.md), [msdb](msdb-database.md), or [resource](resource-database.md) system databases or to modify the default server-level collation.</span></span> <span data-ttu-id="a4c28-104">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でシステム データベースを再構築する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-104">This topic provides step-by-step instructions to rebuild system databases in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="a4c28-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a4c28-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a4c28-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a4c28-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a4c28-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a4c28-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a4c28-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="a4c28-108">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="a4c28-109">**手順:**</span><span class="sxs-lookup"><span data-stu-id="a4c28-109">**Procedures:**</span></span>  
  
     [<span data-ttu-id="a4c28-110">システム データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="a4c28-110">Rebuild System Databases</span></span>](#RebuildProcedure)  
  
     [<span data-ttu-id="a4c28-111">resource データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="a4c28-111">Rebuild the resource Database</span></span>](#Resource)  
  
     [<span data-ttu-id="a4c28-112">新しい msdb データベースの作成</span><span class="sxs-lookup"><span data-stu-id="a4c28-112">Create a New msdb Database</span></span>](#CreateMSDB)  
  
-   <span data-ttu-id="a4c28-113">**補足情報:**</span><span class="sxs-lookup"><span data-stu-id="a4c28-113">**Follow Up:**</span></span>  
  
     [<span data-ttu-id="a4c28-114">再構築エラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a4c28-114">Troubleshoot Rebuild Errors</span></span>](#Troubleshoot)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a4c28-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="a4c28-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a4c28-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a4c28-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a4c28-117">master、model、msdb、および tempdb の各システム データベースを再構築する場合は、元の場所からデータベースを削除して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-117">When the master, model, msdb, and tempdb system databases are rebuilt, the databases are dropped and re-created in their original location.</span></span> <span data-ttu-id="a4c28-118">再構築ステートメントに新しい照合順序を指定する場合は、その照合順序の設定でシステム データベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-118">If a new collation is specified in the rebuild statement, the system databases are created using that collation setting.</span></span> <span data-ttu-id="a4c28-119">これらのデータベースに対するユーザーの変更はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-119">Any user modifications to these databases are lost.</span></span> <span data-ttu-id="a4c28-120">たとえば、master データベースのユーザー定義オブジェクト、msdb にスケジュールされたジョブ、または model データベースの既定のデータベース設定に対する変更が対象になります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-120">For example, you may have user-defined objects in the master database, scheduled jobs in msdb, or changes to the default database settings in the model database.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a4c28-121">前提条件</span><span class="sxs-lookup"><span data-stu-id="a4c28-121">Prerequisites</span></span>  
 <span data-ttu-id="a4c28-122">システム データベースを再構築する前に次の作業を行い、システム データベースを現在の設定に復元できるようにしておいてください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-122">Perform the following tasks before you rebuild the system databases to ensure that you can restore the system databases to their current settings.</span></span>  
  
1.  <span data-ttu-id="a4c28-123">サーバー全体のすべての構成値を記録します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-123">Record all server-wide configuration values.</span></span>  
  
    ```  
    SELECT * FROM sys.configurations;  
    ```  
  
2.  <span data-ttu-id="a4c28-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および現在の照合順序のインスタンスに適用されているすべてのサービス パックと修正プログラムを記録します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-124">Record all service packs and hotfixes applied to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the current collation.</span></span> <span data-ttu-id="a4c28-125">システム データベースの再構築後にこれらの更新を再適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-125">You must reapply these updates after rebuilding the system databases.</span></span>  
  
    ```  
    SELECT  
    SERVERPROPERTY('ProductVersion ') AS ProductVersion,  
    SERVERPROPERTY('ProductLevel') AS ProductLevel,  
    SERVERPROPERTY('ResourceVersion') AS ResourceVersion,  
    SERVERPROPERTY('ResourceLastUpdateDateTime') AS ResourceLastUpdateDateTime,  
    SERVERPROPERTY('Collation') AS Collation;  
    ```  
  
3.  <span data-ttu-id="a4c28-126">システム データベースのすべてのデータとログ ファイルの現在の場所を記録します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-126">Record the current location of all data and log files for the system databases.</span></span> <span data-ttu-id="a4c28-127">システム データベースを再構築すると、すべてのシステム データベースがそれぞれ元の場所にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-127">Rebuilding the system databases installs all system databases to their original location.</span></span> <span data-ttu-id="a4c28-128">システム データベースのデータまたはログ ファイルを別の場所に移動していた場合は、そのファイルを再度移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-128">If you have moved system database data or log files to a different location, you must move the files again.</span></span>  
  
    ```  
    SELECT name, physical_name AS current_file_location  
    FROM sys.master_files  
    WHERE database_id IN (DB_ID('master'), DB_ID('model'), DB_ID('msdb'), DB_ID('tempdb'));  
    ```  
  
4.  <span data-ttu-id="a4c28-129">master、model、および msdb の各データベースの現在のバックアップを探します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-129">Locate the current backup of the master, model, and msdb databases.</span></span>  
  
5.  <span data-ttu-id="a4c28-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがレプリケーション ディストリビューターとして構成されている場合は、ディストリビューション データベースの現在のバックアップを探します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-130">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured as a replication Distributor, locate the current backup of the distribution database.</span></span>  
  
6.  <span data-ttu-id="a4c28-131">システム データベースの再構築に必要な権限を持っていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-131">Ensure you have appropriate permissions to rebuild the system databases.</span></span> <span data-ttu-id="a4c28-132">この操作を実行するには、`sysadmin` 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-132">To perform this operation, you must be a member of the `sysadmin` fixed server role.</span></span> <span data-ttu-id="a4c28-133">詳細については、「 [サーバー レベルのロール](../security/authentication-access/server-level-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-133">For more information, see [Server-Level Roles](../security/authentication-access/server-level-roles.md).</span></span>  
  
7.  <span data-ttu-id="a4c28-134">master、model、msdb のデータおよびログのテンプレート ファイルのコピーがローカル サーバーに存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-134">Verify that copies of the master, model, msdb data and log template files exist on the local server.</span></span> <span data-ttu-id="a4c28-135">テンプレート ファイルの既定の場所は、C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates です。</span><span class="sxs-lookup"><span data-stu-id="a4c28-135">The default location for the template files is C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates.</span></span> <span data-ttu-id="a4c28-136">これらのファイルは再構築プロセスで使用され、セットアップを成功させるにはこれらのファイルが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-136">These files are used during the rebuild process and must be present for Setup to succeed.</span></span> <span data-ttu-id="a4c28-137">これらのファイルがない場合は、セットアップの修復機能を実行するか、インストール メディアからファイルを手動でコピーします。</span><span class="sxs-lookup"><span data-stu-id="a4c28-137">If they are missing, run the Repair feature of Setup, or manually copy the files from your installation media.</span></span> <span data-ttu-id="a4c28-138">インストール メディアのファイルを探すには、適切なプラットフォーム ディレクトリ (x86 または x64) に移動し、次に setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates に移動します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-138">To locate the files on the installation media, navigate to the appropriate platform directory (x86 or x64) and then navigate to setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates.</span></span>  
  
##  <a name="rebuild-system-databases"></a><a name="RebuildProcedure"></a> <span data-ttu-id="a4c28-139">システム データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="a4c28-139">Rebuild System Databases</span></span>  
 <span data-ttu-id="a4c28-140">次の手順では、master、model、msdb、および tempdb の各システム データベースを再構築します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-140">The following procedure rebuilds the master, model, msdb, and tempdb system databases.</span></span> <span data-ttu-id="a4c28-141">再構築するシステム データベースを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4c28-141">You cannot specify the system databases to be rebuilt.</span></span> <span data-ttu-id="a4c28-142">クラスター化されたインスタンスの場合、この手順はアクティブ ノードで実行する必要があります。また、手順を実行する前に、対応するクラスター アプリケーション グループ内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースをオフラインにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-142">For clustered instances, this procedure must be performed on the active node and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource in the corresponding cluster application group must be taken offline before performing the procedure.</span></span>  
  
 <span data-ttu-id="a4c28-143">この手順では resource データベースが再構築されません。</span><span class="sxs-lookup"><span data-stu-id="a4c28-143">This procedure does not rebuild the resource database.</span></span> <span data-ttu-id="a4c28-144">このトピックで後述する「resource データベースの再構築手順」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-144">See the section, "Rebuild the resource Database Procedure" later in this topic.</span></span>  
  
#### <a name="to-rebuild-system-databases-for-an-instance-of-sql-server"></a><span data-ttu-id="a4c28-145">SQL Server のインスタンスのシステム データベースを再構築するには</span><span class="sxs-lookup"><span data-stu-id="a4c28-145">To rebuild system databases for an instance of SQL Server:</span></span>  
  
1.  <span data-ttu-id="a4c28-146">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール メディアをディスク ドライブに挿入するか、コマンド プロンプトから、ディレクトリをローカル サーバーの setup.exe ファイルがある場所に変更します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-146">Insert the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media into the disk drive, or, from a command prompt, change directories to the location of the setup.exe file on the local server.</span></span> <span data-ttu-id="a4c28-147">サーバーの既定の場所は C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release です。</span><span class="sxs-lookup"><span data-stu-id="a4c28-147">The default location on the server is C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release.</span></span>  
  
2.  <span data-ttu-id="a4c28-148">コマンド プロンプト ウィンドウから、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-148">From a command prompt window, enter the following command.</span></span> <span data-ttu-id="a4c28-149">角かっこは省略可能なパラメーターであることを示します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-149">Square brackets are used to indicate optional parameters.</span></span> <span data-ttu-id="a4c28-150">角かっこは入力しません。</span><span class="sxs-lookup"><span data-stu-id="a4c28-150">Do not enter the brackets.</span></span> <span data-ttu-id="a4c28-151">ユーザー アカウント制御 (UAC) が有効な Windows オペレーション システムを使用する場合は、セットアップの実行に高度な特権が必要になります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-151">When using a Windows operating system that has User Account Control (UAC) enabled, running Setup requires elevated privileges.</span></span> <span data-ttu-id="a4c28-152">管理者としてコマンド プロンプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-152">The command prompt must be run as Administrator.</span></span>  
  
     `Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName /SQLSYSADMINACCOUNTS=accounts [ /SAPWD= StrongPassword ] [ /SQLCOLLATION=CollationName]`  
  
    |<span data-ttu-id="a4c28-153">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="a4c28-153">Parameter name</span></span>|<span data-ttu-id="a4c28-154">説明</span><span class="sxs-lookup"><span data-stu-id="a4c28-154">Description</span></span>|  
    |--------------------|-----------------|  
    |<span data-ttu-id="a4c28-155">/QUIET または /Q</span><span class="sxs-lookup"><span data-stu-id="a4c28-155">/QUIET or /Q</span></span>|<span data-ttu-id="a4c28-156">セットアップがユーザー インターフェイスなしで実行されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-156">Specifies that Setup run without any user interface.</span></span>|  
    |<span data-ttu-id="a4c28-157">/ACTION=REBUILDDATABASE</span><span class="sxs-lookup"><span data-stu-id="a4c28-157">/ACTION=REBUILDDATABASE</span></span>|<span data-ttu-id="a4c28-158">セットアップでシステム データベースを再作成することを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-158">Specifies that Setup re-create the system databases.</span></span>|  
    |<span data-ttu-id="a4c28-159">/INSTANCENAME=*InstanceName*</span><span class="sxs-lookup"><span data-stu-id="a4c28-159">/INSTANCENAME=*InstanceName*</span></span>|<span data-ttu-id="a4c28-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-160">Is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a4c28-161">既定のインスタンスには「MSSQLSERVER」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-161">For the default instance, enter MSSQLSERVER.</span></span>|  
    |<span data-ttu-id="a4c28-162">/SQLSYSADMINACCOUNTS=*accounts*</span><span class="sxs-lookup"><span data-stu-id="a4c28-162">/SQLSYSADMINACCOUNTS=*accounts*</span></span>|<span data-ttu-id="a4c28-163">`sysadmin` 固定サーバー ロールに追加する Windows グループまたは個々のアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-163">Specifies the Windows groups or individual accounts to add to the `sysadmin` fixed server role.</span></span> <span data-ttu-id="a4c28-164">複数のアカウントを指定する場合、各アカウントを空白で区切ります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-164">When specifying more than one account, separate the accounts with a blank space.</span></span> <span data-ttu-id="a4c28-165">たとえば、「 **BUILTIN\Administrators MyDomain\MyUser**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-165">For example, enter **BUILTIN\Administrators MyDomain\MyUser**.</span></span> <span data-ttu-id="a4c28-166">アカウント名に空白を含むアカウントを指定する場合は、アカウントを二重引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-166">When you are specifying an account that contains a blank space within the account name, enclose the account in double quotation marks.</span></span> <span data-ttu-id="a4c28-167">たとえば、「`NT AUTHORITY\SYSTEM`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-167">For example, enter `NT AUTHORITY\SYSTEM`.</span></span>|  
    |<span data-ttu-id="a4c28-168">[ /SAPWD=*StrongPassword* ]</span><span class="sxs-lookup"><span data-stu-id="a4c28-168">[ /SAPWD=*StrongPassword* ]</span></span>|<span data-ttu-id="a4c28-169">アカウントのパスワードを指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` ます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-169">Specifies the password for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` account.</span></span> <span data-ttu-id="a4c28-170">このパラメーターは、インスタンスが混合モード認証 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および Windows 認証) を使用する場合に必要になります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-170">This parameter is required if the instance uses Mixed Authentication ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication) mode.</span></span><br /><br /> <span data-ttu-id="a4c28-171">\*\* \* \* セキュリティ \* \* \*\*に関するメモアカウントは、よく知られたアカウントであり、悪意のある `sa` ユーザーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 対象となることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-171">**\*\* Security Note \*\*** The `sa` account is a well-known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account and it is often targeted by malicious users.</span></span> <span data-ttu-id="a4c28-172">`sa` ログインには、複雑なパスワードを使用することが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="a4c28-172">It is very important that you use a strong password for the `sa` login.</span></span><br /><br /> <span data-ttu-id="a4c28-173">Windows 認証モードにはこのパラメーターを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-173">Do not specify this parameter for Windows Authentication mode.</span></span>|  
    |<span data-ttu-id="a4c28-174">[ /SQLCOLLATION=*CollationName* ]</span><span class="sxs-lookup"><span data-stu-id="a4c28-174">[ /SQLCOLLATION=*CollationName* ]</span></span>|<span data-ttu-id="a4c28-175">新しいサーバー レベルの照合順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-175">Specifies a new server-level collation.</span></span> <span data-ttu-id="a4c28-176">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a4c28-176">This parameter is optional.</span></span> <span data-ttu-id="a4c28-177">これを指定しない場合は、サーバーの現在の照合順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-177">When not specified, the current collation of the server is used.</span></span><br /><br /> <span data-ttu-id="a4c28-178">**\*\* 重要 \*\*** サーバー レベルの照合順序を変更しても、既存のユーザー データベースの照合順序は変更されません。</span><span class="sxs-lookup"><span data-stu-id="a4c28-178">**\*\* Important \*\*** Changing the server-level collation does not change the collation of existing user databases.</span></span> <span data-ttu-id="a4c28-179">新しく作成されたすべてのユーザー データベースには、既定で新しい照合順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-179">All newly created user databases will use the new collation by default.</span></span><br /><br /> <span data-ttu-id="a4c28-180">詳細については、「 [サーバーの照合順序の設定または変更](../collations/set-or-change-the-server-collation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-180">For more information, see [Set or Change the Server Collation](../collations/set-or-change-the-server-collation.md).</span></span>|  
  
3.  <span data-ttu-id="a4c28-181">セットアップによりシステム データベースの再構築が完了すると、メッセージが表示されることなく、コマンド プロンプトに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-181">When Setup has completed rebuilding the system databases, it returns to the command prompt with no messages.</span></span> <span data-ttu-id="a4c28-182">Summary.txt ログ ファイルを調査し、プロセスが正常に完了したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-182">Examine the Summary.txt log file to verify that the process completed successfully.</span></span> <span data-ttu-id="a4c28-183">このファイルは C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs にあります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-183">This file is located at C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.</span></span>  
  
## <a name="post-rebuild-tasks"></a><span data-ttu-id="a4c28-184">再構築後の作業</span><span class="sxs-lookup"><span data-stu-id="a4c28-184">Post-Rebuild Tasks</span></span>  
 <span data-ttu-id="a4c28-185">データベースを再構築した後は、次の追加作業の実行が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-185">After rebuilding the database you may need to perform the following additional tasks:</span></span>  
  
-   <span data-ttu-id="a4c28-186">master、model、および msdb の各データベースを最新の完全バックアップの状態に復元します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-186">Restore your most recent full backups of the master, model, and msdb databases.</span></span> <span data-ttu-id="a4c28-187">詳細については、「[システム データベースのバックアップと復元 &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-187">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a4c28-188">サーバー照合順序を変更した場合は、システム データベースを復元しないでください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-188">If you have changed the server collation, do not restore the system databases.</span></span> <span data-ttu-id="a4c28-189">復元すると、新しい照合順序が元の照合順序の設定に置き換わります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-189">Doing so will replace the new collation with the previous collation setting.</span></span>  
  
     <span data-ttu-id="a4c28-190">バックアップが存在しないか、復元されたバックアップが最新のものでない場合は、存在しないエントリを再作成します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-190">If a backup is not available or if the restored backup is not current, re-create any missing entries.</span></span> <span data-ttu-id="a4c28-191">たとえば、ユーザー データベース、バックアップ デバイス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン、エンドポイントなどの存在しないエントリをすべて再作成します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-191">For example, re-create all missing entries for your user databases, backup devices, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins, end points, and so on.</span></span> <span data-ttu-id="a4c28-192">エントリを再作成する場合、エントリの作成時と同じスクリプトを実行してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-192">The best way to re-create entries is to run the original scripts that created them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a4c28-193">不正ユーザーによる変更を防ぐために、スクリプトを保護しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a4c28-193">We recommend that you secure your scripts to prevent their being altered by unauthorized by individuals.</span></span>  
  
-   <span data-ttu-id="a4c28-194">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがレプリケーション ディストリビューターとして構成されている場合は、ディストリビューション データベースを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-194">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured as a replication Distributor, you must restore the distribution database.</span></span> <span data-ttu-id="a4c28-195">詳細については、「 [レプリケートされたデータベースのバックアップと復元](../replication/administration/back-up-and-restore-replicated-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-195">For more information, see [Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
-   <span data-ttu-id="a4c28-196">システム データベースを記録した以前の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-196">Move the system databases to the locations you recorded previously.</span></span> <span data-ttu-id="a4c28-197">詳細については、「 [システム データベースの移動](system-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-197">For more information, see [Move System Databases](system-databases.md).</span></span>  
  
-   <span data-ttu-id="a4c28-198">サーバー全体の構成値が記録した以前の値と一致することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-198">Verify the server-wide configuration values match the values you recorded previously.</span></span>  
  
##  <a name="rebuild-the-resource-database"></a><a name="Resource"></a> <span data-ttu-id="a4c28-199">resource データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="a4c28-199">Rebuild the resource Database</span></span>  
 <span data-ttu-id="a4c28-200">次の手順では、resource システム データベースを再構築します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-200">The following procedure rebuilds the resource system database.</span></span> <span data-ttu-id="a4c28-201">resource システム データベースを再構築する場合は、サービス パックと修正プログラムがすべて失われるため、再適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-201">When you rebuild the resource database, all service packs and hot fixes are lost, and therefore must be reapplied.</span></span>  
  
#### <a name="to-rebuild-the-resource-system-database"></a><span data-ttu-id="a4c28-202">resource システム データベースを再構築するには</span><span class="sxs-lookup"><span data-stu-id="a4c28-202">To rebuild the resource system database:</span></span>  
  
1.  <span data-ttu-id="a4c28-203">配布メディアから、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ プログラム (setup.exe) を起動します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-203">Launch the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup program (setup.exe) from the distribution media.</span></span>  
  
2.  <span data-ttu-id="a4c28-204">左側のナビゲーション領域の **[メンテナンス]** をクリックし、 **[修復]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4c28-204">In the left navigation area, click **Maintenance**, and then click **Repair**.</span></span>  
  
3.  <span data-ttu-id="a4c28-205">セットアップ サポート ルールおよびセットアップ サポート ファイルのルーチンが実行されて、システムに必須コンポーネントがインストールされていること、およびコンピューターがセットアップの検証ルールに合格していることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-205">Setup support rule and file routines run to ensure that your system has prerequisites installed and that the computer passes Setup validation rules.</span></span> <span data-ttu-id="a4c28-206">続行するには、 **[OK]** または **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4c28-206">Click **OK** or **Install** to continue.</span></span>  
  
4.  <span data-ttu-id="a4c28-207">[インスタンスの選択] ページで、修復するインスタンスを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4c28-207">On the Select Instance page, select the instance to repair, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="a4c28-208">修復ルールが実行され、操作が検証されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-208">The repair rules will run to validate the operation.</span></span> <span data-ttu-id="a4c28-209">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4c28-209">To continue, click **Next**.</span></span>  
  
6.  <span data-ttu-id="a4c28-210">**[修復の準備完了]** ページで **[修復]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4c28-210">From the **Ready to Repair** page, click **Repair**.</span></span> <span data-ttu-id="a4c28-211">[完了] ページでは、操作が完了したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-211">The Complete page indicates that the operation is finished.</span></span>  
  
##  <a name="create-a-new-msdb-database"></a><a name="CreateMSDB"></a> <span data-ttu-id="a4c28-212">新しい msdb データベースの作成</span><span class="sxs-lookup"><span data-stu-id="a4c28-212">Create a New msdb Database</span></span>  
 <span data-ttu-id="a4c28-213">`msdb`データベースが破損していて、データベースのバックアップがない場合は、 `msdb` `msdb` **instmsdb**スクリプトを使用して新しいを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-213">If the `msdb` database is damaged and you do not have a backup of the `msdb` database, you can create a new `msdb` by using the **instmsdb** script.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a4c28-214">`msdb` **Instmsdb**スクリプトを使用してデータベースを再構築すると、 `msdb` ジョブ、警告、オペレーター、メンテナンスプラン、バックアップ履歴、ポリシーベースの管理設定、データベースメール、パフォーマンスデータウェアハウスなど、に格納されているすべての情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-214">Rebuilding the `msdb` database using the **instmsdb** script will eliminate all the information stored in `msdb` such as jobs, alert, operators, maintenance plans, backup history, Policy-Based Management settings, Database Mail, Performance Data Warehouse, etc.</span></span>  
  
1.  <span data-ttu-id="a4c28-215">[!INCLUDE[ssDE](../../includes/ssde-md.md)]エージェント、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、および [!INCLUDE[ssRS](../../includes/ssrs.md)]と、 [!INCLUDE[ssIS](../../includes/ssis-md.md)]をデータ ストアとして使用しているすべてのアプリケーションを含め、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続しているすべてのサービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-215">Stop all services connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, [!INCLUDE[ssRS](../../includes/ssrs.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)], and all applications using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as data store.</span></span>  
  
2.  <span data-ttu-id="a4c28-216">というコマンドを使用して、コマンド ラインから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を開始します。 `NET START MSSQLSERVER /T3608`</span><span class="sxs-lookup"><span data-stu-id="a4c28-216">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the command line using the command: `NET START MSSQLSERVER /T3608`</span></span>  
  
     <span data-ttu-id="a4c28-217">詳細については、「 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-217">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="a4c28-218">別のコマンドラインウィンドウで、 `msdb` 次のコマンドを実行してデータベースをデタッチし *\<servername>* ます。をのインスタンスに置き換え [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。`SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`</span><span class="sxs-lookup"><span data-stu-id="a4c28-218">In another command line window, detach the `msdb` database by executing the following command, replacing *\<servername>* with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: `SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`</span></span>  
  
4.  <span data-ttu-id="a4c28-219">Windows エクスプローラーを使用して、データベースファイルの名前を変更 `msdb` します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-219">Using the Windows Explorer, rename the `msdb` database files.</span></span> <span data-ttu-id="a4c28-220">これらのファイルは、既定で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの DATA サブフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="a4c28-220">By default these are in the DATA sub-folder for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="a4c28-221">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスを通常の方法で停止および再起動します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-221">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, stop and restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service normally.</span></span>  
  
6.  <span data-ttu-id="a4c28-222">コマンド ライン ウィンドウで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、コマンド `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`</span><span class="sxs-lookup"><span data-stu-id="a4c28-222">In a command line window, connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and execute the command: `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`</span></span>  
  
     <span data-ttu-id="a4c28-223">*\<servername>* は [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-223">Replace *\<servername>* with the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="a4c28-224">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスのファイル システム パスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-224">Use the file system path of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
7.  <span data-ttu-id="a4c28-225">Windows のメモ帳を使用して **instmsdb.out** ファイルを開き、エラーの出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-225">Using the Windows Notepad, open the **instmsdb.out** file and check the output for any errors.</span></span>  
  
8.  <span data-ttu-id="a4c28-226">インスタンスにインストールされていたサービス パックまたは修正プログラムがあれば、再適用します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-226">Re-apply any service packs or hotfix installed on the instance.</span></span>  
  
9. <span data-ttu-id="a4c28-227">ジョブや警告など、データベースに格納されているユーザーコンテンツを再作成し `msdb` ます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-227">Recreate the user content stored in the `msdb` database, such as jobs, alert, etc.</span></span>  
  
10. <span data-ttu-id="a4c28-228">`msdb` をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="a4c28-228">Backup the `msdb` database.</span></span>  
  
##  <a name="troubleshoot-rebuild-errors"></a><a name="Troubleshoot"></a> <span data-ttu-id="a4c28-229">再構築エラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a4c28-229">Troubleshoot Rebuild Errors</span></span>  
 <span data-ttu-id="a4c28-230">コマンド プロンプト ウィンドウには、構文エラーおよびその他の実行時エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-230">Syntax and other run-time errors are displayed in the command prompt window.</span></span> <span data-ttu-id="a4c28-231">セットアップ ステートメントに次の構文エラーがないか調査してください。</span><span class="sxs-lookup"><span data-stu-id="a4c28-231">Examine the Setup statement for the following syntax errors:</span></span>  
  
-   <span data-ttu-id="a4c28-232">パラメーター名の前のスラッシュ記号 (/) の欠如。</span><span class="sxs-lookup"><span data-stu-id="a4c28-232">Missing slash mark (/) in front of each parameter name.</span></span>  
  
-   <span data-ttu-id="a4c28-233">パラメーター名とパラメーター値の間の等号 (=) の欠如。</span><span class="sxs-lookup"><span data-stu-id="a4c28-233">Missing equal sign (=) between the parameter name and the parameter value.</span></span>  
  
-   <span data-ttu-id="a4c28-234">パラメーター名と等号の間の空白文字の存在。</span><span class="sxs-lookup"><span data-stu-id="a4c28-234">Presence of blank spaces between the parameter name and the equal sign.</span></span>  
  
-   <span data-ttu-id="a4c28-235">構文に指定されていないコンマ (,) またはその他の文字の存在。</span><span class="sxs-lookup"><span data-stu-id="a4c28-235">Presence of commas (,) or other characters that are not specified in the syntax.</span></span>  
  
 <span data-ttu-id="a4c28-236">再構築操作が完了した後で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログにエラーがないか調査します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-236">After the rebuild operation is complete, examine the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logs for any errors.</span></span> <span data-ttu-id="a4c28-237">ログの既定の場所は C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs です。</span><span class="sxs-lookup"><span data-stu-id="a4c28-237">The default log location is C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.</span></span> <span data-ttu-id="a4c28-238">再構築プロセスの結果を含むログ ファイルを探すには、ディレクトリをコマンド プロンプトから Logs フォルダーに変更し、 `findstr /s RebuildDatabase summary*.*`を実行します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-238">To locate the log file that contains the results of the rebuild process, change directories to the Logs folder from a command prompt, and then run `findstr /s RebuildDatabase summary*.*`.</span></span> <span data-ttu-id="a4c28-239">この検索により、システム データベースの再構築結果を含むログ ファイルが検出されます。</span><span class="sxs-lookup"><span data-stu-id="a4c28-239">This search will point you to any log files that contain the results of rebuilding system databases.</span></span> <span data-ttu-id="a4c28-240">ログ ファイルを開き、該当するエラー メッセージがないか調査します。</span><span class="sxs-lookup"><span data-stu-id="a4c28-240">Open the log files and examine them for relevant error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c28-241">参照</span><span class="sxs-lookup"><span data-stu-id="a4c28-241">See Also</span></span>  
 [<span data-ttu-id="a4c28-242">システム データベース</span><span class="sxs-lookup"><span data-stu-id="a4c28-242">System Databases</span></span>](system-databases.md)  
  
  
