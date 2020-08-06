---
title: Visual Database Tools のデザイナー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- data sources [SQL Server]
- View Designer
- Visual Database Tools [SQL Server]
- Database Diagram Designer
- Query Designer [SQL Server]
- design tools [Visual Database Tools]
- Table Designer
- Visual Database Tools [SQL Server], designers
- Properties window [Visual Database Tools]
ms.assetid: bd0ca68e-6f69-42dd-bcb5-ce511673769c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6a307a0a82aa02e7197189ca6cfc9ba70a3fea33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632881"
---
# <a name="visual-database-tool-designers"></a><span data-ttu-id="6c1e3-102">Visual Database Tools のデザイナー</span><span class="sxs-lookup"><span data-stu-id="6c1e3-102">Visual Database Tool Designers</span></span>
  <span data-ttu-id="6c1e3-103">Visual Database Tools は、データ ソースの処理に使用できるデザイン ツールの組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-103">The Visual Database Tools are a combination of design tools you can use to work with a data source.</span></span> <span data-ttu-id="6c1e3-104">デザイン ツールを使用して、クエリの作成、データベース構造のデザインまたは変更、データの更新を実行できます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-104">You can use them to create queries, design or modify a database structure, or update data.</span></span> <span data-ttu-id="6c1e3-105">ツールには、データベース ダイアグラム デザイナー、テーブル デザイナー、クエリおよびビュー デザイナーがあります。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-105">The tools are Database Diagram Designer, Table Designer, and Query and View Designer.</span></span>  
  
## <a name="properties-window"></a><span data-ttu-id="6c1e3-106">[プロパティ] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="6c1e3-106">Properties Window</span></span>  
 <span data-ttu-id="6c1e3-107">プロパティ ウィンドウは、Visual Database Tools に固有ではありませんが、このウィンドウを使用してさまざまな変更を実行できます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-107">The properties window is not specific to Visual Database Tools, but it is where many modifications can be made.</span></span> <span data-ttu-id="6c1e3-108">プロパティ ウィンドウには、現在選択されている項目 (テーブルなど) のプロパティが表示され、そのプロパティ名や列の照合順序などのすべてのプロパティを編集できます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-108">It shows the properties for the item currently selected (like a table) and allows you to edit those properties (everything from the properties name to the collation of a column).</span></span> <span data-ttu-id="6c1e3-109">プロパティ ウィンドウに表示できても、変更するには別のツールが必要になるプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-109">Some properties can be seen in the properties window but must be modified in a different tool.</span></span>  
  
## <a name="database-diagram-designer"></a><span data-ttu-id="6c1e3-110">データベース ダイアグラム デザイナー</span><span class="sxs-lookup"><span data-stu-id="6c1e3-110">Database Diagram Designer</span></span>  
 <span data-ttu-id="6c1e3-111">データベース ダイアグラム デザイナーには、データベース内のテーブルとリレーションシップを視覚的に作成、編集、および表示できるウィンドウが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-111">Database Diagram Designer provides a window where you can visually create, edit, and show the tables and relationships in a database.</span></span>  
  
 <span data-ttu-id="6c1e3-112">データベース ダイアグラム デザイナーを表示するには、既存のダイアグラムを開くか、オブジェクト エクスプローラーのデータベース ノードを右クリックして、ドロップダウン メニューの **[新しいデータベース ダイアグラム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-112">To display Database Diagram Designer, open an existing diagram or right-click the Database node in Object Explorer and choose **New Database Diagram** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="6c1e3-113">デザイナーが開くと、メイン メニューに **[データベース ダイアグラム]** メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-113">Once the designer is open, the **Database Diagram** menu appears in the main menu.</span></span> <span data-ttu-id="6c1e3-114">このメニューから、デザイナーの特殊な機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-114">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c1e3-115">このデザイナーは、Microsoft SQL Server データベースに使用します。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-115">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="6c1e3-116">このバージョンの Visual Database Tools では、Microsoft SQL Server バージョン 7 以前はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-116">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="table-designer"></a><span data-ttu-id="6c1e3-117">テーブル デザイナー (Table Designer)</span><span class="sxs-lookup"><span data-stu-id="6c1e3-117">Table Designer</span></span>  
 <span data-ttu-id="6c1e3-118">テーブル デザイナーは、接続している Microsoft SQL Server データベースに含まれる 1 つのテーブルをデザインおよび視覚的にデザインできるビジュアル ツールです。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-118">Table Designer is a visual tool allowing you to design and visualize a single table in a Microsoft SQL Server database to which you are connected.</span></span>  
  
 <span data-ttu-id="6c1e3-119">テーブル デザイナーには 2 つのペインがあります。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-119">Table Designer has two panes.</span></span> <span data-ttu-id="6c1e3-120">上の部分にはグリッドが表示されて、グリッドの各行はデータベースの 1 つの列を表しています。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-120">The upper area shows a grid; each row of the grid describes one database column.</span></span> <span data-ttu-id="6c1e3-121">グリッドの部分には、列名、データ型、null 値を許可するかどうかの設定など、各データベース列の基本的な属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-121">For each database column, the grid displays its fundamental attributes: column name, data type, and nulls-allowed setting.</span></span>  
  
 <span data-ttu-id="6c1e3-122">テーブル デザイナーの下部にある [列のプロパティ] タブには、上部で強調表示されている列の追加属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-122">The lower area of Table Designer, the Column Properties tab, shows additional attributes for whichever column is highlighted in the upper area.</span></span>  
  
 <span data-ttu-id="6c1e3-123">テーブル デザイナーからは、グリッド セクションを右クリックしてダイアログ ボックスにアクセスし、テーブルのリレーションシップ、制約、インデックス、およびキーを作成したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-123">From Table Designer, you can also right-click in the grid section to access dialog boxes through which you can create and modify relationships, constraints, indexes, and keys for the table.</span></span>  
  
 <span data-ttu-id="6c1e3-124">テーブル デザイナーを表示するには、既存のテーブルを開くか、オブジェクト エクスプローラーの **[テーブル]** ノードを右クリックして、ドロップダウン メニューの **[新しいテーブルの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-124">To display Table Designer, open an existing table, or right-click the **Tables** node in Object Explorer, and choose **Add New Table** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="6c1e3-125">デザイナーが開くと、メイン メニューに [テーブル デザイナー] メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-125">Once the designer is open, the Table Designer menu appears in the main menu.</span></span> <span data-ttu-id="6c1e3-126">このメニューから、デザイナーの特殊な機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-126">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c1e3-127">このデザイナーは、Microsoft SQL Server データベースに使用します。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-127">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="6c1e3-128">このバージョンの Visual Database Tools では、Microsoft SQL Server バージョン 7 以前はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-128">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="query-and-view-designer"></a><span data-ttu-id="6c1e3-129">クエリおよびビュー デザイナー</span><span class="sxs-lookup"><span data-stu-id="6c1e3-129">Query and View Designer</span></span>  
 <span data-ttu-id="6c1e3-130">クエリおよびビュー デザイナーは、実際には 2 つのツールで、よく似た動作をします。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-130">Query and View designer is actually two tools that work in very similar ways.</span></span> <span data-ttu-id="6c1e3-131">主な違いの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-131">Some of the major differences are:</span></span>  
  
-   <span data-ttu-id="6c1e3-132">ビューはデータベースと共に保存されますが、クエリは Visual Studio データベース プロジェクトと共に保存されます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-132">Views are saved with the database while a query is saved with a Visual Studio database project.</span></span>  
  
-   <span data-ttu-id="6c1e3-133">クエリ デザイナーはほぼすべてのデータ ソースに使用できますが、ビュー デザイナーは SQL Server だけに使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-133">Query Designer works with nearly any data source, where View Designer works only with SQL Server.</span></span>  
  
-   <span data-ttu-id="6c1e3-134">クエリ デザイナーでは、SELECT、INSERT、UPDATE、および DELETE の DML ステートメントをデザインできますが、ビューで使用できるのは SELECT ステートメントだけです。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-134">Query Designer allows you to design SELECT, INSERT, UPDATE and DELETE DML statements, while views can only contain SELECT statements.</span></span>  
  
### <a name="view-designer"></a><span data-ttu-id="6c1e3-135">ビュー デザイナー</span><span class="sxs-lookup"><span data-stu-id="6c1e3-135">View Designer</span></span>  
 <span data-ttu-id="6c1e3-136">ビュー デザイナーを使用すると、既存のビューをデザインして視覚化したり、接続する Microsoft SQL Server データベースに新しいビューを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-136">View Designer allows you to design and visualize an existing view or create a new one in a Microsoft SQL Server database to which you are connected.</span></span>  
  
 <span data-ttu-id="6c1e3-137">ビュー デザイナーには、ダイアグラム ペイン、抽出条件ペイン、SQL ペイン、および結果ペインの 4 つのペインがあります。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-137">View Designer has four panes: the Diagram pane, the Criteria pane, the SQL pane, and the Results pane.</span></span> <span data-ttu-id="6c1e3-138">これらのペインのそれぞれの詳細については、「[クエリおよびビュー デザイナー ツール (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-138">For more detailed information on each of these panes, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="6c1e3-139">ビュー デザイナーを表示するには、既存のビューを開くか、オブジェクト エクスプローラーの **[ビュー]** ノードを右クリックして、ドロップダウン メニューの **[新しいビューの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-139">To display View Designer, open an existing view or right-click the **View** node in Object Explorer and choose **Add New View** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="6c1e3-140">デザイナーが開くと、メイン メニューに **[クエリ デザイナー]** メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-140">Once the designer is open, the **Query Designer** menu appears in the main menu.</span></span> <span data-ttu-id="6c1e3-141">このメニューから、デザイナーの特殊な機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-141">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c1e3-142">このデザイナーは、Microsoft SQL Server データベースに使用します。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-142">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="6c1e3-143">このバージョンの Visual Database Tools では、Microsoft SQL Server バージョン 7 以前はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6c1e3-143">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c1e3-144">参照</span><span class="sxs-lookup"><span data-stu-id="6c1e3-144">See Also</span></span>  
 <span data-ttu-id="6c1e3-145">[データベースダイアグラムのデザイン &#40;Visual Database Tools&#41;](design-database-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6c1e3-145">[Design Database Diagrams &#40;Visual Database Tools&#41;](design-database-diagrams-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6c1e3-146">[Visual Database Tools &#40;テーブルのデザイン&#41;](design-tables-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6c1e3-146">[Design Tables &#40;Visual Database Tools&#41;](design-tables-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6c1e3-147">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6c1e3-147">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
