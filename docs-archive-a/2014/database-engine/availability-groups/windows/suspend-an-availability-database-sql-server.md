---
title: 可用性データベースの中断 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.suspenddatamove.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], suspending a database
- Availability Groups [SQL Server], databases
ms.assetid: 86858982-6af1-4e80-9a93-87451f0d7ee9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49afe868a509f84160fc1ad154135e8e67f6900a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741289"
---
# <a name="suspend-an-availability-database-sql-server"></a><span data-ttu-id="09378-102">可用性データベースの中断 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="09378-102">Suspend an Availability Database (SQL Server)</span></span>
  <span data-ttu-id="09378-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用して、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の可用性データベースを中断できます。</span><span class="sxs-lookup"><span data-stu-id="09378-103">You can suspend an availability database in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="09378-104">中断コマンドは、中断または再開するデータベースをホストするサーバー インスタンス上で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09378-104">Note that a suspend command needs to be issued on the server instance that hosts the database to be suspended or resumed.</span></span>  
  
 <span data-ttu-id="09378-105">中断コマンドの効果は、次のように、中断するのがセカンダリ データベースかプライマリ データベースかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="09378-105">The effect of a suspend command depends on whether you suspend a secondary database or a primary database, as follows:</span></span>  
  
|<span data-ttu-id="09378-106">中断されたデータベース</span><span class="sxs-lookup"><span data-stu-id="09378-106">Suspended Database</span></span>|<span data-ttu-id="09378-107">中断コマンドの影響</span><span class="sxs-lookup"><span data-stu-id="09378-107">Effect of Suspend Command</span></span>|  
|------------------------|-------------------------------|  
|<span data-ttu-id="09378-108">[セカンダリ データベース]</span><span class="sxs-lookup"><span data-stu-id="09378-108">Secondary database</span></span>|<span data-ttu-id="09378-109">ローカルのセカンダリ データベースのみが中断され、同期の状態は NOT SYNCHRONIZING になります。</span><span class="sxs-lookup"><span data-stu-id="09378-109">Only the local secondary database is suspended and its synchronization state becomes NOT SYNCHRONIZING.</span></span> <span data-ttu-id="09378-110">他のセカンダリ データベースは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="09378-110">Other secondary databases are not affected.</span></span> <span data-ttu-id="09378-111">中断されたデータベースはデータ (ログ レコード) を受信および適用しなくなり、プライマリ データベースと同期されなくなります。</span><span class="sxs-lookup"><span data-stu-id="09378-111">The suspended database stops receiving and applying data (log records) and begins to fall behind the primary database.</span></span> <span data-ttu-id="09378-112">読み取り可能なセカンダリ上の既存の接続は、引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="09378-112">Existing connections on the readable secondary remain usable.</span></span> <span data-ttu-id="09378-113">読み取り可能なセカンダリ上で中断されたデータベースに対する新しい接続は、データ移動が再開されるまでは許可されません。</span><span class="sxs-lookup"><span data-stu-id="09378-113">New connections to the suspended database on the readable secondary are not allowed until data movement is resumed.</span></span><br /><br /> <span data-ttu-id="09378-114">プライマリ データベースは使用可能です。</span><span class="sxs-lookup"><span data-stu-id="09378-114">The primary database remains available.</span></span> <span data-ttu-id="09378-115">対応する各セカンダリ データベースを中断した場合、プライマリ データベースは公開された状態で実行されます。</span><span class="sxs-lookup"><span data-stu-id="09378-115">If you suspend each of the corresponding secondary databases, the primary database runs exposed.</span></span><br /><br /> <span data-ttu-id="09378-116">**\*\* 重要 \*\*** セカンダリ データベースが中断されている間、対応するプライマリ データベースの送信キューが未送信トランザクション ログ レコードに蓄積されます。</span><span class="sxs-lookup"><span data-stu-id="09378-116">**\*\* Important \*\*** While a secondary database is suspended, the send queue of the corresponding primary database will accumulate unsent transaction log records.</span></span> <span data-ttu-id="09378-117">セカンダリ レプリカへの接続では、データ移動が中断されたときに使用可能であったデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="09378-117">Connections to the secondary replica return data that was available at the time the data movement was suspended.</span></span>|  
|<span data-ttu-id="09378-118">プライマリ データベース</span><span class="sxs-lookup"><span data-stu-id="09378-118">Primary database</span></span>|<span data-ttu-id="09378-119">プライマリ データベースは、接続されているすべてのセカンダリ データベースへのデータ移動を停止します。</span><span class="sxs-lookup"><span data-stu-id="09378-119">The primary database stops data movement to every connected secondary database.</span></span> <span data-ttu-id="09378-120">プライマリ データベースは、公開モードで実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="09378-120">The primary database continues running, in an exposed mode.</span></span> <span data-ttu-id="09378-121">クライアントはプライマリ データベースを使用でき、読み取り可能なセカンダリ上の既存の接続は引き続き使用でき、新しい接続も確立できます。</span><span class="sxs-lookup"><span data-stu-id="09378-121">The primary database remains available to clients, and existing connections on a readable secondary remain usable and new connections can be made.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="09378-122">AlwaysOn セカンダリ データベースの中断が、プライマリ データベースの可用性に直接影響することはありません。</span><span class="sxs-lookup"><span data-stu-id="09378-122">Suspending an AlwaysOn secondary database does not directly affect the availability of the primary database.</span></span> <span data-ttu-id="09378-123">ただし、セカンダリ データベースを中断すると、プライマリ データベースの冗長性とフェールオーバー機能に影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="09378-123">However, suspending a secondary database can impact redundancy and failover capabilities for the primary database.</span></span> <span data-ttu-id="09378-124">ミラーリングの場合はこれと異なり、ミラーリングの状態はミラー データベースでもプリンシパル データベースでも中断になります。</span><span class="sxs-lookup"><span data-stu-id="09378-124">This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database.</span></span> <span data-ttu-id="09378-125">AlwaysOn プライマリ データベースを中断すると、対応するすべてのセカンダリ データベースでデータ移動が中断され、そのデータベースの冗長性とフェールオーバー機能はプライマリ データベースが再開されるまで停止されます。</span><span class="sxs-lookup"><span data-stu-id="09378-125">Suspending an AlwaysOn primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.</span></span>  
  
-   <span data-ttu-id="09378-126">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="09378-126">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="09378-127">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="09378-127">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="09378-128">前提条件</span><span class="sxs-lookup"><span data-stu-id="09378-128">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="09378-129">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="09378-129">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="09378-130">Security</span><span class="sxs-lookup"><span data-stu-id="09378-130">Security</span></span>](#Security)  
  
-   <span data-ttu-id="09378-131">**データベースを中断するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="09378-131">**To suspend a database, using:**</span></span>  
  
-   [<span data-ttu-id="09378-132">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="09378-132">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="09378-133">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="09378-133">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="09378-134">PowerShell</span><span class="sxs-lookup"><span data-stu-id="09378-134">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="09378-135">**補足情報:** [トランザクション ログがいっぱいになった状態の回避](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="09378-135">**Follow up:** [Avoiding a Full Transaction Log](#FollowUp)</span></span>  
  
-   [<span data-ttu-id="09378-136">関連タスク</span><span class="sxs-lookup"><span data-stu-id="09378-136">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="09378-137">はじめに</span><span class="sxs-lookup"><span data-stu-id="09378-137">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="09378-138">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="09378-138">Limitations and Restrictions</span></span>  
 <span data-ttu-id="09378-139">SUSPEND コマンドは、対象のデータベースをホストするレプリカによって受け付けられるとすぐに戻りますが、実際にはデータベースの中断が非同期に行われます。</span><span class="sxs-lookup"><span data-stu-id="09378-139">A SUSPEND command returns as soon as it has been accepted by the replica that hosts the target database, but actually suspending the database occurs asynchronously.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="09378-140">前提条件</span><span class="sxs-lookup"><span data-stu-id="09378-140">Prerequisites</span></span>  
 <span data-ttu-id="09378-141">中断するデータベースをホストするサーバー インスタンスに接続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="09378-141">You must be connected to the server instance that hosts the database that you want to suspend.</span></span> <span data-ttu-id="09378-142">プライマリ データベースとそれに対応するセカンダリ データベースを中断するには、プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="09378-142">To suspend a primary database and the corresponding secondary databases, connect to the server instance that hosts the primary replica.</span></span> <span data-ttu-id="09378-143">プライマリ データベースを使用可能な状態で維持したままセカンダリ データベースを中断するには、セカンダリ レプリカに接続します。</span><span class="sxs-lookup"><span data-stu-id="09378-143">To suspend a secondary database while leaving the primary database available, connect to the secondary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="09378-144">推奨事項</span><span class="sxs-lookup"><span data-stu-id="09378-144">Recommendations</span></span>  
 <span data-ttu-id="09378-145">ボトルネックの発生中、1 つ以上のセカンダリ データベースを短時間中断すると、プライマリ レプリカのパフォーマンスが一時的に高まる効果が見込めます。</span><span class="sxs-lookup"><span data-stu-id="09378-145">During bottlenecks, suspending one or more secondary databases briefly might be useful to improve performance temporarily on the primary replica.</span></span> <span data-ttu-id="09378-146">セカンダリ データベースが中断している間、対応するプライマリ データベースのトランザクション ログを切り捨てることはできません。</span><span class="sxs-lookup"><span data-stu-id="09378-146">As long as a secondary database remains suspended, the transaction log of the corresponding primary database cannot be truncated.</span></span> <span data-ttu-id="09378-147">これにより、プライマリ データベースでログ レコードが蓄積されます。</span><span class="sxs-lookup"><span data-stu-id="09378-147">This causes log records to accumulate on the primary database.</span></span> <span data-ttu-id="09378-148">そのため、中断したセカンダリ データベースをすぐに再開または削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="09378-148">Therefore, we recommend that you resume, or remove, a suspended secondary database quickly.</span></span> <span data-ttu-id="09378-149">詳細については、このトピックで後述する「[補足情報: トランザクション ログがいっぱいになった状態の回避](#FollowUp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09378-149">For more information, see [Follow up: Avoiding a Full Transaction Log](#FollowUp), later in this topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="09378-150">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="09378-150">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="09378-151">Permissions</span><span class="sxs-lookup"><span data-stu-id="09378-151">Permissions</span></span>  
 <span data-ttu-id="09378-152">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="09378-152">Requires ALTER permission on the database.</span></span>  
  
 <span data-ttu-id="09378-153">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="09378-153">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="09378-154">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="09378-154">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="09378-155">**データベースを中断するには**</span><span class="sxs-lookup"><span data-stu-id="09378-155">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="09378-156">オブジェクト エクスプローラーで、データベースを中断する可用性レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="09378-156">In Object Explorer, connect to the server instance that hosts the availability replica on which you want to suspend a database, and expand the server tree.</span></span> <span data-ttu-id="09378-157">詳細については、このトピックの「 [前提条件](#Prerequisites)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09378-157">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="09378-158">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="09378-158">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="09378-159">可用性グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="09378-159">Expand the availability group.</span></span>  
  
4.  <span data-ttu-id="09378-160">**[可用性データベース]** ノードを展開し、データベースを右クリックして、 **[データ移動の中断]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="09378-160">Expand the **Availability Databases** node, right-click the database, and click **Suspend Data Movement**.</span></span>  
  
5.  <span data-ttu-id="09378-161">**[データ移動の中断]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="09378-161">In the **Suspend Data Movement** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="09378-162">オブジェクト エクスプローラーで、データベース アイコンに中断インジケーターが表示され、データベースが中断されていることが示されます。</span><span class="sxs-lookup"><span data-stu-id="09378-162">Object Explorer indicates that the database is suspended by changing  the database icon to display a pause indicator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09378-163">このレプリカの場所で他のデータベースを中断するには、データベースごとに手順 4. と手順 5. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="09378-163">To suspend additional databases on this replica location, repeat steps 4 and 5  for each database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="09378-164">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="09378-164">Using Transact-SQL</span></span>  
 <span data-ttu-id="09378-165">**データベースを中断するには**</span><span class="sxs-lookup"><span data-stu-id="09378-165">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="09378-166">中断するデータベースのレプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="09378-166">Connect to the server instance that hosts the replica whose database you want to suspend.</span></span> <span data-ttu-id="09378-167">詳細については、このトピックの「 [前提条件](#Prerequisites)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09378-167">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="09378-168">次の [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)ステートメントを使用して、データベースを中断します。</span><span class="sxs-lookup"><span data-stu-id="09378-168">Suspend the database by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)statement:</span></span>  
  
     <span data-ttu-id="09378-169">ALTER DATABASE *database_name*設定 HADR SUSPEND</span><span class="sxs-lookup"><span data-stu-id="09378-169">ALTER DATABASE *database_name* SET HADR SUSPEND</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="09378-170">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="09378-170">Using PowerShell</span></span>  
 <span data-ttu-id="09378-171">**データベースを中断するには**</span><span class="sxs-lookup"><span data-stu-id="09378-171">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="09378-172">ディレクトリ (`cd`) を、中断するデータベースのレプリカをホストするサーバー インスタンスに変更します。</span><span class="sxs-lookup"><span data-stu-id="09378-172">Change directory (`cd`) to the server instance that hosts the replica whose database you want to suspend.</span></span> <span data-ttu-id="09378-173">詳細については、このトピックの「 [前提条件](#Prerequisites)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09378-173">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="09378-174">`Suspend-SqlAvailabilityDatabase` コマンドレットを使用して可用性グループを中断します。</span><span class="sxs-lookup"><span data-stu-id="09378-174">Use the `Suspend-SqlAvailabilityDatabase` cmdlet to suspend the availability group.</span></span>  
  
     <span data-ttu-id="09378-175">たとえば、次のコマンドでは、 `MyDb3` という名前のサーバー インスタンス上の可用性グループ `MyAg` に含まれている可用性データベース `Computer\Instance`のデータの同期を中断します。</span><span class="sxs-lookup"><span data-stu-id="09378-175">For example, the following command suspends data synchronization for the availability database `MyDb3` in the availability group `MyAg` on the server instance named `Computer\Instance`.</span></span>  
  
    ```powershell
    Suspend-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="09378-176">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="09378-176">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="09378-177">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09378-177">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="09378-178">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="09378-178">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="09378-179">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="09378-179">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-avoiding-a-full-transaction-log"></a><a name="FollowUp"></a><span data-ttu-id="09378-180">補足情報: トランザクション ログがいっぱいになった状態の回避</span><span class="sxs-lookup"><span data-stu-id="09378-180">Follow Up: Avoiding a Full Transaction Log</span></span>  
 <span data-ttu-id="09378-181">通常、データベースで自動チェックポイントが実行されている場合は、次のログ バックアップの後、そのチェックポイントまでトランザクション ログが切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="09378-181">Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup.</span></span> <span data-ttu-id="09378-182">ただし、セカンダリ データベースを中断している間、現在のすべてのログ レコードは、プライマリ データベースでアクティブのままになります。</span><span class="sxs-lookup"><span data-stu-id="09378-182">However, while a secondary database is suspended, all of the current log records remain active on the primary database.</span></span> <span data-ttu-id="09378-183">最大サイズに到達したか、サーバー インスタンスの領域が不足して、トランザクション ログがいっぱいになると、データベースではそれ以上の更新を実行できません。</span><span class="sxs-lookup"><span data-stu-id="09378-183">If the transaction log fills up (either because it reaches its maximum size or the server instance runs out of space), the database cannot perform any more updates.</span></span>  
  
 <span data-ttu-id="09378-184">この問題を回避するには、次のいずれかの操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09378-184">To avoid this problem, you should do one of the following:</span></span>  
  
-   <span data-ttu-id="09378-185">プライマリ データベースのログ領域を追加します。</span><span class="sxs-lookup"><span data-stu-id="09378-185">Add more log space for the primary database.</span></span>  
  
-   <span data-ttu-id="09378-186">ログがいっぱいになる前に、セカンダリ データベースを再開します。</span><span class="sxs-lookup"><span data-stu-id="09378-186">Resume the secondary database before the log fills up.</span></span> <span data-ttu-id="09378-187">詳細については、このトピックの「 [可用性データベースの再開 &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md)の可用性データベースを中断できます。</span><span class="sxs-lookup"><span data-stu-id="09378-187">For more information, see [Resume an Availability Database &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md).</span></span>  
  
-   <span data-ttu-id="09378-188">セカンダリ データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="09378-188">Remove the secondary database.</span></span> <span data-ttu-id="09378-189">詳細については、「[可用性グループからのセカンダリ データベースの削除 &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09378-189">For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="09378-190">**満杯になったトランザクション ログのトラブルシューティング**</span><span class="sxs-lookup"><span data-stu-id="09378-190">**To troubleshoot a full transaction log**</span></span>  
  
-   [<span data-ttu-id="09378-191">満杯になったトランザクション ログのトラブルシューティング &#40;SQL Server エラー 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="09378-191">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](../../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="09378-192">関連タスク</span><span class="sxs-lookup"><span data-stu-id="09378-192">Related Tasks</span></span>  
  
-   [<span data-ttu-id="09378-193">可用性データベースの再開 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="09378-193">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="09378-194">参照</span><span class="sxs-lookup"><span data-stu-id="09378-194">See Also</span></span>  
 <span data-ttu-id="09378-195">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="09378-195">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="09378-196">可用性データベースの再開 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="09378-196">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
