---
title: recovery interval サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- restoring recovery interval [SQL Server]
- checkpoints [SQL Server]
- recovery interval option [SQL Server]
- default recovery interval option
- time [SQL Server], recovery interval
- interval for recovery [SQL Server]
- maximum number of minutes per database recovery
- recovery [SQL Server], recovery interval option
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 560d514ba8dd1503b59b3b59ecf404d876e24cd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632695"
---
# <a name="configure-the-recovery-interval-server-configuration-option"></a><span data-ttu-id="859fd-102">recovery interval サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="859fd-102">Configure the recovery interval Server Configuration Option</span></span>
  <span data-ttu-id="859fd-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] recovery interval [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="859fd-103">This topic describes how to configure the **recovery interval** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="859fd-104">**recovery interval** オプションは、データベースの復旧に必要な時間の上限を定義します。</span><span class="sxs-lookup"><span data-stu-id="859fd-104">The **recovery interval** option defines an upper limit on the time recovering a database should take.</span></span> <span data-ttu-id="859fd-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] は、 [自動チェックポイント](../../relational-databases/logs/database-checkpoints-sql-server.md) が特定のデータベースに対して発行されるおおよその頻度を、このオプションに指定された値を使用して決定します。</span><span class="sxs-lookup"><span data-stu-id="859fd-105">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses the value specified for this option to determine approximately how often [automatic checkpoints](../../relational-databases/logs/database-checkpoints-sql-server.md) to issue automatic checkpoints on a given database.</span></span>  
  
 <span data-ttu-id="859fd-106">recovery-interval の既定値は 0 で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によって自動的に復旧間隔が構成されます。</span><span class="sxs-lookup"><span data-stu-id="859fd-106">The default recovery-interval value is 0, which allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to automatically configure the recovery interval.</span></span> <span data-ttu-id="859fd-107">既定の recovery interval では、通常、アクティブなデータベースの自動チェックポイントの発生間隔は約 1 分、復旧時間は 1 分未満になります。</span><span class="sxs-lookup"><span data-stu-id="859fd-107">Typically, the default recovery interval results in automatic checkpoints occurring approximately once a minute for active databases and a recovery time of less than one minute.</span></span> <span data-ttu-id="859fd-108">既定値より大きな値は、おおよその最大リカバリ時間 (分単位) を示します。</span><span class="sxs-lookup"><span data-stu-id="859fd-108">Higher values indicate the approximate maximum recovery time, in minutes.</span></span> <span data-ttu-id="859fd-109">たとえば、recovery interval を '3' に設定した場合は、最大リカバリ時間は約 3 分になります。</span><span class="sxs-lookup"><span data-stu-id="859fd-109">For example, setting the recovery interval to 3 indicates a maximum recovery time of approximately three minutes.</span></span>  
  
 <span data-ttu-id="859fd-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="859fd-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="859fd-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="859fd-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="859fd-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="859fd-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="859fd-113">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="859fd-113">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="859fd-114">Security</span><span class="sxs-lookup"><span data-stu-id="859fd-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="859fd-115">**recovery interval サーバー構成オプションを構成する方法:**</span><span class="sxs-lookup"><span data-stu-id="859fd-115">**To Configure the recovery interval Server Configuration Option, using:**</span></span>  
  
     [<span data-ttu-id="859fd-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="859fd-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="859fd-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="859fd-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="859fd-118">**補足情報:** [recovery interval オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="859fd-118">**Follow Up:**  [After you configure the recovery interval option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="859fd-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="859fd-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="859fd-120">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="859fd-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="859fd-121">recovery interval が作用するのは、既定のターゲット復旧時間 (0) を使用するデータベースだけです。</span><span class="sxs-lookup"><span data-stu-id="859fd-121">The recovery interval affects only databases that use the default target recovery time (0).</span></span> <span data-ttu-id="859fd-122">データベース上のサーバー復旧間隔をオーバーライドするには、データベースの既定のターゲット復旧時間を既定以外の値に変更します。</span><span class="sxs-lookup"><span data-stu-id="859fd-122">To override the server recovery interval on a database, configure a non-default target recovery time on the database.</span></span> <span data-ttu-id="859fd-123">詳細については、「 [データベースのターゲットの復旧時間の変更 &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="859fd-123">For more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="859fd-124">推奨事項</span><span class="sxs-lookup"><span data-stu-id="859fd-124">Recommendations</span></span>  
  
-   <span data-ttu-id="859fd-125">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="859fd-125">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="859fd-126">通常は、パフォーマンス上の問題が発生する場合を除いて、recovery interval は 0 のままにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="859fd-126">Typically, we recommend that you keep the recovery interval at 0, unless you experience performance problems.</span></span> <span data-ttu-id="859fd-127">recovery interval 設定を長くする場合には、少しずつ値を増やして、そのたびに復旧のパフォーマンスへの影響を評価することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="859fd-127">If you decide to increase the recovery-interval setting, we recommend increasing it gradually by small increments and evaluating the effect of each incremental increase on recovery performance.</span></span>  
  
-   <span data-ttu-id="859fd-128">**sp_configure** を使用し、**recovery interval** オプションの値を 60 (分) よりも大きくするには、RECONFIGURE WITH OVERRIDE を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="859fd-128">If you use **sp_configure** to change the value of the **recovery interval** option to more than 60 (minutes), specify RECONFIGURE WITH OVERRIDE.</span></span> <span data-ttu-id="859fd-129">WITH OVERRIDE は、構成値のチェック (無効な値や非推奨値のチェック) を無効にします。</span><span class="sxs-lookup"><span data-stu-id="859fd-129">WITH OVERRIDE disables configuration value checking (for values that are not valid or are nonrecommended values).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="859fd-130">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="859fd-130">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="859fd-131">Permissions</span><span class="sxs-lookup"><span data-stu-id="859fd-131">Permissions</span></span>  
 <span data-ttu-id="859fd-132">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="859fd-132">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="859fd-133">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="859fd-133">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="859fd-134">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="859fd-134">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="859fd-135">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="859fd-135">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="859fd-136">**復旧間隔を設定するには**</span><span class="sxs-lookup"><span data-stu-id="859fd-136">**To set the recovery interval**</span></span>  
  
1.  <span data-ttu-id="859fd-137">オブジェクト エクスプローラーでサーバー インスタンスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="859fd-137">In Object Explorer, right-click server instance and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="859fd-138">**[データベースの設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="859fd-138">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="859fd-139">**[復旧]** の **[復旧間隔 (分単位)]** ボックスで、0 ～ 32767 の値を入力するか選択して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動時に各データベースの復旧に要する最大時間を分単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="859fd-139">Under **Recovery**, in the **Recovery interval (minutes)** box, type or select a value from 0 through 32767 to set the maximum amount of time, in minutes, that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should spend recovering each database at startup.</span></span> <span data-ttu-id="859fd-140">既定値は 0 です。0 の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="859fd-140">The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="859fd-141">実際には、復旧時間が 1 分未満で、アクティブなデータベースのチェックポイントは約 1 分間隔になります。</span><span class="sxs-lookup"><span data-stu-id="859fd-141">In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="859fd-142">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="859fd-142">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-recovery-interval"></a><span data-ttu-id="859fd-143">復旧間隔を設定するには</span><span class="sxs-lookup"><span data-stu-id="859fd-143">To set the recovery interval</span></span>  
  
1.  <span data-ttu-id="859fd-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="859fd-144">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="859fd-145">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="859fd-145">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="859fd-146">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="859fd-146">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="859fd-147">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `recovery interval` オプションの値を `3` 分に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="859fd-147">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `recovery interval` option to `3` minutes.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="859fd-148">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="859fd-148">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-recovery-internal-option"></a><a name="FollowUp"></a><span data-ttu-id="859fd-149">補足情報: recovery internal オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="859fd-149">Follow Up: After you configure the recovery internal option</span></span>  
 <span data-ttu-id="859fd-150">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="859fd-150">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859fd-151">参照</span><span class="sxs-lookup"><span data-stu-id="859fd-151">See Also</span></span>  
 <span data-ttu-id="859fd-152">[データベースのターゲットの復旧時間の変更 &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="859fd-152">[Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md) </span></span>  
 <span data-ttu-id="859fd-153">[データベース チェックポイント &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="859fd-153">[Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md) </span></span>  
 <span data-ttu-id="859fd-154">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="859fd-154">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="859fd-155">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="859fd-155">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="859fd-156">[show advanced options サーバー構成オプション](show-advanced-options-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="859fd-156">[show advanced options Server Configuration Option](show-advanced-options-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="859fd-157">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="859fd-157">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
