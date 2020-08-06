---
title: remote query timeout サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- time limit for remote queries [SQL Server]
- remote query timeout option
ms.assetid: 888c8448-933b-41e3-8aa1-c206bc0cdb78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 74f82d621d7f0375a6a3ca604abba00f83fc6024
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740429"
---
# <a name="configure-the-remote-query-timeout-server-configuration-option"></a><span data-ttu-id="d533a-102">remote query timeout サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="d533a-102">Configure the remote query timeout Server Configuration Option</span></span>
  <span data-ttu-id="d533a-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または[!INCLUDE[tsql](../../includes/tsql-md.md)]を利用して[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の **remote query timeout** サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d533a-103">This topic describes how to configure the **remote query timeout** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d533a-104">**remote query timeout** オプションは、リモート操作を実行してから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がタイムアウトになるまでの時間 (秒単位) を指定します。このオプションの既定値は 600 で、10 分間の待機時間が見込まれています。</span><span class="sxs-lookup"><span data-stu-id="d533a-104">The **remote query timeout** option specifies how long, in seconds, a remote operation can take before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] times out. The default value for this option is 600, which allows a 10-minute wait.</span></span> <span data-ttu-id="d533a-105">この値は、[!INCLUDE[ssDE](../../includes/ssde-md.md)] によってリモート クエリとして開始された発信接続に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d533a-105">This value applies to an outgoing connection initiated by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] as a remote query.</span></span> <span data-ttu-id="d533a-106">この値は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が受信したクエリには影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="d533a-106">This value has no effect on queries received by the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="d533a-107">タイムアウトを無効にするには、値を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d533a-107">To disable the time-out, set the value to 0.</span></span> <span data-ttu-id="d533a-108">クエリは完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="d533a-108">A query will wait until it completes.</span></span>  
  
 <span data-ttu-id="d533a-109">異種クエリの場合、 **remote query timeout** は、リモート プロバイダーが結果セットを待機する場合のクエリのタイムアウト時間を秒数で指定します。この値は、DBPROP_COMMANDTIMEOUT 行セット プロパティを使用してコマンド オブジェクトで初期化されます。また、リモート プロバイダーで DBPROP_GENERALTIMEOUT がサポートされている場合、この値は DBPROP_GENERALTIMEOUT の設定にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="d533a-109">For heterogeneous queries, **remote query timeout** specifies the number of seconds (initialized in the command object using the DBPROP_COMMANDTIMEOUT rowset property) that a remote provider should wait for result sets before the query times out. This value is also used to set DBPROP_GENERALTIMEOUT if supported by the remote provider.</span></span> <span data-ttu-id="d533a-110">これによって、他の操作に対しても、指定した秒数の後にタイムアウトが適用されます。</span><span class="sxs-lookup"><span data-stu-id="d533a-110">This will cause any other operations to time out after the specified number of seconds.</span></span>  
  
 <span data-ttu-id="d533a-111">リモート ストアド プロシージャの場合、 **remote query timeout** は、リモート `EXEC` ステートメントを送信してからリモート ストアド プロシージャがタイムアウトするまでの経過時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="d533a-111">For remote stored procedures, **remote query timeout** specifies the number of seconds that must elapse after sending a remote `EXEC` statement before the remote stored procedure times out.</span></span>  
  
 <span data-ttu-id="d533a-112">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d533a-112">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d533a-113">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d533a-113">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d533a-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="d533a-114">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="d533a-115">Security</span><span class="sxs-lookup"><span data-stu-id="d533a-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d533a-116">**以下を使用して remote query timeout オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="d533a-116">**To configure the remote query timeout option, using:**</span></span>  
  
     [<span data-ttu-id="d533a-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d533a-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d533a-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d533a-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d533a-119">**補足情報:** [remote query timeout オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d533a-119">**Follow Up:**  [After you configure the remote query timeout option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d533a-120">はじめに</span><span class="sxs-lookup"><span data-stu-id="d533a-120">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d533a-121">前提条件</span><span class="sxs-lookup"><span data-stu-id="d533a-121">Prerequisites</span></span>  
  
-   <span data-ttu-id="d533a-122">この値を設定するには、あらかじめリモート サーバー接続が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d533a-122">Remote server connections must be allowed before this value can be set.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d533a-123">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d533a-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d533a-124">Permissions</span><span class="sxs-lookup"><span data-stu-id="d533a-124">Permissions</span></span>  
 <span data-ttu-id="d533a-125">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="d533a-125">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="d533a-126">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d533a-126">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="d533a-127">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="d533a-127">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d533a-128">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d533a-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a><span data-ttu-id="d533a-129">remote query timeout オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="d533a-129">To configure the remote query timeout option</span></span>  
  
1.  <span data-ttu-id="d533a-130">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d533a-130">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="d533a-131">**[接続]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d533a-131">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="d533a-132">**[リモート サーバー接続]** の **[リモート クエリ タイムアウト]** ボックスで、0 ～ 2,147,483,647 の値を入力するか選択し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がタイムアウトするまでの最大秒数を設定します。</span><span class="sxs-lookup"><span data-stu-id="d533a-132">Under **Remote server connections**, in the **Remote query timeout** box, type or select a value from 0 through 2,147,483,647 to set the maximum number seconds for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to wait before timing out.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d533a-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d533a-133">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a><span data-ttu-id="d533a-134">remote query timeout オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="d533a-134">To configure the remote query timeout option</span></span>  
  
1.  <span data-ttu-id="d533a-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="d533a-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d533a-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d533a-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d533a-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d533a-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d533a-138">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `remote query timeout` オプションの値を `0` に設定し、タイムアウトを無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d533a-138">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote query timeout` option to `0` to disable the time-out.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote query timeout', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="d533a-139">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d533a-139">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-query-timeout-option"></a><a name="FollowUp"></a><span data-ttu-id="d533a-140">補足情報: remote query timeout オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="d533a-140">Follow Up: After you configure the remote query timeout option</span></span>  
 <span data-ttu-id="d533a-141">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="d533a-141">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d533a-142">参照</span><span class="sxs-lookup"><span data-stu-id="d533a-142">See Also</span></span>  
 <span data-ttu-id="d533a-143">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d533a-143">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="d533a-144">[行セットのプロパティと動作](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span><span class="sxs-lookup"><span data-stu-id="d533a-144">[Rowset Properties and Behaviors](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span></span>  
 <span data-ttu-id="d533a-145">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d533a-145">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="d533a-146">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d533a-146">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
