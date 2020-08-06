---
title: Employee テーブルの現在の構造の確認 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7f63773ebc1f28fb24f8f1000c3f87ee4d50544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630856"
---
# <a name="examining-the-current-structure-of-the-employee-table"></a><span data-ttu-id="92bdf-102">Employee テーブルの現在の構造の確認</span><span class="sxs-lookup"><span data-stu-id="92bdf-102">Examining the Current Structure of the Employee Table</span></span>
  <span data-ttu-id="92bdf-103"> サンプル [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースには、**HumanResources** スキーマに含まれる **Employee** テーブルがあります。</span><span class="sxs-lookup"><span data-stu-id="92bdf-103">The sample [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database contains an **Employee** table in the **HumanResources** schema.</span></span> <span data-ttu-id="92bdf-104">元のテーブルを変更しないように、この手順では、 **Employee** テーブルのコピーを作成して **EmployeeDemo**という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="92bdf-104">To avoid changing the original table, this step makes a copy of the **Employee** table named **EmployeeDemo**.</span></span> <span data-ttu-id="92bdf-105">例を単純にするために、元のテーブルから 5 列だけをコピーします。</span><span class="sxs-lookup"><span data-stu-id="92bdf-105">To simplify the example, you only copy five columns from the original table.</span></span> <span data-ttu-id="92bdf-106">次に、 **Humanresources.employee demo**テーブルに対してクエリを実行し、データ型を使用せずにテーブルでデータがどのように構造化されているかを確認します `hierarchyid` 。</span><span class="sxs-lookup"><span data-stu-id="92bdf-106">Then, you query the **HumanResources.EmployeeDemo** table to review how the data is structured in a table without using the `hierarchyid` data type.</span></span>  
  
### <a name="to-copy-the-employee-table"></a><span data-ttu-id="92bdf-107">Employee テーブルをコピーするには</span><span class="sxs-lookup"><span data-stu-id="92bdf-107">To copy the Employee table</span></span>  
  
1.  <span data-ttu-id="92bdf-108">クエリ エディターのウィンドウで、次のコードを実行し、 **Employee** テーブルから新しいテーブルの **EmployeeDemo**にテーブル構造とデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="92bdf-108">In a Query Editor window, run the following code to copy the table structure and data from the **Employee** table into a new table named **EmployeeDemo**.</span></span>  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a><span data-ttu-id="92bdf-109">EmployeeDemo テーブルの構造とデータを確認するには</span><span class="sxs-lookup"><span data-stu-id="92bdf-109">To examine the structure and data of the EmployeeDemo table</span></span>  
  
-   <span data-ttu-id="92bdf-110">この新しい **EmployeeDemo** テーブルは、新しい構造に移行可能な、既存のデータベースの一般的なテーブルを表しています。</span><span class="sxs-lookup"><span data-stu-id="92bdf-110">This new **EmployeeDemo** table represents a typical table in an existing database that you might want to migrate to a new structure.</span></span> <span data-ttu-id="92bdf-111">クエリ エディター ウィンドウで次のコードを実行すると、テーブルで自己結合を使用して従業員と管理者のリレーションシップを示しているようすを確認できます。</span><span class="sxs-lookup"><span data-stu-id="92bdf-111">In a Query Editor window, run the following code to show how the table uses a self join to display the employee/manager relationships:</span></span>  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
     <span data-ttu-id="92bdf-112">結果は合計 290 行にわたります。</span><span class="sxs-lookup"><span data-stu-id="92bdf-112">The results continue for a total of 290 rows.</span></span>  
  
 <span data-ttu-id="92bdf-113">`ORDER BY` 句を使用していることによって、出力では、各管理レベルの直属の部下がまとめて表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="92bdf-113">Notice that the `ORDER BY` clause caused the output to list the direct reports of each management level together.</span></span> <span data-ttu-id="92bdf-114">たとえば、 **MgrID** 3 (roberto0) の 7 人の直属の部下がすべて左右に並べて表示されています。</span><span class="sxs-lookup"><span data-stu-id="92bdf-114">For instance, all seven of the direct reports of **MgrID** 3 (roberto0) are listed adjacent to each other.</span></span> <span data-ttu-id="92bdf-115">実際に **MgrID** 3 に直属するすべての人をグループ化することは、不可能ではありませんが、かなり難しくなります。</span><span class="sxs-lookup"><span data-stu-id="92bdf-115">Although not impossible, it is much more difficult to group all those who eventually report to **MgrID** 3.</span></span>  
  
 <span data-ttu-id="92bdf-116">次の作業では、`hierarchyid` データ型を使用して新しいテーブルを作成し、この新しいテーブルにデータを移動します。</span><span class="sxs-lookup"><span data-stu-id="92bdf-116">In the next task, we will create a new table with a `hierarchyid` data type, and move the data into the new table.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="92bdf-117">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="92bdf-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="92bdf-118">既存の階層データを使用したテーブルの設定</span><span class="sxs-lookup"><span data-stu-id="92bdf-118">Populating a Table with Existing Hierarchical Data</span></span>](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
