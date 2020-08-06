---
title: データ品質照合の列 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 939ec9727cc81ce3b206b8bc7ca3ed8dd62c3877
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631120"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a><span data-ttu-id="62793-102">データ品質照合の列 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="62793-102">Data Quality Matching Columns (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="62793-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]でデータを照合した後、リボンの **[データ品質]** グループの **[詳細の表示]** をクリックすると照合の詳細が含まれる列を表示できます。</span><span class="sxs-lookup"><span data-stu-id="62793-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], after you match data, in the **Data Quality** group on the ribbon, you can click **Show Details** to display columns that provide matching details.</span></span>  
  
 <span data-ttu-id="62793-104">次の表に、データの照合時に表示される列を示します。</span><span class="sxs-lookup"><span data-stu-id="62793-104">The following table shows the columns that are displayed when matching data.</span></span>  
  
|<span data-ttu-id="62793-105">名前</span><span class="sxs-lookup"><span data-stu-id="62793-105">Name</span></span>|<span data-ttu-id="62793-106">説明</span><span class="sxs-lookup"><span data-stu-id="62793-106">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="62793-107">**CLUSTER_ID**</span><span class="sxs-lookup"><span data-stu-id="62793-107">**CLUSTER_ID**</span></span>|<span data-ttu-id="62793-108">類似レコードのグループ化に使用する一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="62793-108">A unique identifier used to group similar records.</span></span> <span data-ttu-id="62793-109">類似するすべての行は、同じ **CLUSTER_ID**を持ちます。</span><span class="sxs-lookup"><span data-stu-id="62793-109">All rows that are similar have the same **CLUSTER_ID**.</span></span> <span data-ttu-id="62793-110">**CLUSTER_ID** が行に対して表示されない場合、類似レコードが見つかっていません。</span><span class="sxs-lookup"><span data-stu-id="62793-110">If no **CLUSTER_ID** is displayed for a row, then no similar records were found.</span></span>|  
|<span data-ttu-id="62793-111">**RECORD_ID**</span><span class="sxs-lookup"><span data-stu-id="62793-111">**RECORD_ID**</span></span>|<span data-ttu-id="62793-112">レコードの識別に使用する一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="62793-112">A unique identifier used to identify records.</span></span> <span data-ttu-id="62793-113">MDS リポジトリに格納されているコード値と同様に、レコードの識別に使用される値です。</span><span class="sxs-lookup"><span data-stu-id="62793-113">Similar to the Code value stored in the MDS repository, it is a value used to identify a record.</span></span> <span data-ttu-id="62793-114">照合が実行されるたびに自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="62793-114">It is generated automatically each time matching takes place.</span></span>|  
|<span data-ttu-id="62793-115">**PIVOT_MARK**</span><span class="sxs-lookup"><span data-stu-id="62793-115">**PIVOT_MARK**</span></span>|<span data-ttu-id="62793-116">他のレコードと比較される任意のレコードで、スコアの値はありません。</span><span class="sxs-lookup"><span data-stu-id="62793-116">An arbitrary record that other records are compared to; it does not have a score value.</span></span>|  
|<span data-ttu-id="62793-117">**学生**</span><span class="sxs-lookup"><span data-stu-id="62793-117">**SCORE**</span></span>|<span data-ttu-id="62793-118">グループ内のレコードがピボット レコードとどの程度類似しているかを表します。</span><span class="sxs-lookup"><span data-stu-id="62793-118">Represents how similar the records in the group are to the pivot record.</span></span> <span data-ttu-id="62793-119">このスコアは DQS によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="62793-119">This score is determined by DQS.</span></span> <span data-ttu-id="62793-120">スコアが表示されない場合、そのレコードは他のレコードのピボットであるか、照合が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="62793-120">If no score is displayed, either the record is the pivot for other records, or no matches were found.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62793-121">参照</span><span class="sxs-lookup"><span data-stu-id="62793-121">See Also</span></span>  
 <span data-ttu-id="62793-122">[Excel 用 MDS アドインでのデータ品質照合](data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="62793-122">[Data Quality Matching in the MDS Add-in for Excel](data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="62793-123">[類似データ &#40;Excel 用 MDS アドインに一致&#41;](match-similar-data-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="62793-123">[Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="62793-124">データ照合</span><span class="sxs-lookup"><span data-stu-id="62793-124">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
