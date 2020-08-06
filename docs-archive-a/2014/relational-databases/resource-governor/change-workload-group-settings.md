---
title: ワークロード グループの設定の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], alter
- Resource Governor, workload group alter
ms.assetid: 73b6109c-2ad0-4915-b11b-d40d5a0fdc25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 579aad71d32a629d75f1eecd76e7dacfe32d94f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630885"
---
# <a name="change-workload-group-settings"></a><span data-ttu-id="d0b15-102">ワークロード グループの設定の変更</span><span class="sxs-lookup"><span data-stu-id="d0b15-102">Change Workload Group Settings</span></span>
  <span data-ttu-id="d0b15-103">ワークロード グループの設定を変更するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-103">You can change workload group settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="d0b15-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="d0b15-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="d0b15-105">**ワークロード グループの設定変更に使用するもの:** [SQL Server Management Studio](#ChgWGProp)、[Transact-SQL](#ChgWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="d0b15-105">**To change the settings for a workload group, using:**  [SQL Server Management Studio](#ChgWGProp), [Transact-SQL](#ChgWGTSQL)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="d0b15-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="d0b15-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="d0b15-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d0b15-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="d0b15-108">既定のワークロード グループとユーザー定義のワークロード グループの設定を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="d0b15-108">You can change the settings of the default workload group and user-defined workload groups.</span></span>  
  
 <span data-ttu-id="d0b15-109">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="d0b15-109">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span></span>  
  
 <span data-ttu-id="d0b15-110">非固定パーティション テーブルのインデックス作成によって消費されるメモリは、含まれるパーティションの数に比例します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-110">The memory consumed by index creation on a non-aligned partitioned table is proportional to the number of partitions involved.</span></span> <span data-ttu-id="d0b15-111">必要なメモリの合計が、ワークロード グループの設定によって課せられているクエリごとの制限 (REQUEST_MAX_MEMORY_GRANT_PERCENT) を超えると、インデックス作成の実行に失敗します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-111">If the total required memory exceeds the per-query limit, (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposed by the workload group setting, this index creation may fail.</span></span> <span data-ttu-id="d0b15-112">default ワークロード グループでは、SQL Server 2005 との互換性のために、クエリごとの制限を超えてもクエリの開始に必要な最低限のメモリを使用できるようになっているので、そのようなクエリを実行するのに十分な量のメモリが default リソース プールに対して構成されていれば、同じインデックス作成を default ワークロード グループで実行できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d0b15-112">Because the default workload group allows a query to exceed the per-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.</span></span>  
  
 <span data-ttu-id="d0b15-113">インデックス作成では、パフォーマンスを向上させるため、最初に許可されたメモリ量を超えるメモリ ワークスペースの使用が許可されます。</span><span class="sxs-lookup"><span data-stu-id="d0b15-113">Index creation is allowed to use more memory workspace than initially granted for performance.</span></span> <span data-ttu-id="d0b15-114">この特別な処理はリソース ガバナーでサポートされていますが、最初のメモリ許可も追加のメモリ許可も、ワークロード グループ設定およびリソース プール設定によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="d0b15-114">This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d0b15-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="d0b15-115">Permissions</span></span>  
 <span data-ttu-id="d0b15-116">ワークロード グループの設定を変更するには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d0b15-116">Changing workload group settings requires CONTROL SERVER permission.</span></span>  
  
##  <a name="change-workload-group-settings-using-sql-server-management-studio"></a><a name="ChgWGProp"></a> <span data-ttu-id="d0b15-117">SQL Server Management Studio を使用してワークロード グループの設定を変更する</span><span class="sxs-lookup"><span data-stu-id="d0b15-117">Change Workload Group Settings Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d0b15-118">**ワークロード グループの設定を変更するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="d0b15-118">**To change workload group settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="d0b15-119">オブジェクト エクスプローラーで、変更するワークロード グループを含む **ワークロード グループ** フォルダーまで **[管理]** ノードを再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-119">In Object Explorer, recursively expand the **Management** node down to and including the **Workload Groups** folder that contains the workload group to be modified.</span></span>  
  
2.  <span data-ttu-id="d0b15-120">変更するワークロード グループを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0b15-120">Right-click the workload group to be modified, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d0b15-121">**[リソース ガバナーのプロパティ]** ページで、自動的に **[リソース プールのワークロード グループ]** グリッドの対象ワークロード グループの行が選択されない場合は、その行を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-121">In the **Resource Governor Properties** page, select the row for the workload group in the **Workload groups for resource pool** grid if it is not automatically selected.</span></span>  
  
4.  <span data-ttu-id="d0b15-122">変更する行のセルをクリックまたはダブルクリックし、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-122">Click or double-click the cells in the row to be changed, and enter the new values.</span></span>  
  
5.  <span data-ttu-id="d0b15-123">変更を保存するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0b15-123">To save the changes, click **OK**</span></span>  
  
##  <a name="change-workload-group-settings-using-transact-sql"></a><a name="ChgWGTSQL"></a> <span data-ttu-id="d0b15-124">Transact-SQL を使用してワークロード グループの設定を変更する</span><span class="sxs-lookup"><span data-stu-id="d0b15-124">Change Workload Group Settings Using Transact-SQL</span></span>  
 <span data-ttu-id="d0b15-125">**Transact-SQL を使用してワークロード グループの設定を変更するには**</span><span class="sxs-lookup"><span data-stu-id="d0b15-125">**To change workload group settings by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="d0b15-126">変更するプロパティ値を指定する ALTER WORKLOAD GROUP ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-126">Run the ALTER WORKLOAD GROUP statement specifying the property values to be changed.</span></span>  
  
2.  <span data-ttu-id="d0b15-127">ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-127">Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="d0b15-128">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d0b15-128">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="d0b15-129">次の例では、 `groupAdhoc`という名前のワークロード グループに割り当てられたメモリ許可の割合の最大値を変更します。</span><span class="sxs-lookup"><span data-stu-id="d0b15-129">The following example changes the max memory grant percent setting for the workload group named `groupAdhoc`.</span></span>  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
WITH (REQUEST_MAX_MEMORY_GRANT_PERCENT = 30);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0b15-130">参照</span><span class="sxs-lookup"><span data-stu-id="d0b15-130">See Also</span></span>  
 <span data-ttu-id="d0b15-131">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="d0b15-131">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="d0b15-132">[ワークロード グループの作成](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="d0b15-132">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="d0b15-133">[リソース プールの作成](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="d0b15-133">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="d0b15-134">[リソース プールの設定の変更](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="d0b15-134">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="d0b15-135">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0b15-135">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="d0b15-136">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0b15-136">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="d0b15-137">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0b15-137">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
