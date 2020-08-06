---
title: Excel 用 MDS アドインでのデータ品質照合 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: be78d051-0d56-46d3-bb89-327e218dadd6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 037e535452e7f19644837e0cbcfd02efec5422b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643999"
---
# <a name="data-quality-matching-in-the-mds-add-in-for-excel"></a><span data-ttu-id="1ee72-102">Excel 用 MDS アドインでのデータ品質照合</span><span class="sxs-lookup"><span data-stu-id="1ee72-102">Data Quality Matching in the MDS Add-in for Excel</span></span>
  <span data-ttu-id="1ee72-103">後で、MDS リポジトリにさらにデータを追加する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1ee72-103">Over time, you will want to add more data to the MDS repository.</span></span> <span data-ttu-id="1ee72-104">データを追加する前に、新しいデータと既に MDS で管理されているデータを比較することは、重複するデータや不正確なデータの追加を避けるために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1ee72-104">Before adding data, it can be useful to compare the new data to the data that's already managed in MDS, to ensure you are not adding duplicate or inaccurate data.</span></span>  
  
 <span data-ttu-id="1ee72-105">MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Data Quality Services (DQS) 機能を使用して、類似するデータを照合します。</span><span class="sxs-lookup"><span data-stu-id="1ee72-105">The MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] uses the Data Quality Services (DQS) feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to match data that's similar.</span></span> <span data-ttu-id="1ee72-106">アドインの照合機能を使用すると、類似するレコードがグループ化され、結果の精度を表すスコアが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ee72-106">When you use the matching functionality in the Add-in, similar records are grouped together and a score that represents the accuracy of the result is displayed.</span></span> <span data-ttu-id="1ee72-107">DQS によって提供される照合機能の詳細については、「 [データ照合](../../data-quality-services/data-matching.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ee72-107">For more information about the matching functionality provided by DQS, see [Data Matching](../../data-quality-services/data-matching.md).</span></span>  
  
## <a name="workflow-for-data-quality-matching"></a><span data-ttu-id="1ee72-108">データ品質照合のワークフロー</span><span class="sxs-lookup"><span data-stu-id="1ee72-108">Workflow for Data Quality Matching</span></span>  
 <span data-ttu-id="1ee72-109">MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で DQS を使用する場合、次のワークフローを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ee72-109">When using DQS with the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use the following workflow:</span></span>  
  
1.  <span data-ttu-id="1ee72-110">MDS によって管理されるデータの一覧を取得して、MDS によって管理されていないデータの一覧と結合します。</span><span class="sxs-lookup"><span data-stu-id="1ee72-110">Retrieve a list of MDS-managed data and combine it with a list that is not managed in MDS.</span></span> <span data-ttu-id="1ee72-111">詳細については、「 [データの結合 (Excel 用 MDS アドイン)](combine-data-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ee72-111">For more information, see [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="1ee72-112">DQS ナレッジを使用して、結合した一覧のデータを比較します。</span><span class="sxs-lookup"><span data-stu-id="1ee72-112">Use DQS knowledge to compare the data in the combined list.</span></span> <span data-ttu-id="1ee72-113">詳細については、「 [類似データの照合 (Excel 用 MDS アドイン)](match-similar-data-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ee72-113">For more information, see [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).</span></span>  
  
3.  <span data-ttu-id="1ee72-114">DQS で見つかった類似性について詳細を確認するには、詳細列を表示します。</span><span class="sxs-lookup"><span data-stu-id="1ee72-114">To view more details about the similarities found by DQS, show the detail columns.</span></span>  
  
4.  <span data-ttu-id="1ee72-115">結果を確認し、MDS リポジトリに追加する必要があるデータと重複しているデータを判別します。</span><span class="sxs-lookup"><span data-stu-id="1ee72-115">Go through the results and determine which data should be added to the MDS repository and which data is duplicated.</span></span>  
  
5.  <span data-ttu-id="1ee72-116">新しいデータと更新されたデータを MDS リポジトリにパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="1ee72-116">Publish the new and/or updated data to the MDS repository.</span></span>  
  
## <a name="knowledge-bases"></a><span data-ttu-id="1ee72-117">ナレッジ ベース</span><span class="sxs-lookup"><span data-stu-id="1ee72-117">Knowledge Bases</span></span>  
 <span data-ttu-id="1ee72-118">アドインで提供される照合結果は、DQS ナレッジ ベースに基づいています。</span><span class="sxs-lookup"><span data-stu-id="1ee72-118">The matching results provided in the Add-in are based on a DQS knowledge base.</span></span>  
  
-   <span data-ttu-id="1ee72-119">既定のナレッジ ベース (DQS データ) は、DQS のインストール時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="1ee72-119">The default knowledge base (DQS Data) is created when DQS is installed.</span></span> <span data-ttu-id="1ee72-120">(Data Quality Client で既定のナレッジ ベースに照合ポリシーを追加せずに) 既定のナレッジ ベースを使用する場合は、ワークシート内の列をナレッジ ベース内のドメインにマップしてから、選択したドメインに重み値を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ee72-120">If you choose to use the default knowledge base (without adding a matching policy to the default knowledge base in the Data Quality Client), you must map columns in the worksheet to domains in the knowledge base, and then assign a weight value to the domains you choose.</span></span>  
  
-   <span data-ttu-id="1ee72-121">Data Quality Client を使用して、照合ポリシーと共にナレッジ ベースを作成するか、既定のナレッジ ベースに照合ポリシーを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="1ee72-121">You can use the Data Quality Client to create a new knowledge base with a matching policy, or to add a matching policy to the default knowledge base.</span></span> <span data-ttu-id="1ee72-122">この場合、重み値は既に作成済みの照合ポリシーによって決定されるので、列をドメインにマップするだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="1ee72-122">In this case, the weight values are determined by the matching policy you already created and you need only to map the columns to the domains.</span></span> <span data-ttu-id="1ee72-123">詳細については、「 [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="1ee72-123">For more information, see [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).</span></span>  
  
 <span data-ttu-id="1ee72-124">サポート技術情報の詳細については、「 [DQS のナレッジ ベースとドメイン](../../data-quality-services/dqs-knowledge-bases-and-domains.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ee72-124">For more information about knowledge bases, see [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1ee72-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1ee72-125">Related Tasks</span></span>  
  
|<span data-ttu-id="1ee72-126">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="1ee72-126">Task Description</span></span>|<span data-ttu-id="1ee72-127">トピック</span><span class="sxs-lookup"><span data-stu-id="1ee72-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1ee72-128">外部データを MDS によって管理されるデータと結合して、比較できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1ee72-128">Combine external data with MDS-managed data in preparation to compare it.</span></span>|[<span data-ttu-id="1ee72-129">データの結合 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="1ee72-129">Combine Data &#40;MDS Add-in for Excel&#41;</span></span>](combine-data-mds-add-in-for-excel.md)|  
|<span data-ttu-id="1ee72-130">DQS ナレッジを使用して、データの類似性を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1ee72-130">Use DQS knowledge to find similarities in your data.</span></span>|[<span data-ttu-id="1ee72-131">類似データの照合 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="1ee72-131">Match Similar Data &#40;MDS Add-in for Excel&#41;</span></span>](match-similar-data-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="1ee72-132">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="1ee72-132">Related Content</span></span>  
  
-   [<span data-ttu-id="1ee72-133">データ &#40;Excel 用 MDS アドインの公開&#41;</span><span class="sxs-lookup"><span data-stu-id="1ee72-133">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="1ee72-134">データ照合</span><span class="sxs-lookup"><span data-stu-id="1ee72-134">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
