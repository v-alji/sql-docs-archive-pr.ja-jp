---
title: データソースビューでのテーブルまたは名前付きクエリの置換 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- replacing tables
- data source views [Analysis Services], tables
- named queries [Analysis Services], replacing tables
- tables [Analysis Services], data source views
- partitions [Analysis Services], named queries
ms.assetid: 60c2a018-1299-4915-b60e-e73316524def
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b5055de60ba757c9dcfa118e4e2c4748c6534e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642366"
---
# <a name="replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services"></a><span data-ttu-id="71843-102">データ ソース ビュー内のテーブルまたは名前付きクエリの置換 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="71843-102">Replace a Table or a Named Query in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="71843-103">データ ソース ビュー デザイナーでは、データ ソース ビュー (DSV) 内のテーブル、ビュー、または名前付きクエリを、同じデータ ソースまたは異なるデータ ソースの別のテーブルやビュー、あるいは DSV で定義されている名前付きクエリに置換できます。</span><span class="sxs-lookup"><span data-stu-id="71843-103">In Data Source View Designer, you can replace a table, view, or named query in a data source view (DSV) with a different table or view from the same or a different data source, or with a named query defined in the DSV.</span></span> <span data-ttu-id="71843-104">テーブルを置換した場合、DSV 内のテーブルのオブジェクト ID は変更されないので、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースまたはプロジェクト内でそのテーブルを参照している他のすべてのオブジェクトは、引き続きそのテーブルを参照します。</span><span class="sxs-lookup"><span data-stu-id="71843-104">When you replace a table, all other objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project that have references to the table continue to reference the table because the object ID for the table in the DSV does not change.</span></span> <span data-ttu-id="71843-105">名前や列の型の一致に基づいて、引き続き関連のあるリレーションシップは維持されます。</span><span class="sxs-lookup"><span data-stu-id="71843-105">Any relationships that are still relevant (based on name and column-type matching) are retained.</span></span> <span data-ttu-id="71843-106">これに対して、テーブルを削除して追加した場合、参照とリレーションシップは失われるので、再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71843-106">In contrast, if you delete and then add a table, references and relationships are lost and must be recreated.</span></span>  
  
 <span data-ttu-id="71843-107">テーブルを別のテーブルに置換するには、プロジェクト モードのデータ ソース ビュー デザイナー内のソース データに対するアクティブな接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="71843-107">To replace a table with another table, you must have an active connection to the source data in Data Source View Designer in project mode.</span></span>  
  
 <span data-ttu-id="71843-108">データ ソース ビュー内のテーブルをデータ ソース内の別のテーブルに置換することが最も頻繁に行われます。</span><span class="sxs-lookup"><span data-stu-id="71843-108">You most frequently replace a table in the data source view with another table in the data source.</span></span> <span data-ttu-id="71843-109">ただし、名前付きクエリをテーブルに置換することもできます。</span><span class="sxs-lookup"><span data-stu-id="71843-109">However, you can also replace a named query with a table.</span></span> <span data-ttu-id="71843-110">たとえば、以前にテーブルを名前付きクエリに置換し、今回はテーブルに戻す場合があります。</span><span class="sxs-lookup"><span data-stu-id="71843-110">For example, you previously replaced a table with a named query, and now want to revert to a table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="71843-111">データ ソース内のテーブルの名前を変更した場合は、DSV を更新する前に、テーブルの置換手順を実行し、名前を変更したテーブルを DSV 内の対応するテーブルのソースとして指定します。</span><span class="sxs-lookup"><span data-stu-id="71843-111">If you rename a table in a data source, follow the steps for replacing a table and specify the renamed table as the source of the corresponding table in the DSV before you refresh a DSV.</span></span> <span data-ttu-id="71843-112">置換および名前変更の手順を行うと、DSV 内のテーブル、テーブルの参照、およびテーブルのリレーションシップは維持されます。</span><span class="sxs-lookup"><span data-stu-id="71843-112">Completing the replacement and renaming process preserves the table, the table's references, and the table's relationships in the DSV.</span></span> <span data-ttu-id="71843-113">この手順を実行しないと、DSV を更新したときに、データ ソース内の名前を変更したテーブルは削除されたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="71843-113">Otherwise, when you refresh the DSV, a renamed table in data source is interpreted as being deleted.</span></span> <span data-ttu-id="71843-114">詳細については、「[データ ソース ビューでのスキーマの更新 (Analysis Services)](refresh-the-schema-in-a-data-source-view-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71843-114">For more information, see [Refresh the Schema in a Data Source View &#40;Analysis Services&#41;](refresh-the-schema-in-a-data-source-view-analysis-services.md).</span></span>  
  
##  <a name="replace-a-table-with-a-named-query"></a><a name="bkmk_nq"></a> <span data-ttu-id="71843-115">テーブルを名前付きクエリで置換する</span><span class="sxs-lookup"><span data-stu-id="71843-115">Replace a table with a named query</span></span>  
  
1.  <span data-ttu-id="71843-116">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、テーブルまたは名前付きクエリを置換するデータ ソース ビューが含まれているデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="71843-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to replace a table or a named query.</span></span>  
  
2.  <span data-ttu-id="71843-117">ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開して、データ ソース ビューをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="71843-117">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="71843-118">**[名前付きクエリの作成]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="71843-118">Open the **Create Named Query** dialog box.</span></span> <span data-ttu-id="71843-119">**[テーブル]** または **ダイアグラム** ペインで、置換するテーブルを右クリックし、 **[テーブルの置換]** をポイントして **[新しい名前付きクエリの使用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71843-119">In either **Tables** or **Diagram** pane, right-click the table that you wish to replace, point to **Replace Table** and then click **With New Named Query**.</span></span>  
  
4.  <span data-ttu-id="71843-120">**[名前付きクエリの作成]** ダイアログ ボックスで名前付きクエリを定義し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71843-120">In the **Create Named Query** dialog box, define the named query and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="71843-121">変更したデータ ソース ビューを保存します。</span><span class="sxs-lookup"><span data-stu-id="71843-121">Save the modified data source view.</span></span>  
  
## <a name="replace-a-table-or-named-query-with-a-table"></a><span data-ttu-id="71843-122">テーブルまたは名前付きクエリを別のテーブルで置換する</span><span class="sxs-lookup"><span data-stu-id="71843-122">Replace a table or named query with a table</span></span>  
  
1.  <span data-ttu-id="71843-123">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、テーブルまたは名前付きクエリを置換するデータ ソース ビューが含まれているデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="71843-123">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to replace a table or a named query.</span></span>  
  
2.  <span data-ttu-id="71843-124">ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開して、データ ソース ビューをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="71843-124">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="71843-125">**[テーブルと他のテーブルとの置換]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="71843-125">Open the **Replace Table with Other Table** dialog box.</span></span> <span data-ttu-id="71843-126">**[テーブル]** または **ダイアグラム** ペインで、置換するテーブルまたは名前付きクエリを右クリックし、 **[テーブルの置換]** をポイントして **[他のテーブルを使用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71843-126">In either **Tables** or **Diagram** pane, right-click the table or named query that you wish to replace, point to **Replace Table** and then click **With Other Table**.</span></span>  
  
4.  <span data-ttu-id="71843-127">**[テーブルと他のテーブルとの置換]** ダイアログ ボックスで、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="71843-127">In the **Replace Table with Other Table** dialog box:</span></span>  
  
    1.  <span data-ttu-id="71843-128">**[データソース]** ボックスの一覧で、使用するデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="71843-128">In the **DataSource** drop-down list box, select the desired data source</span></span>  
  
    2.  <span data-ttu-id="71843-129">テーブルまたは名前付きクエリを置換するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="71843-129">Select the table with which you wish to replace the table or named query</span></span>  
  
5.  <span data-ttu-id="71843-130">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71843-130">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="71843-131">変更したデータ ソース ビューを保存します。</span><span class="sxs-lookup"><span data-stu-id="71843-131">Save the modified data source view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71843-132">参照</span><span class="sxs-lookup"><span data-stu-id="71843-132">See Also</span></span>  
 [<span data-ttu-id="71843-133">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="71843-133">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
