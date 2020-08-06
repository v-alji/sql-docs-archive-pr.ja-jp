---
title: リソース ガバナーのプロパティの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties.f1
helpviewer_keywords:
- Resource Governor, properties
ms.assetid: de3510df-f792-4a9d-80fa-f198fd36cdc8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cd7af8f4f8eb3cd0531bc907011846f73f94f6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634926"
---
# <a name="view-resource-governor-properties"></a><span data-ttu-id="9d841-102">View Resource Governor Properties</span><span class="sxs-lookup"><span data-stu-id="9d841-102">View Resource Governor Properties</span></span>
  <span data-ttu-id="9d841-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の [リソース ガバナーのプロパティ] ページを使用して、リソース プールやワークロード グループなどのリソース ガバナー エンティティを作成または構成できます。</span><span class="sxs-lookup"><span data-stu-id="9d841-103">You can create or configure Resource Governor entities, such as resource pools and workload groups, by using the Resource Governor Properties page in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="9d841-104">**作業を開始する準備:** [アクセス許可](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="9d841-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
2.  <span data-ttu-id="9d841-105">**リソース ガバナーのプロパティを表示するには (次を使用):**  [[リソース ガバナーのプロパティ] ページ](#ViewRGProp)</span><span class="sxs-lookup"><span data-stu-id="9d841-105">**To view Resource Governor properties, using:**  [Resource Governor Properties page](#ViewRGProp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9d841-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="9d841-106">Before You Begin</span></span>  
 <span data-ttu-id="9d841-107">**[リソース ガバナーのプロパティ]** ページでは、リソース ガバナー エンティティのプロパティを表示する以外に、さまざまな構成タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9d841-107">In addition to viewing the properties of Resource Governor entities, you can perform several configuration tasks using the **Resource Governor Properties** page.</span></span> <span data-ttu-id="9d841-108">詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d841-108">For more information, see these topics:</span></span>  
  
-   [<span data-ttu-id="9d841-109">リソース ガバナーの有効化</span><span class="sxs-lookup"><span data-stu-id="9d841-109">Enable Resource Governor</span></span>](enable-resource-governor.md)  
  
-   [<span data-ttu-id="9d841-110">リソース ガバナーの無効化</span><span class="sxs-lookup"><span data-stu-id="9d841-110">Disable Resource Governor</span></span>](disable-resource-governor.md)  
  
-   [<span data-ttu-id="9d841-111">リソース プールの作成</span><span class="sxs-lookup"><span data-stu-id="9d841-111">Create a Resource Pool</span></span>](create-a-resource-pool.md)  
  
-   [<span data-ttu-id="9d841-112">ワークロード グループの作成</span><span class="sxs-lookup"><span data-stu-id="9d841-112">Create a Workload Group</span></span>](create-a-workload-group.md)  
  
-   [<span data-ttu-id="9d841-113">リソース プールの設定の変更</span><span class="sxs-lookup"><span data-stu-id="9d841-113">Change Resource Pool Settings</span></span>](change-resource-pool-settings.md)  
  
-   [<span data-ttu-id="9d841-114">ワークロード グループの設定の変更</span><span class="sxs-lookup"><span data-stu-id="9d841-114">Change Workload Group Settings</span></span>](change-workload-group-settings.md)  
  
-   [<span data-ttu-id="9d841-115">ワークロード グループの移動</span><span class="sxs-lookup"><span data-stu-id="9d841-115">Move a Workload Group</span></span>](move-a-workload-group.md)  
  
 <span data-ttu-id="9d841-116">ワークロード グループまたはリソース プールを追加、削除、または移動してから **[OK]** をクリックすると、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="9d841-116">When you click **OK** after adding, deleting, or moving a workload group or resource pool, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.</span></span>  
  
 <span data-ttu-id="9d841-117">リソース プールまたはワークロード グループの作成操作または再構成操作が失敗した場合は、プロパティ ページのタイトルの下に簡単なエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d841-117">If the create or reconfigure operation for the resource pool or workload group fails, a summary error message appears below the title of the property page.</span></span> <span data-ttu-id="9d841-118">詳細なエラー メッセージを表示するには、エラー メッセージの下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d841-118">To see a detailed error message, click the down arrow on the error message.</span></span>  
  
 <span data-ttu-id="9d841-119">[sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 動的管理ビューにクエリを実行して is_configuration_pending の現在の状態を取得することにより、構成が保留中かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9d841-119">You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) dynamic management view to get the current status of is_configuration_pending.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9d841-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="9d841-120">Permissions</span></span>  
 <span data-ttu-id="9d841-121">リソース ガバナーのプロパティを表示するには、VIEW SERVER STATER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9d841-121">Viewing resource governor properties requires VIEW SERVER STATER permission.</span></span> <span data-ttu-id="9d841-122">リソース ガバナーの構成タスクを行うには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9d841-122">The resource governor configuration tasks require CONTROL SERVER permission.</span></span>  
  
##  <a name="view-the-resource-governor-properties-page"></a><a name="ViewRGProp"></a><span data-ttu-id="9d841-123">[Resource Governor のプロパティ] ページを表示する</span><span class="sxs-lookup"><span data-stu-id="9d841-123">View the Resource Governor Properties Page</span></span>  
 <span data-ttu-id="9d841-124">**で、次の [リソース ガバナーのプロパティ] ページでリソース ガバナーのプロパティを表示するには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="9d841-124">**To view resource governor properties by using the Resource Governor Properties page in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="9d841-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="9d841-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="9d841-126">**[リソース ガバナー]** を右クリックし、 **[プロパティ]** をクリックすると、 **[リソース ガバナーのプロパティ]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="9d841-126">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="9d841-127">このページのフィールドの詳細については、「 [リソース ガバナー プロパティ](#RGProp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d841-127">For descriptions of the fields in the page, see [Resource Governor Properties](#RGProp).</span></span>  
  
4.  <span data-ttu-id="9d841-128">変更を保存するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d841-128">To save any changes, click **OK**.</span></span>  
  
##  <a name="resource-governor-properties"></a><a name="RGProp"></a><span data-ttu-id="9d841-129">Resource Governor のプロパティ</span><span class="sxs-lookup"><span data-stu-id="9d841-129">Resource Governor Properties</span></span>  
 <span data-ttu-id="9d841-130">**[分類子関数の名前]**</span><span class="sxs-lookup"><span data-stu-id="9d841-130">**Classifier function name**</span></span>  
 <span data-ttu-id="9d841-131">分類子関数を一覧から選択して指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-131">Specify the classifier function by selecting from the list.</span></span>  
  
 <span data-ttu-id="9d841-132">**リソース ガバナーの有効化**</span><span class="sxs-lookup"><span data-stu-id="9d841-132">**Enable Resource Governor**</span></span>  
 <span data-ttu-id="9d841-133">チェック ボックスをオンまたはオフにしてリソース ガバナーを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="9d841-133">Enable or disable Resource Governor by selecting or clearing the check box.</span></span>  
  
 <span data-ttu-id="9d841-134">**[リソース プール]**</span><span class="sxs-lookup"><span data-stu-id="9d841-134">**Resource pools**</span></span>  
 <span data-ttu-id="9d841-135">提供されるグリッドを使用して、リソース プール構成を作成または変更します。</span><span class="sxs-lookup"><span data-stu-id="9d841-135">Create or change resource pool configuration by using the grid that is provided.</span></span> <span data-ttu-id="9d841-136">このグリッドには、あらかじめ定義されている内部プールおよび既定プールの情報が設定されています。</span><span class="sxs-lookup"><span data-stu-id="9d841-136">This grid is populated with information for the predefined internal and default pools.</span></span> <span data-ttu-id="9d841-137">プールの行の最初の列をクリックして、使用するプールを選択します。</span><span class="sxs-lookup"><span data-stu-id="9d841-137">Select a pool to work with by clicking the first column in the row for the pool.</span></span> <span data-ttu-id="9d841-138">新しいリソース プールを作成するには、先頭にアスタリスク ( **&#42;** ) が付いている行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d841-138">To create a new resource pool, click the row that is prefixed by the asterisk (**&#42;**).</span></span>  
  
 <span data-ttu-id="9d841-139">**名前**</span><span class="sxs-lookup"><span data-stu-id="9d841-139">**Name**</span></span>  
 <span data-ttu-id="9d841-140">リソース プールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-140">Specify the name of the resource pool.</span></span>  
  
 <span data-ttu-id="9d841-141">**[最小 CPU %]**</span><span class="sxs-lookup"><span data-stu-id="9d841-141">**Minimum CPU %**</span></span>  
 <span data-ttu-id="9d841-142">CPU の競合がある場合に、リソース プールのすべての要求に保証される平均 CPU 帯域幅を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-142">Specify the guaranteed average CPU bandwidth for all requests in the resource pool when there is CPU contention.</span></span> <span data-ttu-id="9d841-143">範囲は 0 から 100 です。</span><span class="sxs-lookup"><span data-stu-id="9d841-143">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="9d841-144">**[最大 CPU %]**</span><span class="sxs-lookup"><span data-stu-id="9d841-144">**Maximum CPU %**</span></span>  
 <span data-ttu-id="9d841-145">CPU の競合がある場合に、このリソース プールのすべての要求に割り当てられる最大平均 CPU 帯域幅を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-145">Specify the maximum average CPU bandwidth that all requests in this resource pool will receive when there is CPU contention.</span></span> <span data-ttu-id="9d841-146">範囲は 0 から 100 です。</span><span class="sxs-lookup"><span data-stu-id="9d841-146">Range is 0 to 100.</span></span> <span data-ttu-id="9d841-147">既定の設定は 100 です。</span><span class="sxs-lookup"><span data-stu-id="9d841-147">The default setting is 100.</span></span>  
  
 <span data-ttu-id="9d841-148">**[最小メモリ %]**</span><span class="sxs-lookup"><span data-stu-id="9d841-148">**Minimum Memory %**</span></span>  
 <span data-ttu-id="9d841-149">このリソース プール用に確保され、他のリソース プールとは共有できないメモリ量の最小値を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-149">Specify the minimum amount of memory reserved for this resource pool that can not be shared with other resource pools.</span></span> <span data-ttu-id="9d841-150">範囲は 0 から 100 です。</span><span class="sxs-lookup"><span data-stu-id="9d841-150">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="9d841-151">**[最大メモリ %]**</span><span class="sxs-lookup"><span data-stu-id="9d841-151">**Maximum Memory %**</span></span>  
 <span data-ttu-id="9d841-152">このリソース プールの要求で使用できる合計サーバー メモリを指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-152">Specify the total server memory that can be used by requests in this resource pool.</span></span> <span data-ttu-id="9d841-153">範囲は 0 から 100 です。</span><span class="sxs-lookup"><span data-stu-id="9d841-153">Range is 0 to 100.</span></span> <span data-ttu-id="9d841-154">既定の設定は 100 です。</span><span class="sxs-lookup"><span data-stu-id="9d841-154">The default setting is 100.</span></span>  
  
 <span data-ttu-id="9d841-155">詳細については、「 [CREATE RESOURCE POOL &#40;transact-sql&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d841-155">For more information, see [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql).</span></span>  
  
 <span data-ttu-id="9d841-156">**[リソース プールのワークロード グループ]**</span><span class="sxs-lookup"><span data-stu-id="9d841-156">**Workload groups for resource pool**</span></span>  
 <span data-ttu-id="9d841-157">提供されるグリッドを使用して、ワークロード グループ構成を作成または変更します。</span><span class="sxs-lookup"><span data-stu-id="9d841-157">Create or change the workload group configuration by using the grid that is provided.</span></span> <span data-ttu-id="9d841-158">このグリッドには、あらかじめ定義されている内部グループおよび既定グループの情報が設定されています。</span><span class="sxs-lookup"><span data-stu-id="9d841-158">This grid is populated with information for the predefined internal and default groups.</span></span> <span data-ttu-id="9d841-159">グループの行の最初の列をクリックして、使用するグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="9d841-159">Select a group to work with by clicking the first column in the row for the pool.</span></span> <span data-ttu-id="9d841-160">新しいワークロード グループを作成するには、先頭にアスタリスク ( **&#42;** ) が付いている行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d841-160">To create a new workload group, click the row that is prefixed by the asterisk (**&#42;**).</span></span>  
  
 <span data-ttu-id="9d841-161">**名前**</span><span class="sxs-lookup"><span data-stu-id="9d841-161">**Name**</span></span>  
 <span data-ttu-id="9d841-162">ワークロード グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-162">Specify the name of the workload group.</span></span>  
  
 <span data-ttu-id="9d841-163">**重要度**</span><span class="sxs-lookup"><span data-stu-id="9d841-163">**Importance**</span></span>  
 <span data-ttu-id="9d841-164">ワークロード グループでの要求の相対的な重要度を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-164">Specify the relative importance of a request in the workload group.</span></span> <span data-ttu-id="9d841-165">使用可能な設定は [低]、[中]、および [高] です。</span><span class="sxs-lookup"><span data-stu-id="9d841-165">Available settings are Low, Medium, and High.</span></span>  
  
 <span data-ttu-id="9d841-166">**[最大要求数]**</span><span class="sxs-lookup"><span data-stu-id="9d841-166">**Maximum Requests**</span></span>  
 <span data-ttu-id="9d841-167">ワークロード グループで実行を許可する同時要求の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-167">Specify the maximum number of simultaneous requests that are allowed to execute in the workload group.</span></span> <span data-ttu-id="9d841-168">0 または正の整数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d841-168">Must be 0 or a positive integer.</span></span>  
  
 <span data-ttu-id="9d841-169">**[CPU 時間 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="9d841-169">**CPU Time (sec)**</span></span>  
 <span data-ttu-id="9d841-170">要求が使用できる最大 CPU 時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-170">Specify the maximum amount of CPU time that a request can use.</span></span> <span data-ttu-id="9d841-171">0 または正の整数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d841-171">Must be 0 or a positive integer.</span></span> <span data-ttu-id="9d841-172">0 を指定すると、時間は無制限になります。</span><span class="sxs-lookup"><span data-stu-id="9d841-172">If 0, the time is unlimited.</span></span>  
  
 <span data-ttu-id="9d841-173">**[メモリ許可 (%)]**</span><span class="sxs-lookup"><span data-stu-id="9d841-173">**Memory Grant %**</span></span>  
 <span data-ttu-id="9d841-174">1 つの要求にプールから割り当てられる最大メモリ容量を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-174">Specify the maximum amount of memory that a single request can take from the pool.</span></span> <span data-ttu-id="9d841-175">範囲は 0 から 100 です。</span><span class="sxs-lookup"><span data-stu-id="9d841-175">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="9d841-176">**[許可のタイムアウト (秒)]**</span><span class="sxs-lookup"><span data-stu-id="9d841-176">**Grant Time-out (sec)**</span></span>  
 <span data-ttu-id="9d841-177">クエリが失敗する前に、リソースが使用可能になるのをそのクエリが待機できる最大時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-177">Specify the maximum time that a query can wait for a resource to become available before the query fails.</span></span> <span data-ttu-id="9d841-178">0 または正の整数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d841-178">Must be 0 or a positive integer.</span></span>  
  
 <span data-ttu-id="9d841-179">**並列処理の次数**</span><span class="sxs-lookup"><span data-stu-id="9d841-179">**Degree of Parallelism**</span></span>  
 <span data-ttu-id="9d841-180">並列要求の最大 DOP (並列処理の次数) を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d841-180">Specify the maximum degree of parallelism (DOP) for parallel requests.</span></span> <span data-ttu-id="9d841-181">範囲は 0 ～ 64 です。</span><span class="sxs-lookup"><span data-stu-id="9d841-181">Range is 0 to 64.</span></span>  
  
 <span data-ttu-id="9d841-182">詳細については、「[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d841-182">For more information, see [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql).</span></span>  
  
## <a name="view-resource-governor-properties-by-using-transact-sql"></a><span data-ttu-id="9d841-183">Transact-sql を使用して Resource Governor のプロパティを表示する</span><span class="sxs-lookup"><span data-stu-id="9d841-183">View Resource Governor Properties by Using Transact-SQL</span></span>  
 <span data-ttu-id="9d841-184">**Transact-SQL を使用してリソース ガバナーのプロパティを表示する**</span><span class="sxs-lookup"><span data-stu-id="9d841-184">**View resource governor properties by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="9d841-185">リソース ガバナー エンティティの定義を表示するには、「[リソース ガバナーのカタログ ビュー &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="9d841-185">To view the definitions of resource governor entities, use the [Resource Governor Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql).</span></span>  
  
2.  <span data-ttu-id="9d841-186">リソース ガバナー エンティティの現在の構成を表示するには、「[リソース ガバナー関連の動的管理ビュー &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="9d841-186">To view the current configuration of resource governor entities, use the [Resource Governor Related Dynamic Management Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d841-187">参照</span><span class="sxs-lookup"><span data-stu-id="9d841-187">See Also</span></span>  
 <span data-ttu-id="9d841-188">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="9d841-188">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="9d841-189">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="9d841-189">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="9d841-190">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="9d841-190">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="9d841-191">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="9d841-191">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 [<span data-ttu-id="9d841-192">リソース ガバナーの分類子関数</span><span class="sxs-lookup"><span data-stu-id="9d841-192">Resource Governor Classifier Function</span></span>](resource-governor-classifier-function.md)  
  
  
