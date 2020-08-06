---
title: max text repl size サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- max text repl size option
ms.assetid: 3056cf64-621d-4996-9162-3913f6bc6d5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af0cf426583ee328f0a484de1c3539836c0d8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642305"
---
# <a name="configure-the-max-text-repl-size-server-configuration-option"></a><span data-ttu-id="743c7-102">max text repl size サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="743c7-102">Configure the max text repl size Server Configuration Option</span></span>
  <span data-ttu-id="743c7-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] max text repl size [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="743c7-103">This topic describes how to configure the **max text repl size** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="743c7-104">**Max text repl size**オプションは、 `text` 単一の `ntext` `varchar(max)` `nvarchar(max)` `varbinary(max)` `xml` `image` INSERT、UPDATE、WRITETEXT、または UPDATETEXT ステートメントで、レプリケートされた列またはキャプチャ対象列に追加できる、、、、、、、およびの各データの最大サイズ (バイト単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="743c7-104">The **max text repl size** option specifies the maximum size (in bytes) of `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, `xml`, and `image` data that can be added to a replicated column or captured column in a single INSERT, UPDATE, WRITETEXT, or UPDATETEXT statement.</span></span> <span data-ttu-id="743c7-105">既定値は 65536 バイトです。</span><span class="sxs-lookup"><span data-stu-id="743c7-105">The default value is 65536 bytes.</span></span> <span data-ttu-id="743c7-106">値 -1 は、データ型で許容されるサイズの範囲内であれば、サイズ制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="743c7-106">A value of -1 indicates that there is no size limit, other than the limit imposed by the data type.</span></span>  
  
 <span data-ttu-id="743c7-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="743c7-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="743c7-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="743c7-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="743c7-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="743c7-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="743c7-110">Security</span><span class="sxs-lookup"><span data-stu-id="743c7-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="743c7-111">**以下を使用して max text repl size オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="743c7-111">**To configure the max text repl size option, using:**</span></span>  
  
     [<span data-ttu-id="743c7-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="743c7-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="743c7-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="743c7-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="743c7-114">**補足情報:** [max text repl size オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="743c7-114">**Follow Up:**  [After you configure the max text repl size option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="743c7-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="743c7-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="743c7-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="743c7-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="743c7-117">このオプションは、トランザクション レプリケーションと変更データ キャプチャに適用されます。</span><span class="sxs-lookup"><span data-stu-id="743c7-117">This option applies to transactional replication and Change Data Capture.</span></span> <span data-ttu-id="743c7-118">サーバーでトランザクション レプリケーションと変更データ キャプチャの両方が構成されている場合、指定された値が両方の機能に適用されます。</span><span class="sxs-lookup"><span data-stu-id="743c7-118">When a server is configured for both transactional replication and Change Data Capture, the specified value applies to both features.</span></span> <span data-ttu-id="743c7-119">スナップショット レプリケーションおよびマージ レプリケーションでは、このオプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="743c7-119">This option is ignored by snapshot replication and merge replication.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="743c7-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="743c7-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="743c7-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="743c7-121">Permissions</span></span>  
 <span data-ttu-id="743c7-122">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="743c7-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="743c7-123">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="743c7-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="743c7-124">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="743c7-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="743c7-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="743c7-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a><span data-ttu-id="743c7-126">max text repl size オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="743c7-126">To configure the max text repl size option</span></span>  
  
1.  <span data-ttu-id="743c7-127">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="743c7-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="743c7-128">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="743c7-128">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="743c7-129">**[その他]** の **[テキスト レプリケーションの最大サイズ]** オプションを目的の値に変更します。</span><span class="sxs-lookup"><span data-stu-id="743c7-129">Under **Miscellaneous**, change the **Max Text Replication Size** option to the desired value.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="743c7-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="743c7-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a><span data-ttu-id="743c7-131">max text repl size オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="743c7-131">To configure the max text repl size option</span></span>  
  
1.  <span data-ttu-id="743c7-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="743c7-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="743c7-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="743c7-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="743c7-134">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="743c7-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="743c7-135">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `max text repl size` オプションを `-1`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="743c7-135">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max text repl size` option to `-1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;   
RECONFIGURE ;   
GO  
EXEC sp_configure 'max text repl size', -1 ;   
GO  
RECONFIGURE;   
GO  
  
```  
  
 <span data-ttu-id="743c7-136">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="743c7-136">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-text-repl-size-option"></a><a name="FollowUp"></a><span data-ttu-id="743c7-137">補足情報: max text repl size オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="743c7-137">Follow Up: After you configure the max text repl size option</span></span>  
 <span data-ttu-id="743c7-138">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="743c7-138">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743c7-139">参照</span><span class="sxs-lookup"><span data-stu-id="743c7-139">See Also</span></span>  
 <span data-ttu-id="743c7-140">[SQL Server のレプリケーション](../../relational-databases/replication/sql-server-replication.md) </span><span class="sxs-lookup"><span data-stu-id="743c7-140">[SQL Server Replication](../../relational-databases/replication/sql-server-replication.md) </span></span>  
 <span data-ttu-id="743c7-141">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="743c7-141">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="743c7-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="743c7-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="743c7-143">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="743c7-143">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="743c7-144">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="743c7-144">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="743c7-145">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="743c7-145">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span></span>  
 <span data-ttu-id="743c7-146">[UPDATETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="743c7-146">[UPDATETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql) </span></span>  
 [<span data-ttu-id="743c7-147">WRITETEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="743c7-147">WRITETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/writetext-transact-sql)  
  
  
