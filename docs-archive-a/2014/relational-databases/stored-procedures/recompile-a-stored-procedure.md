---
title: ストアド プロシージャの再コンパイル| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- sp_recompile
- WITH RECOMPILE clause
- recompiling stored procedures
- stored procedures [SQL Server], recompiling
ms.assetid: b90deb27-0099-4fe7-ba60-726af78f7c18
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a9bc0e1d4baecb7f4c66b83b57081ed3131123d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646119"
---
# <a name="recompile-a-stored-procedure"></a><span data-ttu-id="9c919-102">ストアド プロシージャの再コンパイル</span><span class="sxs-lookup"><span data-stu-id="9c919-102">Recompile a Stored Procedure</span></span>
  <span data-ttu-id="9c919-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でストアド プロシージャを再コンパイルする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c919-103">This topic describes how to recompile a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9c919-104">この操作を行うには、 `WITH RECOMPILE` プロシージャの定義でオプションを使用するか、プロシージャを呼び出すときに、 `RECOMPILE` 個々のステートメントに対してクエリヒントを使用するか、または `sp_recompile` システムストアドプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c919-104">There are three ways to do this: `WITH RECOMPILE` option in the procedure definition or when the procedure is called, the `RECOMPILE` query hint on individual statements, or by using the `sp_recompile` system stored procedure.</span></span> <span data-ttu-id="9c919-105">このトピックでは、プロシージャ定義の作成時および既存のプロシージャの実行時に WITH RECOMPILE オプションを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c919-105">This topic describes using the WITH RECOMPILE option when creating a procedure definition and executing an existing procedure.</span></span> <span data-ttu-id="9c919-106">さらに、sp_recompile システム ストアド プロシージャを使用して既存のプロシージャを再コンパイルする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="9c919-106">It also describes using the sp_recompile system stored procedure to recompile an existing procedure.</span></span>  
  
 <span data-ttu-id="9c919-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9c919-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9c919-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9c919-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9c919-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="9c919-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="9c919-110">Security</span><span class="sxs-lookup"><span data-stu-id="9c919-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9c919-111">**ストアド プロシージャを再コンパイルするために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="9c919-111">**To recompile a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="9c919-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9c919-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9c919-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="9c919-113">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="9c919-114">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9c919-114">Recommendations</span></span>  
  
-   <span data-ttu-id="9c919-115">プロシージャを初めてコンパイルするときや再コンパイルするとき、データベースおよびそのオブジェクトの現在の状態に合わせてプロシージャのクエリ プランが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="9c919-115">When a procedure is compiled for the first time or recompiled, the procedure's query plan is optimized for the current state of the database and its objects.</span></span> <span data-ttu-id="9c919-116">データベースのデータまたは構造に大きな変更が加えられた場合、プロシージャを再コンパイルすることにより、その変更に合わせてプロシージャのクエリ プランが更新され、最適化されます。</span><span class="sxs-lookup"><span data-stu-id="9c919-116">If a database undergoes significant changes to its data or structure, recompiling a procedure updates and optimizes the procedure's query plan for those changes.</span></span> <span data-ttu-id="9c919-117">これにより、プロシージャの処理パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="9c919-117">This can improve the procedure's processing performance.</span></span>  
  
-   <span data-ttu-id="9c919-118">プロシージャの再コンパイルは、強制的に実行する必要がある場合もあれば、自動的に実行される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="9c919-118">There are times when procedure recompilation must be forced and other times when it occurs automatically.</span></span> <span data-ttu-id="9c919-119">自動再コンパイルは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再起動されるたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="9c919-119">Automatic recompiling occurs whenever [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span> <span data-ttu-id="9c919-120">また、自動再コンパイルは、プロシージャによって参照されている基になるテーブルの物理デザインが変更された場合にも発生します。</span><span class="sxs-lookup"><span data-stu-id="9c919-120">It also occurs if an underlying table referenced by the procedure has undergone physical design changes.</span></span>  
  
-   <span data-ttu-id="9c919-121">プロシージャの再コンパイルを強制的に行うもう 1 つの理由は、プロシージャのコンパイル時に "パラメーターを見つけ出す" 動作の影響を少なくすることです。</span><span class="sxs-lookup"><span data-stu-id="9c919-121">Another reason to force a procedure to recompile is to counteract the "parameter sniffing" behavior of procedure compilation.</span></span> <span data-ttu-id="9c919-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でプロシージャが実行されるとき、コンパイル時にプロシージャによって使用されるパラメーター値は、クエリ プランの生成の一部に含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c919-122">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes procedures, any parameter values that are used by the procedure when it compiles are included as part of generating the query plan.</span></span> <span data-ttu-id="9c919-123">これらの値が、その後呼び出されるプロシージャの標準的な値を表す場合は、プロシージャのコンパイルや実行のたびに、そのクエリ プランからメリットを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="9c919-123">If these values represent the typical ones with which the procedure is subsequently called, then the procedure benefits from the query plan every time that it compiles and executes.</span></span> <span data-ttu-id="9c919-124">プロシージャのパラメーター値が非定型の値である場合は、プロシージャを強制的に再コンパイルし、異なるパラメーター値に基づく新しいプランを生成することにより、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="9c919-124">If parameter values on the procedure are frequently atypical, forcing a recompile of the procedure and a new plan based on different parameter values can improve performance.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9c919-125">には、プロシージャをステートメント レベルで再コンパイルする機能が備わっています。</span><span class="sxs-lookup"><span data-stu-id="9c919-125">features statement-level recompilation of procedures.</span></span> <span data-ttu-id="9c919-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でストアド プロシージャを再コンパイルすると、プロシージャ全体ではなく、再コンパイルが必要なステートメントだけがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="9c919-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recompiles stored procedures, only the statement that caused the recompilation is compiled, instead of the complete procedure.</span></span>  
  
-   <span data-ttu-id="9c919-127">プロシージャの特定のクエリで通常使用される値が非定型の値や一時的な値である場合は、それらのクエリ内で RECOMPILE クエリ ヒントを使用することにより、プロシージャのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="9c919-127">If certain queries in a procedure regularly use atypical or temporary values, procedure performance can be improved by using the RECOMPILE query hint inside those queries.</span></span> <span data-ttu-id="9c919-128">再コンパイルされるのは、プロシージャ全体ではなく、クエリ ヒントを使用したクエリのみであるため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のステートメント レベルの再コンパイル動作を模倣できます。</span><span class="sxs-lookup"><span data-stu-id="9c919-128">Since only the queries using the query hint will be recompiled instead of the complete procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]'s statement-level recompilation behavior is mimicked.</span></span> <span data-ttu-id="9c919-129">ただし、RECOMPILE クエリ ヒントを使用した場合、ステートメントをコンパイルするときに、プロシージャの現在のパラメーター値に加えてストアド プロシージャ内の任意のローカル変数の値も使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c919-129">But in addition to using the procedure's current parameter values, the RECOMPILE query hint also uses the values of any local variables inside the stored procedure when you compile the statement.</span></span> <span data-ttu-id="9c919-130">詳細については、「 [クエリ ヒント (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c919-130">For more information, see [Query Hint (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9c919-131">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9c919-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9c919-132">Permissions</span><span class="sxs-lookup"><span data-stu-id="9c919-132">Permissions</span></span>  
 <span data-ttu-id="9c919-133">`WITH RECOMPILE`オプション</span><span class="sxs-lookup"><span data-stu-id="9c919-133">`WITH RECOMPILE` Option</span></span>  
 <span data-ttu-id="9c919-134">プロシージャ定義を作成するときにこのオプションを使用する場合、データベースの CREATE PROCEDURE 権限とプロシージャが作成されるスキーマに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c919-134">If this option is used when the procedure definition is created, it requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
 <span data-ttu-id="9c919-135">EXECUTE ステートメントでこのオプションを使用する場合、プロシージャに対する EXECUTE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c919-135">If this option is used in an EXECUTE statement, it requires EXECUTE permissions on the procedure.</span></span> <span data-ttu-id="9c919-136">EXECUTE ステートメント自体に対する権限は必要がありませんが、EXECUTE ステートメント内で参照されているプロシージャに対する実行権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c919-136">Permissions are not required on the EXECUTE statement itself but execute permissions are required on the procedure referenced in the EXECUTE statement.</span></span> <span data-ttu-id="9c919-137">詳細については、「 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c919-137">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
 <span data-ttu-id="9c919-138">`RECOMPILE`クエリヒント</span><span class="sxs-lookup"><span data-stu-id="9c919-138">`RECOMPILE` Query Hint</span></span>  
 <span data-ttu-id="9c919-139">この機能は、プロシージャが作成され、ヒントがプロシージャの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに含まれている場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c919-139">This feature is used when the procedure is created and the hint is included in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the procedure.</span></span> <span data-ttu-id="9c919-140">したがって、データベースの CREATE PROCEDURE 権限と、プロシージャを作成するスキーマに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c919-140">Therefore, it requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
 <span data-ttu-id="9c919-141">`sp_recompile`システムストアドプロシージャ</span><span class="sxs-lookup"><span data-stu-id="9c919-141">`sp_recompile` System Stored Procedure</span></span>  
 <span data-ttu-id="9c919-142">指定したプロシージャに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c919-142">Requires ALTER permission on the specified procedure.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9c919-143">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9c919-143">Using Transact-SQL</span></span>  
  
#### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a><span data-ttu-id="9c919-144">WITH RECOMPILE オプションを使用してストアド プロシージャを実行するには</span><span class="sxs-lookup"><span data-stu-id="9c919-144">To recompile a stored procedure by using the WITH RECOMPILE option</span></span>  
  
1.  <span data-ttu-id="9c919-145">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="9c919-145">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9c919-146">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c919-146">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9c919-147">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c919-147">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9c919-148">この例では、プロシージャ定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="9c919-148">This example creates the procedure definition.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspProductByVendor', 'P' ) IS NOT NULL   
    DROP PROCEDURE dbo.uspProductByVendor;  
GO  
CREATE PROCEDURE dbo.uspProductByVendor @Name varchar(30) = '%'  
WITH RECOMPILE  
AS  
    SET NOCOUNT ON;  
    SELECT v.Name AS 'Vendor name', p.Name AS 'Product name'  
    FROM Purchasing.Vendor AS v   
    JOIN Purchasing.ProductVendor AS pv   
      ON v.BusinessEntityID = pv.BusinessEntityID   
    JOIN Production.Product AS p   
      ON pv.ProductID = p.ProductID  
    WHERE v.Name LIKE @Name;  
  
```  
  
#### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a><span data-ttu-id="9c919-149">WITH RECOMPILE オプションを使用してストアド プロシージャを実行するには</span><span class="sxs-lookup"><span data-stu-id="9c919-149">To recompile a stored procedure by using the WITH RECOMPILE option</span></span>  
  
1.  <span data-ttu-id="9c919-150">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="9c919-150">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9c919-151">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c919-151">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9c919-152">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c919-152">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9c919-153">この例では、全従業員 (フルネーム) とその役職および部署名をビューから返す単純なプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c919-153">This example creates a simple procedure that returns all employees (first and last names supplied), their job titles, and their department names from a view.</span></span>  
  
     <span data-ttu-id="9c919-154">次に、2 番目のコード例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c919-154">And then copy and paste the second code example into the query window and click **Execute**.</span></span> <span data-ttu-id="9c919-155">これにより、プロシージャが実行され、プロシージャのクエリ プランが再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="9c919-155">This executes the procedure and recompiles the procedure's query plan.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXECUTE HumanResources.uspGetAllEmployees WITH RECOMPILE;  
GO  
  
```  
  
#### <a name="to-recompile-a-stored-procedure-by-using-sp_recompile"></a><span data-ttu-id="9c919-156">sp_recompile を使用してストアド プロシージャを実行するには</span><span class="sxs-lookup"><span data-stu-id="9c919-156">To recompile a stored procedure by using sp_recompile</span></span>  
  
1.  <span data-ttu-id="9c919-157">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="9c919-157">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9c919-158">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c919-158">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9c919-159">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c919-159">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9c919-160">この例では、全従業員 (フルネーム) とその役職および部署名をビューから返す単純なプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c919-160">This example creates a simple procedure that returns all employees (first and last names supplied), their job titles, and their department names from a view.</span></span>  
  
     <span data-ttu-id="9c919-161">次に、次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c919-161">Then, copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9c919-162">この場合、プロシージャは実行されません。代わりに、プロシージャが次回実行されるときにクエリ プランが更新されるように、再コンパイルの対象としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="9c919-162">This does not execute the procedure but it does mark the procedure to be recompiled so that its query plan is updated the next time that the procedure is executed.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'HumanResources.uspGetAllEmployees';  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c919-163">参照</span><span class="sxs-lookup"><span data-stu-id="9c919-163">See Also</span></span>  
 <span data-ttu-id="9c919-164">[ストアド プロシージャの作成](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9c919-164">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="9c919-165">[ストアド プロシージャの変更](../stored-procedures/modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9c919-165">[Modify a Stored Procedure](../stored-procedures/modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="9c919-166">[ストアド プロシージャの名前の変更](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9c919-166">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="9c919-167">[ストアド プロシージャの定義の表示](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9c919-167">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="9c919-168">[ストアド プロシージャの依存関係の表示](view-the-dependencies-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9c919-168">[View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="9c919-169">DROP PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9c919-169">DROP PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
