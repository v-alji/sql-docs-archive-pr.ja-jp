---
title: リソース プールの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5abd2e60f4f9bb5290b47f95349782f8b26ad8bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645491"
---
# <a name="create-a-resource-pool"></a><span data-ttu-id="37f51-102">リソース プールの作成</span><span class="sxs-lookup"><span data-stu-id="37f51-102">Create a Resource Pool</span></span>
  <span data-ttu-id="37f51-103">リソース プールを作成するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="37f51-103">You can create a resource pool by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="37f51-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="37f51-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="37f51-105">**リソース プールの作成に使用するもの:** [SQL Server Management Studio](#CreRPProp)、[Transact-SQL](#CreRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="37f51-105">**To create a resource pool, using:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="37f51-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="37f51-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="37f51-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="37f51-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="37f51-108">CPU の割合の最大値は、CPU の割合の最小値以上にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="37f51-108">The maximum CPU percentage must be equal to or higher than the minimum CPU percentage.</span></span> <span data-ttu-id="37f51-109">メモリの割合の最大値は、メモリの割合の最小値以上にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="37f51-109">The maximum memory percentage must be equal to or higher than the minimum memory percentage.</span></span>  
  
 <span data-ttu-id="37f51-110">すべてのリソース プールの CPU の割合の最小値の合計およびメモリの割合の最小値の合計が、それぞれ 100 を超えないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="37f51-110">The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="37f51-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="37f51-111">Permissions</span></span>  
 <span data-ttu-id="37f51-112">リソース プールを作成するには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="37f51-112">Creating a resource pool requires CONTROL SERVER permission.</span></span>  
  
##  <a name="create-a-resource-pool-using-sql-server-management-studio"></a><a name="CreRPProp"></a> <span data-ttu-id="37f51-113">SQL Server Management Studio を使用してリソース プールを作成する</span><span class="sxs-lookup"><span data-stu-id="37f51-113">Create a Resource Pool Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="37f51-114">**を使用してリソース プールを作成するには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="37f51-114">**To create a resource pool by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="37f51-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="37f51-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="37f51-116">**[リソース ガバナー]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37f51-116">Right-click **Resource Governor**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="37f51-117">**[リソース プール]** グリッドで、空白行の最初の列をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37f51-117">In the **Resource pools** grid, click the first column in the empty row.</span></span> <span data-ttu-id="37f51-118">この列にアスタリスク (\*) がラベルとして付加されます。</span><span class="sxs-lookup"><span data-stu-id="37f51-118">This column is labeled with an asterisk (\*).</span></span>  
  
4.  <span data-ttu-id="37f51-119">**[名前]** 列の空のセルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="37f51-119">Double-click the empty cell in the **Name** column.</span></span> <span data-ttu-id="37f51-120">リソース プールに使用する名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="37f51-120">Type in the name that you want to use for the resource pool.</span></span>  
  
5.  <span data-ttu-id="37f51-121">変更する行の他のセルをクリックまたはダブルクリックし、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="37f51-121">Click or double-click any other cells in the row you want to change, and enter the new values.</span></span>  
  
6.  <span data-ttu-id="37f51-122">変更を保存するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37f51-122">To save the changes, click **OK**</span></span>  
  
##  <a name="create-a-resource-pool-using-transact-sql"></a><a name="CreRPTSQL"></a> <span data-ttu-id="37f51-123">Transact-SQL を使用してリソース プールを作成する</span><span class="sxs-lookup"><span data-stu-id="37f51-123">Create a Resource Pool Using Transact-SQL</span></span>  
 <span data-ttu-id="37f51-124">**を使用してリソース プールを作成するには [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="37f51-124">**To create a resource pool by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="37f51-125">設定するプロパティ値を指定する `CREATE RESOURCE POOL` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="37f51-125">Run the `CREATE RESOURCE POOL` statement specifying the property values to be set.</span></span>  
  
2.  <span data-ttu-id="37f51-126">**ALTER RESOURCE GOVERNOR RECONFIGURE** ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="37f51-126">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="37f51-127">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="37f51-127">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="37f51-128">次の例では、 `poolAdhoc`というリソース プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="37f51-128">The following example creates a resource pool named `poolAdhoc`.</span></span>  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="37f51-129">参照</span><span class="sxs-lookup"><span data-stu-id="37f51-129">See Also</span></span>  
 <span data-ttu-id="37f51-130">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="37f51-130">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="37f51-131">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="37f51-131">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="37f51-132">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="37f51-132">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="37f51-133">[リソース プールの設定の変更](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="37f51-133">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="37f51-134">[リソース プールの削除](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="37f51-134">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="37f51-135">[テンプレートを使用してリソース ガバナーを構成する](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="37f51-135">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 <span data-ttu-id="37f51-136">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="37f51-136">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="37f51-137">[リソース ガバナーの分類子関数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="37f51-137">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="37f51-138">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="37f51-138">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="37f51-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="37f51-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
