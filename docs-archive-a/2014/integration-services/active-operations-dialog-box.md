---
title: '[アクティブな操作] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49861de7be207875c554e02d3f3b1b2f941fff64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633282"
---
# <a name="active-operations-dialog-box"></a><span data-ttu-id="18444-102">[アクティブな操作] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="18444-102">Active Operations Dialog Box</span></span>
  <span data-ttu-id="18444-103">配置、検証、パッケージの実行など、 **サーバー上で現在実行中の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 操作の状態を表示するには、** [アクティブな操作][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="18444-103">Use the **Active Operations** dialog box to view the status of currently running [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] operations on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, such as deployment, validation, and package execution.</span></span> <span data-ttu-id="18444-104">このデータは、SSISDB カタログに格納されます。</span><span class="sxs-lookup"><span data-stu-id="18444-104">This data is stored in the SSISDB catalog.</span></span>  
  
 <span data-ttu-id="18444-105">関連 [!INCLUDE[tsql](../includes/tsql-md.md)] ビューの詳細については、「[catalog.operations (SSISDB データベース)](/sql/integration-services/system-views/catalog-operations-ssisdb-database)」、「[catalog.validations (SSISDB データベース)](/sql/integration-services/system-views/catalog-validations-ssisdb-database)」、「[catalog.executions (SSISDB データベース)](/sql/integration-services/system-views/catalog-executions-ssisdb-database)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18444-105">For more information about related [!INCLUDE[tsql](../includes/tsql-md.md)] views, see [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database), and [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)</span></span>  
  
 <span data-ttu-id="18444-106">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="18444-106">**What do you want to do?**</span></span>  
  
1.  <span data-ttu-id="18444-107">[[アクティブな操作] ダイアログボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="18444-107">[Open the Active Operations Dialog Box](#open_dialog)</span></span>  
  
2.  [<span data-ttu-id="18444-108">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="18444-108">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-active-operations-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="18444-109">[アクティブな操作] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="18444-109">Open the Active Operations Dialog Box</span></span>  
  
1.  <span data-ttu-id="18444-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="18444-110">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="18444-111">Microsoft SQL Server データベース エンジンに接続します。</span><span class="sxs-lookup"><span data-stu-id="18444-111">Connect Microsoft SQL Server Database Engine</span></span>  
  
3.  <span data-ttu-id="18444-112">オブジェクト エクスプローラーで、 **[Integration Services]** ノードを展開します。 **[SSISDB]** を右クリックし、 **[アクティブな操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18444-112">In Object Explorer, expand the **Integration Services** node, right-click **SSISDB**, and then click **Active Operations**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="18444-113">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="18444-113">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="18444-114">Options</span><span class="sxs-lookup"><span data-stu-id="18444-114">Options</span></span>  
 <span data-ttu-id="18444-115">**Type**</span><span class="sxs-lookup"><span data-stu-id="18444-115">**Type**</span></span>  
 <span data-ttu-id="18444-116">操作の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="18444-116">Specifies the type of operation.</span></span> <span data-ttu-id="18444-117">次に、**型**フィールドに使用できる値と、transact-sql ビューの [operations_type] 列の対応する値を示し `catalog.operations` ます。</span><span class="sxs-lookup"><span data-stu-id="18444-117">The following are the possible values for the **Type** field and the corresponding values in the operations_type column of the Transact-SQL `catalog.operations` view.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18444-118">Integration Services の初期化</span><span class="sxs-lookup"><span data-stu-id="18444-118">Integration Services initialization</span></span>|<span data-ttu-id="18444-119">1</span><span class="sxs-lookup"><span data-stu-id="18444-119">1</span></span>|  
|<span data-ttu-id="18444-120">操作のクリーンアップ (SQL エージェント ジョブ)</span><span class="sxs-lookup"><span data-stu-id="18444-120">Operations cleanup (SQL Agent job)</span></span>|<span data-ttu-id="18444-121">2</span><span class="sxs-lookup"><span data-stu-id="18444-121">2</span></span>|  
|<span data-ttu-id="18444-122">プロジェクト バージョンのクリーンアップ (SQL エージェント ジョブ)</span><span class="sxs-lookup"><span data-stu-id="18444-122">Project versions cleanup (SQL Agent job)</span></span>|<span data-ttu-id="18444-123">3</span><span class="sxs-lookup"><span data-stu-id="18444-123">3</span></span>|  
|<span data-ttu-id="18444-124">プロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="18444-124">Deploy project</span></span>|<span data-ttu-id="18444-125">101</span><span class="sxs-lookup"><span data-stu-id="18444-125">101</span></span>|  
|<span data-ttu-id="18444-126">プロジェクトの復元</span><span class="sxs-lookup"><span data-stu-id="18444-126">Restore project</span></span>|<span data-ttu-id="18444-127">106</span><span class="sxs-lookup"><span data-stu-id="18444-127">106</span></span>|  
|<span data-ttu-id="18444-128">パッケージ実行の作成および開始</span><span class="sxs-lookup"><span data-stu-id="18444-128">Create and start package execution</span></span>|<span data-ttu-id="18444-129">200</span><span class="sxs-lookup"><span data-stu-id="18444-129">200</span></span>|  
|<span data-ttu-id="18444-130">操作の停止 (検証または実行の停止)</span><span class="sxs-lookup"><span data-stu-id="18444-130">Stop operation (stopping a validation or execution</span></span>|<span data-ttu-id="18444-131">202</span><span class="sxs-lookup"><span data-stu-id="18444-131">202</span></span>|  
|<span data-ttu-id="18444-132">プロジェクトの検証</span><span class="sxs-lookup"><span data-stu-id="18444-132">Validate project</span></span>|<span data-ttu-id="18444-133">300</span><span class="sxs-lookup"><span data-stu-id="18444-133">300</span></span>|  
|<span data-ttu-id="18444-134">パッケージの検証</span><span class="sxs-lookup"><span data-stu-id="18444-134">Validate package</span></span>|<span data-ttu-id="18444-135">301</span><span class="sxs-lookup"><span data-stu-id="18444-135">301</span></span>|  
|<span data-ttu-id="18444-136">カタログの構成</span><span class="sxs-lookup"><span data-stu-id="18444-136">Configure catalog</span></span>|<span data-ttu-id="18444-137">1000</span><span class="sxs-lookup"><span data-stu-id="18444-137">1000</span></span>|  
  
 <span data-ttu-id="18444-138">**Stop**</span><span class="sxs-lookup"><span data-stu-id="18444-138">**Stop**</span></span>  
 <span data-ttu-id="18444-139">現在実行中の操作を停止する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="18444-139">Click to stop a currently running operation.</span></span>  
  
  
