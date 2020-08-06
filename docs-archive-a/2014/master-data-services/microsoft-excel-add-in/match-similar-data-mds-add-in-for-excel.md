---
title: 類似データの結合 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 70dea36de557c6fda909d06ee19ff8fa2ed6908d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715474"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a><span data-ttu-id="36358-102">類似データの照合 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="36358-102">Match Similar Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="36358-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で、Data Quality Services (DQS) 機能を使用してデータ内の類似性を見つけます。</span><span class="sxs-lookup"><span data-stu-id="36358-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use Data Quality Services (DQS) functionality to find similarities in your data.</span></span>  
  
 <span data-ttu-id="36358-104">この手順を実行するには、次のどちらかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="36358-104">To perform this procedure, you can:</span></span>  
  
-   <span data-ttu-id="36358-105">既定の Data Quality Services ナレッジ ベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="36358-105">Use the default Data Quality Services knowledge base, or</span></span>  
  
-   <span data-ttu-id="36358-106">独自のカスタムな DQS ナレッジ ベースと照合ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="36358-106">Create your own custom DQS knowledge base and matching policy.</span></span> <span data-ttu-id="36358-107">詳細については、「 [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="36358-107">For more information, see [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="36358-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="36358-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="36358-109">MDS によって管理されるデータが含まれているワークシートが必要です。</span><span class="sxs-lookup"><span data-stu-id="36358-109">You must have a worksheet that contains MDS-managed data.</span></span> <span data-ttu-id="36358-110">詳細については、「 [MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36358-110">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="36358-111">省略可能。</span><span class="sxs-lookup"><span data-stu-id="36358-111">Optional.</span></span> <span data-ttu-id="36358-112">類似性をチェックする前に、MDS によって管理されるデータとその他のデータを結合することができます。</span><span class="sxs-lookup"><span data-stu-id="36358-112">You can combine other data with the MDS-managed data before checking for similarities.</span></span> <span data-ttu-id="36358-113">詳細については、「 [データの結合 (Excel 用 MDS アドイン)](combine-data-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36358-113">For more information, see [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).</span></span>  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a><span data-ttu-id="36358-114">既定のナレッジ ベースを使用して類似性を見つけるには</span><span class="sxs-lookup"><span data-stu-id="36358-114">To find similarities by using the default knowledge base</span></span>  
  
1.  <span data-ttu-id="36358-115">MDS によって管理されるデータを含むワークシートで、 **[データ品質]** グループの **[データの照合]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36358-115">From the worksheet that contains MDS-managed data, in the **Data Quality** group, click **Match Data**.</span></span>  
  
2.  <span data-ttu-id="36358-116">**[データの照合]** ダイアログ ボックスで、 **[DQS 知識ベース]** の一覧から **[DQS データ (既定値)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36358-116">In the **Match Data** dialog box, from the **DQS Knowledge Base** list, select **DQS Data (default)**.</span></span>  
  
3.  <span data-ttu-id="36358-117">照合するデータを含む各列について、ダイアログ ボックスで行を追加します。</span><span class="sxs-lookup"><span data-stu-id="36358-117">For each column that contains data you want to match, add a row in the dialog box.</span></span> <span data-ttu-id="36358-118">このダイアログ ボックスのフィールドの詳細については、「 [照合ルールのパラメーターを設定する方法](../../data-quality-services/create-a-matching-policy.md#MatchingRules)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36358-118">For information about the fields in this dialog box, see [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules).</span></span>  
  
4.  <span data-ttu-id="36358-119">すべての重み値の合計が 100% になったら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36358-119">When the total of all weight values equals 100 percent, click **OK**.</span></span>  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a><span data-ttu-id="36358-120">カスタム ナレッジ ベースを使用して類似性を見つけるには</span><span class="sxs-lookup"><span data-stu-id="36358-120">To find similarities by using a custom knowledge base</span></span>  
  
1.  <span data-ttu-id="36358-121">MDS によって管理されるデータを含むワークシートで、 **[データ品質]** グループの **[データの照合]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36358-121">From the worksheet that contains MDS-managed data, in the **Data Quality** group, click **Match Data**.</span></span>  
  
2.  <span data-ttu-id="36358-122">**[DQS 知識ベース]** の一覧から、カスタム ナレッジ ベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="36358-122">From the **DQS Knowledge Base** list, select the name of your custom knowledge base.</span></span>  
  
3.  <span data-ttu-id="36358-123">ワークシート内の各列について、DQS ドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="36358-123">For each column in the worksheet, select a DQS domain.</span></span>  
  
4.  <span data-ttu-id="36358-124">すべての DQS ドメインがワークシート内の列にマップされたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36358-124">When all DQS domains are mapped to columns in the worksheet, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="36358-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="36358-125">Next Steps</span></span>  
  
-   <span data-ttu-id="36358-126">類似するデータを判別するには、追加情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="36358-126">View additional information to determine which data is similar.</span></span> <span data-ttu-id="36358-127">詳細については、「[データ品質照合の列 (Excel 用 MDS アドイン)](data-quality-matching-columns-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36358-127">For more information, see [Data Quality Matching Columns &#40;MDS Add-in for Excel&#41;](data-quality-matching-columns-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36358-128">参照</span><span class="sxs-lookup"><span data-stu-id="36358-128">See Also</span></span>  
 <span data-ttu-id="36358-129">[Excel 用 MDS アドインでのデータ品質照合](data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="36358-129">[Data Quality Matching in the MDS Add-in for Excel](data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="36358-130">データ照合</span><span class="sxs-lookup"><span data-stu-id="36358-130">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
