---
title: データフローの分析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 184b53d3e982cd80d7c9c0909538a751585ae21d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633986"
---
# <a name="analysis-of-data-flow"></a><span data-ttu-id="602de-102">データ フローの分析</span><span class="sxs-lookup"><span data-stu-id="602de-102">Analysis of Data Flow</span></span>
  <span data-ttu-id="602de-103">[catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` データベースビューを使用すると、パッケージのデータフローを分析できます。</span><span class="sxs-lookup"><span data-stu-id="602de-103">You can use the [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md)`SSISDB` database view to analyze the data flow of packages.</span></span> <span data-ttu-id="602de-104">このビューは、データ フロー コンポーネントが下流コンポーネントへデータを送信するたびに 1 行表示します。</span><span class="sxs-lookup"><span data-stu-id="602de-104">This view displays a row each time a data flow component sends data to a downstream component.</span></span> <span data-ttu-id="602de-105">この情報を使用して、各コンポーネントに送信される行をより詳しく理解できます。</span><span class="sxs-lookup"><span data-stu-id="602de-105">The information can be used to gain a deeper understanding of the rows that are sent to each component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="602de-106">catalog.execution_data_statistics ビューに関する情報を取得するために、ログ レベルは **詳細** に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="602de-106">The logging level must be set to **Verbose** in order to capture information with the catalog.execution_data_statistics view.</span></span>  
  
 <span data-ttu-id="602de-107">次の例では、パッケージのコンポーネント間で送信された行の数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="602de-107">The following example displays the number of rows sent between components of a package.</span></span>  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 <span data-ttu-id="602de-108">以下の例では、特定の実行で各コンポーネントによって送信された 1 ミリ秒あたりの行数が計算されます。</span><span class="sxs-lookup"><span data-stu-id="602de-108">The following example calculates the number of rows per millisecond sent by each component for a specific execution.</span></span> <span data-ttu-id="602de-109">計算される値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="602de-109">The calculated values are:</span></span>  
  
-   <span data-ttu-id="602de-110">**total_rows** - コンポーネントによって送信されたすべての行の合計数</span><span class="sxs-lookup"><span data-stu-id="602de-110">**total_rows** - the sum of all the rows sent by the component</span></span>  
  
-   <span data-ttu-id="602de-111">**wall_clock_time_ms** - コンポーネントごとの実行の合計経過時間 (ミリ秒単位)</span><span class="sxs-lookup"><span data-stu-id="602de-111">**wall_clock_time_ms** - the total elapsed execution time, in milliseconds, for each component</span></span>  
  
-   <span data-ttu-id="602de-112">**num_rows_per_millisecond** - 各コンポーネントによって送信された 1 ミリ秒あたりの行数</span><span class="sxs-lookup"><span data-stu-id="602de-112">**num_rows_per_millisecond** - the number of rows per millisecond sent by each component</span></span>  
  
 <span data-ttu-id="602de-113">`HAVING`句は、計算で0除算エラーを防ぐために使用されます。</span><span class="sxs-lookup"><span data-stu-id="602de-113">The `HAVING` clause is used to prevent a divide-by-zero error in the calculations.</span></span>  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="602de-114">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="602de-114">Related Tasks</span></span>  
 [<span data-ttu-id="602de-115">データ フローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="602de-115">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
 [<span data-ttu-id="602de-116">パッケージ実行のトラブルシューティング ツール</span><span class="sxs-lookup"><span data-stu-id="602de-116">Troubleshooting Tools for Package Execution</span></span>](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a><span data-ttu-id="602de-117">参照</span><span class="sxs-lookup"><span data-stu-id="602de-117">See Also</span></span>  
 [<span data-ttu-id="602de-118">データ フロー内のデータ</span><span class="sxs-lookup"><span data-stu-id="602de-118">Data in Data Flows</span></span>](data-flow/data-in-data-flows.md)  
  
  
