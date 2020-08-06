---
title: MSSQLSERVER_4186 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4186 (Database Engine error)
ms.assetid: 1ae88554-f291-45bc-a186-6f41d9cd0fca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 525c1c3bd6e631044b8bc7f17b2c2a01aeb1ef8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631980"
---
# <a name="mssqlserver_4186"></a><span data-ttu-id="daccc-102">MSSQLSERVER_4186</span><span class="sxs-lookup"><span data-stu-id="daccc-102">MSSQLSERVER_4186</span></span>
    
## <a name="details"></a><span data-ttu-id="daccc-103">詳細</span><span class="sxs-lookup"><span data-stu-id="daccc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="daccc-104">製品名</span><span class="sxs-lookup"><span data-stu-id="daccc-104">Product Name</span></span>|<span data-ttu-id="daccc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="daccc-105">SQL Server</span></span>|  
|<span data-ttu-id="daccc-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="daccc-106">Event ID</span></span>|<span data-ttu-id="daccc-107">4186</span><span class="sxs-lookup"><span data-stu-id="daccc-107">4186</span></span>|  
|<span data-ttu-id="daccc-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="daccc-108">Event Source</span></span>|<span data-ttu-id="daccc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="daccc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="daccc-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="daccc-110">Component</span></span>|<span data-ttu-id="daccc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="daccc-111">SQLEngine</span></span>|  
|<span data-ttu-id="daccc-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="daccc-112">Symbolic Name</span></span>||  
|<span data-ttu-id="daccc-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="daccc-113">Message Text</span></span>|<span data-ttu-id="daccc-114">列 '%ls.%.\*ls' は、OUTPUT 句で参照できません。列定義にサブクエリが含まれているか、列定義でユーザー データまたはシステム データにアクセスする関数を参照しています。</span><span class="sxs-lookup"><span data-stu-id="daccc-114">Column '%ls.%.\*ls' cannot be referenced in the OUTPUT clause because the column definition contains a subquery or references a function that performs user or system data access.</span></span> <span data-ttu-id="daccc-115">関数は、スキーマ バインドされていない場合、既定でデータ アクセスを実行すると想定されます。</span><span class="sxs-lookup"><span data-stu-id="daccc-115">A function is assumed by default to perform data access if it is not schemabound.</span></span> <span data-ttu-id="daccc-116">列定義からサブクエリまたは関数を削除するか、OUTPUT 句から列を削除することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="daccc-116">Consider removing the subquery or function from the column definition or removing the column from the OUTPUT clause.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="daccc-117">説明</span><span class="sxs-lookup"><span data-stu-id="daccc-117">Explanation</span></span>  
 <span data-ttu-id="daccc-118">非決定的な動作を防ぐために、ビューまたはインライン テーブル値関数から返される列が次のいずれかの方法で定義されている場合、OUTPUT 句ではその列を参照できません。</span><span class="sxs-lookup"><span data-stu-id="daccc-118">To prevent nondeterministic behavior, the OUTPUT clause cannot reference a column from a view or inline table-valued function when that column is defined by one of the following methods:</span></span>  
  
-   <span data-ttu-id="daccc-119">サブクエリ。</span><span class="sxs-lookup"><span data-stu-id="daccc-119">A subquery.</span></span>  
  
-   <span data-ttu-id="daccc-120">ユーザー データやシステム データにアクセスするユーザー定義関数、またはそのようなアクセスを行うと想定されるユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="daccc-120">A user-defined function that performs user or system data access, or is assumed to perform such access.</span></span>  
  
-   <span data-ttu-id="daccc-121">ユーザー データやシステム データにアクセスするユーザー定義関数を定義に含む計算列</span><span class="sxs-lookup"><span data-stu-id="daccc-121">A computed column that contains a user-defined function that performs user or system data access in its definition.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="daccc-122">例</span><span class="sxs-lookup"><span data-stu-id="daccc-122">Examples</span></span>  
 <span data-ttu-id="daccc-123">**サブクエリで定義されたビュー列**</span><span class="sxs-lookup"><span data-stu-id="daccc-123">**View Column Defined by a Subquery**</span></span>  
  
 <span data-ttu-id="daccc-124">次の例では、選択リストでサブクエリを使用して `State` 列を定義するビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="daccc-124">The following example creates a view that uses a subquery in the select list to define the column `State`.</span></span> <span data-ttu-id="daccc-125">次に、UPDATE ステートメントで OUTPUT 句の `State` 列を参照すると、選択リストのサブクエリが原因でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="daccc-125">An UPDATE statement then references the `State` column in the OUTPUT clause and fails because ob the subquery in the select list.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.V1  
AS  
    SELECT City,  
-- subquery to return the State name  
           (SELECT Name FROM Person.StateProvince AS sp   
            WHERE sp.StateProvinceID = a.StateProvinceID) AS State  
    FROM Person.Address AS a;  
GO  
--Reference the State column in the OUTPUT clause of an UPDATE statement  
UPDATE dbo.V1   
SET City = City + 'Test'   
OUTPUT deleted.City, deleted.State, inserted.City, inserted.State  
WHERE State = 'Texas';  
GO  
```  
  
 <span data-ttu-id="daccc-126">**関数で定義されたビュー列**</span><span class="sxs-lookup"><span data-stu-id="daccc-126">**View Column Defined by a Function**</span></span>  
  
 <span data-ttu-id="daccc-127">次の例では、データにアクセスするスカラー関数 `dbo.ufnGetStock`を選択リストで使用して `CurrentInventory` 列を定義するビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="daccc-127">The following example creates a view that uses the data accessing, scalar function `dbo.ufnGetStock` in the select list to define the column `CurrentInventory`.</span></span> <span data-ttu-id="daccc-128">次に、UPDATE ステートメントで OUTPUT 句の `CurrentInventory` 列を参照します。</span><span class="sxs-lookup"><span data-stu-id="daccc-128">An UPDATE statement then references the `CurrentInventory` column in the OUTPUT clause .</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW Production.ReorderLevels  
AS  
    SELECT ProductID, ProductModelID, ReorderPoint,  
           dbo.ufnGetStock(ProductID) AS CurrentInventory  
    FROM Production.Product;  
GO  
  
UPDATE Production.ReorderLevels  
SET ReorderPoint += CurrentInventory  
OUTPUT deleted.ReorderPoint, deleted.CurrentInventory,  
       inserted.ReorderPoint, inserted.CurrentInventory  
WHERE ProductModelID BETWEEN 75 and 80;  
```  
  
## <a name="user-action"></a><span data-ttu-id="daccc-129">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="daccc-129">User Action</span></span>  
 <span data-ttu-id="daccc-130">エラー 4186 は、次のいずれかの方法で解決できます。</span><span class="sxs-lookup"><span data-stu-id="daccc-130">Error 4186 can be corrected in one of the following ways:</span></span>  
  
-   <span data-ttu-id="daccc-131">サブクエリの代わりに結合を使用して、ビューまたは関数の列を定義します。</span><span class="sxs-lookup"><span data-stu-id="daccc-131">Use joins instead of subqueries to define the column in the view or function.</span></span> <span data-ttu-id="daccc-132">たとえば、`dbo.V1` ビューは次のように作成し直すことができます。</span><span class="sxs-lookup"><span data-stu-id="daccc-132">For example, you can rewrite the view `dbo.V1` as follows.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE VIEW dbo.V1  
    AS  
        SELECT City, sp.Name AS State  
        FROM Person.Address AS a   
        JOIN Person.StateProvince AS sp   
        ON sp.StateProvinceID = a.StateProvinceID;  
    ```  
  
-   <span data-ttu-id="daccc-133">ユーザー定義関数の定義を調べます。</span><span class="sxs-lookup"><span data-stu-id="daccc-133">Examine the definition of the user-defined function.</span></span> <span data-ttu-id="daccc-134">関数でユーザー データまたはシステム データにアクセスしない場合は、WITH SCHEMABINDING 句を含めるように関数を変更します。</span><span class="sxs-lookup"><span data-stu-id="daccc-134">If the function does not perform user or system data access, alter the function to include the WITH SCHEMABINDING clause.</span></span>  
  
-   <span data-ttu-id="daccc-135">OUTPUT 句から列を削除します。</span><span class="sxs-lookup"><span data-stu-id="daccc-135">Remove the column from the OUTPUT clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daccc-136">参照</span><span class="sxs-lookup"><span data-stu-id="daccc-136">See Also</span></span>  
 [<span data-ttu-id="daccc-137">OUTPUT 句 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="daccc-137">OUTPUT Clause &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/output-clause-transact-sql)  
  
  
