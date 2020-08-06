---
title: リソース ガバナーを無効にしたとき | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 172f01bdde0f792cd9ed72ad371e5811b8de8885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715157"
---
# <a name="disable-resource-governor"></a><span data-ttu-id="8e9e0-102">リソース ガバナーを無効にしたとき</span><span class="sxs-lookup"><span data-stu-id="8e9e0-102">Disable Resource Governor</span></span>
  <span data-ttu-id="8e9e0-103">リソース ガバナーを無効にするには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-103">You can disable the Resource Governor by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="8e9e0-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="8e9e0-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="8e9e0-105">**リソース ガバナーの無効化に使用するもの:** [オブジェクト エクスプローラー](#RGOffObjEx)、[リソース ガバナーのプロパティ](#RGOffProp)、[Transact-SQL](#RGOffTSQL)</span><span class="sxs-lookup"><span data-stu-id="8e9e0-105">**To disable Resource Governorn, using:**  [Object Explorer](#RGOffObjEx), [Resource Governor Properties](#RGOffProp), [Transact-SQL](#RGOffTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8e9e0-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="8e9e0-106">Before You Begin</span></span>  
 <span data-ttu-id="8e9e0-107">リソース ガバナーを無効にすると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-107">Disabling the Resource Governor has the following results:</span></span>  
  
-   <span data-ttu-id="8e9e0-108">分類子関数は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-108">The classifier function is not run.</span></span>  
  
-   <span data-ttu-id="8e9e0-109">すべての新しい接続が、既定のワークロード グループに自動的に分類されます。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-109">All new connections are automatically classified into the default workload group.</span></span>  
  
-   <span data-ttu-id="8e9e0-110">システムによって開始される要求は、内部ワークロード グループに分類されます。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-110">System-initiated requests are classified into the internal workload group.</span></span>  
  
-   <span data-ttu-id="8e9e0-111">ワークロード グループとリソース プールの既存の設定は、すべて既定値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-111">All existing workload group and resource pool settings are reset to their default values.</span></span> <span data-ttu-id="8e9e0-112">この場合、制限に達してもイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-112">In this case, no events are fired when limits are reached.</span></span>  
  
-   <span data-ttu-id="8e9e0-113">通常のシステム監視は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-113">Normal system monitoring is not affected.</span></span>  
  
-   <span data-ttu-id="8e9e0-114">構成は変更できますが、リソース ガバナーを有効にするまで変更は反映されません。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-114">Configuration changes can be made, but the changes do not take effect until the Resource Governor is enabled.</span></span>  
  
-   <span data-ttu-id="8e9e0-115">SQL Server の再起動時に、リソース ガバナーはその構成を読み込みません。このとき、既定および内部のワークロード グループとリソース プールのみが存在します。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-115">Upon restarting SQL Server, the Resource Governor will not load its configuration, but instead will have only the default and internal workload groups and resource pools.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="8e9e0-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="8e9e0-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8e9e0-117">ユーザー トランザクション内でリソース ガバナーを無効にする場合、`ALTER RESOURCE GOVERNOR` ステートメントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-117">You cannot use the `ALTER RESOURCE GOVERNOR` statement to disable Resource Governor when in a user transaction.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8e9e0-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="8e9e0-118">Permissions</span></span>  
 <span data-ttu-id="8e9e0-119">リソース ガバナーを無効にするには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-119">Disabling the Resource Governor requires CONTROL SERVER permission.</span></span>  
  
##  <a name="disable-resource-governor-using-object-explorer"></a><a name="RGOffObjEx"></a> <span data-ttu-id="8e9e0-120">オブジェクト エクスプローラーを使用してリソース ガバナーを無効にする</span><span class="sxs-lookup"><span data-stu-id="8e9e0-120">Disable Resource Governor Using Object Explorer</span></span>  
 <span data-ttu-id="8e9e0-121">**オブジェクト エクスプローラーを使用してリソース ガバナーを無効にするには**</span><span class="sxs-lookup"><span data-stu-id="8e9e0-121">**To disable the Resource Governor by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="8e9e0-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="8e9e0-123">**[リソース ガバナー]** を右クリックし、 **[無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-123">Right-click **Resource Governor**, and then click **Disable**.</span></span>  
  
##  <a name="disable-resource-governor-using-resource-governor-properties"></a><a name="RGOffProp"></a> <span data-ttu-id="8e9e0-124">リソース ガバナーのプロパティを使用してリソース ガバナーを無効にする</span><span class="sxs-lookup"><span data-stu-id="8e9e0-124">Disable Resource Governor Using Resource Governor Properties</span></span>  
 <span data-ttu-id="8e9e0-125">**[リソース ガバナーのプロパティ] ページでリソース ガバナーを無効にするには**</span><span class="sxs-lookup"><span data-stu-id="8e9e0-125">**To disable the Resource Governor by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="8e9e0-126">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-126">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="8e9e0-127">**[リソース ガバナー]** を右クリックし、 **[プロパティ]** をクリックすると、 **[リソース ガバナーのプロパティ]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-127">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="8e9e0-128">**[リソース ガバナーの有効化]** チェック ボックスをオフにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-128">Click the **Enable Resource Governor** check box, ensure that the box is not selected, and then click **OK**.</span></span>  
  
##  <a name="disable-resource-governor-using-transact-sql"></a><a name="RGOffTSQL"></a> <span data-ttu-id="8e9e0-129">Transact-SQL を使用してリソース ガバナーを無効にする</span><span class="sxs-lookup"><span data-stu-id="8e9e0-129">Disable Resource Governor Using Transact-SQL</span></span>  
 <span data-ttu-id="8e9e0-130">**Transact-SQL を使用してリソース ガバナーを無効にするには**</span><span class="sxs-lookup"><span data-stu-id="8e9e0-130">**To disable the Resource Governor by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="8e9e0-131">**ALTER RESOURCE GOVERNOR DISABLE** ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-131">Run the **ALTER RESOURCE GOVERNOR DISABLE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="8e9e0-132">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8e9e0-132">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="8e9e0-133">リソース ガバナーを有効にする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8e9e0-133">The following example enables the Resource Governor.</span></span>  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e9e0-134">参照</span><span class="sxs-lookup"><span data-stu-id="8e9e0-134">See Also</span></span>  
 <span data-ttu-id="8e9e0-135">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="8e9e0-135">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="8e9e0-136">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="8e9e0-136">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="8e9e0-137">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="8e9e0-137">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="8e9e0-138">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="8e9e0-138">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="8e9e0-139">[リソース ガバナーの分類子関数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="8e9e0-139">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 [<span data-ttu-id="8e9e0-140">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8e9e0-140">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
