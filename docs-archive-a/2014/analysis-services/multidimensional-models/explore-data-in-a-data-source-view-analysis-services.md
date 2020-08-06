---
title: データソースビューでのデータの探索 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adf9edecd807158ba1d0de3287cccd6fa8dd787
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645870"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a><span data-ttu-id="08ac8-102">データ ソース ビューでのデータの検索 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="08ac8-102">Explore Data in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="08ac8-103">**のデータ ソース ビュー デザイナーにある** [データの探索] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、テーブル、ビュー、または名前付きクエリのデータをデータ ソース ビュー (DSV) で参照できます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-103">You can use the **Explore Data** dialog box in Data Source View Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to browse data for a table, view, or named query in a data source view (DSV).</span></span> <span data-ttu-id="08ac8-104">データ ソース ビュー デザイナーでデータを探索すると、選択したテーブル、ビュー、または名前付きクエリの各データ列の内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-104">When you explore the data in Data Source View Designer, you can view the contents of each column of data in a selected table, view, or named query.</span></span> <span data-ttu-id="08ac8-105">実際の内容を表示すると、すべての列が必要であるかどうか、使いやすさを向上させるために名前付き計算が必要であるかどうか、既存の名前付き計算または名前付きクエリによって予想値が返されるかどうかなどを判断できます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-105">Viewing the actual contents assists you in determining whether all columns are needed, if named calculations are required to increase user friendliness and usability, and whether existing named calculations or named queries return the anticipated values.</span></span>  
  
 <span data-ttu-id="08ac8-106">データを表示するには、DSV で選択したオブジェクトのデータ ソースに対するアクティブな接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="08ac8-106">To view data, you must have an active connection to the data source or sources for the selected object in the DSV.</span></span> <span data-ttu-id="08ac8-107">また、テーブル内の名前付き計算もクエリで送信されます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-107">Any named calculations in a table are also sent in the query.</span></span>  
  
 <span data-ttu-id="08ac8-108">データは表形式で返されるので、並べ替えてコピーできます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-108">The data returned in a tabular format that you can sort and copy.</span></span> <span data-ttu-id="08ac8-109">列のヘッダーをクリックすると、その列で行が再度並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-109">Click on the column headers to re-sort the rows by that column.</span></span> <span data-ttu-id="08ac8-110">グリッドでデータを選択して、Ctrl キーを押しながら C キーを押すと、選択範囲をクリップボードにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-110">You can also highlight data in the grid and press Ctrl-C to copy the selection to the clipboard.</span></span>  
  
 <span data-ttu-id="08ac8-111">また、サンプリング方法やサンプル数を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-111">You can also control the sample method and the sample count.</span></span> <span data-ttu-id="08ac8-112">既定では、上位 5,000 行が返されます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-112">By default, the top 5000 rows are returned.</span></span>  
  
## <a name="to-browse-data-or-change-sampling-options"></a><span data-ttu-id="08ac8-113">データの参照またはサンプリング オプションを変更するには</span><span class="sxs-lookup"><span data-stu-id="08ac8-113">To browse data or change sampling options</span></span>  
  
1.  <span data-ttu-id="08ac8-114">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、またはデータを参照するデータ ソース ビューが含まれているデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="08ac8-114">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to browse data.</span></span>  
  
2.  <span data-ttu-id="08ac8-115">ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開して、データ ソース ビューをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="08ac8-115">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="08ac8-116">表示するデータが含まれているテーブル、ビュー、または名前付きクエリを右クリックして、 **[データの探索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08ac8-116">Right-click the table, view, or named query that contains the data you want to view, and then click **Explore Data**.</span></span>  
  
     <span data-ttu-id="08ac8-117">データソースビューのテーブル、ビュー、または名前付きクエリの基になるデータソースはクエリで、結果は [ \*\* \<object name> テーブルの探索\*\*] タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-117">The data source underlying the table, view, or named query in the data source view are queries, and the results appear in the **Explore \<object name> Table** tab.</span></span>  
  
4.  <span data-ttu-id="08ac8-118">[ \*\* \<object name> テーブルの探索**] ツールバーで、[**サンプリングオプション\*\*] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="08ac8-118">On the **Explore \<object name> Table** toolbar, click the **Sampling options** icon.</span></span>  
  
     <span data-ttu-id="08ac8-119">**[データ探索オプション]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-119">The **Data Exploration Options** dialog box opens.</span></span> <span data-ttu-id="08ac8-120">このダイアログ ボックスでは、サンプリング方法 (既定のサンプリング サイズである 5,000 行以外のレコード数) またはサンプル数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="08ac8-120">In this dialog box you can specify the sampling method (fewer or more records than the default sampling size of 5000 rows), or sample count.</span></span>  
  
5.  <span data-ttu-id="08ac8-121">**[OK]** または **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08ac8-121">Click **OK** or **Cancel** as appropriate.</span></span>  
  
6.  <span data-ttu-id="08ac8-122">データを再サンプリングするには、[ \*\* \<object name> テーブルの探索**] ツールバーの [データの再**サンプリング\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08ac8-122">To resample the data, click **Resample Data** on the **Explore \<object name> Table** toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ac8-123">参照</span><span class="sxs-lookup"><span data-stu-id="08ac8-123">See Also</span></span>  
 [<span data-ttu-id="08ac8-124">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="08ac8-124">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
