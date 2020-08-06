---
title: 階層的な手法を使用した階層テーブルのデータの並べ替え Methods | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac6c93f359a81a80af81182120f213564680de0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631729"
---
# <a name="reordering-data-in-a-hierarchical-table-using-hierarchical-methods"></a><span data-ttu-id="d6951-102">階層的な手法を使用した階層テーブルのデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="d6951-102">Reordering Data in a Hierarchical Table Using Hierarchical Methods</span></span>
  <span data-ttu-id="d6951-103">階層の再編成は、一般的なメンテナンス タスクです。</span><span class="sxs-lookup"><span data-stu-id="d6951-103">Reorganizing a hierarchy is a common maintenance task.</span></span> <span data-ttu-id="d6951-104">ここでは、UPDATE ステートメントを [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) メソッドと共に使用して、まず 1 つの行を階層内の新しい位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="d6951-104">In this task, we will use an UPDATE statement with the [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) method to first move a single row to a new location in the hierarchy.</span></span> <span data-ttu-id="d6951-105">次に、サブツリー全体を新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="d6951-105">Then we will move an entire sub-tree to a new location.</span></span>  
  
 <span data-ttu-id="d6951-106">`GetReparentedValue` メソッドは 2 つの引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d6951-106">The `GetReparentedValue` method takes two arguments.</span></span> <span data-ttu-id="d6951-107">最初の引数は、変更する階層の一部を表します。</span><span class="sxs-lookup"><span data-stu-id="d6951-107">The first argument describes the part of the hierarchy to be modified.</span></span> <span data-ttu-id="d6951-108">たとえば、階層が **/1/4/2/3/** の場合に、最後の 2 つのノード ( **2/3/** ) はそのままで、 **/1/4/** セクションを変更して階層を **/2/1/2/3/** にするときは、変更するノード (**/1/4/**) を最初の引数として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6951-108">For example, if a hierarchy is **/1/4/2/3/** and you want to change the **/1/4/** section, the hierarchy becomes **/2/1/2/3/**, leaving the last two nodes (**2/3/**) unchanged, you must provide the changing nodes (**/1/4/**) as the first argument.</span></span> <span data-ttu-id="d6951-109">2 番目の引数には、新しい階層レベルを指定します。この例では、 **/2/1/** です。</span><span class="sxs-lookup"><span data-stu-id="d6951-109">The second argument provides the new hierarchy level, in our example **/2/1/**.</span></span> <span data-ttu-id="d6951-110">2 つの引数には、異なるレベル数を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6951-110">The two arguments do not have to contain the same number of levels.</span></span>  
  
### <a name="to-move-a-single-row-to-a-new-location-in-the-hierarchy"></a><span data-ttu-id="d6951-111">1 つの行を階層内の新しい位置に移動するには</span><span class="sxs-lookup"><span data-stu-id="d6951-111">To move a single row to a new location in the hierarchy</span></span>  
  
1.  <span data-ttu-id="d6951-112">現在、Wanida は Sariya に直属しています。</span><span class="sxs-lookup"><span data-stu-id="d6951-112">Currently Wanida reports to Sariya.</span></span> <span data-ttu-id="d6951-113">この手順では、Wanida を現在のノード **/1/1/** から移動して、Jill に直属するようにします。</span><span class="sxs-lookup"><span data-stu-id="d6951-113">In this procedure, you move Wanida from her current node **/1/1/,** so that she reports to Jill.</span></span> <span data-ttu-id="d6951-114">Wanida の新しいノードは **/3/1/** になるので、最初の引数は **/1/** 、2 番目の引数は **/3/** になります。</span><span class="sxs-lookup"><span data-stu-id="d6951-114">Her new node will become **/3/1/** so **/1/** is the first argument and **/3/** is the second.</span></span> <span data-ttu-id="d6951-115">これらは、Sariya と Jill の **OrgNode** 値に相当します。</span><span class="sxs-lookup"><span data-stu-id="d6951-115">These correspond to the **OrgNode** values of Sariya and Jill.</span></span> <span data-ttu-id="d6951-116">Wanida を Sariya の組織から Jill の組織に移動するには、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="d6951-116">Execute the following code to move Wanida from Sariya's organization to Jill's:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  <span data-ttu-id="d6951-117">結果を表示するには、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="d6951-117">Execute the following code to see the result:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     <span data-ttu-id="d6951-118">Wanida がノード **/3/1/** に移動しています。</span><span class="sxs-lookup"><span data-stu-id="d6951-118">Wanida is now at node **/3/1/**.</span></span>  
  
### <a name="to-reorganize-a-section-of-a-hierarchy"></a><span data-ttu-id="d6951-119">階層のセクションを再編成するには</span><span class="sxs-lookup"><span data-stu-id="d6951-119">To reorganize a section of a hierarchy</span></span>  
  
1.  <span data-ttu-id="d6951-120">多数の人員を一度に移動する方法を示すため、まず次のコードを実行して Wanida に直属するインターンを追加します。</span><span class="sxs-lookup"><span data-stu-id="d6951-120">To demonstrate how to move a larger number of people at the same time, first execute the following code to add an intern reporting to Wanida:</span></span>  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  <span data-ttu-id="d6951-121">Kevin が Wanida に直属するようになりました。Wanida は Jill に直属し、Jill は David に直属します。</span><span class="sxs-lookup"><span data-stu-id="d6951-121">Now Kevin reports to Wanida, who reports to Jill, who reports to David.</span></span> <span data-ttu-id="d6951-122">したがって、Kevin のレベルは **/3/1/1/** です。</span><span class="sxs-lookup"><span data-stu-id="d6951-122">That means that Kevin is at level **/3/1/1/**.</span></span> <span data-ttu-id="d6951-123">Jill の部下をすべて新しい管理者に移動するには、 **OrgNode** として **/3/** を持つすべてのノードを新しい値に更新します。</span><span class="sxs-lookup"><span data-stu-id="d6951-123">To move all of Jill's subordinates to a new manager, we will update all nodes that have **/3/** as their **OrgNode** to a new value.</span></span> <span data-ttu-id="d6951-124">Kevin を Wanida に直属させたまま、Wanida を Sariya に直属するように更新するには、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="d6951-124">Execute the following code to update Wanida to report to Sariya, but keep  Kevin reporting to Wanida:</span></span>  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  <span data-ttu-id="d6951-125">結果を表示するには、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="d6951-125">Execute the following code to see the result:</span></span>  
  
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
/1/1//2      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
 <span data-ttu-id="d6951-126">Jill に直属していた組織のツリー全体 (Wanida と Kevin の両方) が Sariya に直属するようになりました。</span><span class="sxs-lookup"><span data-stu-id="d6951-126">The entire organizational tree that had reported to Jill (both Wanida and Kevin) now reports to Sariya.</span></span>  
  
 <span data-ttu-id="d6951-127">階層のセクションを再編成するストアド プロシージャについては、「 [サブツリーの移動](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees)」の「サブツリーの移動」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6951-127">For a stored procedure to reorganize a section of a hierarchy, see the "Moving Subtrees" section of [Moving Subtrees](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d6951-128">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="d6951-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d6951-129">概要: 階層テーブルでのデータの管理</span><span class="sxs-lookup"><span data-stu-id="d6951-129">Summary: Managing Data in a Hierarchical Table</span></span>](lesson-2-5-summary-managing-data-in-a-hierarchical-table.md)  
  
  
