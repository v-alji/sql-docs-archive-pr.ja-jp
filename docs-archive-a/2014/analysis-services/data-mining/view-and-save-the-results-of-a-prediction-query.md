---
title: 予測クエリの結果を表示して保存する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- viewing prediction query results
- displaying prediction query results
- Mining Model Prediction [Analysis Services], viewing results
ms.assetid: abba4d24-3619-44c1-8279-88f27ad627d3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6da4b515c4280969f665dba2cf5bee5281df0a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639783"
---
# <a name="view-and-save-the-results-of-a-prediction-query"></a><span data-ttu-id="15abd-102">予測クエリの結果の表示および保存</span><span class="sxs-lookup"><span data-stu-id="15abd-102">View and Save the Results of a Prediction Query</span></span>
  <span data-ttu-id="15abd-103">で、予測クエリビルダーを使用してクエリを定義した後、クエリを実行して結果を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] クエリ結果ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="15abd-103">After you have defined a query in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using Prediction Query Builder, you can run the query and view the results by switching to the query result view.</span></span>  
  
 <span data-ttu-id="15abd-104">予測クエリの結果は、プロジェクトで定義されている任意のデータソース内のテーブルに保存でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="15abd-104">You can save the results of a prediction query to a table in any data source that is defined in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="15abd-105">新しいテーブルを作成するか、または既存のテーブルにクエリ結果を保存できます。</span><span class="sxs-lookup"><span data-stu-id="15abd-105">You can either create a new table or save the query results to an existing table.</span></span> <span data-ttu-id="15abd-106">既存のテーブルに結果を保存する場合は、テーブルに現在保存されているデータを上書きするように選択できます。上書きしない場合、クエリ結果は、テーブルの既存のデータに追加されます。</span><span class="sxs-lookup"><span data-stu-id="15abd-106">If you save the results to an existing table, you can choose to overwrite the data that is currently stored in the table; otherwise, the query results are appended to the existing data in the table.</span></span>  
  
### <a name="run-a-query-and-view-the-results"></a><span data-ttu-id="15abd-107">クエリを実行し、結果を表示する</span><span class="sxs-lookup"><span data-stu-id="15abd-107">Run a query and view the results</span></span>  
  
1.  <span data-ttu-id="15abd-108">**のデータ マイニング デザイナーの** [マイニング モデル予測] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブにあるツール バーで、 **[結果]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15abd-108">On the toolbar of the **Mining Model Prediction** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Result** .</span></span>  
  
     <span data-ttu-id="15abd-109">クエリ結果ビューが表示され、クエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="15abd-109">The query results view opens and runs the query.</span></span> <span data-ttu-id="15abd-110">結果がビューアーのグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="15abd-110">The results are displayed in a grid in the viewer.</span></span>  
  
### <a name="save-the-results-of-a-prediction-query-to-a-table"></a><span data-ttu-id="15abd-111">予測クエリの結果をテーブルに保存する</span><span class="sxs-lookup"><span data-stu-id="15abd-111">Save the results of a prediction query to a table</span></span>  
  
1.  <span data-ttu-id="15abd-112">データ マイニング デザイナーの **[マイニング モデル予測]** タブのツール バーで、 **[クエリ結果の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15abd-112">On the toolbar of the **Mining Model Prediction** tab in Data Mining Designer, click **Save query result**.</span></span>  
  
     <span data-ttu-id="15abd-113">**[データ マイニングのクエリ結果を保存]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="15abd-113">The **Save Data Mining Query Result** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="15abd-114">**[データ ソース]** 一覧からデータ ソースを選択するか、 **[新規作成]** をクリックして新しいデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="15abd-114">Select a data source from the **Data Source** list, or click **New** to create a new data source.</span></span>  
  
3.  <span data-ttu-id="15abd-115">**[テーブル名]** ボックスにテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="15abd-115">In the **Table Name** box, enter the name of the table.</span></span> <span data-ttu-id="15abd-116">同じテーブル名が既に存在する場合、テーブルの内容をクエリ結果に置き換えるには、 **[存在する場合は上書きする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="15abd-116">If the table already exists, select **Overwrite if exists** to replace the contents of the table with the query results.</span></span> <span data-ttu-id="15abd-117">テーブルの内容を上書きしない場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="15abd-117">If you do not want to overwrite the contents of the table, do not select this check box.</span></span> <span data-ttu-id="15abd-118">新しいクエリ結果が、テーブルの既存のデータに追加されます。</span><span class="sxs-lookup"><span data-stu-id="15abd-118">The new query results will be appended to the existing data in the table.</span></span>  
  
4.  <span data-ttu-id="15abd-119">データ ソース ビューにテーブルを追加する場合は、 **[DSV に追加]** からデータ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="15abd-119">Select a data source view from **Add to DSV** if you want to add the table to a data source view.</span></span>  
  
5.  <span data-ttu-id="15abd-120">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15abd-120">Click **Save**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="15abd-121">保存先で階層的な行セットがサポートされていない場合は、結果に FALTTENED キーワードを追加して、フラット テーブルとして保存できます。</span><span class="sxs-lookup"><span data-stu-id="15abd-121">If the destination does not support hierarchical rowsets, you can add the FALTTENED keyword to the results to save as a flat table.</span></span>  
  
  
