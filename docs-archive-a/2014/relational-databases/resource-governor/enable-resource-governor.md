---
title: リソース ガバナーの有効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b1b0f780457aa5a4d26cbb463c9f31a94185f0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715153"
---
# <a name="enable-resource-governor"></a><span data-ttu-id="40a35-102">リソース ガバナーの有効化</span><span class="sxs-lookup"><span data-stu-id="40a35-102">Enable Resource Governor</span></span>
  <span data-ttu-id="40a35-103">リソース ガバナーは、既定ではオフになっています。</span><span class="sxs-lookup"><span data-stu-id="40a35-103">The Resource Governor is turned off by default.</span></span> <span data-ttu-id="40a35-104">リソース ガバナーを有効にするには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。</span><span class="sxs-lookup"><span data-stu-id="40a35-104">You can enable the Resource Governor by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="40a35-105">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="40a35-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="40a35-106">**リソース ガバナーの有効化に使用するもの:** [オブジェクト エクスプローラー](#RGOnObjEx)、[リソース ガバナーのプロパティ](#RGOnProp)、[Transact-SQL](#RGOnTSQL)</span><span class="sxs-lookup"><span data-stu-id="40a35-106">**To enable Resource Governorn, using:**  [Object Explorer](#RGOnObjEx), [Resource Governor Properties](#RGOnProp), [Transact-SQL](#RGOnTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="40a35-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="40a35-107">Before You Begin</span></span>  
 <span data-ttu-id="40a35-108">リソース ガバナーを有効にすると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="40a35-108">Enabling the resource governor has the following results:</span></span>  
  
-   <span data-ttu-id="40a35-109">新しい接続に対して分類子関数が実行され、それらのワークロードがワークロード グループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="40a35-109">The classifier function is run for new connections so that their workloads can be assigned to workload groups.</span></span>  
  
-   <span data-ttu-id="40a35-110">リソース ガバナー構成で指定されているリソース制限が有効になり適用されます。</span><span class="sxs-lookup"><span data-stu-id="40a35-110">The resource limits that are specified in the Resource Governor configuration are honored and enforced.</span></span>  
  
-   <span data-ttu-id="40a35-111">リソース ガバナーを有効にする前に存在していた要求に、リソース ガバナーが無効であったときに加えた構成の変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="40a35-111">Requests that existed before enabling Resource Governor are affected by any configuration changes that were made when the Resource Governor was disabled.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="40a35-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="40a35-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="40a35-113">ユーザー トランザクション内でリソース ガバナーを有効にする場合、`ALTER RESOURCE GOVERNOR` ステートメントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="40a35-113">You cannot use the `ALTER RESOURCE GOVERNOR` statement to enable Resource Governor when in a user transaction.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="40a35-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="40a35-114">Permissions</span></span>  
 <span data-ttu-id="40a35-115">リソース ガバナーを有効にするには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="40a35-115">Enabling the Resource Governor requires CONTROL SERVER permission.</span></span>  
  
##  <a name="enable-resource-governor-using-object-explorer"></a><a name="RGOnObjEx"></a> <span data-ttu-id="40a35-116">オブジェクト エクスプローラーを使用してリソース ガバナーを有効にする</span><span class="sxs-lookup"><span data-stu-id="40a35-116">Enable Resource Governor Using Object Explorer</span></span>  
 <span data-ttu-id="40a35-117">**オブジェクト エクスプローラーを使用してリソース ガバナーを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="40a35-117">**To enable the Resource Governor by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="40a35-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="40a35-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="40a35-119">**[リソース ガバナー]** を右クリックし、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40a35-119">Right-click **Resource Governor**, and then click **Enable**.</span></span>  
  
##  <a name="enable-resource-governor-using-resource-governor-properties"></a><a name="RGOnProp"></a> <span data-ttu-id="40a35-120">リソース ガバナーのプロパティを使用してリソース ガバナーを有効にする</span><span class="sxs-lookup"><span data-stu-id="40a35-120">Enable Resource Governor Using Resource Governor Properties</span></span>  
 <span data-ttu-id="40a35-121">**[リソース ガバナーのプロパティ] ページでリソース ガバナーを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="40a35-121">**To enable the Resource Governor by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="40a35-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。</span><span class="sxs-lookup"><span data-stu-id="40a35-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="40a35-123">**[リソース ガバナー]** を右クリックし、 **[プロパティ]** をクリックすると、 **[リソース ガバナーのプロパティ]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="40a35-123">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="40a35-124">**[リソース ガバナーの有効化]** チェック ボックスをオンにしてから、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40a35-124">Click the **Enable Resource Governor** check box, and then click **OK**.</span></span>  
  
##  <a name="enable-resource-governor-using-transact-sql"></a><a name="RGOnTSQL"></a> <span data-ttu-id="40a35-125">Transact-SQL を使用してリソース ガバナーを有効にする</span><span class="sxs-lookup"><span data-stu-id="40a35-125">Enable Resource Governor Using Transact-SQL</span></span>  
 <span data-ttu-id="40a35-126">**Transact-SQL を使用してリソース ガバナーを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="40a35-126">**To enable the Resource Governor by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="40a35-127">**ALTER RESOURCE GOVERNOR RECONFIGURE** ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="40a35-127">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="40a35-128">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="40a35-128">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="40a35-129">リソース ガバナーを有効にする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40a35-129">The following example enables the Resource Governor.</span></span>  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="40a35-130">参照</span><span class="sxs-lookup"><span data-stu-id="40a35-130">See Also</span></span>  
 <span data-ttu-id="40a35-131">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="40a35-131">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="40a35-132">[リソース ガバナーを無効にしたとき](disable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="40a35-132">[Disable Resource Governor](disable-resource-governor.md) </span></span>  
 <span data-ttu-id="40a35-133">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="40a35-133">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="40a35-134">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="40a35-134">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="40a35-135">[リソース ガバナーの分類子関数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="40a35-135">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 [<span data-ttu-id="40a35-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40a35-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
