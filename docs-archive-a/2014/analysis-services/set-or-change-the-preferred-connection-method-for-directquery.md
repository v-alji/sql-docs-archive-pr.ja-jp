---
title: DirectQuery | の優先接続方法を設定または変更します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
author: minewiskan
ms.author: owend
ms.openlocfilehash: 239c80ace0daa3498c8dafd8fea358ce540931d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736906"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a><span data-ttu-id="95a23-102">DirectQuery の優先接続方法の設定または変更</span><span class="sxs-lookup"><span data-stu-id="95a23-102">Set or Change the Preferred Connection Method for DirectQuery</span></span>
  <span data-ttu-id="95a23-103">DirectQuery モードで使用するモデルを作成する場合は、まず、DirectQuery の使用をサポートするようにデザイン環境を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a23-103">When you create a model for use in DirectQuery mode, you must first configure the design environment to support use of DirectQuery.</span></span> <span data-ttu-id="95a23-104">これを行うには、「 [SSAS 表形式&#41;&#40;DirectQuery デザインモードを有効に](tabular-models/enable-directquery-mode-in-ssdt.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95a23-104">To do this, see [Enable DirectQuery Design Mode &#40;SSAS Tabular&#41;](tabular-models/enable-directquery-mode-in-ssdt.md).</span></span>  
  
 <span data-ttu-id="95a23-105">モデルを配置する準備ができたら、追加のプロパティを設定して、ユーザーが DirectQuery モードの 1 つを使用してモデルにアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a23-105">When you are ready to deploy the model, you must set some additional properties to enable users to access your model using one of the DirectQuery modes:</span></span>  
  
-   <span data-ttu-id="95a23-106">モデルに対するクエリでキャッシュ データとリレーショナル データ ソースのどちらを使用する必要があるかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a23-106">You must indicate whether queries against the model should use cached data or the relational data source.</span></span> <span data-ttu-id="95a23-107">ハイブリッド モードまたは DirectQuery のみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="95a23-107">You can use a hybrid mode or DirectQuery only.</span></span>  
  
-   <span data-ttu-id="95a23-108">パーティションを使用している場合は、DirectQuery データ ソースとして使用するパーティションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a23-108">If you are using partitions, you must indicate which partition to use as the DirectQuery data source.</span></span>  
  
-   <span data-ttu-id="95a23-109">SQL Server データ ソースにアクセスするユーザーの権限借用オプションを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a23-109">You must set impersonation options for users who will be accessing the SQL Server data source.</span></span>  
  
 <span data-ttu-id="95a23-110">この手順では、デザイナーで DirectQuery モデルの優先接続方法を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95a23-110">This procedure describes how to set the preferred connection method for a DirectQuery model in the designer.</span></span> <span data-ttu-id="95a23-111">モデルの配置後に [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でこのプロパティを変更する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="95a23-111">It also describes how you can change this property in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] after the model has been deployed.</span></span>  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a><span data-ttu-id="95a23-112">DirectQuery モデルの優先接続方法を設定するには</span><span class="sxs-lookup"><span data-stu-id="95a23-112">To set the preferred connection method for a DirectQuery model</span></span>  
  
1.  <span data-ttu-id="95a23-113">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、DirectQuery モデルのソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="95a23-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution file for the DirectQuery model.</span></span>  
  
2.  <span data-ttu-id="95a23-114">Visual Studio で、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95a23-114">In Visual Studio, from the **Project** menu, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="95a23-115">**[プロパティ]** ペインで、 **DirectQueryMode**プロパティを、DirectQuery の使用をサポートする値の 1 つに変更します。</span><span class="sxs-lookup"><span data-stu-id="95a23-115">In the **Properties** pane, change the property, **DirectQueryMode**, to one of the values that support DirectQuery usage:</span></span>  
  
    -   <span data-ttu-id="95a23-116">**インメモリ (DirectQuery あり)**: このオプションを使用する場合、モデルは配置されますが、モデルに対してクエリを実行する前にキャッシュを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a23-116">**InMemory with DirectQuery**: If you use this option, the model is deployed but you must process the cache before you can run queries against the model.</span></span>  
  
    -   <span data-ttu-id="95a23-117">**DirectQuery (インメモリあり)**: このオプションを使用する場合、キャッシュは既に処理されている場合にクライアントで使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="95a23-117">**DirectQuery with InMemory**: If you use this option, the cache will be available for use by clients if it has already been processed.</span></span> <span data-ttu-id="95a23-118">この設定でモデルを配置し、キャッシュを処理しない場合、一部のクライアントではモデルに接続しようとするとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="95a23-118">If you deploy the model with this setting and do not process the cache, some clients must get an error on trying to connect to the model.</span></span>  
  
    -   <span data-ttu-id="95a23-119">**DirectQuery のみ**: このオプションを使用する場合、メタデータは配置されますが、モデルにはデータがありません。</span><span class="sxs-lookup"><span data-stu-id="95a23-119">**DirectQuery only**: If you use this option, the metadata is deployed but the model has no data in it.</span></span> <span data-ttu-id="95a23-120">インメモリ モードを使用して接続しようとするクライアントでは、モデルが存在しないか処理されていないことを示すエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="95a23-120">Clients that attempt to connect using In-Memory mode will get an error, indicating that the model does not exist or has not been processed.</span></span>  
  
4.  <span data-ttu-id="95a23-121">エラーがある場合は、Visual Studio で **[エラー一覧]** を開き、モデルが DirectQuery モードで配置されるのを妨げている問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="95a23-121">If there are errors, in Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being deployed in DirectQuery mode.</span></span>  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a><span data-ttu-id="95a23-122">DirectQuery モデルの優先接続方法を検証または変更するには</span><span class="sxs-lookup"><span data-stu-id="95a23-122">To verify or change the preferred connection method for a DirectQuery model</span></span>  
  
1.  <span data-ttu-id="95a23-123">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、DirectQuery モデルを配置したインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="95a23-123">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to the instance where you deployed the DirectQuery model.</span></span>  
  
2.  <span data-ttu-id="95a23-124">モデル データベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95a23-124">Right-click the model database, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="95a23-125">**[プロパティ]** ペインで、 **DirectQueryMode**プロパティを次のいずれかの値に変更します。</span><span class="sxs-lookup"><span data-stu-id="95a23-125">In the **Properties** pane, change the property, **DirectQueryMode**, to one of these values:</span></span>  
  
    -   <span data-ttu-id="95a23-126">**DirectQuery のみ**</span><span class="sxs-lookup"><span data-stu-id="95a23-126">**DirectQuery Only**</span></span>  
  
    -   <span data-ttu-id="95a23-127">**インメモリ (DirectQuery あり)**</span><span class="sxs-lookup"><span data-stu-id="95a23-127">**InMemory with DirectQuery**</span></span>  
  
    -   <span data-ttu-id="95a23-128">**DirectQuery と InMemory**</span><span class="sxs-lookup"><span data-stu-id="95a23-128">**DirectQuery with InMemory**</span></span>  
  
 <span data-ttu-id="95a23-129">これらのプロパティは、配置前に Visual Studio でプロジェクトに設定したプロパティと同じです。</span><span class="sxs-lookup"><span data-stu-id="95a23-129">Note that these properties are the same as the properties that you set on the project before deployment in Visual Studio.</span></span> <span data-ttu-id="95a23-130">DirectQuery の使用をサポートするようにモデルを構成してあれば、DirectQuery モードの優先接続方法をいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="95a23-130">You can change the preferred connection mode for DirectQuery mode at any time, provided that you have configured the model to support DirectQuery usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a23-131">参照</span><span class="sxs-lookup"><span data-stu-id="95a23-131">See Also</span></span>  
 <span data-ttu-id="95a23-132">[SSAS テーブル &#40;の DirectQuery モード&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="95a23-132">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="95a23-133">SSAS 表形式&#41;&#40;DirectQuery デザインモードを有効にする</span><span class="sxs-lookup"><span data-stu-id="95a23-133">Enable DirectQuery Design Mode &#40;SSAS Tabular&#41;</span></span>](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  
