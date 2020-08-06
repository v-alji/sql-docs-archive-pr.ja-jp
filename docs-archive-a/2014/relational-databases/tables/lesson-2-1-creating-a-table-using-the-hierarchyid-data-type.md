---
title: hierarchyid データ型を使用したテーブルの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2c9b59795949e11cabd21b0be8de844b33d73c37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740789"
---
# <a name="creating-a-table-using-the-hierarchyid-data-type"></a><span data-ttu-id="c6656-102">hierarchyid データ型を使用したテーブルの作成</span><span class="sxs-lookup"><span data-stu-id="c6656-102">Creating a Table Using the hierarchyid Data Type</span></span>
  <span data-ttu-id="c6656-103">EmployeeOrg という名前のテーブルを作成する例を次に示します。このテーブルには、従業員データと、それらの従業員のレポート階層が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c6656-103">The following example creates a table named EmployeeOrg, which includes employee data together with their reporting hierarchy.</span></span> <span data-ttu-id="c6656-104">この例では、テーブルを [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに作成しますが、これは任意です。</span><span class="sxs-lookup"><span data-stu-id="c6656-104">The example creates the table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, but that is optional.</span></span> <span data-ttu-id="c6656-105">例をわかりやすくするために、このテーブルには 5 つの列のみ含まれています。</span><span class="sxs-lookup"><span data-stu-id="c6656-105">To keep the example simple, this table includes only five columns:</span></span>  
  
-   <span data-ttu-id="c6656-106">OrgNode は、階層リレーションシップを格納する `hierarchyid` 列です。</span><span class="sxs-lookup"><span data-stu-id="c6656-106">OrgNode is a `hierarchyid` column that stores the hierarchical relationship.</span></span>  
  
-   <span data-ttu-id="c6656-107">OrgLevel は OrgNode 列に基づく計算列であり、階層内での各ノードのレベルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="c6656-107">OrgLevel is a computed column, based on the OrgNode column that stores each nodes level in the hierarchy.</span></span> <span data-ttu-id="c6656-108">これは、幅優先のインデックスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="c6656-108">It will be used for a breadth-first index.</span></span>  
  
-   <span data-ttu-id="c6656-109">EmployeeID には、給与処理などのアプリケーションで使用される通常の従業員識別番号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c6656-109">EmployeeID contains the typical employee identification number that is used for applications such as payroll.</span></span> <span data-ttu-id="c6656-110">新しいアプリケーションの開発では、アプリケーションは OrgNode 列を使用でき、この個別の EmployeeID 列は不要です。</span><span class="sxs-lookup"><span data-stu-id="c6656-110">In new application development, applications can use the OrgNode column and this separate EmployeeID column is not needed.</span></span>  
  
-   <span data-ttu-id="c6656-111">EmpName には、従業員の名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c6656-111">EmpName contains the name of the employee.</span></span>  
  
-   <span data-ttu-id="c6656-112">Title には、従業員の役職が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c6656-112">Title contains the title of the employee.</span></span>  
  
### <a name="to-create-the-employeeorg-table"></a><span data-ttu-id="c6656-113">EmployeeOrg テーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="c6656-113">To create the EmployeeOrg table</span></span>  
  
1.  <span data-ttu-id="c6656-114">クエリ エディター ウィンドウで、次のコードを実行し、 `EmployeeOrg` テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c6656-114">In a Query Editor window, run the following code to create the `EmployeeOrg` table.</span></span> <span data-ttu-id="c6656-115">`OrgNode` 列を、クラスター化インデックスのある主キーとして指定すると、深さ優先のインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c6656-115">Specifying the `OrgNode` column as the primary key with a clustered index will create a depth-first index:</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  <span data-ttu-id="c6656-116">次のコードを実行して `OrgLevel` 列と `OrgNode` 列に複合インデックスを作成し、効率的な幅優先の検索をサポートします。</span><span class="sxs-lookup"><span data-stu-id="c6656-116">Run the following code to create a composite index on the `OrgLevel` and `OrgNode` columns to support efficient breadth-first searches:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
 <span data-ttu-id="c6656-117">これでテーブルはデータを受け入れる準備ができました。</span><span class="sxs-lookup"><span data-stu-id="c6656-117">The table is now ready for data.</span></span> <span data-ttu-id="c6656-118">次に、階層的な手法を使用してテーブルにデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="c6656-118">The next task will populate the table by using hierarchical methods.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c6656-119">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="c6656-119">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c6656-120">階層的な手法を使用した階層テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="c6656-120">Populating a Hierarchical Table Using Hierarchical Methods</span></span>](lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
