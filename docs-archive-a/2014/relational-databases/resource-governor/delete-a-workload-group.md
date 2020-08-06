---
title: ワークロード グループの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], delete
- Resource Governor, workload group delete
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 801a731db6c5b31bc479d1a3f6079c45ad9a7c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715166"
---
# <a name="delete-a-workload-group"></a><span data-ttu-id="f8f7a-102">ワークロード グループの削除</span><span class="sxs-lookup"><span data-stu-id="f8f7a-102">Delete a Workload Group</span></span>
  <span data-ttu-id="f8f7a-103">ワークロード グループまたはリソース プールを削除にするには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-103">You can delete a workload group or resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="f8f7a-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="f8f7a-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="f8f7a-105">**ワークロード グループの削除に使用するもの:** [オブジェクト エクスプローラー](#DelWGObjEx)、[リソース ガバナーのプロパティ](#DelWGRGProp)、[Transact-SQL](#DelWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="f8f7a-105">**To delete a workload group, using:**  [Object Explorer](#DelWGObjEx), [Resource Governor Properties](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f8f7a-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="f8f7a-106">Before You Begin</span></span>  
 <span data-ttu-id="f8f7a-107">アクティブなセッションが含まれている場合は、ワークロード グループを削除できません。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-107">You cannot delete a workload group if it contains active sessions.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="f8f7a-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f8f7a-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f8f7a-109">ワークロード グループにアクティブなセッションが含まれている場合、そのワークロード グループの削除や別のリソース プールへの移動を行う操作は、その変更を適用するための ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを呼び出した時点で失敗します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-109">If a workload group contains active sessions, deleting or moving the workload group to a different resource pool will fail when the ALTER RESOURCE GOVERNOR RECONFIGURE statement is called to apply the change.</span></span> <span data-ttu-id="f8f7a-110">この問題を回避するには、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-110">To avoid this problem, you can take one of the following actions:</span></span>  
  
-   <span data-ttu-id="f8f7a-111">そのグループからすべてのセッションが切断されるまで待ってから、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-111">Wait until all the sessions from the affected group have disconnected, and then rerun the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
-   <span data-ttu-id="f8f7a-112">そのグループ内のセッションを KILL コマンドで明示的に停止してから、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-112">Explicitly stop sessions in the affected group by using the KILL command, and then rerun the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span> <span data-ttu-id="f8f7a-113">**[削除]** を使用した後アクティブなセッションを停止する前に、セッションを明示的に停止するのは不適切であると判断した場合は、元の名前でグループを再作成し、このグループを元のリソース プールに移動します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-113">If you decide that you do not want to explicitly stop sessions after you use **Delete** but before you stop active sessions, re-create the group by using the original name and move the group to the original resource pool.</span></span>  
  
-   <span data-ttu-id="f8f7a-114">サーバーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-114">Restart the server.</span></span> <span data-ttu-id="f8f7a-115">再起動プロセスの完了後、削除したグループは作成されず、移動したグループは新しいリソース プール割り当てを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-115">After the restart process is completed, the deleted group will not be created, and a moved group will use the new resource pool assignment.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f8f7a-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="f8f7a-116">Permissions</span></span>  
 <span data-ttu-id="f8f7a-117">ワークロード グループを削除するには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-117">Deleting a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="delete-a-workload-group-using-object-explorer"></a><a name="DelWGObjEx"></a> <span data-ttu-id="f8f7a-118">オブジェクト エクスプ ローラーを使用してワークロード グループを削除する</span><span class="sxs-lookup"><span data-stu-id="f8f7a-118">Delete a Workload Group Using Object Explorer</span></span>  
 <span data-ttu-id="f8f7a-119">**オブジェクト エクスプ ローラーを使用してワークロード グループを削除するには**</span><span class="sxs-lookup"><span data-stu-id="f8f7a-119">**To delete a workload group by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="f8f7a-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース プール]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-120">In[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="f8f7a-121">削除するワークロード グループを含むリソース プールで、 **[リソース プール]** ノードを **[ワークロード グループ]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-121">Recursively expand **Resource Pools** down to and including the **Workload Groups** node in the resource pool that contains the workload group to be deleted.</span></span>  
  
3.  <span data-ttu-id="f8f7a-122">ワークロード グループを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-122">Right-click the workload group, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="f8f7a-123">**[オブジェクトの削除]** ウィンドウの **[削除されるオブジェクト]** ボックスの一覧に、ワークロード グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-123">In the **Delete Object** window, the workload group is listed in the **Object to be deleted** list.</span></span> <span data-ttu-id="f8f7a-124">ワークロード グループを削除するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-124">To delete the workload group, click **OK**.</span></span>  
  
##  <a name="delete-a-workload-group-using-resource-governor-properties"></a><a name="DelWGRGProp"></a> <span data-ttu-id="f8f7a-125">リソース ガバナーのプロパティを使用してワークロード グループを削除する</span><span class="sxs-lookup"><span data-stu-id="f8f7a-125">Delete a Workload Group Using Resource Governor Properties</span></span>  
 <span data-ttu-id="f8f7a-126">**[リソース ガバナーのプロパティ] ページでワークロード グループを削除にするには**</span><span class="sxs-lookup"><span data-stu-id="f8f7a-126">**To delete a workload group by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="f8f7a-127">オブジェクト エクスプローラーで、 **[管理]** ノードを **[リソース プール]** ノードまで展開します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-127">In Object Explorer, recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="f8f7a-128">削除するワークロード グループを含むリソース プールを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-128">Right-click the resource pool that contains the workload group to be deleted, and then click **Properties**.</span></span> <span data-ttu-id="f8f7a-129">**[リソース ガバナーのプロパティ]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-129">This opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="f8f7a-130">**[リソース プールのワークロード グループ]** ウィンドウで、削除するワークロード グループの行をクリックし、行の左側にある右矢印を右クリックして **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-130">In the **Workload groups for resource pool** window, click the line for the workload group to be deleted, then right-click the right arrow on the left side of the line, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="f8f7a-131">ワークロード グループを削除するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-131">To delete the workload group, click **OK**.</span></span>  
  
##  <a name="delete-a-workload-group-using-transact-sql"></a><a name="DelWGTSQL"></a> <span data-ttu-id="f8f7a-132">Transact-SQL を使用してワークロード グループを削除する</span><span class="sxs-lookup"><span data-stu-id="f8f7a-132">Delete a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="f8f7a-133">**Transact-SQL を使用してワークロード グループを削除するには**</span><span class="sxs-lookup"><span data-stu-id="f8f7a-133">**To delete a workload group by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="f8f7a-134">削除するワークロード グループの名前を示す `DROP WORKLOAD GROUP` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-134">Run the `DROP WORKLOAD GROUP` statement specifying the name of the workload group to delete.</span></span>  
  
2.  <span data-ttu-id="f8f7a-135">`ALTER RESOURCE GOVERNOR RECONFIGURE` ステートメントを実行する前に、削除するワークロード グループにアクティブな要求がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-135">Before you issue the `ALTER RESOURCE GOVERNOR RECONFIGURE` statement, verify that there are no active requests in the workload group being deleted.</span></span> <span data-ttu-id="f8f7a-136">アクティブな要求があると `ALTER RESOURCE GOVERNOR` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-136">If there are active requests, `ALTER RESOURCE GOVERNOR` will fail.</span></span> <span data-ttu-id="f8f7a-137">この問題を回避するには、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-137">To avoid this issue, you can take one of the following actions:</span></span>  
  
    -   <span data-ttu-id="f8f7a-138">ワークロード グループからのセッションがすべて接続解除されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-138">Wait until all the sessions from the workload group have disconnected.</span></span>  
  
    -   <span data-ttu-id="f8f7a-139">`KILL` コマンドを使用して、ワークロード グループのセッションを明示的に停止します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-139">Explicitly stop sessions in the workload group by using the `KILL` command.</span></span>  
  
    -   <span data-ttu-id="f8f7a-140">サーバーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-140">Restart the server.</span></span> <span data-ttu-id="f8f7a-141">ワークロード グループは再作成されません。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-141">The workload group will not be re-created.</span></span>  
  
    -   <span data-ttu-id="f8f7a-142">`DROP WORKLOAD GROUP` ステートメントを実行してから、変更適用のためにセッションを明示的に停止するのは不適切であると判断した場合、DROP ステートメントの実行前と同じ名前でグループを再作成し、このグループを元のリソース プールに移動することができます。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-142">In a scenario in which you have issued the `DROP WORKLOAD GROUP` statement but decide that you do not want to explicitly stop sessions to apply the change, you can re-create the group by using the same name that it had before you issued the DROP statement, and then move the group to the original resource pool.</span></span>  
  
3.  <span data-ttu-id="f8f7a-143">ステートメントを実行 `ALTER RESOURCE GOVERNOR RECONFIGURE` します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-143">Run the `ALTER RESOURCE GOVERNOR RECONFIGURE` statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="f8f7a-144">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f8f7a-144">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f8f7a-145">次の例では、 `groupAdhoc`というワークロード グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="f8f7a-145">The following example drops a workload group named `groupAdhoc`.</span></span>  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8f7a-146">参照</span><span class="sxs-lookup"><span data-stu-id="f8f7a-146">See Also</span></span>  
 <span data-ttu-id="f8f7a-147">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="f8f7a-147">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="f8f7a-148">[リソース プールの作成](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="f8f7a-148">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="f8f7a-149">[ワークロード グループの作成](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="f8f7a-149">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="f8f7a-150">[リソース プールの削除](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="f8f7a-150">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="f8f7a-151">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f8f7a-151">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="f8f7a-152">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f8f7a-152">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="f8f7a-153">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f8f7a-153">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
