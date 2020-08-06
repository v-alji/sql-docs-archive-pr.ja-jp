---
title: データソースビューでの名前付き計算の定義 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying named calculations
- data source views [Analysis Services], named calculations
- named calculations [Analysis Services]
ms.assetid: 729e7b12-6185-4b73-8bcb-cfe459b15355
author: minewiskan
ms.author: owend
ms.openlocfilehash: ae901c340fe29c042430d928a4abaea8e8cfe84b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641342"
---
# <a name="define-named-calculations-in-a-data-source-view-analysis-services"></a><span data-ttu-id="cc799-102">データ ソース ビューでの名前付き計算の定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="cc799-102">Define Named Calculations in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="cc799-103">名前付き計算は、計算される列として表現されている SQL 式です。</span><span class="sxs-lookup"><span data-stu-id="cc799-103">A named calculation is a SQL expression represented as a calculated column.</span></span> <span data-ttu-id="cc799-104">この式は、テーブル内の列として表示され動作します。</span><span class="sxs-lookup"><span data-stu-id="cc799-104">This expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="cc799-105">名前付き計算を使用すると、基になるデータ ソースのテーブルやビューを変更しなくても、データ ソース ビュー内の既存のテーブルまたはビューのリレーショナル スキーマを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="cc799-105">A named calculation lets you extend the relational schema of existing tables or views in a data source view without modifying the tables or views in the underlying data source.</span></span> <span data-ttu-id="cc799-106">次の例を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="cc799-106">Consider the following examples:</span></span>

-   <span data-ttu-id="cc799-107">ファクト テーブルの複数の列から派生した 1 つの名前付き計算を作成します (たとえば、税率に販売価格を乗算して Tax Amount を作成します)。</span><span class="sxs-lookup"><span data-stu-id="cc799-107">Create a single named calculation that is derived from multiple columns in a fact table (for example, creating Tax Amount by multiplying a tax rate by a sales price).</span></span>

-   <span data-ttu-id="cc799-108">ディメンション メンバーにわかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="cc799-108">Construct a user friendly name for a dimension member.</span></span>

-   <span data-ttu-id="cc799-109">クエリ パフォーマンスの強化として、キューブに計算済みのメンバーを作成するのではなく、DSV に名前付き計算を作成します。</span><span class="sxs-lookup"><span data-stu-id="cc799-109">As a query performance enhancement, create a named calculation in the DSV instead of creating a calculated member in a cube.</span></span> <span data-ttu-id="cc799-110">名前付き計算は処理中に計算されますが、計算されるメンバーはクエリ時に計算されます。</span><span class="sxs-lookup"><span data-stu-id="cc799-110">Named calculations are calculated during processing whereas calculated members are calculated at query time.</span></span>

## <a name="creating-named-calculations"></a><span data-ttu-id="cc799-111">名前付き計算の作成</span><span class="sxs-lookup"><span data-stu-id="cc799-111">Creating Named Calculations</span></span>

> [!NOTE]
>  <span data-ttu-id="cc799-112">名前付き計算を名前付きクエリに追加したり、名前付き計算を含んでいるテーブルに基づいて名前付きクエリを作成したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cc799-112">You cannot add a named calculation to a named query, nor can you base a named query on a table that contains a named calculation.</span></span>

 <span data-ttu-id="cc799-113">名前付き計算を作成するには、名前と SQL 式を指定し、必要に応じて計算の説明も指定します。</span><span class="sxs-lookup"><span data-stu-id="cc799-113">When you create a named calculation, you specify a name, the SQL expression, and, optionally, a description of the calculation.</span></span> <span data-ttu-id="cc799-114">SQL 式は、データ ソース ビュー内の他のテーブルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="cc799-114">The SQL expression can refer to other tables in the data source view.</span></span> <span data-ttu-id="cc799-115">名前付き計算を定義すると、名前付き計算の式がデータ ソースのプロバイダーに送信され、次の SQL ステートメントとして検証されます。ここで、 `<Expression>` には、名前付き計算を定義する式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc799-115">After the named calculation is defined, the expression in a named calculation is sent to the provider for the data source and validated as the following SQL statement in which `<Expression>` contains the expression that defines the named calculation.</span></span>

```
SELECT 
   <Table Name in Data Source>.*, 
   <Expression> AS <Column Name> 
FROM 
   <Table Name in Data Source> AS <Table Name in Data Source View>
```

 <span data-ttu-id="cc799-116">列のデータ型は、式によって返されたスカラー値のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="cc799-116">The data type of the column is determined by the data type of the scalar value returned by the expression.</span></span> <span data-ttu-id="cc799-117">プロバイダーによって式でエラーが検出されなければ、列がテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="cc799-117">If the provider does not find any errors in the expression, the column is added to the table.</span></span>

 <span data-ttu-id="cc799-118">式で参照される列は、修飾する必要がないか、テーブル名によってのみ修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc799-118">Columns referenced in the expression should not be qualified or should be qualified by the table name only.</span></span> <span data-ttu-id="cc799-119">たとえば、テーブルの SaleAmount 列を参照するには、 `SaleAmount` または `Sales.SaleAmount` は有効ですが、 `dbo.Sales.SaleAmount` ではエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="cc799-119">For example, to refer to the SaleAmount column in a table, `SaleAmount` or `Sales.SaleAmount` is valid, but `dbo.Sales.SaleAmount` generates an error.</span></span>

 <span data-ttu-id="cc799-120">式は、自動的にはかっこで囲まれません。</span><span class="sxs-lookup"><span data-stu-id="cc799-120">The expression is not automatically enclosed between parentheses.</span></span> <span data-ttu-id="cc799-121">このため、SELECT ステートメントなどの式で、かっこが必要な場合は、 **[式]** ボックスでかっこを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc799-121">Therefore, if an expression, such as a SELECT statement, requires parentheses, you must type the parentheses in the **Expression** box.</span></span> <span data-ttu-id="cc799-122">たとえば、次の式は、かっこを入力した場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="cc799-122">For example, the following expression is valid only if you type the parentheses.</span></span>

```
(SELECT Description FROM Categories WHERE Categories.CategoryID = CategoryID)
```

## <a name="add-or-edit-a-named-calculation"></a><span data-ttu-id="cc799-123">名前付き計算の追加または編集</span><span class="sxs-lookup"><span data-stu-id="cc799-123">Add or Edit a Named Calculation</span></span>

1.  <span data-ttu-id="cc799-124">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、名前付き計算を定義するデータ ソース ビューが含まれているデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="cc799-124">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to define a named calculation.</span></span>

2.  <span data-ttu-id="cc799-125">ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開し、データ ソース ビューをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc799-125">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>

3.  <span data-ttu-id="cc799-126">**[テーブル]** ペインまたは **[ダイアグラム]** ペインで、名前付き計算を定義するテーブルを右クリックし、 **[新しい名前付き計算]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc799-126">Right-click the table in which you wish to define the named calculation in either the **Tables** or the **Diagram** pane, and then click **New Named Calculation**.</span></span> <span data-ttu-id="cc799-127">必ず、属性ではなくテーブル名を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="cc799-127">Be sure to right-click on the table name, and not on an attribute.</span></span> <span data-ttu-id="cc799-128">メニューは以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="cc799-128">The menu should look like the following:</span></span>

     <span data-ttu-id="cc799-129">![ダイアグラム ワークスペース (右クリック メニュー) のスクリーンショット](../media/ssas-olapdsv-diagram.gif "ダイアグラム ワークスペース (右クリック メニュー) のスクリーンショット")</span><span class="sxs-lookup"><span data-stu-id="cc799-129">![Screenshot of diagram workspace, right-click menu](../media/ssas-olapdsv-diagram.gif "Screenshot of diagram workspace, right-click menu")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cc799-130">テーブルまたはビューを検索する場合は、 **[データ ソース ビュー]** メニューをクリックするか、 **[テーブル]** ペインまたは **[ダイアグラム]** ペインの空いている領域を右クリックすることで、 **[テーブルの検索]** オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc799-130">To locate a table or view, you can use the **Find Table** option by either clicking the **Data Source View** menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>

4.  <span data-ttu-id="cc799-131">**[名前付き計算の作成]** ダイアログ ボックスで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="cc799-131">In the **Create Named Calculations** dialog box, do the following:</span></span>

    -   <span data-ttu-id="cc799-132">**[列名]** テキスト ボックスに新しい列の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cc799-132">In the **Column name** text box, type the name of the new column.</span></span>

    -   <span data-ttu-id="cc799-133">**[説明]** テキスト ボックスに新しい列の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="cc799-133">In the **Description** text box type a description for the new column.</span></span>

    -   <span data-ttu-id="cc799-134">**[式]** テキスト ボックスに、データ プロバイダーに適した SQL 言語仕様で新しい列の内容をもたらす式を入力します。</span><span class="sxs-lookup"><span data-stu-id="cc799-134">In the **Expression** text box, type the expression that yields the content of the new column in the SQL dialect appropriate for the data provider.</span></span>

5.  <span data-ttu-id="cc799-135">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc799-135">Click **OK**.</span></span>

     <span data-ttu-id="cc799-136">名前付き計算の列がデータ ソース ビュー テーブルの最後の列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc799-136">The named calculation column appears as the last column in the data source view table.</span></span> <span data-ttu-id="cc799-137">名前付き計算を含む列は、計算機の記号で示されます。</span><span class="sxs-lookup"><span data-stu-id="cc799-137">A calculator symbol indicates that the column contains a named calculation.</span></span>

## <a name="delete-a-named-calculation"></a><span data-ttu-id="cc799-138">名前付き計算の削除</span><span class="sxs-lookup"><span data-stu-id="cc799-138">Delete a Named Calculation</span></span>
 <span data-ttu-id="cc799-139">名前付き計算を削除しようとすると、削除するかどうかを確認するメッセージが、削除によって無効になるプロジェクトまたはデータベースに定義されているオブジェクトのリストと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc799-139">When you attempt to delete a named calculation, you are prompted with a list of the objects defined in the project or database that will be invalidated by the deletion.</span></span> <span data-ttu-id="cc799-140">計算を削除する前に、リストを慎重に確認します。</span><span class="sxs-lookup"><span data-stu-id="cc799-140">Review the list carefully before deleting the calculation.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc799-141">参照</span><span class="sxs-lookup"><span data-stu-id="cc799-141">See Also</span></span>
 [<span data-ttu-id="cc799-142">データ ソース ビューでの名前付きクエリの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="cc799-142">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-queries-in-a-data-source-view-analysis-services.md)


