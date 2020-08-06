---
title: データベースのターゲットの復旧時間の変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c4331d2ade2819d172189a0de9daddecf3d9f6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639509"
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a><span data-ttu-id="0f4b3-102">データベースのターゲットの復旧時間の変更 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0f4b3-102">Change the Target Recovery Time of a Database (SQL Server)</span></span>
  <span data-ttu-id="0f4b3-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [!INCLUDE[tsql](../../includes/tsql-md.md)]データベースのターゲットの復旧時間を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-103">This topic describes how to set the change the target recovery time of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0f4b3-104">既定では、ターゲットの復旧時間は 0 で、データベースは *自動チェックポイント* ( **復旧間隔** サーバー オプションによって制御されます) を使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-104">By default, the target recovery time is 0, and the database uses *automatic checkpoints* (which are controlled by the **recovery interval** server option).</span></span> <span data-ttu-id="0f4b3-105">ターゲットの復旧時間を 0 より大きい値に設定すると、データベースは *間接的なチェックポイント* を使用するようになり、このデータベースの復旧時間に上限を設定します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-105">Setting the target recovery time to greater than 0 causes the database to use the *indirect-checkpoints* and establishes an upper-bound on recovery time for this database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f4b3-106">ターゲットの復旧時間の設定によって特定のデータベースに対して指定された上限は、実行時間の長いトランザクションによって UNDO が過度に繰り返される場合には超過することがあります。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-106">The upper-bound that is specified for a given database by its target recovery time setting could be exceeded if a long-running transaction causes excessive UNDO times.</span></span>  
  
-   <span data-ttu-id="0f4b3-107">**作業を開始する準備:** [制限事項と制約事項](#Restrictions)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="0f4b3-107">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="0f4b3-108">**ターゲットの復旧時間を変更するには:** [SQL Server Management Studio](#SSMSProcedure) または [Transact-SQL](#TsqlProcedure) を使用</span><span class="sxs-lookup"><span data-stu-id="0f4b3-108">**To change the target recovery time, using:**  [SQL Server Management Studio](#SSMSProcedure) or [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0f4b3-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="0f4b3-109">Before You Begin</span></span>  
  
###  <a name="Restrictions"></a>  
  
> [!CAUTION]  
>  <span data-ttu-id="0f4b3-110">間接チェックポイントが構成されたデータベースでオンライン トランザクション ワークロードが生じると、パフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-110">An online transactional workload on a database that is configured for indirect checkpoints could experience performance degradation.</span></span> <span data-ttu-id="0f4b3-111">間接チェックポイントは、ターゲットの復旧時間内でデータベースの回復が完了するように、ダーティ ページの数が特定のしきい値を下回るようにします。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-111">Indirect checkpoints make sure that the number of dirty pages are below a certain threshold so that the database recovery completes within the target recovery time.</span></span> <span data-ttu-id="0f4b3-112">復旧間隔構成オプションは、ダーティ ページ数を使用する間接チェックポイントとは異なり、トランザクション数を使用して復旧時間を決定します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-112">The recovery interval configuration option uses the number of transactions to determine the recovery time as opposed to indirect checkpoints which makes use of number of dirty pages.</span></span> <span data-ttu-id="0f4b3-113">DML 操作の受信数が多いデータベースで間接チェックポイントが有効な場合、バックグラウンド ライターは積極的にディスクにダーティ バッファーのフラッシュを開始し、回復を実行するのに必要な時間をデータベースのターゲット復旧時間内にすることができます。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-113">When indirect checkpoints are enabled on a database receiving a large number of DML operations, the background writer can start aggressively flushing dirty buffers to disk to ensure that the time required to perform recovery is within the target recovery time set of the database.</span></span> <span data-ttu-id="0f4b3-114">これにより、ディスクのサブシステムが I/O のしきい値よりも高い動作をするかまたはその値に近づいた場合、パフォーマンス ボトルネックの原因となる追加の I/O アクティビティが特定のシステムで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-114">This can cause additional I/O activity on certain systems which can contribute to a performance bottleneck if the disk subsystem is operating above or nearing the I/O threshold.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0f4b3-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0f4b3-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0f4b3-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="0f4b3-116">Permissions</span></span>  
 <span data-ttu-id="0f4b3-117">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0f4b3-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="0f4b3-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="0f4b3-119">**ターゲットの復旧時間を変更するには**</span><span class="sxs-lookup"><span data-stu-id="0f4b3-119">**To change the target recovery time**</span></span>  
  
1.  <span data-ttu-id="0f4b3-120">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and expand that instance.</span></span>  
  
2.  <span data-ttu-id="0f4b3-121">変更するデータベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-121">Right-click the database you want to change, and click the **Properties** command.</span></span>  
  
3.  <span data-ttu-id="0f4b3-122">**[データベースのプロパティ]** ダイアログ ボックスで、 **[オプション]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-122">In the **Database Properties** dialog box, click the **Options** page.</span></span>  
  
4.  <span data-ttu-id="0f4b3-123">**[復旧]** パネルの **[ターゲットの復旧時間 (秒)]** フィールドで、このデータベースの復旧時間の上限にする秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-123">In the **Recovery** panel, in the **Target Recovery Time (Seconds)** field, specify the number of seconds that you want as the upper-bound on the recovery time for this database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0f4b3-124">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="0f4b3-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="0f4b3-125">**ターゲットの復旧時間を変更するには**</span><span class="sxs-lookup"><span data-stu-id="0f4b3-125">**To change the target recovery time**</span></span>  
  
1.  <span data-ttu-id="0f4b3-126">データベースがある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-126">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the database resides.</span></span>  
  
2.  <span data-ttu-id="0f4b3-127">次の [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)ステートメントを、次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-127">Use the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)statement, as follows:</span></span>  
  
     <span data-ttu-id="0f4b3-128">TARGET_RECOVERY_TIME **=** _target_recovery_time_ { SECONDS | MINUTES }</span><span class="sxs-lookup"><span data-stu-id="0f4b3-128">TARGET_RECOVERY_TIME **=**_target_recovery_time_ { SECONDS | MINUTES }</span></span>  
  
     <span data-ttu-id="0f4b3-129">*target_recovery_time*</span><span class="sxs-lookup"><span data-stu-id="0f4b3-129">*target_recovery_time*</span></span>  
     <span data-ttu-id="0f4b3-130">0 (既定値) より大きい値の場合は、指定されたデータベースでクラッシュが発生したときの復旧時間に上限を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-130">When greater than 0 (the default), specifies the upper-bound on the recovery time for the specified database in the event of a crash.</span></span>  
  
     <span data-ttu-id="0f4b3-131">SECONDS</span><span class="sxs-lookup"><span data-stu-id="0f4b3-131">SECONDS</span></span>  
     <span data-ttu-id="0f4b3-132">*target_recovery_time* が秒単位で表されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-132">Indicates that *target_recovery_time* is expressed as the number of seconds.</span></span>  
  
     <span data-ttu-id="0f4b3-133">MINUTES</span><span class="sxs-lookup"><span data-stu-id="0f4b3-133">MINUTES</span></span>  
     <span data-ttu-id="0f4b3-134">*target_recovery_time* が分単位で表されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-134">Indicates that *target_recovery_time* is expressed as the number of minutes.</span></span>  
  
     <span data-ttu-id="0f4b3-135">次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースのターゲットの復旧時間を `60` 秒に設定します。</span><span class="sxs-lookup"><span data-stu-id="0f4b3-135">The following example sets the target recovery time of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to `60` seconds.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0f4b3-136">参照</span><span class="sxs-lookup"><span data-stu-id="0f4b3-136">See Also</span></span>  
 <span data-ttu-id="0f4b3-137">[データベース チェックポイント &#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0f4b3-137">[Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span></span>  
 [<span data-ttu-id="0f4b3-138">ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0f4b3-138">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
