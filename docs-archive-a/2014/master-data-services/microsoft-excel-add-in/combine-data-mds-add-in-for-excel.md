---
title: データの結合 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bc2d5bffb6d7a12164a8643e9a790b32538f8979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714478"
---
# <a name="combine-data-mds-add-in-for-excel"></a><span data-ttu-id="94c76-102">データの結合 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="94c76-102">Combine Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="94c76-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で、パブリッシュする前にデータを比較する場合は、2 つのワークシートのデータを結合します。</span><span class="sxs-lookup"><span data-stu-id="94c76-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], combine data from two worksheets when you want to compare data before publishing.</span></span> <span data-ttu-id="94c76-104">この手順では、2 つのワークシートのデータを 1 つに結合します。</span><span class="sxs-lookup"><span data-stu-id="94c76-104">In this procedure, you combine data from a two worksheets into one.</span></span> <span data-ttu-id="94c76-105">これにより、さらに比較を実行して、MDS リポジトリにパブリッシュするデータを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="94c76-105">Then you can perform further comparisons and determine which data, if any, to publish to the MDS repository.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="94c76-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="94c76-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="94c76-107">MDS によって管理されるデータが含まれているワークシートが必要です。</span><span class="sxs-lookup"><span data-stu-id="94c76-107">You must have a worksheet that contains MDS-managed data.</span></span> <span data-ttu-id="94c76-108">詳細については、「 [MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94c76-108">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="94c76-109">MDS によって管理されるデータに結合するデータが含まれているワークシートが必要です。</span><span class="sxs-lookup"><span data-stu-id="94c76-109">You must have a worksheet that contains data you want to combine with MDS-managed data.</span></span> <span data-ttu-id="94c76-110">このシートには、ヘッダー行が必要です。</span><span class="sxs-lookup"><span data-stu-id="94c76-110">This sheet must have a header row.</span></span>  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a><span data-ttu-id="94c76-111">MDS によって管理されるシートに管理されないデータを結合するには</span><span class="sxs-lookup"><span data-stu-id="94c76-111">To combine non-managed data into an MDS-managed sheet</span></span>  
  
1.  <span data-ttu-id="94c76-112">MDS によって管理されるデータを含むシートで、 **[パブリッシュと検証]** グループの **[データの結合]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94c76-112">On the sheet that contains MDS-managed data, in the **Publish and Validate** group, click **Combine Data**.</span></span>  
  
2.  <span data-ttu-id="94c76-113">**[データの結合]** ダイアログ ボックスで、 **[MDS データと結合する範囲]** ボックスの横にあるアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="94c76-113">In the **Combine Data** dialog box, next to the **Range to combine with MDS data** text box, click the icon.</span></span> <span data-ttu-id="94c76-114">ダイアログ ボックスが縮小されます。</span><span class="sxs-lookup"><span data-stu-id="94c76-114">The dialog box contracts.</span></span>  
  
3.  <span data-ttu-id="94c76-115">結合するデータを含むシートをクリックします。</span><span class="sxs-lookup"><span data-stu-id="94c76-115">Click the sheet that contains the data you want to combine.</span></span>  
  
4.  <span data-ttu-id="94c76-116">シート上の結合するすべてのセル (ヘッダー行を含む) を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="94c76-116">Highlight all cells on the sheet that you want to combine, including the header row.</span></span>  
  
5.  <span data-ttu-id="94c76-117">**[データの結合]** ダイアログ ボックスで、アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="94c76-117">In the **Combine Data** dialog box, click the icon.</span></span> <span data-ttu-id="94c76-118">ダイアログ ボックスが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="94c76-118">The dialog box expands.</span></span>  
  
6.  <span data-ttu-id="94c76-119">MDS エンティティに一覧表示される列について、 **[対応する列]** の下にある列を選択します。</span><span class="sxs-lookup"><span data-stu-id="94c76-119">For a column listed for the MDS entity, select a column under **Corresponding Column**.</span></span> <span data-ttu-id="94c76-120">すべての MDS 列に対応する列が必要なわけではありません。</span><span class="sxs-lookup"><span data-stu-id="94c76-120">All MDS columns do not need corresponding columns.</span></span>  
  
7.  <span data-ttu-id="94c76-121">**[結合]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94c76-121">Click **Combine**.</span></span> <span data-ttu-id="94c76-122">MDS からのデータか外部ソースからのデータかを示す **[SOURCE]** 列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="94c76-122">A **SOURCE** column is displayed, indicating whether the data is from MDS or an external source.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="94c76-123">次の手順</span><span class="sxs-lookup"><span data-stu-id="94c76-123">Next Steps</span></span>  
  
-   <span data-ttu-id="94c76-124">MDS によって管理されるデータと外部データの類似性を見つける場合は、「[類似データの照合 &#40;Excel 用 MDS アドイン&#41;](match-similar-data-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94c76-124">To find similarities between the MDS-managed and external data, see [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c76-125">参照</span><span class="sxs-lookup"><span data-stu-id="94c76-125">See Also</span></span>  
 <span data-ttu-id="94c76-126">[データ &#40;Excel 用 MDS アドインの読み込み&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="94c76-126">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="94c76-127">Excel 用 MDS アドインでのデータ品質照合</span><span class="sxs-lookup"><span data-stu-id="94c76-127">Data Quality Matching in the MDS Add-in for Excel</span></span>](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
