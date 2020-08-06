---
title: query wait サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], timing out
- time [SQL Server], query wait time
- query wait option [SQL Server]
ms.assetid: 0fc4aa01-65a3-4a33-9ef4-caca41add238
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 638afff2aa05a9fc4e61bc71e8610dba1dda8cf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642297"
---
# <a name="configure-the-query-wait-server-configuration-option"></a><span data-ttu-id="84ca3-102">query wait サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="84ca3-102">Configure the query wait Server Configuration Option</span></span>
  <span data-ttu-id="84ca3-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [クエリの待機] [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="84ca3-103">This topic describes how to configure the **query wait** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="84ca3-104">メモリを集中的に使用するクエリ (並べ替えやハッシュ演算に関係するクエリなど) は、そのクエリの実行に使用できるメモリが不足しているとキューに登録されます。</span><span class="sxs-lookup"><span data-stu-id="84ca3-104">Memory-intensive queries (such as those involving sorting and hashing) are queued when there is not enough memory available to run the query.</span></span> <span data-ttu-id="84ca3-105">**[クエリの待機]** オプションは、タイムアウトになるまでのクエリのリソース待ち時間を秒数 (0 ～ 2147483647) で指定します。このオプションの既定値は -1 です。</span><span class="sxs-lookup"><span data-stu-id="84ca3-105">The **query wait** option specifies the time, in seconds (from 0 through 2147483647), that a query waits for resources before it times out. The default value for this option is -1.</span></span> <span data-ttu-id="84ca3-106">このとき、タイムアウトは予測されるクエリ コストの 25 倍になります。</span><span class="sxs-lookup"><span data-stu-id="84ca3-106">This means the time-out is calculated as 25 times the estimated query cost.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="84ca3-107">待機状態のクエリを含むトランザクションでは、クエリがメモリを待機している間、ロック状態が維持されることがあります。</span><span class="sxs-lookup"><span data-stu-id="84ca3-107">A transaction that contains the waiting query might hold locks while the query waits for memory.</span></span> <span data-ttu-id="84ca3-108">まれに、検出できないデッドロックが発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="84ca3-108">In rare situations, it is possible for an undetectable deadlock to occur.</span></span> <span data-ttu-id="84ca3-109">クエリの待機時間を減らすと、このようなデッドロックが発生する可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="84ca3-109">Decreasing the query wait time lowers the probability of such deadlocks.</span></span> <span data-ttu-id="84ca3-110">最終的には、待機状態のクエリが終了し、トランザクション ロックが解放されます。</span><span class="sxs-lookup"><span data-stu-id="84ca3-110">Eventually, a waiting query will be terminated and the transaction locks released.</span></span> <span data-ttu-id="84ca3-111">これに対して、最大待機時間を増やすと、クエリを終了するのに必要な時間も増加することがあります。</span><span class="sxs-lookup"><span data-stu-id="84ca3-111">However, increasing the maximum wait time may increase the amount of time for the query to be terminated.</span></span> <span data-ttu-id="84ca3-112">このオプションを変更することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="84ca3-112">Changes to this option are not recommended.</span></span>  
  
 <span data-ttu-id="84ca3-113">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="84ca3-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="84ca3-114">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="84ca3-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="84ca3-115">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="84ca3-115">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="84ca3-116">Security</span><span class="sxs-lookup"><span data-stu-id="84ca3-116">Security</span></span>](#Security)  
  
-   <span data-ttu-id="84ca3-117">**[クエリの待機] オプションを構成する方法:**</span><span class="sxs-lookup"><span data-stu-id="84ca3-117">**To configure the query wait option, using:**</span></span>  
  
     [<span data-ttu-id="84ca3-118">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="84ca3-118">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="84ca3-119">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="84ca3-119">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="84ca3-120">**補足情報:** [[クエリの待機] オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="84ca3-120">**Follow Up:**  [After you configure the query wait option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="84ca3-121">はじめに</span><span class="sxs-lookup"><span data-stu-id="84ca3-121">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="84ca3-122">推奨事項</span><span class="sxs-lookup"><span data-stu-id="84ca3-122">Recommendations</span></span>  
  
-   <span data-ttu-id="84ca3-123">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="84ca3-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="84ca3-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="84ca3-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="84ca3-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="84ca3-125">Permissions</span></span>  
 <span data-ttu-id="84ca3-126">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="84ca3-126">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="84ca3-127">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="84ca3-127">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="84ca3-128">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="84ca3-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="84ca3-129">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="84ca3-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-query-wait-option"></a><span data-ttu-id="84ca3-130">[クエリの待機] オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="84ca3-130">To configure the query wait option</span></span>  
  
1.  <span data-ttu-id="84ca3-131">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84ca3-131">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="84ca3-132">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="84ca3-132">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="84ca3-133">**[並列処理]** の **[クエリの待機]** オプションに希望の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="84ca3-133">Under **Parallelism**, type the desired value for the **query wait** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="84ca3-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="84ca3-134">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-query-wait-option"></a><span data-ttu-id="84ca3-135">[クエリの待機] オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="84ca3-135">To configure the query wait option</span></span>  
  
1.  <span data-ttu-id="84ca3-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="84ca3-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="84ca3-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84ca3-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="84ca3-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84ca3-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="84ca3-139">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `query wait` オプションの値を `7500` 秒に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84ca3-139">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `query wait` option to `7500` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query wait', 7500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="84ca3-140">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84ca3-140">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-query-wait-option"></a><a name="FollowUp"></a><span data-ttu-id="84ca3-141">補足情報: [クエリの待機] オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="84ca3-141">Follow Up: After you configure the query wait option</span></span>  
 <span data-ttu-id="84ca3-142">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="84ca3-142">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ca3-143">参照</span><span class="sxs-lookup"><span data-stu-id="84ca3-143">See Also</span></span>  
 <span data-ttu-id="84ca3-144">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84ca3-144">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="84ca3-145">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="84ca3-145">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="84ca3-146">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="84ca3-146">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
