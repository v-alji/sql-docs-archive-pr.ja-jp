---
title: リソース プールの設定の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool alter
- resource pools [SQL Server], alter
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2183cceaaf8a3e183d96c154075f9a922942c2c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714141"
---
# <a name="change-resource-pool-settings"></a><span data-ttu-id="4c63e-102">リソース プールの設定の変更</span><span class="sxs-lookup"><span data-stu-id="4c63e-102">Change Resource Pool Settings</span></span>
  <span data-ttu-id="4c63e-103">リソース プールの設定を変更するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c63e-103">You can change resource pool settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="4c63e-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="4c63e-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="4c63e-105">**リソース プールの設定変更に使用するもの:** [SQL Server Management Studio](#ChgRPProp)、[Transact-SQL](#ChgRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="4c63e-105">**To change the settings for a resource pool, using:**  [SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4c63e-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="4c63e-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="4c63e-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4c63e-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="4c63e-108">CPU の割合の最大値は、CPU の割合の最小値以上にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c63e-108">The maximum CPU percentage must be equal to or higher than the minimum CPU percentage.</span></span> <span data-ttu-id="4c63e-109">メモリの割合の最大値は、メモリの割合の最小値以上にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c63e-109">The maximum memory percentage must be equal to or higher than the minimum memory percentage.</span></span>  
  
 <span data-ttu-id="4c63e-110">すべてのリソース プールの CPU の割合の最小値の合計およびメモリの割合の最小値の合計が、それぞれ 100 を超えないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4c63e-110">The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4c63e-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="4c63e-111">Permissions</span></span>  
 <span data-ttu-id="4c63e-112">リソース プールの設定を変更するには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4c63e-112">Changing resource pool settings requires CONTROL SERVER permission.</span></span>  
  
##  <a name="change-resource-pool-settings-using-sql-server-management-studio"></a><a name="ChgRPProp"></a> <span data-ttu-id="4c63e-113">SQL Server Management Studio を使用してリソース プールの設定を変更する</span><span class="sxs-lookup"><span data-stu-id="4c63e-113">Change Resource Pool Settings Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4c63e-114">**リソース プールの設定を変更するには - [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="4c63e-114">**To change resource pool settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="4c63e-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース プール]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="4c63e-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="4c63e-116">変更するリソース プールを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c63e-116">Right-click the resource pool to be modified, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4c63e-117">**[リソース ガバナーのプロパティ]** ページで、自動的に **[リソース プール]** グリッドの対象リソース プールの行が選択されない場合は、その行を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c63e-117">In the **Resource Governor Properties** page, select the row for the resource pool in the **Resource pools** grid if it is not automatically selected.</span></span>  
  
4.  <span data-ttu-id="4c63e-118">変更する行のセルをクリックまたはダブルクリックし、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="4c63e-118">Click or double-click the cells in the row to be changed, and enter the new values.</span></span>  
  
5.  <span data-ttu-id="4c63e-119">変更を保存するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c63e-119">To save the changes, click **OK**</span></span>  
  
##  <a name="change-resource-pool-settings-using-transact-sql"></a><a name="ChgRPTSQL"></a> <span data-ttu-id="4c63e-120">Transact-SQL を使用してリソース プールの設定を変更する</span><span class="sxs-lookup"><span data-stu-id="4c63e-120">Change Resource Pool Settings Using Transact-SQL</span></span>  
 <span data-ttu-id="4c63e-121">**リソース プールの設定を変更するには - [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="4c63e-121">**To change resource pool settings by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="4c63e-122">変更するプロパティ値を指定する `ALTER RESOURCE POOL` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4c63e-122">Run the `ALTER RESOURCE POOL` statement specifying the property values to be changed.</span></span>  
  
2.  <span data-ttu-id="4c63e-123">**ALTER RESOURCE GOVERNOR RECONFIGURE** ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4c63e-123">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="4c63e-124">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c63e-124">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4c63e-125">次の例では、 `poolAdhoc`という名前のリソース プールの CPU の割合の最大値を変更します。</span><span class="sxs-lookup"><span data-stu-id="4c63e-125">The following example changes the max CPU percentage setting for the resource pool named `poolAdhoc`.</span></span>  
  
```  
ALTER RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c63e-126">参照</span><span class="sxs-lookup"><span data-stu-id="4c63e-126">See Also</span></span>  
 <span data-ttu-id="4c63e-127">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="4c63e-127">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="4c63e-128">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="4c63e-128">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="4c63e-129">[リソース プールの作成](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="4c63e-129">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="4c63e-130">[リソース プールの削除](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="4c63e-130">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="4c63e-131">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="4c63e-131">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="4c63e-132">[リソース ガバナーの分類子関数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="4c63e-132">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="4c63e-133">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4c63e-133">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="4c63e-134">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4c63e-134">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
