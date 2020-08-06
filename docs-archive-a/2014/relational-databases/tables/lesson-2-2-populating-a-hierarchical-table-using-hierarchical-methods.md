---
title: 階層的な手法を使用した階層テーブルの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID
ms.assetid: 2c95fa60-5b8e-4a05-ac09-cffe2b05900a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef99d711a772a075f568a83f5d56fcecaaa598f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642661"
---
# <a name="populating-a-hierarchical-table-using-hierarchical-methods"></a><span data-ttu-id="bcd55-102">階層的な手法を使用した階層テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="bcd55-102">Populating a Hierarchical Table Using Hierarchical Methods</span></span>
  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="bcd55-103">のマーケティング部門には 8 人の従業員が勤務しています。</span><span class="sxs-lookup"><span data-stu-id="bcd55-103">has 8 employees working in the Marketing department.</span></span> <span data-ttu-id="bcd55-104">従業員の階層は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bcd55-104">The employee hierarchy looks like this:</span></span>  
  
 <span data-ttu-id="bcd55-105">**David**( **EmployeeID 6** ) は Marketing Manager です。</span><span class="sxs-lookup"><span data-stu-id="bcd55-105">**David**, **EmployeeID** 6, is the Marketing Manager.</span></span> <span data-ttu-id="bcd55-106">**David**には、次の 3 人の Marketing Specialist が直属します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-106">Three Marketing Specialists report to **David**:</span></span>  
  
-   <span data-ttu-id="bcd55-107">**Sariya**( **EmployeeID 46** )</span><span class="sxs-lookup"><span data-stu-id="bcd55-107">**Sariya**, **EmployeeID** 46</span></span>  
  
-   <span data-ttu-id="bcd55-108">**John**( **EmployeeID 271** )</span><span class="sxs-lookup"><span data-stu-id="bcd55-108">**John**, **EmployeeID** 271</span></span>  
  
-   <span data-ttu-id="bcd55-109">**Jill**( **EmployeeID 119** )</span><span class="sxs-lookup"><span data-stu-id="bcd55-109">**Jill**, **EmployeeID** 119</span></span>  
  
 <span data-ttu-id="bcd55-110">Marketing Assistant の **Wanida** (**EmployeeID** 269) は **Sariya**に直属し、Marketing Assistant の **Mary** (**EmployeeID** 272) は **John**に直属します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-110">Marketing Assistant **Wanida** (**EmployeeID** 269), reports to **Sariya**, and Marketing Assistant **Mary** (**EmployeeID** 272), reports to **John**.</span></span>  
  
### <a name="to-insert-the-root-of-the-hierarchy-tree"></a><span data-ttu-id="bcd55-111">階層ツリーのルートを挿入するには</span><span class="sxs-lookup"><span data-stu-id="bcd55-111">To insert the root of the hierarchy tree</span></span>  
  
1.  <span data-ttu-id="bcd55-112">次の例では、Marketing Manager である **David** を、階層のルートに位置するテーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-112">The following example inserts **David** the Marketing Manager into the table at the root of the hierarchy.</span></span> <span data-ttu-id="bcd55-113">**OrdLevel** 列は計算列です。</span><span class="sxs-lookup"><span data-stu-id="bcd55-113">The **OrdLevel** column is a computed column.</span></span> <span data-ttu-id="bcd55-114">したがって、INSERT ステートメントの一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="bcd55-114">Therefore, it is not part of the INSERT statement.</span></span> <span data-ttu-id="bcd55-115">この最初のレコードでは、 [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) メソッドを使用して、この最初のレコードを階層のルートとして挿入します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-115">This first record uses the [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) method to populate this first record as the root of the hierarchy.</span></span>  
  
    ```  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  <span data-ttu-id="bcd55-116">テーブルの最初の行を調べるには、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-116">Execute the following code to examine initial row in the table:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
 <span data-ttu-id="bcd55-117">前のレッスンと同様、`ToString()` メソッドを使用して、`hierarchyid` データ型をよりわかりやすい形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-117">As in the previous lesson, we use the `ToString()` method to convert the `hierarchyid` data type to a format that is more easily understood.</span></span>  
  
### <a name="to-insert-a-subordinate-employee"></a><span data-ttu-id="bcd55-118">部下を挿入するには</span><span class="sxs-lookup"><span data-stu-id="bcd55-118">To insert a subordinate employee</span></span>  
  
1.  <span data-ttu-id="bcd55-119">**Sariya** は **David**に直属します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-119">**Sariya** reports to **David**.</span></span> <span data-ttu-id="bcd55-120">**Sariya の**ノードを挿入するには、データ型の適切な**orgnode**値を作成する必要があり `hierarchyid` ます。</span><span class="sxs-lookup"><span data-stu-id="bcd55-120">To insert **Sariya's** node, you must create an appropriate **OrgNode** value of data type `hierarchyid`.</span></span> <span data-ttu-id="bcd55-121">次のコードでは、`hierarchyid` データ型の変数を作成して、テーブルのルート OrgNode 値をその変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-121">The following code creates a variable of data type `hierarchyid` and populates it with the root OrgNode value of the table.</span></span> <span data-ttu-id="bcd55-122">次に、その変数を [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) メソッドと共に使用して、部下のノードである行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-122">Then uses that variable with the [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) method to insert row that is a subordinate node.</span></span> <span data-ttu-id="bcd55-123">`GetDescendant` は、2 つの引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bcd55-123">`GetDescendant` takes two arguments.</span></span> <span data-ttu-id="bcd55-124">引数値の次のオプションを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bcd55-124">Review the following options for the argument values:</span></span>  
  
    -   <span data-ttu-id="bcd55-125">parent が NULL の場合、 `GetDescendant` は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-125">If parent is NULL, `GetDescendant` returns NULL.</span></span>  
  
    -   <span data-ttu-id="bcd55-126">parent が NULL でなく、child1 と child2 の両方が NULL の場合、 `GetDescendant` は parent の子を返します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-126">If parent is not NULL, and both child1 and child2 are NULL, `GetDescendant` returns a child of parent.</span></span>  
  
    -   <span data-ttu-id="bcd55-127">parent と child1 が NULL でなく、child2 が NULL の場合、 `GetDescendant` は child1 より大きい parent の子を返します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-127">If parent and child1 are not NULL, and child2 is NULL, `GetDescendant` returns a child of parent greater than child1.</span></span>  
  
    -   <span data-ttu-id="bcd55-128">parent と child2 が NULL でなく、child1 が NULL の場合、 `GetDescendant` は child2 より小さい parent の子を返します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-128">If parent and child2 are not NULL and child1 is NULL, `GetDescendant` returns a child of parent less than child2.</span></span>  
  
    -   <span data-ttu-id="bcd55-129">parent、child1、child2 のすべてが NULL でない場合、 `GetDescendant` は child1 より大きく child2 より小さい parent の子を返します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-129">If parent, child1, and child2 are all not NULL, `GetDescendant` returns a child of parent greater than child1 and less than child2.</span></span>  
  
     <span data-ttu-id="bcd55-130">テーブルにはルート以外にまだ 1 行もないため、次のコードではルートの `(NULL, NULL)` 引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-130">The following code uses the `(NULL, NULL)` arguments of the root parent because there are not yet any rows in the table except the root.</span></span> <span data-ttu-id="bcd55-131">**Sariya**を挿入するには、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-131">Execute the following code to insert **Sariya**:</span></span>  
  
    ```  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  <span data-ttu-id="bcd55-132">テーブルにクエリを実行してエントリがどのように表示されるかを確認するには、最初の手順のクエリを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-132">Repeat the query from the first procedure to query the table and see how the entries appear:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="to-create-a-procedure-for-entering-new-nodes"></a><span data-ttu-id="bcd55-133">新しいノードを入力するためのプロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="bcd55-133">To create a procedure for entering new nodes</span></span>  
  
1.  <span data-ttu-id="bcd55-134">データの入力を簡略化するには、次のストアド プロシージャを作成して、 **EmployeeOrg** テーブルに従業員を追加します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-134">To simplify entering data, create the following stored procedure to add employees to the **EmployeeOrg** table.</span></span> <span data-ttu-id="bcd55-135">このプロシージャは、追加される従業員に関する入力値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bcd55-135">The procedure accepts input values about the employee being added.</span></span> <span data-ttu-id="bcd55-136">これには、新しい従業員の管理者の **EmployeeID** 、新しい従業員の **EmployeeID** 番号、従業員の名と役職が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bcd55-136">This includes the **EmployeeID** of the new employee's manager, the new employee's **EmployeeID** number, and their first name and title.</span></span> <span data-ttu-id="bcd55-137">このプロシージャでは、 `GetDescendant()` と [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) メソッドも使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-137">The procedure uses `GetDescendant()` and also the [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) method.</span></span> <span data-ttu-id="bcd55-138">プロシージャを作成するには、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-138">Execute the following code to create the procedure:</span></span>  
  
    ```  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  <span data-ttu-id="bcd55-139">次の例では、 **David**の直接または間接的な部下である残り 4 人の従業員を追加します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-139">The following example adds the remaining 4 employees that report directly or indirectly to **David**.</span></span>  
  
    ```  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  <span data-ttu-id="bcd55-140">**EmployeeOrg** テーブルの行を調べるには、再び次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="bcd55-140">Again, execute the following query examine the rows in the **EmployeeOrg** table:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    /1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
 <span data-ttu-id="bcd55-141">テーブルに、マーケティング組織が完全に作成されました。</span><span class="sxs-lookup"><span data-stu-id="bcd55-141">The table is now fully populated with the Marketing organization.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bcd55-142">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="bcd55-142">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bcd55-143">階層的な手法を使用した階層テーブルのクエリ</span><span class="sxs-lookup"><span data-stu-id="bcd55-143">Querying a Hierarchical Table Using Hierarchy Methods</span></span>](lesson-2-3-querying-a-hierarchical-table-using-hierarchy-methods.md)  
  
  
