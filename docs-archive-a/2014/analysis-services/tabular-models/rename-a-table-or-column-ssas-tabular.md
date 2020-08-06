---
title: テーブルまたは列の名前の変更 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.renametableorcolumn.f1
ms.assetid: 88061a39-c5aa-403d-a52b-7fdb365fc235
author: minewiskan
ms.author: owend
ms.openlocfilehash: d3a2e9a9f41434e64f9ec5ea2180861b459e8f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738838"
---
# <a name="rename-a-table-or-column-ssas-tabular"></a><span data-ttu-id="34389-102">テーブルまたは列名の変更 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="34389-102">Rename a Table or Column (SSAS Tabular)</span></span>
  <span data-ttu-id="34389-103">**テーブルのインポート ウィザード** の **[テーブルとビューの選択]** ページで **表示名**を入力することにより、インポート処理中にテーブルの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="34389-103">You can change the name of a table during the import process by typing a **Friendly Name** in the **Select Tables and Views** page of the **Table Import Wizard**.</span></span> <span data-ttu-id="34389-104">**テーブルのインポート ウィザード** の **[SQL クエリの指定]** ページでクエリを指定してデータをインポートした場合は、テーブルおよび列の名前を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="34389-104">You can also change table and column names if you import data by specifying a query on the **Specify a SQL Query** page of the **Table Import Wizard**.</span></span>  
  
 <span data-ttu-id="34389-105">データをモデルに追加すると、テーブルの名前 (つまりタイトル) がモデル デザイナーの下部にあるテーブル タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="34389-105">After you have added the data to the model, the name (or title) of a table appears on the table tab, at the bottom of the model designer.</span></span> <span data-ttu-id="34389-106">テーブルの名前は、より適切な名前に変更できます。</span><span class="sxs-lookup"><span data-stu-id="34389-106">You can change the name of your table to give it a more appropriate name.</span></span> <span data-ttu-id="34389-107">列の名前は、データをモデルに追加した後で変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="34389-107">You can also rename a column after the data has been added to the model.</span></span> <span data-ttu-id="34389-108">このオプションは、複数のソースからデータをインポートして、別のテーブルの列にわかりやすい名前を付けたい場合に特に重要となります。</span><span class="sxs-lookup"><span data-stu-id="34389-108">This option is especially important when you have imported data from multiple sources, and want to ensure that columns in different tables have names that are easy to distinguish.</span></span>  
  
### <a name="to-rename-a-table"></a><span data-ttu-id="34389-109">テーブル名を変更するには</span><span class="sxs-lookup"><span data-stu-id="34389-109">To rename a table</span></span>  
  
1.  <span data-ttu-id="34389-110">モデル デザイナーで、名前を変更するテーブルが入っているタブを右クリックして、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34389-110">In the model designer, right-click the tab that contains the table that you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="34389-111">新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="34389-111">Type the new name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34389-112">**[テーブルのプロパティの編集]** ダイアログ ボックスを使用すると、接続情報や列マッピングなど、名前以外のテーブルのプロパティを編集できます。</span><span class="sxs-lookup"><span data-stu-id="34389-112">You can edit other properties of a table, including the connection information and column mappings, by using the **Edit Table Properties** dialog box.</span></span> <span data-ttu-id="34389-113">ただし、このダイアログ ボックスでは、名前を変更できません。</span><span class="sxs-lookup"><span data-stu-id="34389-113">However, you cannot change the name in this dialog box.</span></span>  
  
### <a name="to-rename-a-column"></a><span data-ttu-id="34389-114">列名を変更するには</span><span class="sxs-lookup"><span data-stu-id="34389-114">To rename a column</span></span>  
  
1.  <span data-ttu-id="34389-115">モデル デザイナーで名前を変更する列の見出しをダブルクリックするか、見出しを右クリックし、コンテキスト メニューの **[列名の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34389-115">In the model designer, double-click the header of the column that you want to rename, or right-click the header and select **Rename Column** from the context menu.</span></span>  
  
2.  <span data-ttu-id="34389-116">新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="34389-116">Type the new name.</span></span>  
  
## <a name="naming-requirements-for-columns-and-tables"></a><span data-ttu-id="34389-117">列とテーブルの名前付けに関する要件</span><span class="sxs-lookup"><span data-stu-id="34389-117">Naming Requirements for Columns and Tables</span></span>  
 <span data-ttu-id="34389-118">次の単語と文字をテーブルまたは列の名前で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="34389-118">The following words and characters cannot be used in the name of a table or column:</span></span>  
  
-   <span data-ttu-id="34389-119">先頭または末尾の空白。</span><span class="sxs-lookup"><span data-stu-id="34389-119">Leading or trailing spaces</span></span>  
  
-   <span data-ttu-id="34389-120">制御文字。</span><span class="sxs-lookup"><span data-stu-id="34389-120">Control characters</span></span>  
  
-   <span data-ttu-id="34389-121">次の文字 (Analysis Services オブジェクトの名前では無効):.,; ':/ \\*|?&% $! + = () [] {}<></span><span class="sxs-lookup"><span data-stu-id="34389-121">The following characters (which are not valid in the names of Analysis Services objects): .,;':/\\*|?&%$!+=()[]{}<></span></span>  
  
-   <span data-ttu-id="34389-122">Analysis Services の予約済みキーワード。多次元式 (MDX) とデータ マイニング拡張機能 (DMX) の関数名と演算子を含みます。</span><span class="sxs-lookup"><span data-stu-id="34389-122">Analysis Services reserved keywords, including Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) function names and operators.</span></span>  
  
## <a name="effect-of-renaming-on-existing-tables-columns-and-calculations"></a><span data-ttu-id="34389-123">既存のテーブル、列、および計算名を変更することによる影響</span><span class="sxs-lookup"><span data-stu-id="34389-123">Effect of Renaming on Existing Tables, Columns, and Calculations</span></span>  
 <span data-ttu-id="34389-124">テーブルの名前を変更するたびに、基になるテーブル オブジェクトの名前も変更されます。このテーブル オブジェクトには複数の列またはメジャーが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="34389-124">Whenever you change the name of a table, you change the name of the underlying table object, which may contain multiple columns or measures.</span></span> <span data-ttu-id="34389-125">そのため、テーブル内のすべての列、およびテーブルを使用するすべてのリレーションシップを更新して、定義内で新しい名前を使用するようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34389-125">Therefore, any columns that are in the table, and any relationships that use the table, must be updated to use the new name in their definitions.</span></span> <span data-ttu-id="34389-126">この更新は自動的に行われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="34389-126">This update happens automatically in some cases.</span></span> <span data-ttu-id="34389-127">メジャーは自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="34389-127">Measures are not updated automatically.</span></span>  
  
 <span data-ttu-id="34389-128">さらに名前を変更したテーブルを使用する計算、および名前を変更したテーブルの列を使用する計算を更新し、これらの計算から派生したデータも更新して再計算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34389-128">Moreover, any calculations that use the renamed table, or that use columns from the renamed table, must also be updated, and the data derived from those calculations must be refreshed and recalculated.</span></span> <span data-ttu-id="34389-129">影響を受けるテーブルと計算の数によっては、完了までに時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="34389-129">Depending on how many tables and calculations are affected, this can take some time to complete.</span></span> <span data-ttu-id="34389-130">このため、テーブル名を変更するタイミングとしては、インポート処理時か、複雑なリレーションシップや計算を構築する前が最適です。</span><span class="sxs-lookup"><span data-stu-id="34389-130">Therefore, the best time to rename tables is either during the import process, or before you start to build complex relationships and calculations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34389-131">参照</span><span class="sxs-lookup"><span data-stu-id="34389-131">See Also</span></span>  
 <span data-ttu-id="34389-132">[SSAS 表形式のテーブルと列 &#40;&#41;](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="34389-132">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="34389-133">[PowerPivot からのインポート &#40;SSAS 表形式&#41;](import-from-power-pivot-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="34389-133">[Import from PowerPivot &#40;SSAS Tabular&#41;](import-from-power-pivot-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="34389-134">Analysis Services からのインポート (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="34389-134">Import from Analysis Services &#40;SSAS Tabular&#41;</span></span>](import-from-analysis-services-ssas-tabular.md)  
  
  
