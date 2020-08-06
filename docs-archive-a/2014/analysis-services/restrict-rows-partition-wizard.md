---
title: 行の制限 (パーティションウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.typefilterexpression.f1
ms.assetid: eec8da8f-eab4-4ac4-a81d-995c814f88ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b0acc9ab24cfe92877d9abcd86353c85b4f8905
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633398"
---
# <a name="restrict-rows-partition-wizard"></a><span data-ttu-id="012c6-102">[行の制限] (パーティション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="012c6-102">Restrict Rows (Partition Wizard)</span></span>
  <span data-ttu-id="012c6-103">**[行の制限]** ページを使用すると、指定したテーブルから取得、集計されて、パーティションに含まれる行を制限できます。</span><span class="sxs-lookup"><span data-stu-id="012c6-103">Use the **Restrict Rows** page to restrict the rows that will be retrieved from the specified table and will be aggregated and included in the partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="012c6-104"> このページは、 **[基になる情報の指定]** ページでテーブルを 1 つ選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="012c6-104">This page is appears only if you selected a single table in the **Specify Source Information** page.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="012c6-105"> 他のパーティションで使用されている **[基になる情報の指定]** ページの **[使用できるテーブル]** でテーブルを指定した場合は、 **[行の制限]** ページでクエリを指定するか、キューブでリスクの複製データを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="012c6-105">If you specified a table in **Available Tables** on the **Specify Source Information** page that is used by another partition, you must provide a query in the **Restrict Rows** page or risk duplicating data in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="012c6-106">Options</span><span class="sxs-lookup"><span data-stu-id="012c6-106">Options</span></span>  
 <span data-ttu-id="012c6-107">**[クエリを指定して行を制限する]**</span><span class="sxs-lookup"><span data-stu-id="012c6-107">**Specify a query to restrict rows**</span></span>  
 <span data-ttu-id="012c6-108">**[クエリ]** ボックスに、行を制限するクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="012c6-108">Select to enter a query that restricts rows into the **Query** box.</span></span>  
  
 <span data-ttu-id="012c6-109">このオプションを選択していて **[クエリ]** が空の場合、以前に選択したテーブルからすべての列と行を取得する SQL ステートメントと共に、オプションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="012c6-109">If **Supply a WHERE clause** is empty when this option is selected, that option is populated with an SQL statement that retrieves all columns and all rows from the previously selected table.</span></span>  
  
 <span data-ttu-id="012c6-110">**クエリ**</span><span class="sxs-lookup"><span data-stu-id="012c6-110">**Query**</span></span>  
 <span data-ttu-id="012c6-111">パーティションの処理時に、テーブルから行を取得する場合に使用される SQL ステートメントを、入力または変更します。</span><span class="sxs-lookup"><span data-stu-id="012c6-111">Type or modify the SQL statement used when retrieving rows from the table when the partition is processed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="012c6-112">WHERE 句を指定することにより、レコードのサブセットをこのパーティションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="012c6-112">By specifying a WHERE clause, a subset of records can be used for this partition.</span></span> <span data-ttu-id="012c6-113">複数のパーティションが 1 つのファクト テーブルに基づいている場合は、データを複製しないでください。</span><span class="sxs-lookup"><span data-stu-id="012c6-113">This is essential to prevent duplication of data when multiple partitions are based on a single fact table.</span></span>  
  
 <span data-ttu-id="012c6-114">**確認事項**</span><span class="sxs-lookup"><span data-stu-id="012c6-114">**Check**</span></span>  
 <span data-ttu-id="012c6-115">**[クエリ]** のステートメントが有効な SQL ステートメントであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="012c6-115">Verifies that the statement in **Query** is a valid SQL statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="012c6-116">参照</span><span class="sxs-lookup"><span data-stu-id="012c6-116">See Also</span></span>  
 [<span data-ttu-id="012c6-117">パーティション (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="012c6-117">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
