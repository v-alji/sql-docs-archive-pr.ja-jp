---
title: scan for startup procs サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- scan for startup procs option
ms.assetid: 6bf9d252-e766-458d-9dcd-23d895f032a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fbf46fc7476e6e879991cfe3f649fd5617f3275e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634625"
---
# <a name="configure-the-scan-for-startup-procs-server-configuration-option"></a><span data-ttu-id="4f9f3-102">scan for startup procs サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="4f9f3-102">Configure the scan for startup procs Server Configuration Option</span></span>
  <span data-ttu-id="4f9f3-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] scan for startup procs [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-103">This topic describes how to configure the **scan for startup procs** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4f9f3-104">**scan for startup procs** オプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 起動時のストアド プロシージャの自動実行をスキャンする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-104">Use the **scan for startup procs** option to scan for automatic execution of stored procedures at [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup time.</span></span> <span data-ttu-id="4f9f3-105">このオプションを 1 に設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、サーバーで定義されているすべての自動実行ストアド プロシージャがスキャンされ、実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-105">If this option is set to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] scans for and runs all automatically run stored procedures that are defined on the server.</span></span> <span data-ttu-id="4f9f3-106">**scan for startup procs** の既定値は 0 です。この値を設定した場合、スキャンは行われません。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-106">The default value for **scan for startup procs** is 0 (do not scan).</span></span>  
  
 <span data-ttu-id="4f9f3-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4f9f3-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4f9f3-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4f9f3-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4f9f3-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="4f9f3-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="4f9f3-110">Security</span><span class="sxs-lookup"><span data-stu-id="4f9f3-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4f9f3-111">**以下を使用して scan for startup procs オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="4f9f3-111">**To configure the scan for startup procs option, using:**</span></span>  
  
     [<span data-ttu-id="4f9f3-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4f9f3-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4f9f3-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4f9f3-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="4f9f3-114">**補足情報:** [scan for startup procs オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="4f9f3-114">**Follow Up:**  [After you configure the scan for startup procs option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4f9f3-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="4f9f3-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="4f9f3-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="4f9f3-116">Recommendations</span></span>  
  
-   <span data-ttu-id="4f9f3-117">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-117">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="4f9f3-118">このオプションの値は **sp_configure**を使用して設定できますが、ストアド プロシージャを自動的に実行するかどうかを設定する **sp_procoption**を使用すれば、値が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-118">The value for this option can be set by using **sp_configure**; however, it will be set automatically if you use **sp_procoption**, which is used to mark or unmark automatically run stored procedures.</span></span> <span data-ttu-id="4f9f3-119">**sp_procoption** を使用して、最初のストアド プロシージャを autoproc として設定すると、このオプションの値は自動的に 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-119">When **sp_procoption** is used to mark the first stored procedure as an autoproc, this option is set automatically to a value of 1.</span></span> <span data-ttu-id="4f9f3-120">**sp_procoption** を使用して、最後のストアド プロシージャを autoproc として設定解除すると、このオプションの値は自動的に 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-120">When **sp_procoption** is used to unmark the last stored procedure as an autoproc, this option is automatically set to a value of 0.</span></span> <span data-ttu-id="4f9f3-121">**sp_procoption** を使用して autoprocs として設定またはその設定を解除し、ストアド プロシージャを削除する前に必ず autoprocs の設定を解除すれば、このオプションを手動で設定する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-121">If you use **sp_procoption** to mark and unmark autoprocs, and if you always unmark autoprocs before dropping them, there is no need to set this option manually.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4f9f3-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4f9f3-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4f9f3-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="4f9f3-123">Permissions</span></span>  
 <span data-ttu-id="4f9f3-124">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="4f9f3-125">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="4f9f3-126">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4f9f3-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4f9f3-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a><span data-ttu-id="4f9f3-128">[スタートアップ プロシージャのスキャン] オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="4f9f3-128">To configure the scan for startup procs option</span></span>  
  
1.  <span data-ttu-id="4f9f3-129">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4f9f3-130">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-130">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="4f9f3-131">**[その他]** で、 **[スタートアップ プロシージャのスキャン]** オプションのドロップダウン リストから値を選択して、[True] または [False] を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-131">Under **Miscellaneous**, change the **Scan for Startup Procs** option to True or False by selecting the value you want from the drop-down list box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4f9f3-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4f9f3-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a><span data-ttu-id="4f9f3-133">[スタートアップ プロシージャのスキャン] オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="4f9f3-133">To configure the scan for startup procs option</span></span>  
  
1.  <span data-ttu-id="4f9f3-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4f9f3-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4f9f3-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4f9f3-137">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `scan for startup procs` オプションの値を `1`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `scan for startup procs` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'scan for startup procs', 1 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-scan-for-startup-procs-option"></a><a name="FollowUp"></a><span data-ttu-id="4f9f3-138">補足情報: scan for startup procs オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="4f9f3-138">Follow Up: After you configure the scan for startup procs option</span></span>  
 <span data-ttu-id="4f9f3-139">設定を有効にするには、サーバーを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f9f3-139">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9f3-140">参照</span><span class="sxs-lookup"><span data-stu-id="4f9f3-140">See Also</span></span>  
 <span data-ttu-id="4f9f3-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4f9f3-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="4f9f3-142">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4f9f3-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="4f9f3-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4f9f3-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="4f9f3-144">sp_procoption &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4f9f3-144">sp_procoption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)  
  
  
