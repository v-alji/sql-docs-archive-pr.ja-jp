---
title: NewOrg テーブルの最適化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
author: stevestein
ms.author: sstein
ms.openlocfilehash: 39c09a3a73051e7a61f3a62a125232d83d1570c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630853"
---
# <a name="optimizing-the-neworg-table"></a><span data-ttu-id="6342e-102">NewOrg テーブルの最適化</span><span class="sxs-lookup"><span data-stu-id="6342e-102">Optimizing the NewOrg Table</span></span>
  <span data-ttu-id="6342e-103">「[既存の階層データを使用したテーブルの](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)設定」タスクで作成した**neword**テーブルには、すべての従業員情報が含まれており、データ型を使用して階層構造を表してい `hierarchyid` ます。</span><span class="sxs-lookup"><span data-stu-id="6342e-103">The **NewOrd** table that you created in the [Populating a Table with Existing Hierarchical Data](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) task contains all the employee information, and represents the hierarchical structure by using a `hierarchyid` data type.</span></span> <span data-ttu-id="6342e-104">ここでは、`hierarchyid` 列の検索をサポートする新しいインデックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="6342e-104">This task adds new indexes to support searches on the `hierarchyid` column.</span></span>  
  
## <a name="clustered-index"></a><span data-ttu-id="6342e-105">クラスター化インデックス</span><span class="sxs-lookup"><span data-stu-id="6342e-105">Clustered Index</span></span>  
 <span data-ttu-id="6342e-106">`hierarchyid`列 (**orgnode**) は、 **neworg**テーブルの主キーです。</span><span class="sxs-lookup"><span data-stu-id="6342e-106">The `hierarchyid` column (**OrgNode**) is the primary key for the **NewOrg** table.</span></span> <span data-ttu-id="6342e-107">**OrgNode** 列に一意性を持たせるため、このテーブルには作成時に **PK_NewOrg_OrgNode** という名前のクラスター化インデックスが格納されています。</span><span class="sxs-lookup"><span data-stu-id="6342e-107">When the table was created, it contained a clustered index named **PK_NewOrg_OrgNode** to enforce the uniqueness of the **OrgNode** column.</span></span> <span data-ttu-id="6342e-108">このクラスター化インデックスは、テーブルの深さ優先検索もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6342e-108">This clustered index also supports a depth-first search of the table.</span></span>  
  
## <a name="nonclustered-index"></a><span data-ttu-id="6342e-109">非クラスター化インデックス</span><span class="sxs-lookup"><span data-stu-id="6342e-109">Nonclustered Index</span></span>  
 <span data-ttu-id="6342e-110">この手順では、一般的な検索をサポートする 2 つの非クラスター化インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6342e-110">This step creates two nonclustered indexes to support typical searches.</span></span>  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a><span data-ttu-id="6342e-111">効率的な検索のため NewOrg テーブルにインデックスを付けるには</span><span class="sxs-lookup"><span data-stu-id="6342e-111">To index the NewOrg table for efficient searches</span></span>  
  
1.  <span data-ttu-id="6342e-112">階層の同じレベルでのクエリを容易にするには、 [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) メソッドを使用して、階層内のレベルを格納する計算列を作成します。</span><span class="sxs-lookup"><span data-stu-id="6342e-112">To help queries at the same level in the hierarchy, use the [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) method to create a computed column that contains the level in the hierarchy.</span></span> <span data-ttu-id="6342e-113">次に、レベルと `Hierarchyid` に基づく複合インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6342e-113">Then, create a composite index on the level and the `Hierarchyid`.</span></span> <span data-ttu-id="6342e-114">次のコードを実行すると、計算列と幅優先のインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6342e-114">Run the following code to create the computed column and the breadth-first index:</span></span>  
  
    ```  
    ALTER TABLE NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  <span data-ttu-id="6342e-115">**EmployeeID** 列に一意のインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6342e-115">Create a unique index on the **EmployeeID** column.</span></span> <span data-ttu-id="6342e-116">これは、 **EmployeeID** の番号によって 1 人の従業員を検索する従来の単一参照です。</span><span class="sxs-lookup"><span data-stu-id="6342e-116">This is the traditional singleton lookup of a single employee by **EmployeeID** number.</span></span> <span data-ttu-id="6342e-117">次のコードを実行すると、 **EmployeeID**のインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6342e-117">Run the following code to create an index on **EmployeeID**:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON NewOrg(EmployeeID) ;  
    GO  
    ```  
  
3.  <span data-ttu-id="6342e-118">次のコードを実行して、3 種類の各インデックスの順にテーブルからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="6342e-118">Run the following code to retrieve data from the table in the order of each of the three indexes:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM NewOrg   
    ORDER BY OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY H_Level, OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  <span data-ttu-id="6342e-119">結果セットを比較して、順序がどのように格納されているかをインデックスの種類ごとに確認します。</span><span class="sxs-lookup"><span data-stu-id="6342e-119">Compare the result sets to see how the order is stored in each type of index.</span></span> <span data-ttu-id="6342e-120">それぞれの出力の最初の 4 行だけを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6342e-120">Only the first four rows of each output follow.</span></span>  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     <span data-ttu-id="6342e-121">深さ優先のインデックス : 従業員のレコードは、それぞれのマネージャーのレコードに隣接して格納されます。</span><span class="sxs-lookup"><span data-stu-id="6342e-121">Depth-first index: Employee records are stored adjacent to their manager.</span></span>  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     <span data-ttu-id="6342e-122">**EmployeeID**優先のインデックス: 行は **EmployeeID** の順に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6342e-122">**EmployeeID**-first index: Rows are stored in **EmployeeID** sequence.</span></span>  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
> [!NOTE]  
>  <span data-ttu-id="6342e-123">深さ優先のインデックスと幅優先のインデックスの違いを示す図については、「[階層データ (SQL Server)](../hierarchical-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6342e-123">For diagrams that show the difference between a depth-first index and a breadth-first index, see [Hierarchical Data &#40;SQL Server&#41;](../hierarchical-data-sql-server.md).</span></span>  
  
#### <a name="to-drop-the-unnecessary-columns"></a><span data-ttu-id="6342e-124">不要な列を削除するには</span><span class="sxs-lookup"><span data-stu-id="6342e-124">To drop the unnecessary columns</span></span>  
  
1.  <span data-ttu-id="6342e-125">**ManagerID** 列が表す従業員とマネージャーのリレーションシップは、現在は **OrgNode** 列によって表されるようになっています。</span><span class="sxs-lookup"><span data-stu-id="6342e-125">The **ManagerID** column represents the employee/manager relationship, which is now represented by the **OrgNode** column.</span></span> <span data-ttu-id="6342e-126">**ManagerID** 列を必要とするアプリケーションが他にない場合は、次のステートメントを使用してこの列を削除することを検討します。</span><span class="sxs-lookup"><span data-stu-id="6342e-126">If other applications do not need the **ManagerID** column, consider dropping it by using the following statement:</span></span>  
  
    ```  
    ALTER TABLE NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  <span data-ttu-id="6342e-127">**EmployeeID** 列も冗長です。</span><span class="sxs-lookup"><span data-stu-id="6342e-127">The **EmployeeID** column is also redundant.</span></span> <span data-ttu-id="6342e-128">各従業員は、 **OrgNode** 列によって一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="6342e-128">The **OrgNode** column uniquely identifies each employee.</span></span> <span data-ttu-id="6342e-129">**EmployeeID** 列を必要とするアプリケーションが他にない場合は、次のコードを使用して、インデックスを削除した後に列を削除することを検討します。</span><span class="sxs-lookup"><span data-stu-id="6342e-129">If other applications do not need the **EmployeeID** column, consider dropping the index and then the column by using the following code:</span></span>  
  
    ```  
    DROP INDEX EmpIDs_unq ON NewOrg ;  
    ALTER TABLE NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a><span data-ttu-id="6342e-130">元のテーブルを新しいテーブルに置き換えるには</span><span class="sxs-lookup"><span data-stu-id="6342e-130">To replace the original table with the new table</span></span>  
  
1.  <span data-ttu-id="6342e-131">元のテーブルに追加のインデックスや制約が格納されている場合は、それらを **NewOrg** テーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="6342e-131">If your original table contained any additional indexes or constraints, add them to the **NewOrg** table.</span></span>  
  
2.  <span data-ttu-id="6342e-132">古い **EmployeeDemo** テーブルを新しいテーブルに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6342e-132">Replace the old **EmployeeDemo** table with the new table.</span></span> <span data-ttu-id="6342e-133">次のコードを実行すると、古いテーブルが削除され、新しいテーブルの名前がその古い名前に変更されます。</span><span class="sxs-lookup"><span data-stu-id="6342e-133">Run the following code to drop the old table, and then rename the new table with the old name:</span></span>  
  
    ```  
    DROP TABLE EmployeeDemo ;  
    GO  
    sp_rename 'NewOrg', EmployeeDemo ;  
    GO  
    ```  
  
3.  <span data-ttu-id="6342e-134">次のコードを実行して、最終的なテーブルを確認します。</span><span class="sxs-lookup"><span data-stu-id="6342e-134">Run the following code to examine the final table:</span></span>  
  
    ```  
    SELECT * FROM EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6342e-135">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="6342e-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6342e-136">概要: テーブルの階層構造への変換</span><span class="sxs-lookup"><span data-stu-id="6342e-136">Summary: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
