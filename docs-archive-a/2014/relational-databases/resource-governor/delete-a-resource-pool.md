---
title: リソース プールの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a67b0e2262fa3007597091b6087cc937bb0f3276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715158"
---
# <a name="delete-a-resource-pool"></a><span data-ttu-id="a509d-102">リソース プールの削除</span><span class="sxs-lookup"><span data-stu-id="a509d-102">Delete a Resource Pool</span></span>
  <span data-ttu-id="a509d-103">リソース プールを削除にするには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。</span><span class="sxs-lookup"><span data-stu-id="a509d-103">You can delete a resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="a509d-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="a509d-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="a509d-105">**リソース プールの削除に使用するもの:** [SQL Server Management Studio](#DelRPSSMS)、[Transact-SQL](#DelRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="a509d-105">**To delete a resource pool, using:** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a509d-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="a509d-106">Before You Begin</span></span>  
 <span data-ttu-id="a509d-107">ワークロード グループが含まれている場合は、リソース プールを削除できません。</span><span class="sxs-lookup"><span data-stu-id="a509d-107">You cannot delete a resource pool if it contains workload groups.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="a509d-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a509d-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a509d-109">リソース ガバナーの既定のリソース プールや内部リソース プールを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="a509d-109">You cannot delete the Resource Governor default or internal resource pools.</span></span> <span data-ttu-id="a509d-110">ワークロード グループが含まれている場合は、リソース プールを削除できません。</span><span class="sxs-lookup"><span data-stu-id="a509d-110">You cannot delete a resource pool if it contains workload groups.</span></span> <span data-ttu-id="a509d-111">詳細については、「 [Delete a Workload Group](delete-a-workload-group.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a509d-111">For more information, see [Delete a Workload Group](delete-a-workload-group.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a509d-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="a509d-112">Permissions</span></span>  
 <span data-ttu-id="a509d-113">リソース プールを削除するには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a509d-113">Deleting a resource pool requires CONTROL SERVER permission.</span></span>  
  
##  <a name="delete-a-resource-pool-using-object-explorer"></a><a name="DelRPSSMS"></a> <span data-ttu-id="a509d-114">オブジェクト エクスプ ローラーを使用してリソース プールを削除する</span><span class="sxs-lookup"><span data-stu-id="a509d-114">Delete a Resource Pool Using Object Explorer</span></span>  
 <span data-ttu-id="a509d-115">**SQL Server Management Studio を使用してリソース プールを削除するには**</span><span class="sxs-lookup"><span data-stu-id="a509d-115">**To delete a resource pool by using SQL Server Management Studio**</span></span>  
  
1.  <span data-ttu-id="a509d-116">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="a509d-116">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="a509d-117">削除するリソース プールを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a509d-117">Right-click the resource pool to be deleted, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="a509d-118">**[オブジェクトの削除]** ウィンドウの **[削除されるオブジェクト]** ボックスの一覧に、リソース プールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a509d-118">In the **Delete Object** window, the resource pool is listed in the **Object to be deleted** list.</span></span> <span data-ttu-id="a509d-119">リソース プールを削除するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a509d-119">To delete the resource pool, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a509d-120">ワークロード グループが含まれているリソース プールを削除しようとすると失敗します。</span><span class="sxs-lookup"><span data-stu-id="a509d-120">If the resource pool that you are trying to delete contains a workload group, this action will fail.</span></span>  
  
##  <a name="delete-a-resource-pool-using-transact-sql"></a><a name="DelRPTSQL"></a> <span data-ttu-id="a509d-121">Transact-SQL を使用してリソース プールを削除する</span><span class="sxs-lookup"><span data-stu-id="a509d-121">Delete a Resource Pool Using Transact-SQL</span></span>  
 <span data-ttu-id="a509d-122">**Transact-SQL を使用してリソース プールを削除するには**</span><span class="sxs-lookup"><span data-stu-id="a509d-122">**To delete a resource pool by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="a509d-123">削除するリソース プールの名前を示す `DROP RESOURCE POOL` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a509d-123">Run the `DROP RESOURCE POOL` statement specifying the name of the resource pool to delete.</span></span>  
  
2.  <span data-ttu-id="a509d-124">**ALTER RESOURCE GOVERNOR RECONFIGURE** ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a509d-124">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="a509d-125">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a509d-125">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="a509d-126">次の例では、 `poolAdhoc`というワークロード グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="a509d-126">The following example drops a workload group named `poolAdhoc`.</span></span>  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a509d-127">参照</span><span class="sxs-lookup"><span data-stu-id="a509d-127">See Also</span></span>  
 <span data-ttu-id="a509d-128">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="a509d-128">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="a509d-129">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="a509d-129">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="a509d-130">[リソース プールの作成](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="a509d-130">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="a509d-131">[リソース プールの設定の変更](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="a509d-131">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="a509d-132">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="a509d-132">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="a509d-133">[リソース ガバナーの分類子関数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="a509d-133">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="a509d-134">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a509d-134">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="a509d-135">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a509d-135">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="a509d-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a509d-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
