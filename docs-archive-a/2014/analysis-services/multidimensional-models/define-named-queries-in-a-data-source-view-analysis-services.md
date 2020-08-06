---
title: データソースビューでの名前付きクエリの定義 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- named queries [Analysis Services], creating
- modifying named queries
- data source views [Analysis Services], named queries
ms.assetid: f09ba8aa-950e-4c0d-961e-970de13200be
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfe2dbc6081e0c33f681ba894b16057c8890e0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634114"
---
# <a name="define-named-queries-in-a-data-source-view-analysis-services"></a><span data-ttu-id="f2b8b-102">データ ソース ビューでの名前付きクエリの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="f2b8b-102">Define Named Queries in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="f2b8b-103">名前付きクエリは、テーブルとして表現されている SQL 式です。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-103">A named query is a SQL expression represented as a table.</span></span> <span data-ttu-id="f2b8b-104">名前付きクエリでは、1 つ以上のデータ ソースの 1 つ以上のテーブルから返される行および列を選択する SQL 式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-104">In a named query, you can specify an SQL expression to select rows and columns returned from one or more tables in one or more data sources.</span></span> <span data-ttu-id="f2b8b-105">名前付きクエリは、式に基づいていることを除いて、行とリレーションシップを持つデータ ソース ビュー (DSV) 内の他のテーブルに似ています。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-105">A named query is like any other table in a data source view (DSV) with rows and relationships, except that the named query is based on an expression.</span></span>  
  
 <span data-ttu-id="f2b8b-106">名前付きクエリを使用すると、基になるデータ ソースを変更せずに、DSV 内の既存のテーブルのリレーショナル スキーマを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-106">A named query lets you extend the relational schema of existing tables in DSV without modifying the underlying data source.</span></span> <span data-ttu-id="f2b8b-107">たとえば、一連の名前付きクエリを使用して、複雑なディメンション テーブルを、データベース ディメンション用により小さく単純なディメンション テーブルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-107">For example, a series of named queries can be used to split up a complex dimension table into smaller, simpler dimension tables for use in database dimensions.</span></span> <span data-ttu-id="f2b8b-108">名前付きクエリは、1 つ以上のデータ ソースの複数のデータベース テーブルを 1 つのデータ ソース ビュー テーブルに結合するために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-108">A named query can also be used to join multiple database tables from one or more data sources into a single data source view table.</span></span>  
  
## <a name="creating-a-named-query"></a><span data-ttu-id="f2b8b-109">名前付きクエリの作成</span><span class="sxs-lookup"><span data-stu-id="f2b8b-109">Creating a Named Query</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2b8b-110">名前付き計算を名前付きクエリに追加したり、名前付き計算を含んでいるテーブルに基づいて名前付きクエリを作成したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-110">You cannot add a named calculation to a named query, nor can you base a named query on a table that contains a named calculation.</span></span>  
  
 <span data-ttu-id="f2b8b-111">名前付きクエリを作成するときは、名前と、テーブルの列およびデータを返す SQL クエリを指定します。必要に応じて、名前付きクエリの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-111">When you create a named query, you specify a name, the SQL query returning the columns and data for the table, and optionally, a description of the named query.</span></span> <span data-ttu-id="f2b8b-112">SQL 式は、データ ソース ビュー内の他のテーブルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-112">The SQL expression can refer to other tables in the data source view.</span></span> <span data-ttu-id="f2b8b-113">名前付きクエリを定義すると、名前付きクエリ内の SQL クエリがデータ ソースのプロバイダーに送信され、すべて検証されます。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-113">After the named query is defined, the SQL query in a named query is sent to the provider for the data source and validated as a whole.</span></span> <span data-ttu-id="f2b8b-114">プロバイダーによって SQL クエリでエラーが検出されなければ、列がテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-114">If the provider does not find any errors in the SQL query, the column is added to the table.</span></span>  
  
 <span data-ttu-id="f2b8b-115">SQL クエリで参照されるテーブルと列は、修飾しないか、修飾する場合はテーブル名によってのみ修飾します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-115">Tables and columns referenced in the SQL query should not be qualified or should be qualified by the table name only.</span></span> <span data-ttu-id="f2b8b-116">たとえば、テーブルの SaleAmount 列を参照するには、 `SaleAmount` または `Sales.SaleAmount` は有効ですが、 `dbo.Sales.SaleAmount` ではエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-116">For example, to refer to the SaleAmount column in a table, `SaleAmount` or `Sales.SaleAmount` is valid, but `dbo.Sales.SaleAmount` generates an error.</span></span>  
  
 <span data-ttu-id="f2b8b-117">**注**[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 のデータ ソースに対してクエリを実行する名前付きクエリを定義する場合、相関サブクエリおよび GROUP BY 句を含む名前付きクエリは失敗します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-117">**Note** When defining a named query that queries a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 data source, a named query that contains a correlated subquery and a GROUP BY clause will fail.</span></span> <span data-ttu-id="f2b8b-118">詳細については、 [サポート技術情報の「](https://support.microsoft.com/kb/274729) 相関サブクエリと GROUP BY を含む SELECT ステートメントでバグ: 内部エラー [!INCLUDE[msCoName](../../includes/msconame-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-118">For more information, see [Internal Error with SELECT Statement Containing Correlated Subquery and GROUP BY](https://support.microsoft.com/kb/274729) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base.</span></span>  
  
## <a name="add-or-edit-a-named-query"></a><span data-ttu-id="f2b8b-119">名前付きクエリの追加または編集</span><span class="sxs-lookup"><span data-stu-id="f2b8b-119">Add or Edit a Named Query</span></span>  
  
1.  <span data-ttu-id="f2b8b-120">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、名前付きクエリを追加するデータ ソース ビューが含まれているデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to add a named query.</span></span>  
  
2.  <span data-ttu-id="f2b8b-121">ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開し、データ ソース ビューをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-121">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="f2b8b-122">**[テーブル]** ペインまたは **ダイアグラム** ペインの空いている領域を右クリックし、 **[新しい名前付きクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-122">In the **Tables** or **Diagram** pane, right-click an open area and then click **New Named Query**.</span></span>  
  
4.  <span data-ttu-id="f2b8b-123">**[名前付きクエリの作成]** ダイアログ ボックスで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-123">In the **Create Named Query** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="f2b8b-124">**[名前]** ボックスにクエリ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-124">In the **Name** text box, type a query name.</span></span>  
  
    2.  <span data-ttu-id="f2b8b-125">必要に応じて、 **[説明]** ボックスにクエリの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-125">Optionally, in the **Description** text box, type a description for the query.</span></span>  
  
    3.  <span data-ttu-id="f2b8b-126">**[データ ソース]** ボックスの一覧で、名前付きクエリを実行するデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-126">In the **Data Source** list box, select the data source against which the named query will execute.</span></span>  
  
    4.  <span data-ttu-id="f2b8b-127">下のペインでクエリを入力するか、グラフィカルなクエリ作成ツールを使用してクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-127">Type the query in the bottom pane, or use the graphical query building tools to create a query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f2b8b-128">クエリ作成ユーザー インターフェイス (UI) はデータ ソースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-128">The query-building user interface (UI) depends on the data source.</span></span> <span data-ttu-id="f2b8b-129">グラフィカルな UI ではなく、テキスト ベースの一般的な UI を入手できます。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-129">Instead of getting a graphical UI, you can get a generic UI, which is text-based.</span></span> <span data-ttu-id="f2b8b-130">これらのさまざまな UI の機能は同じですが、使用方法は異なります。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-130">You can accomplish the same things with these different UIs, but you must do so in different ways.</span></span> <span data-ttu-id="f2b8b-131">詳細については、「[[名前付きクエリの作成] または [名前付きクエリの編集] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](../create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-131">For more information, see [Create or Edit Named Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
5.  <span data-ttu-id="f2b8b-132">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-132">Click **OK**.</span></span> <span data-ttu-id="f2b8b-133">重なった 2 つのテーブルを示すアイコンがテーブル ヘッダーに表示され、そのテーブルが名前付きクエリに置換されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="f2b8b-133">An icon showing two overlapping tables appears in the table header to indicate that the table has been replaced by a named query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b8b-134">参照</span><span class="sxs-lookup"><span data-stu-id="f2b8b-134">See Also</span></span>  
 <span data-ttu-id="f2b8b-135">[多次元モデルのデータソースビュー](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="f2b8b-135">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="f2b8b-136">データ ソース ビューでの名前付き計算の定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="f2b8b-136">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
