---
title: コレクション セットの開始または停止 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e37d4b2edcd7a6e048c405b072bcbf9b1fef78c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643983"
---
# <a name="start-or-stop-a-collection-set"></a><span data-ttu-id="61663-102">コレクション セットの開始または停止</span><span class="sxs-lookup"><span data-stu-id="61663-102">Start or Stop a Collection Set</span></span>
  <span data-ttu-id="61663-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でコレクション セットを開始または停止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="61663-103">This topic describes how to start or stop a collection set in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="61663-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="61663-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="61663-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="61663-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="61663-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="61663-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="61663-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="61663-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="61663-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="61663-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="61663-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="61663-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="61663-110">**コレクション セットを開始または停止する方法:**</span><span class="sxs-lookup"><span data-stu-id="61663-110">**To start or stop a collection set, using:**</span></span>  
  
     [<span data-ttu-id="61663-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61663-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="61663-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="61663-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="61663-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="61663-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="61663-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="61663-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="61663-115">データ コレクターのストアド プロシージャとカタログ ビューは、 **msdb** データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="61663-115">Data Collector stored procedures and catalog views are stored in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="61663-116">通常のストアド プロシージャとは異なり、データ コレクターで使用するストアド プロシージャではパラメーターのデータ型が厳密に定義されており、データ型の自動変換はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="61663-116">Unlike regular stored procedures, the parameters for data collector stored procedures are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="61663-117">これらのパラメーターが、引数の説明で指定されている正しいデータ型で呼び出されないと、このストアド プロシージャではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="61663-117">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="61663-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="61663-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="61663-119">SQL Server エージェントが開始されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="61663-119">SQL Server Agent must be started.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="61663-120">推奨事項</span><span class="sxs-lookup"><span data-stu-id="61663-120">Recommendations</span></span>  
  
-   <span data-ttu-id="61663-121">コレクション セットに関する情報を取得するには、 [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) カタログ ビューのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="61663-121">To obtain information about collection sets, query the [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) catalog view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="61663-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="61663-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="61663-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="61663-123">Permissions</span></span>  
 <span data-ttu-id="61663-124">**dc_operator** 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="61663-124">Requires membership in the **dc_operator** fixed database role.</span></span> <span data-ttu-id="61663-125">コレクション セットにプロキシ アカウントがない場合は、 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="61663-125">If the collection set does not have a proxy account, membership in the **sysadmin** fixed server role is required.Examples</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="61663-126">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="61663-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-start-a-collection-set"></a><span data-ttu-id="61663-127">コレクション セットを開始するには</span><span class="sxs-lookup"><span data-stu-id="61663-127">To start a collection set</span></span>  
  
1.  <span data-ttu-id="61663-128">オブジェクト エクスプローラーで、 **[管理]** ノード、 **[データ コレクション]** 、 **[システム データ コレクション セット]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="61663-128">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="61663-129">開始するコレクション セットを右クリックして **[データ コレクション セットの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61663-129">Right-click the collection set that you want to start, and then click **Start Data Collection Set**.</span></span>  
  
     <span data-ttu-id="61663-130">メッセージ ボックスにはこのアクションの結果が表示され、コレクション セットのアイコンに緑色の矢印が付いている場合は、コレクション セットが開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="61663-130">A message box displays the results of this action, and a green arrow on the icon for the collection set indicates that the collection set has started.</span></span>  
  
#### <a name="to-stop-a-collection-set"></a><span data-ttu-id="61663-131">コレクション セットを停止するには</span><span class="sxs-lookup"><span data-stu-id="61663-131">To stop a collection set</span></span>  
  
1.  <span data-ttu-id="61663-132">オブジェクト エクスプローラーで、 **[管理]** ノード、 **[データ コレクション]** 、 **[システム データ コレクション セット]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="61663-132">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="61663-133">停止するコレクション セットを右クリックして **[データ コレクション セットの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61663-133">Right-click the collection set that you want to stop, and then click **Stop Data Collection Set**.</span></span>  
  
     <span data-ttu-id="61663-134">メッセージ ボックスにはこのアクションの結果が表示され、コレクション セットのアイコンに赤い丸が付いている場合は、コレクション セットが停止していることを示します。</span><span class="sxs-lookup"><span data-stu-id="61663-134">A message box displays the results of this action, and a red circle on the icon for the collection set indicates that the collection set has stopped.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="61663-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="61663-135">Using Transact-SQL</span></span>  
  
#### <a name="to-start-a-collection-set"></a><span data-ttu-id="61663-136">コレクション セットを開始するには</span><span class="sxs-lookup"><span data-stu-id="61663-136">To start a collection set</span></span>  
  
1.  <span data-ttu-id="61663-137">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="61663-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="61663-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61663-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="61663-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61663-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="61663-140">この例では、 [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) を使用して、ID が `1`であるコレクション セットを開始します。</span><span class="sxs-lookup"><span data-stu-id="61663-140">This example uses [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) to start the collection set that has the ID of `1`.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a><span data-ttu-id="61663-141">コレクション セットを停止するには</span><span class="sxs-lookup"><span data-stu-id="61663-141">To stop a collection set</span></span>  
  
1.  <span data-ttu-id="61663-142">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="61663-142">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="61663-143">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61663-143">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="61663-144">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61663-144">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="61663-145">この例では、 [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) を使用して、ID が `1`であるコレクション セットを停止します。</span><span class="sxs-lookup"><span data-stu-id="61663-145">This example uses [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) to stop the collection set that has the ID of `1`.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="61663-146">参照</span><span class="sxs-lookup"><span data-stu-id="61663-146">See Also</span></span>  
 <span data-ttu-id="61663-147">[データ コレクターのビュー &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="61663-147">[Data Collector Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql) </span></span>  
 <span data-ttu-id="61663-148">[[データ コレクション]](data-collection.md)</span><span class="sxs-lookup"><span data-stu-id="61663-148">[Data Collection](data-collection.md)</span></span>  
  
  
