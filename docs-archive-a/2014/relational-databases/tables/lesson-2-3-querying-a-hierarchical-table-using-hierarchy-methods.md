---
title: 階層的な手法を使用した階層テーブルのクエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6c86c8e8678fc821dc3796a511349c1c3498bdb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641996"
---
# <a name="querying-a-hierarchical-table-using-hierarchy-methods"></a><span data-ttu-id="c7fde-102">階層的な手法を使用した階層テーブルのクエリ</span><span class="sxs-lookup"><span data-stu-id="c7fde-102">Querying a Hierarchical Table Using Hierarchy Methods</span></span>
  <span data-ttu-id="c7fde-103">HumanResources.EmployeeOrg テーブルに完全にデータが設定されたので、ここでは階層的な手法のいくつかを使用して階層をクエリする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-103">Now that the HumanResources.EmployeeOrg table is fully populated, this task will show you how to query the hierarchy using some of the hierarchical methods.</span></span>  
  
### <a name="to-find-subordinate-nodes"></a><span data-ttu-id="c7fde-104">下位要素を検索するには</span><span class="sxs-lookup"><span data-stu-id="c7fde-104">To find subordinate nodes</span></span>  
  
1.  <span data-ttu-id="c7fde-105">Sariya には 1 人の部下がいます。</span><span class="sxs-lookup"><span data-stu-id="c7fde-105">Sariya has one subordinate employee.</span></span> <span data-ttu-id="c7fde-106">Sariya の部下に対するクエリを実行するには、 [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) メソッドを使用する次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-106">To query for Sariya's subordinates, execute the following query that uses the [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) method:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
     <span data-ttu-id="c7fde-107">結果には、Sariya と Wanida の両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7fde-107">The result lists both Sariya and Wanida.</span></span> <span data-ttu-id="c7fde-108">Sariya は、0 レべルの子孫であるために表示されています。</span><span class="sxs-lookup"><span data-stu-id="c7fde-108">Sariya is listed because she is the descendant at the 0 level.</span></span> <span data-ttu-id="c7fde-109">Wanida は 1 レベルの子孫です。</span><span class="sxs-lookup"><span data-stu-id="c7fde-109">Wanida is the descendant at the 1 level.</span></span>  
  
2.  <span data-ttu-id="c7fde-110">[GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) メソッドを使用してこの情報に対してクエリを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="c7fde-110">You can also query for this information by using the [GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) method.</span></span> <span data-ttu-id="c7fde-111">`GetAncestor` 返そうとしているレベルの引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c7fde-111">`GetAncestor` takes an argument for the level that you are trying to return.</span></span> <span data-ttu-id="c7fde-112">Wanida は Sariya よりも 1 つ下のレベルであるため、次のコードに示すように `GetAncestor(1)` を使用します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-112">Since Wanida is one level underneath Sariya, use `GetAncestor(1)` as demonstrated in the following code:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
     <span data-ttu-id="c7fde-113">この場合、結果には Wanida のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7fde-113">This time the result lists only Wanida.</span></span>  
  
3.  <span data-ttu-id="c7fde-114">次に、 `@CurrentEmployee` を David (EmployeeID 6) に、レベルを 2 にそれぞれ変更します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-114">Now change the `@CurrentEmployee` to David (EmployeeID 6) and the level to 2.</span></span> <span data-ttu-id="c7fde-115">次のコードを実行した場合も Wanida が返されます。</span><span class="sxs-lookup"><span data-stu-id="c7fde-115">Execute the following to also return Wanida:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
     <span data-ttu-id="c7fde-116">この場合は、David に直属する 2 つ下のレベルの Mary も返されます。</span><span class="sxs-lookup"><span data-stu-id="c7fde-116">This time, you also receive Mary who also reports to David, two levels down.</span></span>  
  
### <a name="to-use-getroot-and-getlevel"></a><span data-ttu-id="c7fde-117">GetRoot および GetLevel を使用するには</span><span class="sxs-lookup"><span data-stu-id="c7fde-117">To use GetRoot, and GetLevel</span></span>  
  
1.  <span data-ttu-id="c7fde-118">階層が大きくなるにつれ、メンバーが階層内のどこに位置するのかを確認するのが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="c7fde-118">As the hierarchy grows larger it is more difficult to determine where the members are in the hierarchy.</span></span> <span data-ttu-id="c7fde-119">各行が階層内の何レベル下にあるかを検索するには、 [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-119">Use the [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) method to find how many levels down each row is in the hierarchy.</span></span> <span data-ttu-id="c7fde-120">すべての行のレベルを表示するには次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-120">Execute the following code to view the levels of all the rows:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  <span data-ttu-id="c7fde-121">階層内のルート ノードを検索するには、 [GetRoot](/sql/t-sql/data-types/getroot-database-engine) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-121">Use the [GetRoot](/sql/t-sql/data-types/getroot-database-engine) method to find the root node in the hierarchy.</span></span> <span data-ttu-id="c7fde-122">次のコードは、ルートである 1 つの行を返します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-122">The following code returns the single row which is the root:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
 <span data-ttu-id="c7fde-123">次に、階層を再編成します。</span><span class="sxs-lookup"><span data-stu-id="c7fde-123">The next task will reorganize the hierarchy.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c7fde-124">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="c7fde-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c7fde-125">階層的な手法を使用した階層テーブルのデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="c7fde-125">Reordering Data in a Hierarchical Table Using Hierarchical Methods</span></span>](lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
