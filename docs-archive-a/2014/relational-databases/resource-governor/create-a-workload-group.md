---
title: ワークロード グループの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group create
- workload groups [SQL Server], create
ms.assetid: 072868ec-ceff-4db6-941b-281af731a067
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 144bcef57b3d6e191b03b1539e9e7382a9085c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639435"
---
# <a name="create-a-workload-group"></a><span data-ttu-id="221ab-102">ワークロード グループの作成</span><span class="sxs-lookup"><span data-stu-id="221ab-102">Create a Workload Group</span></span>
  <span data-ttu-id="221ab-103">ワークロード グループを作成するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="221ab-103">You can create a workload group by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="221ab-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="221ab-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="221ab-105">**ワークロード グループの作成に使用するもの:** [SQL Server Management Studio](#CreWGProp)、[Transact-SQL](#CreWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="221ab-105">**To create a workload group, using:**  [SQL Server Management Studio](#CreWGProp), [Transact-SQL](#CreWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="221ab-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="221ab-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="221ab-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="221ab-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="221ab-108">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="221ab-108">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span></span>  
  
 <span data-ttu-id="221ab-109">非固定パーティション テーブルのインデックス作成によって消費されるメモリは、含まれるパーティションの数に比例します。</span><span class="sxs-lookup"><span data-stu-id="221ab-109">The memory consumed by index creation on a non-aligned partitioned table is proportional to the number of partitions involved.</span></span> <span data-ttu-id="221ab-110">必要なメモリの合計が、ワークロード グループの設定によって課せられているクエリごとの制限 (REQUEST_MAX_MEMORY_GRANT_PERCENT) を超えると、インデックス作成の実行に失敗します。</span><span class="sxs-lookup"><span data-stu-id="221ab-110">If the total required memory exceeds the per-query limit, (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposed by the workload group setting, this index creation may fail.</span></span> <span data-ttu-id="221ab-111">default ワークロード グループでは、SQL Server 2005 との互換性のために、クエリごとの制限を超えてもクエリの開始に必要な最低限のメモリを使用できるようになっているので、そのようなクエリを実行するのに十分な量のメモリが default リソース プールに対して構成されていれば、同じインデックス作成を default ワークロード グループで実行できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="221ab-111">Because the default workload group allows a query to exceed the per-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.</span></span>  
  
 <span data-ttu-id="221ab-112">インデックス作成では、パフォーマンスを向上させるため、最初に許可されたメモリ量を超えるメモリ ワークスペースの使用が許可されます。</span><span class="sxs-lookup"><span data-stu-id="221ab-112">Index creation is allowed to use more memory workspace than initially granted for performance.</span></span> <span data-ttu-id="221ab-113">この特別な処理はリソース ガバナーでサポートされていますが、最初のメモリ許可も追加のメモリ許可も、ワークロード グループ設定およびリソース プール設定によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="221ab-113">This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="221ab-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="221ab-114">Permissions</span></span>  
 <span data-ttu-id="221ab-115">ワークロード グループを作成するには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="221ab-115">Creating a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="create-a-workload-group-using-sql-server-management-studio"></a><a name="CreWGProp"></a> <span data-ttu-id="221ab-116">SQL Server Management Studio を使用してワークロード グループを作成する</span><span class="sxs-lookup"><span data-stu-id="221ab-116">Create a Workload Group Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="221ab-117">**ワークロード グループを作成するには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="221ab-117">**To create a workload group by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="221ab-118">オブジェクト エクスプローラーで、変更するワークロード グループを含むリソース プールまで **[管理]** ノードを再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="221ab-118">In Object Explorer, recursively expand the **Management** node down to and including the resource pool that contains the workload group to be modified.</span></span>  
  
2.  <span data-ttu-id="221ab-119">**[ワークロード グループ]** フォルダーを右クリックし、 **[新しいワークロード グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="221ab-119">Right-click the **Workload Groups** folder, and then click **New Workload Group**.</span></span>  
  
3.  <span data-ttu-id="221ab-120">**[リソース プール]** グリッドに、ワークロード グループを追加するリソース プールが強調表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="221ab-120">In the **Resource pools** grid, ensure the resource pool where you want to add the workload group is highlighted.</span></span>  
  
4.  <span data-ttu-id="221ab-121">**[リソース プールのワークロード グループ]** グリッドに新規行が追加され、他の列には空の名前と既定値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="221ab-121">The **Workload groups for resource pool** grid will have a new line with a blank name and default values in the other columns.</span></span>  
  
5.  <span data-ttu-id="221ab-122">**[名前]** セルをクリックし、ワークロード グループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="221ab-122">Click the **Name** cell and enter a name for the workload group.</span></span>  
  
6.  <span data-ttu-id="221ab-123">既定値から変更する場合は、その対象となる行の他のセルをクリックまたはダブルクリックし、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="221ab-123">Click or double-click any other cells in the row you want to change from their default settings, and enter the new values.</span></span>  
  
7.  <span data-ttu-id="221ab-124">変更を保存するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="221ab-124">To save the changes, click **OK**</span></span>  
  
##  <a name="create-a-workload-group-using-transact-sql"></a><a name="CreWGTSQL"></a> <span data-ttu-id="221ab-125">Transact-SQL を使用してワークロード グループを作成する</span><span class="sxs-lookup"><span data-stu-id="221ab-125">Create a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="221ab-126">**ワークロード グループを作成するには [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="221ab-126">**To create a workload group by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="221ab-127">設定するプロパティ値を指定する CREATE WORKLOAD GROUP ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="221ab-127">Run the CREATE WORKLOAD GROUP statement specifying the property values to be set.</span></span>  
  
2.  <span data-ttu-id="221ab-128">ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="221ab-128">Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="221ab-129">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="221ab-129">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="221ab-130">次の例では、 `groupAdhoc` という名前のリソース プール内に `poolAdhoc`という名前のワークロード グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="221ab-130">The following example creates a workload group named `groupAdhoc` in the resource pool named `poolAdhoc`.</span></span>  
  
```  
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="221ab-131">参照</span><span class="sxs-lookup"><span data-stu-id="221ab-131">See Also</span></span>  
 <span data-ttu-id="221ab-132">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="221ab-132">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="221ab-133">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="221ab-133">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="221ab-134">[リソース プールの作成](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="221ab-134">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="221ab-135">[ワークロード グループの設定の変更](change-workload-group-settings.md) </span><span class="sxs-lookup"><span data-stu-id="221ab-135">[Change Workload Group Settings](change-workload-group-settings.md) </span></span>  
 <span data-ttu-id="221ab-136">[ユーザー定義の分類子関数の作成とテスト](create-and-test-a-classifier-user-defined-function.md) </span><span class="sxs-lookup"><span data-stu-id="221ab-136">[Create and Test a Classifier User-Defined Function](create-and-test-a-classifier-user-defined-function.md) </span></span>  
 <span data-ttu-id="221ab-137">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="221ab-137">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 [<span data-ttu-id="221ab-138">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="221ab-138">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
