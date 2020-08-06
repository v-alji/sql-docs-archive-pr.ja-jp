---
title: cursor threshold サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cursor threshold option
ms.assetid: 189f2067-c6c4-48bd-9bd9-65f6b2021c12
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0d7fd9ecafda270a02f1fba9f5dd74adc9e299d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645852"
---
# <a name="configure-the-cursor-threshold-server-configuration-option"></a><span data-ttu-id="90b40-102">cursor threshold サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="90b40-102">Configure the cursor threshold Server Configuration Option</span></span>
  <span data-ttu-id="90b40-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] cursor threshold [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90b40-103">This topic describes how to configure the **cursor threshold** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="90b40-104">**cursor threshold** オプションは、カーソル キーセットが非同期に生成されるカーソル セット内の行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="90b40-104">The **cursor threshold** option specifies the number of rows in the cursor set at which cursor keysets are generated asynchronously.</span></span> <span data-ttu-id="90b40-105">カーソルが結果セットのキーセットを生成するとき、その結果セットに返される行数をクエリ オプティマイザーが予測します。</span><span class="sxs-lookup"><span data-stu-id="90b40-105">When cursors generate a keyset for a result set, the query optimizer estimates the number of rows that will be returned for that result set.</span></span> <span data-ttu-id="90b40-106">返される行数がこのしきい値を超えていると予測された場合、カーソルは非同期に生成されます。これにより、ユーザーはカーソルの作成が続行されている間に行を取り出すことができます。</span><span class="sxs-lookup"><span data-stu-id="90b40-106">If the query optimizer estimates that the number of returned rows is greater than this threshold, the cursor is generated asynchronously, allowing the user to fetch rows from the cursor while the cursor continues to be populated.</span></span> <span data-ttu-id="90b40-107">返される行数がこのしきい値以下と予測された場合、カーソルは同期をとって生成され、すべての行が返されるまでクエリが待機します。</span><span class="sxs-lookup"><span data-stu-id="90b40-107">Otherwise, the cursor is generated synchronously, and the query waits until all rows are returned.</span></span>  
  
 <span data-ttu-id="90b40-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="90b40-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="90b40-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="90b40-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="90b40-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="90b40-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="90b40-111">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="90b40-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="90b40-112">Security</span><span class="sxs-lookup"><span data-stu-id="90b40-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="90b40-113">**以下を使用して cursor threshold オプションを構成するには**</span><span class="sxs-lookup"><span data-stu-id="90b40-113">**To configure the cursor threshold option, using:**</span></span>  
  
     [<span data-ttu-id="90b40-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="90b40-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="90b40-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="90b40-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="90b40-116">**補足情報:** [cursor threshold オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="90b40-116">**Follow Up:**  [After you configure the cursor threshold option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="90b40-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="90b40-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="90b40-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="90b40-118">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90b40-119">では、キーセット ドリブン カーソルまたは静的 [!INCLUDE[tsql](../../includes/tsql-md.md)] カーソルの非同期な作成はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="90b40-119">does not support generating keyset-driven or static [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors asynchronously.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="90b40-120">カーソル操作はバッチで行われます。したがって、 [!INCLUDE[tsql](../../includes/tsql-md.md)] カーソルを非同期に生成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="90b40-120">cursor operations such as OPEN or FETCH are batched, so there is no need for the asynchronous generation of [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90b40-121">各カーソル操作におけるクライアントのラウンド トリップのため、待機時間が少ない OPEN が問題になるような非同期キーセット ドリブン カーソルまたは静的 API (アプリケーション プログラミング インターフェイス) サーバー カーソルは、 で引き続きサポートされます。</span><span class="sxs-lookup"><span data-stu-id="90b40-121">continues to support asynchronous keyset-driven or static application programming interface (API) server cursors where low latency OPEN is a concern, due to client round trips for each cursor operation.</span></span>  
  
-   <span data-ttu-id="90b40-122">キーセットの行数を予測するクエリ オプティマイザーの精度は、カーソル内の各テーブルの統計の新しさによって左右されます。</span><span class="sxs-lookup"><span data-stu-id="90b40-122">The accuracy of the query optimizer to determine an estimate for the number of rows in a keyset depends on the currency of the statistics for each of the tables in the cursor.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="90b40-123">推奨事項</span><span class="sxs-lookup"><span data-stu-id="90b40-123">Recommendations</span></span>  
  
-   <span data-ttu-id="90b40-124">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="90b40-124">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="90b40-125">**cursor threshold** を -1 に設定すると、すべてのキーセットが同期して生成されます。これはカーソル セットが小さい場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="90b40-125">If you set **cursor threshold** to -1, all keysets are generated synchronously, which benefits small cursor sets.</span></span> <span data-ttu-id="90b40-126">**cursor threshold** を 0 に設定すると、すべてのカーソル キーセットが非同期に生成されます。</span><span class="sxs-lookup"><span data-stu-id="90b40-126">If you set **cursor threshold** to 0, all cursor keysets are generated asynchronously.</span></span> <span data-ttu-id="90b40-127">それ以外の値を設定した場合、クエリ オプティマイザーによってカーソル セットの予測行数が比較され、 **cursor threshold**に設定した値を超えていれば、キーセットが非同期に生成されます。</span><span class="sxs-lookup"><span data-stu-id="90b40-127">With other values, the query optimizer compares the number of expected rows in the cursor set and builds the keyset asynchronously if it exceeds the number set in **cursor threshold**.</span></span> <span data-ttu-id="90b40-128">小さな結果セットは同期をとって作成する方がよいので、 **cursor threshold** の値は小さくしすぎないでください。</span><span class="sxs-lookup"><span data-stu-id="90b40-128">Do not set **cursor threshold** too low, because small result sets are better built synchronously.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="90b40-129">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="90b40-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="90b40-130">Permissions</span><span class="sxs-lookup"><span data-stu-id="90b40-130">Permissions</span></span>  
 <span data-ttu-id="90b40-131">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="90b40-131">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="90b40-132">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b40-132">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="90b40-133">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="90b40-133">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="90b40-134">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="90b40-134">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-cursor-threshold-option"></a><span data-ttu-id="90b40-135">cursor threshold オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="90b40-135">To configure the cursor threshold option</span></span>  
  
1.  <span data-ttu-id="90b40-136">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90b40-136">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="90b40-137">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="90b40-137">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="90b40-138">**[その他]** の **[カーソルのしきい値]** オプションを目的の値に変更します。</span><span class="sxs-lookup"><span data-stu-id="90b40-138">Under **Miscellaneous**, change the **Cursor Threshold** option to the value you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="90b40-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="90b40-139">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-cursor-threshold-option"></a><span data-ttu-id="90b40-140">cursor threshold オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="90b40-140">To configure the cursor threshold option</span></span>  
  
1.  <span data-ttu-id="90b40-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="90b40-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="90b40-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90b40-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="90b40-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90b40-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="90b40-144">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `cursor threshold` オプションを `0` に設定して、カーソル キーセットを非同期に生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90b40-144">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the `cursor threshold` option to `0` so that cursor keysets are generated asynchronously.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cursor threshold', 0 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="90b40-145">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90b40-145">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-cursor-threshold-option"></a><a name="FollowUp"></a><span data-ttu-id="90b40-146">補足情報: cursor threshold オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="90b40-146">Follow Up: After you configure the cursor threshold option</span></span>  
 <span data-ttu-id="90b40-147">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="90b40-147">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b40-148">参照</span><span class="sxs-lookup"><span data-stu-id="90b40-148">See Also</span></span>  
 <span data-ttu-id="90b40-149">[@@CURSOR_ROWS &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-rows-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90b40-149">[@@CURSOR_ROWS &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-rows-transact-sql) </span></span>  
 <span data-ttu-id="90b40-150">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90b40-150">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="90b40-151">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="90b40-151">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="90b40-152">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90b40-152">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="90b40-153">UPDATE STATISTICS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90b40-153">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
