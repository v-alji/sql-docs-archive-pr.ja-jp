---
title: データの探索 (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2572c11e92dcf99dfa3adf661603e8f65f05116e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718873"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a><span data-ttu-id="8e586-102">データの探索 (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="8e586-102">Explore Data (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="8e586-103">![データの探索ウィザード](media/dmc-explore.gif "データの探索ウィザード")</span><span class="sxs-lookup"><span data-stu-id="8e586-103">![Explore Data wizard](media/dmc-explore.gif "Explore Data wizard")</span></span>  
  
 <span data-ttu-id="8e586-104">データの**探索**ウィザードは、データテーブル内のデータの種類と量を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8e586-104">The **Explore Data** wizard helps you understand the type and amount of data in your data table.</span></span> <span data-ttu-id="8e586-105">ウィザードは、選択した列の分布と値を一度に 1 列ずつグラフ化します。</span><span class="sxs-lookup"><span data-stu-id="8e586-105">The wizard graphs the distribution and values for the selected columns, one column at a time.</span></span> <span data-ttu-id="8e586-106">その後、データのグループ化の方法を変更したり、確認用に内容を示すグラフを Excel ブックにコピーしたりできます。</span><span class="sxs-lookup"><span data-stu-id="8e586-106">You can then experiment with changing the way that data is grouped, or copy the chart that shows the content to an Excel workbook for review.</span></span>  
  
 <span data-ttu-id="8e586-107">データに連続する数値データが含まれている場合は、次の 2 つのビューを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8e586-107">If your data contains continuous numeric data, you can toggle between these two views:</span></span>  
  
-   <span data-ttu-id="8e586-108">**折れ線グラフ。**</span><span class="sxs-lookup"><span data-stu-id="8e586-108">**Line graph.**</span></span> <span data-ttu-id="8e586-109">このグラフは、データ値を X 軸、ケース数を Y 軸として表示します。</span><span class="sxs-lookup"><span data-stu-id="8e586-109">This graph charts the data values on the X-axis and the number of cases on the y-axis.</span></span>  
  
-   <span data-ttu-id="8e586-110">**横棒グラフ。**</span><span class="sxs-lookup"><span data-stu-id="8e586-110">**Bar chart.**</span></span> <span data-ttu-id="8e586-111">このグラフは、それぞれの値のケース数に基づいて値をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="8e586-111">This graph groups values by the number of cases for each value.</span></span>  
  
 <span data-ttu-id="8e586-112">データにグループが見つかると、データ値の実際の分布が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8e586-112">When the wizard finds groups in the data, it uses the actual distribution of data values.</span></span> <span data-ttu-id="8e586-113">そのため、横棒グラフには、一般的な 10 や 100 などの整数値軸マーカーが表示されません。</span><span class="sxs-lookup"><span data-stu-id="8e586-113">Therefore, the bar chart does not show typical whole-number numeric axis markers such as 10 or 100.</span></span> <span data-ttu-id="8e586-114">代わりに、横棒グラフに表示される範囲は 43521-55603 のようになります (Income 列の場合)。</span><span class="sxs-lookup"><span data-stu-id="8e586-114">Instead, the ranges shown in the bar chart might be something like 43521-55603 (for the Income column).</span></span>  
  
 <span data-ttu-id="8e586-115">データを別の範囲にグループ化するには、データを分析する前に Excel でこの操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e586-115">If you want to group your data into other ranges, you should do this in Excel before analyzing the data.</span></span> <span data-ttu-id="8e586-116">または、[ラベル](relabel-sql-server-data-mining-add-ins.md)の再付けウィザードを使用して、データのラベルを再作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8e586-116">Or, you can relabel the data by using the [Relabel](relabel-sql-server-data-mining-add-ins.md) wizard.</span></span>  
  
## <a name="using-the-explore-data-wizard"></a><span data-ttu-id="8e586-117">データの探索ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="8e586-117">Using the Explore Data Wizard</span></span>  
  
1.  <span data-ttu-id="8e586-118">[**データマイニング**] リボンで、[**データの探索**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e586-118">In the **Data Mining** ribbon, click **Explore Data**.</span></span>  
  
2.  <span data-ttu-id="8e586-119">**[ソースの選択**] ダイアログボックスで、データを含むテーブルまたはセルの範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e586-119">In the **Select Source** dialog box, select the table or range of cells that contains your data.</span></span>  
  
3.  <span data-ttu-id="8e586-120">**[列の選択**] ダイアログボックスで、分析する列をペインに表示されているサンプルデータから選択します。</span><span class="sxs-lookup"><span data-stu-id="8e586-120">In the **Select Column** dialog box, choose the column to analyze, from the sample data displayed in the pane.</span></span>  
  
4.  <span data-ttu-id="8e586-121">[**データの探索**] ダイアログボックスで、データの分布を表示するグラフの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e586-121">In the **Explore Data** dialog box, choose the chart types for displaying the distribution of data.</span></span>  
  
5.  <span data-ttu-id="8e586-122">オプションで、新しい列をデータに追加したり、データを分割する方法を変更したり、グラフを Excel にコピーしたりできます。</span><span class="sxs-lookup"><span data-stu-id="8e586-122">Optionally, you can add new columns to the data, change the way that the data is segmented, or copy the chart to Excel.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="8e586-123">要件</span><span class="sxs-lookup"><span data-stu-id="8e586-123">Requirements</span></span>  
 <span data-ttu-id="8e586-124">**データの探索**ウィザードを使用するには、Excel データテーブルにデータが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e586-124">To use the **Explore Data** wizard, your data must be in an Excel data table.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="8e586-125">参照</span><span class="sxs-lookup"><span data-stu-id="8e586-125">See Also</span></span>  
 [<span data-ttu-id="8e586-126">データ マイニングの準備のチェック リスト</span><span class="sxs-lookup"><span data-stu-id="8e586-126">Checklist of Preparation for Data Mining</span></span>](checklist-of-preparation-for-data-mining.md)  
  
  
