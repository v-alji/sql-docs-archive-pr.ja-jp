---
title: 既存の階層データを使用したテーブルの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 966548b11ad4697abc06de5c5c239a511f80b7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713025"
---
# <a name="populating-a-table-with-existing-hierarchical-data"></a><span data-ttu-id="88ba5-102">既存の階層データを使用したテーブルの設定</span><span class="sxs-lookup"><span data-stu-id="88ba5-102">Populating a Table with Existing Hierarchical Data</span></span>
  <span data-ttu-id="88ba5-103"> ここでは、新しいテーブルを作成して、そのテーブルに **EmployeeDemo** テーブルのデータを設定します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-103">This task creates a new table and populates it with the data in the **EmployeeDemo** table.</span></span> <span data-ttu-id="88ba5-104">この作業には、次の手順があります。</span><span class="sxs-lookup"><span data-stu-id="88ba5-104">This task has the following steps:</span></span>  
  
-   <span data-ttu-id="88ba5-105">`hierarchyid` 列を含む新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-105">Create a new table that contains a `hierarchyid` column.</span></span> <span data-ttu-id="88ba5-106">この列を、既存の **EmployeeID** 列や **ManagerID** 列の代わりに使用してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="88ba5-106">This column could replace the existing **EmployeeID** and **ManagerID** columns.</span></span> <span data-ttu-id="88ba5-107">ただし、これらの列は保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88ba5-107">However, you will retain those columns.</span></span> <span data-ttu-id="88ba5-108">これは、既存のアプリケーションがこれらの列を参照している可能性があるためでもあり、転送後のデータをわかりやすくするためでもあります。</span><span class="sxs-lookup"><span data-stu-id="88ba5-108">This is because existing applications might refer to those columns, and also to help you understand the data after the transfer.</span></span> <span data-ttu-id="88ba5-109">テーブル定義では、 **OrgNode** が主キーであることを指定します。したがって、この列には一意の値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88ba5-109">The table definition specifies that **OrgNode** is the primary key, which requires the column to contain unique values.</span></span> <span data-ttu-id="88ba5-110">**OrgNode** 列のクラスター化インデックスは、 **OrgNode** シーケンスのデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-110">The clustered index on the **OrgNode** column will store the date in **OrgNode** sequence.</span></span>  
  
-   <span data-ttu-id="88ba5-111">各管理者に直属する従業員の数を追跡するために使用する一時テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-111">Create a temporary table that is used to track how many employees report directly to each manager.</span></span>  
  
-   <span data-ttu-id="88ba5-112">新しいテーブルを、 **EmployeeDemo** テーブルのデータを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-112">Populate the new table by using data from the **EmployeeDemo** table.</span></span>  
  
### <a name="to-create-a-new-table-named-neworg"></a><span data-ttu-id="88ba5-113">NewOrg という名前の新しいテーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="88ba5-113">To create a new table named NewOrg</span></span>  
  
-   <span data-ttu-id="88ba5-114">クエリ エディター ウィンドウで、次のコードを実行し、 **HumanResources.NewOrg**という名前の新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-114">In a Query Editor window, run the following code to create a new table named **HumanResources.NewOrg**:</span></span>  
  
    ```  
    CREATE TABLE NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="to-create-a-temporary-table-named-children"></a><span data-ttu-id="88ba5-115">#Children という名前の一時テーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="88ba5-115">To create a temporary table named #Children</span></span>  
  
1.  <span data-ttu-id="88ba5-116">**Num** という名前の列を持つ **#Children** という名前の一時テーブルを作成します。この列は、各ノードの子の数を格納します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-116">Create a temporary table named **#Children** with a column named **Num** that will contain the number of children for each node:</span></span>  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  <span data-ttu-id="88ba5-117">インデックスを作成します。このインデックスによって、 **NewOrg** テーブルを設定するクエリの速度が大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-117">Add an index that will significantly speed up the query that populates the **NewOrg** table:</span></span>  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a><span data-ttu-id="88ba5-118">NewOrg テーブルを設定するには</span><span class="sxs-lookup"><span data-stu-id="88ba5-118">To populate the NewOrg table</span></span>  
  
1.  <span data-ttu-id="88ba5-119">再帰クエリでは、集計を含むサブクエリが禁止されています。</span><span class="sxs-lookup"><span data-stu-id="88ba5-119">Recursive queries forbid subqueries with aggregates.</span></span> <span data-ttu-id="88ba5-120">代わりに、 **ROW_NUMBER()** メソッドを使用して [Num](/sql/t-sql/functions/row-number-transact-sql) 列を設定する次のコードによって、 **#Children** テーブルを設定します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-120">Instead, populate the **#Children** table with the following code, which uses the [ROW_NUMBER()](/sql/t-sql/functions/row-number-transact-sql) method to populate the **Num** column:</span></span>  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM EmployeeDemo  
    GO  
  
    ```  
  
2.  <span data-ttu-id="88ba5-121">**#Children** テーブルを確認します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-121">Review the **#Children** table.</span></span> <span data-ttu-id="88ba5-122">**Num** 列に、各管理者の連続する番号がどのように格納されているかに注目してください。</span><span class="sxs-lookup"><span data-stu-id="88ba5-122">Note how the **Num** column contains sequential numbers for each manager.</span></span>  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     `EmployeeID ManagerID Num`  
  
     `---------- --------- ---`  
  
     `1        NULL       1`  
  
     `2         1         1`  
  
     `3         1         2`  
  
     `4         2         1`  
  
     `5         2         2`  
  
     `6         2         3`  
  
     `7         3         1`  
  
     `8         3         2`  
  
     `9         4         1`  
  
     `10        4         2`  
  
3.  <span data-ttu-id="88ba5-123">**Neworg**テーブルを設定します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-123">Populate the **NewOrg** table.</span></span> <span data-ttu-id="88ba5-124">GetRoot メソッドと ToString メソッドを使用して、 **Num**値を形式に連結し、次に、 `hierarchyid` 結果の階層値で**orgnode**列を更新します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-124">Use the GetRoot and ToString methods to concatenate the **Num** values into the `hierarchyid` format, and then update the **OrgNode** column with the resultant hierarchical values:</span></span>  
  
    ```  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   
  
    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO  
  
    ```  
  
4.  <span data-ttu-id="88ba5-125">`hierarchyid` 列は、文字形式に変換すると、よりわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="88ba5-125">A `hierarchyid` column is more understandable when you convert it to character format.</span></span> <span data-ttu-id="88ba5-126">次のコードを実行して、 **NewOrg** テーブルのデータを確認します。このコードには、 **OrgNode** 列の 2 つの表記が含まれています。</span><span class="sxs-lookup"><span data-stu-id="88ba5-126">Review the data in the **NewOrg** table by executing the following code, which contains two representations of the **OrgNode** column:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM NewOrg   
    ORDER BY LogicalNode;  
    GO  
  
    ```  
  
     <span data-ttu-id="88ba5-127">**Logicalnode**列は、 `hierarchyid` 列を階層を表すより読みやすいテキスト形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-127">The **LogicalNode** column converts the `hierarchyid` column into a more readable text form that represents the hierarchy.</span></span> <span data-ttu-id="88ba5-128">残りの作業では、`ToString()` メソッドを使用して、`hierarchyid` 列の論理形式を表示します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-128">In the remaining tasks, you will use the `ToString()` method to show the logical format of the `hierarchyid` columns.</span></span>  
  
5.  <span data-ttu-id="88ba5-129">不要になった一時テーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-129">Drop the temporary table, which is no longer needed:</span></span>  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
 <span data-ttu-id="88ba5-130">次の作業では、階層構造をサポートするインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="88ba5-130">The next task will create indexes to support the hierarchical structure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="88ba5-131">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="88ba5-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="88ba5-132">NewOrg テーブルの最適化</span><span class="sxs-lookup"><span data-stu-id="88ba5-132">Optimizing the NewOrg Table</span></span>](lesson-1-3-optimizing-the-neworg-table.md)  
  
  
