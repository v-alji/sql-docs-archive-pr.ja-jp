---
title: Analysis Services の MDX クエリデザイナーでのパラメーターの定義 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], MDX
- Multidimensional Expressions [Reporting Services]
- Data Mining Prediction [Reporting Services]
- MDX [Reporting Services], defining parameters
- DMX [Reporting Services]
ms.assetid: 4ad1e5bc-f510-4752-b4f6-589e55317a90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6b2b05fc0122eb25a7a0799f7b47b1b99486a28c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742889"
---
# <a name="define-parameters-in-the-mdx-query-designer-for-analysis-services-report-builder-and-ssrs"></a><span data-ttu-id="aadf2-102">Analysis Services の MDX クエリ デザイナーでのパラメーターの定義 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="aadf2-102">Define Parameters in the MDX Query Designer for Analysis Services (Report Builder and SSRS)</span></span>
  <span data-ttu-id="aadf2-103">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースに対する MDX クエリをパラメーター化するには、そのクエリにクエリ パラメーターを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aadf2-103">To parameterize an MDX query for an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, you must add a query parameter to the query.</span></span> <span data-ttu-id="aadf2-104">MDX クエリ デザイナーでは、デザイン モードとクエリ モードの両方で、フィルターを指定することによって、クエリ パラメーターを追加できます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-104">In the MDX query designer, you can add a query parameter in both Design mode and Query mode by specifying a filter.</span></span> <span data-ttu-id="aadf2-105">クエリ パラメーターを使用してクエリを定義すると、Reporting Services によってレポート パラメーターとデータセットが自動的に作成され、有効な値の一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-105">After you define the query with a query parameter, Reporting Services automatically creates a report parameter and a dataset to provide the list of valid values.</span></span> <span data-ttu-id="aadf2-106">これにより、クエリに直接渡される値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-106">This enables a user to specify a value that is passed directly to the query.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-define-a-query-parameter-in-mdx-in-design-mode"></a><span data-ttu-id="aadf2-107">MDX のデザイン モードでクエリ パラメーターを定義するには</span><span class="sxs-lookup"><span data-stu-id="aadf2-107">To define a query parameter in MDX in Design mode</span></span>

1.  <span data-ttu-id="aadf2-108">レポート データ ペインで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースの種類から作成されたデータセットを右クリックし、 **[クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-108">In the Report Data pane, right-click on a dataset created from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source type, and then click **Query**.</span></span> <span data-ttu-id="aadf2-109">MDX クエリ デザイナーがデザイン モードで開きます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-109">The MDX query designer opens in Design mode.</span></span>

2.  <span data-ttu-id="aadf2-110">ディメンションをフィルター領域にドラッグし、 **[ディメンション]** 列の最初のセルにドロップします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-110">Drag a dimension to the filter area and drop it on the first cell in the **Dimension** column.</span></span>

3.  <span data-ttu-id="aadf2-111">**[階層]** 列のボックスの一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-111">In the **Hierarchy** column, choose a value from the drop-down list.</span></span>

4.  <span data-ttu-id="aadf2-112">**[演算子]** 列のボックスの一覧から演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-112">In the **Operator** column, choose an operator for the drop-down list.</span></span>

5.  <span data-ttu-id="aadf2-113">**[フィルター式]** 列のボックスの一覧から個々の値を選択するか、 **[すべて]** メンバーをクリックしてすべての値を選択します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-113">In the **Filter Expression** column, select individual values from the drop-down list, or click the **All** member to choose all values.</span></span>

6.  <span data-ttu-id="aadf2-114">**[パラメーター]** 列で、チェック ボックスをオンにしてレポート パラメーターを作成します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-114">In the **Parameters** column, select the check box to create a report parameter.</span></span>

7.  <span data-ttu-id="aadf2-115">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-115">Click **Run**.</span></span>

     <span data-ttu-id="aadf2-116">クエリを実行したら、ツール バーの **[デザイン]** をクリックしてクエリ モードに切り替え、作成した MDX クエリを表示します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-116">After you run the query, click **Design** on the toolbar to toggle to Query mode to view the MDX query that was created.</span></span> <span data-ttu-id="aadf2-117">引き続きデザイン モードを使用してクエリを作成する場合は、クエリ モードでクエリ テキストを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="aadf2-117">Do not change the query text in Query mode if you want to continue to use Design mode to develop the query.</span></span> <span data-ttu-id="aadf2-118">デザイン モードに戻るには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-118">Click **Design** to toggle back to Design mode.</span></span>

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="aadf2-119">レポート データ ペインで [パラメーター] ノードを展開して、フィルター用に自動的に作成されたレポート パラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-119">In the Report Data pane, expand the Parameters node to display the report parameter that was automatically created for the filter.</span></span>

     <span data-ttu-id="aadf2-120">レポート パラメーターで使用可能な値を示すデータセットを確認するには、レポート データ ペインの空白部分を右クリックし、 **[非表示のデータセットの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-120">To view the dataset that provides available values for the report parameter, right-click any blank area in the Report Data pane, and then click **Show Hidden Datasets**.</span></span> <span data-ttu-id="aadf2-121">レポート データ ペインに、レポート内のすべてのデータセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-121">The Report Data pane displays all datasets in the report.</span></span>

### <a name="to-define-a-query-parameter-in-mdx-in-query-mode"></a><span data-ttu-id="aadf2-122">MDX のクエリ モードでクエリ パラメーターを定義するには</span><span class="sxs-lookup"><span data-stu-id="aadf2-122">To define a query parameter in MDX in Query mode</span></span>

1.  <span data-ttu-id="aadf2-123">レポート データ ペインで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースの種類から作成されたデータセットを右クリックし、 **[クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-123">In the Report Data pane, right-click on a dataset created from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source type, and then click **Query**.</span></span> <span data-ttu-id="aadf2-124">MDX クエリ デザイナーがデザイン モードで開きます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-124">The MDX query designer opens in Design mode.</span></span>

2.  <span data-ttu-id="aadf2-125">ツール バーの **[デザイン]** をクリックして、クエリ モードに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-125">On the toolbar, click **Design** to toggle to Query mode.</span></span>

3.  <span data-ttu-id="aadf2-126">MDX クエリ デザイナー ツール バーで **[クエリ パラメーター]** (![[クエリ パラメーター] ダイアログ ボックスのアイコン](../../analysis-services/media/iconqueryparameter.gif "[クエリ パラメーター] ダイアログ ボックスのアイコン")) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-126">On the MDX query designer toolbar, click **Query Parameters** (![Icon for the Query Parameters dialog box](../../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")).</span></span> <span data-ttu-id="aadf2-127">[クエリ パラメーター] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-127">The Query Parameters dialog box opens.</span></span>

4.  <span data-ttu-id="aadf2-128">[**パラメーター** ] 列の [] をクリックし、 **\<Enter Parameter>** パラメーターの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-128">In the **Parameter** column, click **\<Enter Parameter>**, and then type the name of a parameter.</span></span>

5.  <span data-ttu-id="aadf2-129">**[ディメンション]** 列のボックスの一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-129">In the **Dimension** column, choose a value from the drop-down list.</span></span>

6.  <span data-ttu-id="aadf2-130">**[階層]** 列のボックスの一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-130">In the **Hierarchy** column, choose a value from the drop-down list.</span></span>

7.  <span data-ttu-id="aadf2-131">**[複数値]** 列で、チェック ボックスをオンにして複数値パラメーターを作成します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-131">In the **Multiple values** column, select the check box to create a multivalue parameter.</span></span>

8.  <span data-ttu-id="aadf2-132">手順 5. の選択に応じて、 **[既定]** 列のボックスの一覧から 1 つまたは複数の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-132">In the **Default** column, from the drop-down list, select a single value or multiple values depending on your choice in step 5.</span></span>

9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

10. <span data-ttu-id="aadf2-133">クエリ デザイナーのツール バーで、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-133">On the query designer toolbar, click **Run**.</span></span>

11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="aadf2-134">レポート データ ペインで [パラメーター] ノードを展開して、フィルター用に自動的に作成されたレポート パラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="aadf2-134">In the Report Data pane, expand the Parameters node to display the report parameter that was automatically created for the filter.</span></span>

     <span data-ttu-id="aadf2-135">レポート パラメーターで使用可能な値を示すデータセットを確認するには、レポート データ ペインの空白部分を右クリックし、 **[非表示のデータセットの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aadf2-135">To view the dataset that provides available values for the report parameter, right-click any blank area in the Report Data pane, and then click **Show Hidden Datasets**.</span></span> <span data-ttu-id="aadf2-136">レポート データ ペインに、レポート内のすべてのデータセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aadf2-136">The Report Data pane displays all datasets in the report.</span></span>

## <a name="see-also"></a><span data-ttu-id="aadf2-137">参照</span><span class="sxs-lookup"><span data-stu-id="aadf2-137">See Also</span></span>
 <span data-ttu-id="aadf2-138">Mdx [&#40;SSRS&#41;の Analysis Services の接続の種類](analysis-services-connection-type-for-mdx-ssrs.md) [Analysis Services mdx クエリデザイナーのユーザーインターフェイス](analysis-services-mdx-query-designer-user-interface.md)</span><span class="sxs-lookup"><span data-stu-id="aadf2-138">[Analysis Services Connection Type for MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md)</span></span>


