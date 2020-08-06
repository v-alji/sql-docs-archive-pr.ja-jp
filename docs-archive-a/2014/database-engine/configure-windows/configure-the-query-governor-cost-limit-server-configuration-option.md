---
title: query governor cost limit サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], time to execute
- query governor cost limit option [SQL Server]
- time [SQL Server], query run time
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d4f8420bf8ed8c08d3626c797968c041a40f7c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632696"
---
# <a name="configure-the-query-governor-cost-limit-server-configuration-option"></a><span data-ttu-id="8a9b7-102">query governor cost limit サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="8a9b7-102">Configure the query governor cost limit Server Configuration Option</span></span>
  <span data-ttu-id="8a9b7-103">このトピック `query governor cost limit` で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、のサーバー構成オプションを構成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-103">This topic describes how to configure the `query governor cost limit` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8a9b7-104">query governor cost limit オプションは、クエリを実行できる時間の上限を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-104">The query governor cost limit option specifies an upper limit on the time period in which a query can run.</span></span> <span data-ttu-id="8a9b7-105">クエリ コストとは、特定のハードウェア構成でクエリを完了するために必要とされる予測所要時間を秒単位で表したものです。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-105">Query cost refers to the estimated elapsed time, in seconds, that is required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="8a9b7-106">このオプションの既定値は 0 です。クエリ ガバナーはオフに設定されます。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-106">The default value for this option is 0, which sets the query governor to off.</span></span> <span data-ttu-id="8a9b7-107">この場合、すべてのクエリは時間制限なしで実行することが許可されます。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-107">This allows all queries to run without any time limitation.</span></span> <span data-ttu-id="8a9b7-108">0 以外の正の値を指定すると、クエリ ガバナーは、見積コストがこの値を超えるクエリの実行を許可しません。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-108">If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost that exceeds that value.</span></span>  
  
 <span data-ttu-id="8a9b7-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="8a9b7-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8a9b7-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="8a9b7-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8a9b7-111">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="8a9b7-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="8a9b7-112">Security</span><span class="sxs-lookup"><span data-stu-id="8a9b7-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8a9b7-113">**以下を使用して query governor cost limit オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="8a9b7-113">**To configure the query governor cost limit option, using:**</span></span>  
  
     [<span data-ttu-id="8a9b7-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8a9b7-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8a9b7-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8a9b7-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="8a9b7-116">**補足情報:** [query governor cost limit オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="8a9b7-116">**Follow Up:**  [After you configure the query governor cost limit option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8a9b7-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="8a9b7-117">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="8a9b7-118">推奨事項</span><span class="sxs-lookup"><span data-stu-id="8a9b7-118">Recommendations</span></span>  
  
-   <span data-ttu-id="8a9b7-119">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-119">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="8a9b7-120">接続ごとに query governor cost limit 値を変更するには、 [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-120">To change the value query governor cost limit on a per-connection basis, use the [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8a9b7-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8a9b7-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8a9b7-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="8a9b7-122">Permissions</span></span>  
 <span data-ttu-id="8a9b7-123">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-123">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="8a9b7-124">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-124">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="8a9b7-125">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-125">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8a9b7-126">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="8a9b7-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a><span data-ttu-id="8a9b7-127">query governor cost limit オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="8a9b7-127">To configure the query governor cost limit option</span></span>  
  
1.  <span data-ttu-id="8a9b7-128">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-128">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="8a9b7-129">**[接続]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-129">Click the **Connections** page.</span></span>  
  
3.  <span data-ttu-id="8a9b7-130">**[クエリの実行時間が長くならないようにクエリ ガバナーを使用する]** チェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-130">Select or clear the **Use query governor to prevent long-running queries** check box.</span></span>  
  
     <span data-ttu-id="8a9b7-131">このチェック ボックスをオンにした場合、下のボックスに正の値を入力します。任意のクエリの実行時間がこの値を超えると、クエリ ガバナーによりクエリの実行が禁止されます。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-131">If you select this check box, in the box below, enter a positive value, which the query governor uses to disallow execution of any query with a running length exceeding that value.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8a9b7-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="8a9b7-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a><span data-ttu-id="8a9b7-133">query governor cost limit オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="8a9b7-133">To configure the query governor cost limit option</span></span>  
  
1.  <span data-ttu-id="8a9b7-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8a9b7-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8a9b7-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="8a9b7-137">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `query governor cost limit` オプションの値を `120` 秒に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `query governor cost limit` option to `120` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="8a9b7-138">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-query-governor-cost-limit-option"></a><a name="FollowUp"></a><span data-ttu-id="8a9b7-139">補足情報: query governor cost limit オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="8a9b7-139">Follow Up: After you configure the query governor cost limit option</span></span>  
 <span data-ttu-id="8a9b7-140">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="8a9b7-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9b7-141">参照</span><span class="sxs-lookup"><span data-stu-id="8a9b7-141">See Also</span></span>  
 <span data-ttu-id="8a9b7-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a9b7-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="8a9b7-143">[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a9b7-143">[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) </span></span>  
 <span data-ttu-id="8a9b7-144">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8a9b7-144">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="8a9b7-145">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8a9b7-145">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
