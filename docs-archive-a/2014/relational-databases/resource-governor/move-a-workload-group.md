---
title: ワークロード グループの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties_moveworkloadgroup.f1
helpviewer_keywords:
- workload groups [SQL Server], move
- Resource Governor, workload group move
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f73b48f0ec2255760b4ee55acfaf91dc02af7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715149"
---
# <a name="move-a-workload-group"></a><span data-ttu-id="cf369-102">ワークロード グループの移動</span><span class="sxs-lookup"><span data-stu-id="cf369-102">Move a Workload Group</span></span>
  <span data-ttu-id="cf369-103">リソース ガバナーのワークロード グループを別のリソース プールに移動するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。</span><span class="sxs-lookup"><span data-stu-id="cf369-103">You can move a Resource Governor workload group to a different resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="cf369-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="cf369-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="cf369-105">**ワークロード グループの移動に使用するもの:** [SQL Server Management Studio](#MoveWGSSMS)、[Transact-SQL](#MoveWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="cf369-105">**To move a workload group, using:**  [SQL Server Management Studio](#MoveWGSSMS), [Transact-SQL](#MoveWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cf369-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="cf369-106">Before You Begin</span></span>  
 <span data-ttu-id="cf369-107">リソース ガバナーの保留中の構成操作がある場合、ワークロード グループを移動できません。</span><span class="sxs-lookup"><span data-stu-id="cf369-107">You cannot move a workload group if there is a pending Resource Governor configuration operation.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="cf369-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="cf369-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="cf369-109">リソース ガバナーの保留中の構成操作がある場合、ワークロード グループを移動できません。</span><span class="sxs-lookup"><span data-stu-id="cf369-109">You cannot move a workload group if there is a pending Resource Governor configuration operation.</span></span> <span data-ttu-id="cf369-110">[sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 動的管理ビューにクエリを実行して is_configuration_pending の現在の状態を取得することにより、構成が保留中かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="cf369-110">You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) dynamic management view to get the current status of is_configuration_pending.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cf369-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="cf369-111">Permissions</span></span>  
 <span data-ttu-id="cf369-112">ワークロード グループを移動するには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cf369-112">Moving a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="move-a-workload-group-using-sql-server-management-studio"></a><a name="MoveWGSSMS"></a> <span data-ttu-id="cf369-113">SQL Server Management Studio を使用してワークロード グループを移動する</span><span class="sxs-lookup"><span data-stu-id="cf369-113">Move a Workload Group Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cf369-114">**を使用してワークロード グループを移動するには [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="cf369-114">**To move a workload group by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**</span></span>  
  
1.  <span data-ttu-id="cf369-115">オブジェクト エクスプローラーで、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="cf369-115">In Object Explorer, recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="cf369-116">**[リソース ガバナー]** を右クリックし、 **[プロパティ]** をクリックすると、 **[リソース ガバナーのプロパティ]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="cf369-116">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="cf369-117">**[リソース プール]** ウィンドウで、移動するワークロード グループを含むリソース プールをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf369-117">In the **Resource Pools** window, click the resource pool containing the workload group to be moved.</span></span> <span data-ttu-id="cf369-118">**[ワークロード グループ]** ウィンドウに、対象リソース プール内のワークロード グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf369-118">The **Workload Groups** window now lists the workload groups in that resource pool.</span></span>  
  
4.  <span data-ttu-id="cf369-119">**[ワークロード グループ]** ウィンドウで、移動するワークロード グループの左にある右矢印を右クリックして **[移動先]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf369-119">In the **Workload Groups** window, right-click the right arrow to the left of the workload group to be moved, and click **Move to**.</span></span> <span data-ttu-id="cf369-120">**[ワークロード グループの移動]** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf369-120">This displays a **Move Workload Group** window.</span></span>  
  
5.  <span data-ttu-id="cf369-121">使用可能なリソース プールがウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf369-121">Available resource pools are displayed in the window.</span></span> <span data-ttu-id="cf369-122">ワークロード グループの移動先とするリソース プールの名前をクリックし、 **[OK]** をクリックしてこの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="cf369-122">Click the name of the resource pool that you want to move the workload group to, and then click **OK** to carry out this action.</span></span>  
  
6.  <span data-ttu-id="cf369-123">この操作は、 **[OK]** をクリックするまで完了しません。</span><span class="sxs-lookup"><span data-stu-id="cf369-123">This action is not completed until after you click **OK**.</span></span> <span data-ttu-id="cf369-124">**[OK]** をクリックすると、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="cf369-124">When you click **OK**, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.</span></span>  
  
7.  <span data-ttu-id="cf369-125">リソース プールまたはワークロード グループの作成操作または再構成操作が失敗した場合は、プロパティ ページのタイトルの下に簡単なエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf369-125">If the create or reconfigure operation fails for the resource pool or workload group, a summary error message appears below the title of the property page.</span></span> <span data-ttu-id="cf369-126">詳細なエラー メッセージを表示するには、エラー メッセージの下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf369-126">To see a detailed error message, click the down arrow on the error message.</span></span>  
  
##  <a name="move-a-workload-group-using-transact-sql"></a><a name="MoveWGTSQL"></a> <span data-ttu-id="cf369-127">Transact-SQL を使用してワークロード グループを移動する</span><span class="sxs-lookup"><span data-stu-id="cf369-127">Move a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="cf369-128">**Transact-SQL を使用してワークロード グループを移動するには**</span><span class="sxs-lookup"><span data-stu-id="cf369-128">**To move a workload group by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="cf369-129">移動するワークロード グループと移動先とするリソース プールの名前を指定する `ALTER WORKLOAD GROUP` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf369-129">Run the `ALTER WORKLOAD GROUP` statement specifying the name of the workload group to be moved and the resource pool to which it should be moved.</span></span>  
  
2.  <span data-ttu-id="cf369-130">**ALTER RESOURCE GOVERNOR RECONFIGURE** ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf369-130">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="cf369-131">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cf369-131">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="cf369-132">次の例では、 `groupAdhoc` という名前のワークロード グループを既定のリソース プールに移動します。</span><span class="sxs-lookup"><span data-stu-id="cf369-132">The following example moves a workload group named `groupAdhoc` to the default resource pool.</span></span>  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf369-133">参照</span><span class="sxs-lookup"><span data-stu-id="cf369-133">See Also</span></span>  
 <span data-ttu-id="cf369-134">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="cf369-134">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="cf369-135">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="cf369-135">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="cf369-136">[リソース プールの作成](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="cf369-136">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="cf369-137">[ワークロード グループの作成](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="cf369-137">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="cf369-138">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cf369-138">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 [<span data-ttu-id="cf369-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cf369-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
