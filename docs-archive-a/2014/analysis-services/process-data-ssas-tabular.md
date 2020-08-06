---
title: データの処理 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2066cb6d871f43dda719cab3539253db97bfca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741358"
---
# <a name="process-data-ssas-tabular"></a><span data-ttu-id="aa353-102">データの処理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="aa353-102">Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="aa353-103">キャッシュ モードでデータをテーブル モデルにインポートするときは、そのデータのインポート時点でのスナップショットを取得することになります。</span><span class="sxs-lookup"><span data-stu-id="aa353-103">When you import data into a tabular model, in Cached mode, you are capturing a snapshot of that data at the time of import.</span></span> <span data-ttu-id="aa353-104">場合によっては、そのデータは変更されることはないため、モデルで更新される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="aa353-104">In some cases, that data may never change and it does not need to be updated in the model.</span></span> <span data-ttu-id="aa353-105">ただし、インポートするデータが定期的に変更され、かつデータ ソースから取得した最新データをモデルで反映できるようにするため、そのデータを処理 (更新) し計算済みデータを再計算しなければならなくなる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="aa353-105">However, it is more likely that the data you are importing from changes regularly, and in order for your model to reflect the most recent data from the data sources, it is necessary to process (refresh) the data and re-calculate calculated data.</span></span> <span data-ttu-id="aa353-106">モデルのデータを更新するため、すべてのテーブルと個別のテーブルでパーティションまたはデータ ソース接続ごとに処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="aa353-106">To update the data in your model, you perform a process action on all tables, on an individual table, by a partition, or by a data source connection.</span></span>  
  
 <span data-ttu-id="aa353-107">モデル プロジェクト作成時には、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で処理アクションを手動で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa353-107">When authoring your model project, process actions must be initiated manually in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="aa353-108">モデルを配置した後は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して処理操作を実行するか、スクリプトを使用してスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="aa353-108">After a model has been deployed, process operations can be performed by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or scheduled by using a script.</span></span> <span data-ttu-id="aa353-109">ここで説明するタスクはすべて、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]でのモデル作成時に実行できる処理アクションに関係します。</span><span class="sxs-lookup"><span data-stu-id="aa353-109">Tasks described here all pertain to process actions that you can do during model authoring in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="aa353-110">配置済みモデルの処理アクションの詳細については、「[データベース、テーブル、またはパーティションの処理](tabular-models/process-database-table-or-partition-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa353-110">For more information about process actions for a deployed model, see [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="aa353-111">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="aa353-111">Related Tasks</span></span>  
  
|<span data-ttu-id="aa353-112">トピック</span><span class="sxs-lookup"><span data-stu-id="aa353-112">Topic</span></span>|<span data-ttu-id="aa353-113">説明</span><span class="sxs-lookup"><span data-stu-id="aa353-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="aa353-114">データの手動処理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="aa353-114">Manually Process Data &#40;SSAS Tabular&#41;</span></span>](manually-process-data-ssas-tabular.md)|<span data-ttu-id="aa353-115">モデル ワークスペース データを手動で処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aa353-115">Describes how to manually process model workspace data.</span></span>|  
|[<span data-ttu-id="aa353-116">データの処理のトラブルシューティング &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="aa353-116">Troubleshoot Process Data &#40;SSAS Tabular&#41;</span></span>](troubleshoot-process-data-ssas-tabular.md)|<span data-ttu-id="aa353-117">処理操作のトラブルシューティング方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aa353-117">Describes how to troubleshoot process operations.</span></span>|  
  
  
