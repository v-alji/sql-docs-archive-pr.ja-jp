---
title: media retention サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- backup retention duration [SQL Server]
- backup sets [SQL Server], retention duration
- media retention option
ms.assetid: 12e9fe6a-20a5-4c6e-9cc9-d500c003b70a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 092e0a2b5cfc30fd2d2362645fc1242bf4a1651e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634634"
---
# <a name="configure-the-media-retention-server-configuration-option"></a><span data-ttu-id="485fb-102">media retention サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="485fb-102">Configure the media retention Server Configuration Option</span></span>
  <span data-ttu-id="485fb-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] media retention [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="485fb-103">This topic describes how to configure the **media retention** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="485fb-104">**media retention** オプションは、各バックアップ セットを保持する期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="485fb-104">The **media retention** option specifies the length of time to retain each backup set.</span></span> <span data-ttu-id="485fb-105">このオプションを利用して、指定した日数が経過するまでバックアップが上書きされないように保護できます。</span><span class="sxs-lookup"><span data-stu-id="485fb-105">The option helps protect backups from being overwritten until the specified number of days has elapsed.</span></span> <span data-ttu-id="485fb-106">**media retention** オプションを構成すると、バックアップするたびにシステム バックアップを保持する期間を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="485fb-106">After you configure **media retention** option, you do not have to specify the length of time to retain system backups each time you perform a backup.</span></span> <span data-ttu-id="485fb-107">既定値は 0 日であり、最大値は 365 日です。</span><span class="sxs-lookup"><span data-stu-id="485fb-107">The default value is 0 days, and the maximum value is 365 days.</span></span>  
  
 <span data-ttu-id="485fb-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="485fb-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="485fb-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="485fb-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="485fb-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="485fb-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="485fb-111">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="485fb-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="485fb-112">Security</span><span class="sxs-lookup"><span data-stu-id="485fb-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="485fb-113">**以下を使用して media retention オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="485fb-113">**To configure the media retention option, using:**</span></span>  
  
     [<span data-ttu-id="485fb-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="485fb-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="485fb-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="485fb-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="485fb-116">**補足情報:** [media retention オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="485fb-116">**Follow Up:**  [After you configure the media retention option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="485fb-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="485fb-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="485fb-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="485fb-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="485fb-119">設定した日数が経過する前にバックアップ メディアを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって警告メッセージが発行されます。</span><span class="sxs-lookup"><span data-stu-id="485fb-119">If you use the backup medium before the set number of days has passed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] issues a warning message.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="485fb-120">から警告が発行されることはありません。</span><span class="sxs-lookup"><span data-stu-id="485fb-120">does not issue a warning unless you change the default.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="485fb-121">推奨事項</span><span class="sxs-lookup"><span data-stu-id="485fb-121">Recommendations</span></span>  
  
-   <span data-ttu-id="485fb-122">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="485fb-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="485fb-123">**media retention** オプションは、[BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントの RETAINDAYS 句を使用してオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="485fb-123">The **media retention** option can be overridden by using the RETAINDAYS clause of the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="485fb-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="485fb-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="485fb-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="485fb-125">Permissions</span></span>  
 <span data-ttu-id="485fb-126">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="485fb-126">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="485fb-127">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="485fb-127">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="485fb-128">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="485fb-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="485fb-129">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="485fb-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-media-retention-option"></a><span data-ttu-id="485fb-130">media retention オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="485fb-130">To configure the media retention option</span></span>  
  
1.  <span data-ttu-id="485fb-131">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="485fb-131">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="485fb-132">**[データベースの設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="485fb-132">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="485fb-133">**[バックアップと復元]** の **[バックアップ メディアの既定の保有期間 (日)]** ボックスで、0 ～ 365 の値を入力または選択します。ここで指定した日数が、データベース バックアップまたはトランザクション ログ バックアップの後にバックアップ メディアを保持する日数となります。</span><span class="sxs-lookup"><span data-stu-id="485fb-133">Under **Backup/Restore**, in the **Default backup media retention** box, type or select a value from 0 through 365 to set the number of days the backup medium will be retained after a database or transaction log backup.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="485fb-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="485fb-134">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-media-retention-option"></a><span data-ttu-id="485fb-135">media retention オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="485fb-135">To configure the media retention option</span></span>  
  
1.  <span data-ttu-id="485fb-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="485fb-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="485fb-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="485fb-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="485fb-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="485fb-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="485fb-139">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `media retention` オプションの値を `60` 日に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="485fb-139">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `media retention` option to `60` days.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'media retention', 60 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="485fb-140">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="485fb-140">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-media-retention-option"></a><a name="FollowUp"></a><span data-ttu-id="485fb-141">補足情報: media retention オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="485fb-141">Follow Up: After you configure the media retention option</span></span>  
 <span data-ttu-id="485fb-142">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="485fb-142">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485fb-143">参照</span><span class="sxs-lookup"><span data-stu-id="485fb-143">See Also</span></span>  
 <span data-ttu-id="485fb-144">[SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="485fb-144">[Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="485fb-145">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="485fb-145">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="485fb-146">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="485fb-146">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="485fb-147">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="485fb-147">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="485fb-148">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="485fb-148">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
