---
title: min memory per query サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 56d85f36840f0900c8b5e986334a99ba610d3930
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642300"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a><span data-ttu-id="f3370-102">min memory per query サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="f3370-102">Configure the min memory per query Server Configuration Option</span></span>
  <span data-ttu-id="f3370-103">このトピック `min memory per query` で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、のサーバー構成オプションを構成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f3370-103">This topic describes how to configure the `min memory per query` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f3370-104">オプションは、 `min memory per query` クエリの実行用に割り当てられるメモリの最小量 (kb 単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3370-104">The `min memory per query` option specifies the minimum amount of memory (in kilobytes) that will be allocated for the execution of a query.</span></span> <span data-ttu-id="f3370-105">たとえば、 `min memory per query` が 2048 KB に設定されている場合、クエリは少なくともそのメモリ全体を取得することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="f3370-105">For example, if `min memory per query` is set to 2,048 KB, the query is guaranteed to get at least that much total memory.</span></span> <span data-ttu-id="f3370-106">既定値は 1,024 KB です。</span><span class="sxs-lookup"><span data-stu-id="f3370-106">The default value is 1,024 KB.</span></span> <span data-ttu-id="f3370-107">最小値は 512 KB、最大値は 2,147,483,647 KB (2 GB) です。</span><span class="sxs-lookup"><span data-stu-id="f3370-107">The minimum value 512 KB, and the maximum is 2,147,483,647 KB (2 GB).</span></span>  
  
 <span data-ttu-id="f3370-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f3370-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f3370-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f3370-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f3370-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f3370-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f3370-111">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="f3370-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f3370-112">Security</span><span class="sxs-lookup"><span data-stu-id="f3370-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f3370-113">**以下を使用して min memory per query オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="f3370-113">**To configure the min memory per query option, using:**</span></span>  
  
     [<span data-ttu-id="f3370-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f3370-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f3370-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f3370-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="f3370-116">**補足情報:** [min memory per query オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f3370-116">**Follow Up:**  [After you configure the min memory per query option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f3370-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="f3370-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f3370-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f3370-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f3370-119">Min memory per query オプションの値は、 [index create Memory オプション](configure-the-index-create-memory-server-configuration-option.md)よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="f3370-119">The amount of min memory per query has precedence over the [index create memory Option](configure-the-index-create-memory-server-configuration-option.md).</span></span> <span data-ttu-id="f3370-120">両方のオプションを変更し、index create memory の設定値を min memory per query より小さくした場合は、警告メッセージが表示されます。ただし、値はそのまま設定されます。</span><span class="sxs-lookup"><span data-stu-id="f3370-120">If you modify both options and the index create memory is less than min memory per query, you receive a warning message, but the value is set.</span></span> <span data-ttu-id="f3370-121">クエリ実行中にも同様の警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3370-121">During query execution you receive another similar warning.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f3370-122">推奨事項</span><span class="sxs-lookup"><span data-stu-id="f3370-122">Recommendations</span></span>  
  
-   <span data-ttu-id="f3370-123">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="f3370-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="f3370-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ プロセッサは、クエリに割り当てる最適なメモリの量を決定しようとします。</span><span class="sxs-lookup"><span data-stu-id="f3370-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query processor tries to determine the optimal amount of memory to allocate to a query.</span></span> <span data-ttu-id="f3370-125">min memory per query オプションを使用すると、管理者は、どの単一のクエリにも割り当てられるメモリ量の最小値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f3370-125">The min memory per query option lets the administrator specify the minimum amount of memory any single query receives.</span></span> <span data-ttu-id="f3370-126">通常、クエリが大量のデータに対してハッシュおよび並べ替え操作を行う場合は、min memory per query オプションの設定よりも多くメモリがクエリに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f3370-126">Queries generally receive more memory than this if they have hash and sort operations on a large volume of data.</span></span> <span data-ttu-id="f3370-127">min memory per query の値を増やすと、小規模から中規模のクエリではパフォーマンスが向上する可能性があります。ただし、この値の増加によって、メモリ リソースでの競合も増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f3370-127">Increasing the value of min memory per query may improve performance for some small to medium-sized queries, but doing so could lead to increased competition for memory resources.</span></span> <span data-ttu-id="f3370-128">min memory per query オプションには、並べ替え用に割り当てられるメモリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f3370-128">The min memory per query option includes memory allocated for sorting.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f3370-129">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f3370-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f3370-130">Permissions</span><span class="sxs-lookup"><span data-stu-id="f3370-130">Permissions</span></span>  
 <span data-ttu-id="f3370-131">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="f3370-131">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="f3370-132">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3370-132">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="f3370-133">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="f3370-133">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f3370-134">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f3370-134">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a><span data-ttu-id="f3370-135">min memory per query オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="f3370-135">To configure the min memory per query option</span></span>  
  
1.  <span data-ttu-id="f3370-136">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3370-136">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f3370-137">**[メモリ]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3370-137">Click the **Memory** node.</span></span>  
  
3.  <span data-ttu-id="f3370-138">**[クエリごとに使用する最小メモリ (KB 単位)]** ボックスで、クエリの実行用に割り当てる最小メモリ容量 (KB 単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3370-138">In the **Minimum memory per query** box, enter the minimum amount of memory (in kilobytes) that will be allocated for the execution of a query.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f3370-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f3370-139">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a><span data-ttu-id="f3370-140">min memory per query オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="f3370-140">To configure the min memory per query option</span></span>  
  
1.  <span data-ttu-id="f3370-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="f3370-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f3370-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3370-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f3370-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3370-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f3370-144">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `min memory per query` オプションの値を `3500` KB に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f3370-144">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `min memory per query` option to `3500` KB.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-min-memory-per-query-option"></a><a name="FollowUp"></a><span data-ttu-id="f3370-145">補足情報: min memory per query オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="f3370-145">Follow Up: After you configure the min memory per query option</span></span>  
 <span data-ttu-id="f3370-146">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="f3370-146">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3370-147">参照</span><span class="sxs-lookup"><span data-stu-id="f3370-147">See Also</span></span>  
 <span data-ttu-id="f3370-148">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f3370-148">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="f3370-149">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f3370-149">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="f3370-150">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f3370-150">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="f3370-151">index create memory サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="f3370-151">Configure the index create memory Server Configuration Option</span></span>](configure-the-index-create-memory-server-configuration-option.md)  
  
  
