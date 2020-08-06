---
title: '[クエリバインドの詳細] ([パーティションソース] ダイアログボックス) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59d2ae1fed9d22366786e21a287a621f08418a5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641255"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="5722b-102">クエリ バインドの詳細 ([パーティション ソース] ダイアログ ボックス) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="5722b-102">Query Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5722b-103">**[パーティション ソース]** ダイアログ ボックスの **[クエリ バインド]** オプションを使用すると、パーティション用のデータを表示するクエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5722b-103">Use the **Query Binding** option in the **Partition Source** dialog box to specify the query that provides the data for the partition.</span></span> <span data-ttu-id="5722b-104">このペインを表示するには、 **[パーティション ソース]** ダイアログ ボックスの **[バインドの種類]** オプションで **[クエリ バインド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5722b-104">You can display this pane by selecting **Query Binding** from the **Binding type** option in the **Partition Source** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5722b-105">Options</span><span class="sxs-lookup"><span data-stu-id="5722b-105">Options</span></span>  
 <span data-ttu-id="5722b-106">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="5722b-106">**Data source**</span></span>  
 <span data-ttu-id="5722b-107">パーティションのファクト データを提供するためのクエリが実行されるデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="5722b-107">Select the data source on which the query is executed to provide fact data for the partition.</span></span>  
  
 <span data-ttu-id="5722b-108">**クエリ**</span><span class="sxs-lookup"><span data-stu-id="5722b-108">**Query**</span></span>  
 <span data-ttu-id="5722b-109">パーティションを処理する際にファクト データの取得に使用される SQL ステートメントを入力、または変更します。</span><span class="sxs-lookup"><span data-stu-id="5722b-109">Type or modify the SQL statement used when retrieving fact data when the partition is processed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5722b-110">WHERE 句を指定することにより、レコードのサブセットをこのパーティションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5722b-110">By specifying a WHERE clause, a subset of records can be used for this partition.</span></span> <span data-ttu-id="5722b-111">複数のパーティションが 1 つのファクト テーブルに基づいている場合は、データを複製しないでください。</span><span class="sxs-lookup"><span data-stu-id="5722b-111">This is essential to prevent duplication of data when multiple partitions are based on a single fact table.</span></span> <span data-ttu-id="5722b-112">詳細については、「[[パーティションソース] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5722b-112">For more information, see [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5722b-113">**確認事項**</span><span class="sxs-lookup"><span data-stu-id="5722b-113">**Check**</span></span>  
 <span data-ttu-id="5722b-114">クリックすると、 **クエリ** 内のステートメントが有効な SQL ステートメントであるかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="5722b-114">Click to verify that the statement in **Query** is a valid SQL statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5722b-115">参照</span><span class="sxs-lookup"><span data-stu-id="5722b-115">See Also</span></span>  
 <span data-ttu-id="5722b-116">[[パーティションソース] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="5722b-116">[Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
