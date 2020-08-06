---
title: DMX を使用したドリルスルークエリの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
author: minewiskan
ms.author: owend
ms.openlocfilehash: 618732bfe48f7b1fe777f7841d686b07877d10ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643022"
---
# <a name="create-drillthrough-queries-using-dmx"></a><span data-ttu-id="ac1fd-102">DMX を使用したドリルスルー クエリの作成</span><span class="sxs-lookup"><span data-stu-id="ac1fd-102">Create Drillthrough Queries using DMX</span></span>
  <span data-ttu-id="ac1fd-103">ドリルスルーをサポートするすべてのモデルでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または DMX をサポートするその他のクライアントで DMX クエリを作成することで、ケース データと構造データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-103">For all models that support drillthrough, you can retrieve case data and structure data by creating a DMX query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any other client that supports DMX.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ac1fd-104">データを表示するには、ドリルスルーが有効になっており、必要な権限がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-104">To view the data, drillthrough must have been enabled, and you must have the necessary permissions.</span></span>  
  
## <a name="specifying-drillthrough-options"></a><span data-ttu-id="ac1fd-105">ドリルスルー オプションの指定</span><span class="sxs-lookup"><span data-stu-id="ac1fd-105">Specifying Drillthrough Options</span></span>  
 <span data-ttu-id="ac1fd-106">モデル ケースと構造ケースを取得する場合の一般的な構文は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-106">The general syntax is for retrieving model cases and structure cases is as follows:</span></span>  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 <span data-ttu-id="ac1fd-107">DMX クエリを使用してケース データを返す方法については、「[SELECT FROM &#60;model&#62;.CASES (DMX)](/sql/dmx/select-from-model-content-dmx)」と「[SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-107">For additional information about using DMX queries to return case data, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) and [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ac1fd-108">例</span><span class="sxs-lookup"><span data-stu-id="ac1fd-108">Examples</span></span>  
 <span data-ttu-id="ac1fd-109">次に示す DMX クエリでは、タイム シリーズ モデルから特定の製品シリーズのケース データが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-109">The following DMX query returns the case data for a specific product series, from a time series model.</span></span> <span data-ttu-id="ac1fd-110">このクエリでは、`Amount` 列も返されます。この列はモデルでは使用されていませんが、マイニング構造では使用可能です。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-110">The query also returns the column `Amount`, which was not used in the model but is available in the mining structure.</span></span>  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 <span data-ttu-id="ac1fd-111">この例では、別名を使用して構造列の名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-111">Note that in this example, an alias has been used to rename the structure column.</span></span> <span data-ttu-id="ac1fd-112">構造列に別名を割り当てないと、'Expression' という名前で列が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-112">If you do not assign an alias to the structure column, the column is returned with the name 'Expression'.</span></span> <span data-ttu-id="ac1fd-113">これはすべての名前のない列に対する既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="ac1fd-113">This is the default behavior for all unnamed columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1fd-114">参照</span><span class="sxs-lookup"><span data-stu-id="ac1fd-114">See Also</span></span>  
 <span data-ttu-id="ac1fd-115">[データマイニング &#40;のドリルスルークエリ&#41;](drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ac1fd-115">[Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="ac1fd-116">マイニング構造でのドリルスルー</span><span class="sxs-lookup"><span data-stu-id="ac1fd-116">Drillthrough on Mining Structures</span></span>](drillthrough-on-mining-structures.md)  
  
  
