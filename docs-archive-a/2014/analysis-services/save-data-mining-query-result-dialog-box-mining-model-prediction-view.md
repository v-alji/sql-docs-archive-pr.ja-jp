---
title: '[データマイニングのクエリ結果の保存] ダイアログボックス (マイニングモデル予測ビュー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0838c90f0797a0db9c8a66cd8c5f877aaecdad0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633381"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a><span data-ttu-id="36b11-102">[データ マイニングのクエリ結果を保存] ダイアログ ボックス ([マイニング モデル予測] ビュー)</span><span class="sxs-lookup"><span data-stu-id="36b11-102">Save Data Mining Query Result Dialog Box (Mining Model Prediction View)</span></span>
  <span data-ttu-id="36b11-103">**[データ マイニングのクエリ結果を保存]** ダイアログ ボックスを使用すると、新しいテーブルに、データ マイニング クエリの結果を保存できます。</span><span class="sxs-lookup"><span data-stu-id="36b11-103">Use the **Save Data Mining Query Result** dialog box to save the results of a data mining query to a new table.</span></span>  
  
 <span data-ttu-id="36b11-104">この新しいテーブルは、データ ソースで定義されたデータベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="36b11-104">The new table will be created in the database defined by the data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="36b11-105">Options</span><span class="sxs-lookup"><span data-stu-id="36b11-105">Options</span></span>  
 <span data-ttu-id="36b11-106">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="36b11-106">**Data Source**</span></span>  
 <span data-ttu-id="36b11-107">現在のプロジェクトからデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="36b11-107">Select a data source from the current project.</span></span> <span data-ttu-id="36b11-108">適切なデータ ソースがない場合には、 **[新規作成]** をクリックして新しいデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="36b11-108">If the correct data source does not exist, click **New** to create a new data source.</span></span>  
  
 <span data-ttu-id="36b11-109">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="36b11-109">**New**</span></span>  
 <span data-ttu-id="36b11-110">**データ ソース ウィザード**を開きます。</span><span class="sxs-lookup"><span data-stu-id="36b11-110">Opens the **Data Source Wizard**.</span></span>  
  
 <span data-ttu-id="36b11-111">**テーブル名**</span><span class="sxs-lookup"><span data-stu-id="36b11-111">**Table Name**</span></span>  
 <span data-ttu-id="36b11-112">新しいテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="36b11-112">Type a name for the new table.</span></span>  
  
 <span data-ttu-id="36b11-113">**[存在する場合は上書きする]**</span><span class="sxs-lookup"><span data-stu-id="36b11-113">**Overwrite if exists**</span></span>  
 <span data-ttu-id="36b11-114">同じ名前を持つ既存のテーブルを上書きする場合は、このオプションをオンにします。</span><span class="sxs-lookup"><span data-stu-id="36b11-114">Select this option if you want to overwrite an existing table with the same name.</span></span>  
  
 <span data-ttu-id="36b11-115">次のいずれかに該当する場合は、既存のテーブルを上書きする必要があります。</span><span class="sxs-lookup"><span data-stu-id="36b11-115">Overwriting the existing table is required if any of the following is true:</span></span>  
  
-   <span data-ttu-id="36b11-116">予測クエリに列を追加した場合。</span><span class="sxs-lookup"><span data-stu-id="36b11-116">You added columns to the prediction query.</span></span>  
  
-   <span data-ttu-id="36b11-117">予測クエリで列の名前やデータ型を変更した場合。</span><span class="sxs-lookup"><span data-stu-id="36b11-117">You changed the names or data types of any columns in the prediction query.</span></span>  
  
-   <span data-ttu-id="36b11-118">対象となるテーブルで ALTER ステートメントを実行した場合。</span><span class="sxs-lookup"><span data-stu-id="36b11-118">You ran an ALTER statement on the destination table.</span></span>  
  
 <span data-ttu-id="36b11-119">複数の列の名前が同じである場合 (複数の派生列の名前が既定の列名 **Expression**である場合など) は、重複する名前を持つ各列に対して別名を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36b11-119">If multiple columns have the same name (for example, several derived columns might have the default column name **Expression**), you must create an alias for each column with a duplicate name.</span></span> <span data-ttu-id="36b11-120">テーブル内の列には一意の名前が必要であるため、列に一意の名前が存在しない場合は、デザイナーが SQL Server に結果を保存しようとするとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="36b11-120">If the columns do not have unique names, an error will be raised when the designer tries to save the results to SQL Server, because columns in a table must have unique names.</span></span>  
  
 <span data-ttu-id="36b11-121">**[DSV に追加]**</span><span class="sxs-lookup"><span data-stu-id="36b11-121">**Add to DSV**</span></span>  
 <span data-ttu-id="36b11-122">(省略可能) 既存のデータ ソースにテーブルを追加する場合に、プロジェクトに含まれているデータ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="36b11-122">(Optional) Select a data source view contained in the project if you want to add the table to an existing data source.</span></span>  
  
 <span data-ttu-id="36b11-123">このオプションは、モデルのすべての関連テーブル (トレーニングデータ、予測ソースデータ、クエリ結果など) を同じデータソースで保持する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="36b11-123">This option is useful if you want to keep all related tables for a model-such as training data, prediction source data, and query results-in the same data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b11-124">参照</span><span class="sxs-lookup"><span data-stu-id="36b11-124">See Also</span></span>  
 <span data-ttu-id="36b11-125">[予測クエリビルダー &#40;データマイニング&#41;](prediction-query-builder-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="36b11-125">[Prediction Query Builder &#40;Data Mining&#41;](prediction-query-builder-data-mining.md) </span></span>  
 <span data-ttu-id="36b11-126">[データマイニングクエリインターフェイス](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="36b11-126">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="36b11-127">データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス</span><span class="sxs-lookup"><span data-stu-id="36b11-127">Data Mining Extensions &#40;DMX&#41; Statement Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
