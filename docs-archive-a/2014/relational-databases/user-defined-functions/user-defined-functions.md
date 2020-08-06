---
title: ユーザー定義関数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], components
- user-defined functions [SQL Server], about user-defined functions
ms.assetid: d7ddafab-f5a6-44b0-81d5-ba96425aada4
author: rothja
ms.author: jroth
ms.openlocfilehash: c7e4b1a77f2fe5a13e21d8b3fe59e37931669b30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630848"
---
# <a name="user-defined-functions"></a><span data-ttu-id="bd8f7-102">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="bd8f7-102">User-Defined Functions</span></span>
  <span data-ttu-id="bd8f7-103">プログラミング言語の関数と同様、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザー定義関数は、パラメーターを受け取り複雑な計算などの処理を実行してその結果を値として返すルーチンです。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-103">Like functions in programming languages, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined functions are routines that accept parameters, perform an action, such as a complex calculation, and return the result of that action as a value.</span></span> <span data-ttu-id="bd8f7-104">戻り値は、単一のスカラー値または結果セットになります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-104">The return value can either be a single scalar value or a result set.</span></span>  
  
 <span data-ttu-id="bd8f7-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="bd8f7-105">**In This Topic**</span></span>  
  
 [<span data-ttu-id="bd8f7-106">ユーザー定義関数の利点</span><span class="sxs-lookup"><span data-stu-id="bd8f7-106">User-defined Function Benefits</span></span>](#Benefits)  
  
 [<span data-ttu-id="bd8f7-107">関数の種類</span><span class="sxs-lookup"><span data-stu-id="bd8f7-107">Types of Functions</span></span>](#FunctionTypes)  
  
 [<span data-ttu-id="bd8f7-108">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="bd8f7-108">Guidelines</span></span>](#Guidelines)  
  
 [<span data-ttu-id="bd8f7-109">関数内の有効なステートメント</span><span class="sxs-lookup"><span data-stu-id="bd8f7-109">Valid Statements in a Function</span></span>](#ValidStatements)  
  
 [<span data-ttu-id="bd8f7-110">スキーマ バインド関数</span><span class="sxs-lookup"><span data-stu-id="bd8f7-110">Schema Bound Functions</span></span>](#SchemaBound)  
  
 [<span data-ttu-id="bd8f7-111">パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="bd8f7-111">Specifying Parameters</span></span>](#Parameters)  
  
 [<span data-ttu-id="bd8f7-112">関連タスク</span><span class="sxs-lookup"><span data-stu-id="bd8f7-112">Related Tasks</span></span>](#Tasks)  
  
##  <a name="user-defined-function-benefits"></a><a name="Benefits"></a><span data-ttu-id="bd8f7-113">ユーザー定義関数の利点</span><span class="sxs-lookup"><span data-stu-id="bd8f7-113">User-defined Function Benefits</span></span>  
 <span data-ttu-id="bd8f7-114">次に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でユーザー定義関数を使用する利点を示します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-114">The benefits of using user-defined functions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are:</span></span>  
  
-   <span data-ttu-id="bd8f7-115">モジュール プログラミングが可能になります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-115">They allow modular programming.</span></span>  
  
     <span data-ttu-id="bd8f7-116">関数を作成してからデータベースに保存すると、プログラムの中で何度でも呼び出せます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-116">You can create the function once, store it in the database, and call it any number of times in your program.</span></span> <span data-ttu-id="bd8f7-117">ユーザー定義関数は、プログラムのソース コードとは切り離して変更できます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-117">User-defined functions can be modified independently of the program source code.</span></span>  
  
-   <span data-ttu-id="bd8f7-118">実行が高速になります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-118">They allow faster execution.</span></span>  
  
     <span data-ttu-id="bd8f7-119">[!INCLUDE[tsql](../../includes/tsql-md.md)] ユーザー定義関数を使用すると、ストアド プロシージャと同様に、プランがキャッシュされ、これを再利用して繰り返し実行することで、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードのコンパイル コストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-119">Similar to stored procedures, [!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined functions reduce the compilation cost of [!INCLUDE[tsql](../../includes/tsql-md.md)] code by caching the plans and reusing them for repeated executions.</span></span> <span data-ttu-id="bd8f7-120">つまり、ユーザー定義関数は、使用するたびに解析し直したり、最適化し直す必要がないので、実行時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-120">This means the user-defined function does not need to be reparsed and reoptimized with each use resulting in much faster execution times.</span></span>  
  
     <span data-ttu-id="bd8f7-121">計算や文字列の操作、ビジネス ロジックの場合は CLR 関数を使用することで、[!INCLUDE[tsql](../../includes/tsql-md.md)] 関数に比べてかなり高いパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-121">CLR functions offer significant performance advantage over [!INCLUDE[tsql](../../includes/tsql-md.md)] functions for computational tasks, string manipulation, and business logic.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="bd8f7-122">関数は、データ アクセスの多いロジックに適しています。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-122">functions are better suited for data-access intensive logic.</span></span>  
  
-   <span data-ttu-id="bd8f7-123">ネットワーク トラフィックが減少します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-123">They can reduce network traffic.</span></span>  
  
     <span data-ttu-id="bd8f7-124">1 つのスカラー式で表現できない複雑な制約に基づいてデータをフィルター選択する操作を、1 つの関数として表現できます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-124">An operation that filters data based on some complex constraint that cannot be expressed in a single scalar expression can be expressed as a function.</span></span> <span data-ttu-id="bd8f7-125">このような関数を WHERE 句で使用すれば、クライアントに送信される数や行を削減できます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-125">The function can then invoked in the WHERE clause to reduce the number or rows sent to the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd8f7-126">クエリの [!INCLUDE[tsql](../../includes/tsql-md.md)] ユーザー定義関数は、1 つのスレッドでのみ実行できます (直列実行プラン)。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined functions in queries can only be executed on a single thread (serial execution plan).</span></span>  
  
##  <a name="types-of-functions"></a><a name="FunctionTypes"></a><span data-ttu-id="bd8f7-127">関数の種類</span><span class="sxs-lookup"><span data-stu-id="bd8f7-127">Types of Functions</span></span>  
 <span data-ttu-id="bd8f7-128">スカラー関数</span><span class="sxs-lookup"><span data-stu-id="bd8f7-128">Scalar Function</span></span>  
 <span data-ttu-id="bd8f7-129">ユーザー定義のスカラー関数は、RETURNS 句で定義された型の単一のデータ値を返します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-129">User-defined scalar functions return a single data value of the type defined in the RETURNS clause.</span></span> <span data-ttu-id="bd8f7-130">インライン スカラー関数の場合、スカラー値は単一ステートメントの結果であり、関数の本体がありません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-130">For an inline scalar function, there is no function body; the scalar value is the result of a single statement.</span></span> <span data-ttu-id="bd8f7-131">複数ステートメントを持つスカラー関数の場合、BEGIN...END ブロックで定義された関数本体に、単一の値を返す一連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-131">For a multistatement scalar function, the function body, defined in a BEGIN...END block, contains a series of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that return the single value.</span></span> <span data-ttu-id="bd8f7-132">この関数の戻り値には、`text`、`ntext`、`image`、`cursor`、および `timestamp` 以外の任意のデータ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-132">The return type can be any data type except `text`, `ntext`, `image`, `cursor`, and `timestamp`.</span></span>  
  
 <span data-ttu-id="bd8f7-133">テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="bd8f7-133">Table-Valued Functions</span></span>  
 <span data-ttu-id="bd8f7-134">ユーザー定義テーブル値関数は、`table` データ型を返します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-134">User-defined table-valued functions return a `table` data type.</span></span> <span data-ttu-id="bd8f7-135">インライン テーブル値関数の場合、テーブルは単一の SELECT ステートメントの結果セットであり、関数の本体がありません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-135">For an inline table-valued function, there is no function body; the table is the result set of a single SELECT statement.</span></span>  
  
 <span data-ttu-id="bd8f7-136">システム関数</span><span class="sxs-lookup"><span data-stu-id="bd8f7-136">System Functions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bd8f7-137">には、さまざまな操作を実行するために使用できる多数のシステム関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-137">provides many system functions that you can use to perform a variety of operations.</span></span> <span data-ttu-id="bd8f7-138">システム関数は変更できません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-138">They cannot be modified.</span></span> <span data-ttu-id="bd8f7-139">詳細については、「[組み込み関数 &#40;Transact-SQL&#41;](/sql/t-sql/functions/functions)」、「[システム ストアド関数 &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/system-functions-for-transact-sql)」、および「[動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-139">For more information, see [Built-in Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/functions), [System Stored Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/system-functions-for-transact-sql), and [Dynamic Management Views and Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views).</span></span>  
  
##  <a name="guidelines"></a><a name="Guidelines"></a> <span data-ttu-id="bd8f7-140">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="bd8f7-140">Guidelines</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="bd8f7-141">ステートメントが取り消されて、モジュール (トリガーやストアド プロシージャ) 内の次のステートメントが続行されるようなエラーについては、関数内では扱いが異なります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-141">errors that cause a statement to be canceled and continue with the next statement in the module (such as triggers or stored procedures) are treated differently inside a function.</span></span> <span data-ttu-id="bd8f7-142">関数内では、このようなエラーによって関数自体の実行が停止されます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-142">In functions, such errors cause the execution of the function to stop.</span></span> <span data-ttu-id="bd8f7-143">そのため、次に関数を呼び出したステートメントも取り消されることになります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-143">This in turn causes the statement that invoked the function to be canceled.</span></span>  
  
 <span data-ttu-id="bd8f7-144">BEGIN...END ブロック内のステートメントは、副作用を伴いません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-144">The statements in a BEGIN...END block cannot have any side effects.</span></span> <span data-ttu-id="bd8f7-145">関数の副作用とは、データベース テーブルの変更など、その関数の有効範囲外のリソースの状態を永続的に変更してしまうことです。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-145">Function side effects are any permanent changes to the state of a resource that has a scope outside the function such as a modification to a database table.</span></span> <span data-ttu-id="bd8f7-146">関数内のステートメントが変更できる内容は、ローカル カーソルまたはローカル変数など、その関数に対してローカルなオブジェクトの変更のみです。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-146">The only changes that can be made by the statements in the function are changes to objects local to the function, such as local cursors or variables.</span></span> <span data-ttu-id="bd8f7-147">データベース テーブルの変更、関数に対してローカルではないカーソルの操作、電子メールの送信、カタログ変更、ユーザーへ返す結果セットの生成などの操作は、関数では実行できません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-147">Modifications to database tables, operations on cursors that are not local to the function, sending e-mail, attempting a catalog modification, and generating a result set that is returned to the user are examples of actions that cannot be performed in a function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd8f7-148">CREATE FUNCTION ステートメントの実行時に、存在しないリソースに対する副作用がもたらされる場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-148">If a CREATE FUNCTION statement produces side effects against resources that do not exist when the CREATE FUNCTION statement is issued, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes the statement.</span></span> <span data-ttu-id="bd8f7-149">ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では関数は呼び出されても実行されません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-149">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not execute the function when it is invoked.</span></span>  
  
 <span data-ttu-id="bd8f7-150">クエリで指定した関数が実際に実行される回数は、オプティマイザーで作成された実行プランによって異なります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-150">The number of times that a function specified in a query is actually executed can vary between execution plans built by the optimizer.</span></span> <span data-ttu-id="bd8f7-151">WHERE 句のサブクエリによって起動された関数がその一例です。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-151">An example is a function invoked by a subquery in a WHERE clause.</span></span> <span data-ttu-id="bd8f7-152">サブクエリとその関数が実行された回数は、オプティマイザーが選択したアクセス パスの違いによって変わります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-152">The number of times the subquery and its function is executed can vary with different access paths chosen by the optimizer.</span></span>  
  
##  <a name="valid-statements-in-a-function"></a><a name="ValidStatements"></a><span data-ttu-id="bd8f7-153">関数内の有効なステートメント</span><span class="sxs-lookup"><span data-stu-id="bd8f7-153">Valid Statements in a Function</span></span>  
 <span data-ttu-id="bd8f7-154">関数では、次の種類のステートメントが有効です。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-154">The types of statements that are valid in a function include:</span></span>  
  
-   <span data-ttu-id="bd8f7-155">関数に対してローカルなデータ変数やカーソルを定義するために使用できる DECLARE ステートメント。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-155">DECLARE statements can be used to define data variables and cursors that are local to the function.</span></span>  
  
-   <span data-ttu-id="bd8f7-156">関数に対してローカルなオブジェクトへの値の代入。たとえば、SET を使用してスカラー変数やテーブルのローカル変数に値を代入します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-156">Assignments of values to objects local to the function, such as using SET to assign values to scalar and table local variables.</span></span>  
  
-   <span data-ttu-id="bd8f7-157">ローカル カーソルを参照するカーソル操作。ローカル カーソルとは、関数内で宣言され、開かれ、閉じられ、割り当てが解除されるカーソルです。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-157">Cursor operations that reference local cursors that are declared, opened, closed, and deallocated in the function.</span></span> <span data-ttu-id="bd8f7-158">クライアントにデータを返す FETCH ステートメントは使用できません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-158">FETCH statements that return data to the client are not allowed.</span></span> <span data-ttu-id="bd8f7-159">INTO 句を使用してローカル変数に値を代入する FETCH ステートメントのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-159">Only FETCH statements that assign values to local variables using the INTO clause are allowed.</span></span>  
  
-   <span data-ttu-id="bd8f7-160">TRY...CATCH ステートメントを除く、フロー制御ステートメント。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-160">Control-of-flow statements except TRY...CATCH statements.</span></span>  
  
-   <span data-ttu-id="bd8f7-161">選択リストに、関数に対してローカルな変数に値を代入する式が含まれる、SELECT ステートメント。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-161">SELECT statements containing select lists with expressions that assign values to variables that are local to the function.</span></span>  
  
-   <span data-ttu-id="bd8f7-162">関数に対してローカルなテーブル変数を変更する INSERT、UPDATE、および DELETE の各ステートメント。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-162">UPDATE, INSERT, and DELETE statements modifying table variables that are local to the function.</span></span>  
  
-   <span data-ttu-id="bd8f7-163">拡張ストアド プロシージャを呼び出す EXECUTE ステートメント。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-163">EXECUTE statements calling an extended stored procedure.</span></span>  
  
### <a name="built-in-system-functions"></a><span data-ttu-id="bd8f7-164">組み込みシステム関数</span><span class="sxs-lookup"><span data-stu-id="bd8f7-164">Built-in System Functions</span></span>  
 <span data-ttu-id="bd8f7-165">Transact-SQL ユーザー定義関数では、次の非決定的な組み込み関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-165">The following nondeterministic built-in functions can be used in Transact-SQL user-defined functions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd8f7-166">CURRENT_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="bd8f7-166">CURRENT_TIMESTAMP</span></span>|<span data-ttu-id="bd8f7-167">@@MAX_CONNECTIONS</span><span class="sxs-lookup"><span data-stu-id="bd8f7-167">@@MAX_CONNECTIONS</span></span>|  
|<span data-ttu-id="bd8f7-168">GET_TRANSMISSION_STATUS</span><span class="sxs-lookup"><span data-stu-id="bd8f7-168">GET_TRANSMISSION_STATUS</span></span>|<span data-ttu-id="bd8f7-169">@@PACK_RECEIVED</span><span class="sxs-lookup"><span data-stu-id="bd8f7-169">@@PACK_RECEIVED</span></span>|  
|<span data-ttu-id="bd8f7-170">GETDATE</span><span class="sxs-lookup"><span data-stu-id="bd8f7-170">GETDATE</span></span>|<span data-ttu-id="bd8f7-171">@@PACK_SENT</span><span class="sxs-lookup"><span data-stu-id="bd8f7-171">@@PACK_SENT</span></span>|  
|<span data-ttu-id="bd8f7-172">GETUTCDATE</span><span class="sxs-lookup"><span data-stu-id="bd8f7-172">GETUTCDATE</span></span>|<span data-ttu-id="bd8f7-173">@@PACKET_ERRORS</span><span class="sxs-lookup"><span data-stu-id="bd8f7-173">@@PACKET_ERRORS</span></span>|  
|<span data-ttu-id="bd8f7-174">@@CONNECTIONS</span><span class="sxs-lookup"><span data-stu-id="bd8f7-174">@@CONNECTIONS</span></span>|<span data-ttu-id="bd8f7-175">@@TIMETICKS</span><span class="sxs-lookup"><span data-stu-id="bd8f7-175">@@TIMETICKS</span></span>|  
|<span data-ttu-id="bd8f7-176">@@CPU_BUSY</span><span class="sxs-lookup"><span data-stu-id="bd8f7-176">@@CPU_BUSY</span></span>|<span data-ttu-id="bd8f7-177">@@TOTAL_ERRORS</span><span class="sxs-lookup"><span data-stu-id="bd8f7-177">@@TOTAL_ERRORS</span></span>|  
|<span data-ttu-id="bd8f7-178">@@DBTS</span><span class="sxs-lookup"><span data-stu-id="bd8f7-178">@@DBTS</span></span>|<span data-ttu-id="bd8f7-179">@@TOTAL_READ</span><span class="sxs-lookup"><span data-stu-id="bd8f7-179">@@TOTAL_READ</span></span>|  
|<span data-ttu-id="bd8f7-180">@@IDLE</span><span class="sxs-lookup"><span data-stu-id="bd8f7-180">@@IDLE</span></span>|<span data-ttu-id="bd8f7-181">@@TOTAL_WRITE</span><span class="sxs-lookup"><span data-stu-id="bd8f7-181">@@TOTAL_WRITE</span></span>|  
|<span data-ttu-id="bd8f7-182">@@IO_BUSY</span><span class="sxs-lookup"><span data-stu-id="bd8f7-182">@@IO_BUSY</span></span>||  
  
 <span data-ttu-id="bd8f7-183">Transact-SQL ユーザー定義関数では、次の非決定的な組み込み関数を使用できません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-183">The following nondeterministic built-in functions cannot be used in Transact-SQL user-defined functions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd8f7-184">NEWID</span><span class="sxs-lookup"><span data-stu-id="bd8f7-184">NEWID</span></span>|<span data-ttu-id="bd8f7-185">RAND</span><span class="sxs-lookup"><span data-stu-id="bd8f7-185">RAND</span></span>|  
|<span data-ttu-id="bd8f7-186">NEWSEQUENTIALID</span><span class="sxs-lookup"><span data-stu-id="bd8f7-186">NEWSEQUENTIALID</span></span>|<span data-ttu-id="bd8f7-187">TEXTPTR</span><span class="sxs-lookup"><span data-stu-id="bd8f7-187">TEXTPTR</span></span>|  
  
 <span data-ttu-id="bd8f7-188">決定的および非決定的な組み込みシステム関数の一覧については、「[決定的関数と非決定的関数](../user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-188">For a list of deterministic and nondeterministic built-in system functions, see [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span>  
  
##  <a name="schema-bound-functions"></a><a name="SchemaBound"></a><span data-ttu-id="bd8f7-189">スキーマバインド関数</span><span class="sxs-lookup"><span data-stu-id="bd8f7-189">Schema-Bound Functions</span></span>  
 <span data-ttu-id="bd8f7-190">CREATE FUNCTION は、SCHEMABINDING 句をサポートしています。この句は、テーブル、ビュー、およびその他のユーザー定義関数など、参照対象オブジェクトのスキーマにその関数をバインドします。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-190">CREATE FUNCTION supports a SCHEMABINDING clause that binds the function to the schema of any objects it references, such as tables, views, and other user-defined functions.</span></span> <span data-ttu-id="bd8f7-191">スキーマ バインド関数によって参照されるオブジェクトを変更または削除しようとすると、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-191">An attempt to alter or drop any object referenced by a schema-bound function fails.</span></span>  
  
 <span data-ttu-id="bd8f7-192">CREATE FUNCTION に SCHEMABINDING を指定するには、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-192">These conditions must be met before you can specify SCHEMABINDING in CREATE FUNCTION:</span></span>  
  
-   <span data-ttu-id="bd8f7-193">CREATE 関数が参照するすべてのビューとユーザー定義関数が、スキーマにバインドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-193">All views and user-defined functions referenced by the function must be schema-bound.</span></span>  
  
-   <span data-ttu-id="bd8f7-194">この関数が参照するすべてのオブジェクトが、その関数と同じデータベースに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-194">All objects referenced by the function must be in the same database as the function.</span></span> <span data-ttu-id="bd8f7-195">対象となるオブジェクトは、1 つまたは 2 つの要素で構成される名前を使用して参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-195">The objects must be referenced using either one-part or two-part names.</span></span>  
  
-   <span data-ttu-id="bd8f7-196">関数内のすべての参照対象オブジェクト (テーブル、ビュー、およびユーザー定義関数) に REFERENCES 権限を所持している必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-196">You must have REFERENCES permission on all objects (tables, views, and user-defined functions) referenced in the function.</span></span>  
  
 <span data-ttu-id="bd8f7-197">ALTER FUNCTION を使用して、スキーマ バインドを削除できます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-197">You can use ALTER FUNCTION to remove the schema binding.</span></span> <span data-ttu-id="bd8f7-198">関数を再定義するには、ALTER FUNCTION ステートメントを使用します。WITH SCHEMABINDING は指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-198">The ALTER FUNCTION statement should redefine the function without specifying WITH SCHEMABINDING.</span></span>  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a><span data-ttu-id="bd8f7-199">パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="bd8f7-199">Specifying Parameters</span></span>  
 <span data-ttu-id="bd8f7-200">ユーザー定義関数は、0 個またはそれ以上の入力パラメーターを受け取り、スカラー値またはテーブルのいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-200">A user-defined function takes zero or more input parameters and returns either a scalar value or a table.</span></span> <span data-ttu-id="bd8f7-201">1 つの関数では、最大で 1,024 個の入力パラメーターを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-201">A function can have a maximum of 1024 input parameters.</span></span> <span data-ttu-id="bd8f7-202">関数のパラメーターが既定値を持つ場合は、既定値を得るために、関数を呼び出すときに DEFAULT キーワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-202">When a parameter of the function has a default value, the keyword DEFAULT must be specified when calling the function to get the default value.</span></span> <span data-ttu-id="bd8f7-203">この動作はユーザー定義ストアド プロシージャ内の既定値を持つパラメーターとは異なります。ユーザー定義ストアド プロシージャの場合は、パラメーターを省略すると既定値が暗黙的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-203">This behavior is different from parameters with default values in user-defined stored procedures in which omitting the parameter also implies the default value.</span></span> <span data-ttu-id="bd8f7-204">ユーザー定義関数では、出力パラメーターがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-204">User-defined functions do not support output parameters.</span></span>  
  
##  <a name="related-tasks"></a><a name="Tasks"></a> <span data-ttu-id="bd8f7-205">関連タスク</span><span class="sxs-lookup"><span data-stu-id="bd8f7-205">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd8f7-206">**タスクの説明**</span><span class="sxs-lookup"><span data-stu-id="bd8f7-206">**Task Description**</span></span>|<span data-ttu-id="bd8f7-207">**トピック**</span><span class="sxs-lookup"><span data-stu-id="bd8f7-207">**Topic**</span></span>|  
|<span data-ttu-id="bd8f7-208">Transact-SQL ユーザー定義関数を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-208">Describes how to create a Transact-SQL user-defined function.</span></span>|[<span data-ttu-id="bd8f7-209">ユーザー定義関数の作成 &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="bd8f7-209">Create User-defined Functions &#40;Database Engine&#41;</span></span>](../user-defined-functions/create-user-defined-functions-database-engine.md)|  
|<span data-ttu-id="bd8f7-210">CLR 関数を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-210">Describes how create a CLR function.</span></span>|[<span data-ttu-id="bd8f7-211">CLR 関数の作成</span><span class="sxs-lookup"><span data-stu-id="bd8f7-211">Create CLR Functions</span></span>](../user-defined-functions/create-clr-functions.md)|  
|<span data-ttu-id="bd8f7-212">ユーザー定義集計関数を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-212">Describes how to create a user-defined aggregate function</span></span>|[<span data-ttu-id="bd8f7-213">ユーザー定義集計の作成</span><span class="sxs-lookup"><span data-stu-id="bd8f7-213">Create User-defined Aggregates</span></span>](../user-defined-functions/create-user-defined-aggregates.md)|  
|<span data-ttu-id="bd8f7-214">Transact-SQL ユーザー定義関数を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-214">Describes how to modify a Transact-SQL user-defined function.</span></span>|[<span data-ttu-id="bd8f7-215">ユーザー定義関数の変更</span><span class="sxs-lookup"><span data-stu-id="bd8f7-215">Modify User-defined Functions</span></span>](../user-defined-functions/user-defined-functions.md)|  
|<span data-ttu-id="bd8f7-216">ユーザー定義関数を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-216">Describes how to delete a user-defined function.</span></span>|[<span data-ttu-id="bd8f7-217">ユーザー定義関数の削除</span><span class="sxs-lookup"><span data-stu-id="bd8f7-217">Delete User-defined Functions</span></span>](../user-defined-functions/delete-user-defined-functions.md)|  
|<span data-ttu-id="bd8f7-218">ユーザー定義関数を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-218">Describes how to execute a user-defined function.</span></span>|[<span data-ttu-id="bd8f7-219">ユーザー定義関数の実行</span><span class="sxs-lookup"><span data-stu-id="bd8f7-219">Execute User-defined Functions</span></span>](../user-defined-functions/execute-user-defined-functions.md)|  
|<span data-ttu-id="bd8f7-220">ユーザー定義関数の名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-220">Describes how to rename a user-defined function</span></span>|[<span data-ttu-id="bd8f7-221">ユーザー定義関数名の変更</span><span class="sxs-lookup"><span data-stu-id="bd8f7-221">Rename User-defined Functions</span></span>](../user-defined-functions/rename-user-defined-functions.md)|  
|<span data-ttu-id="bd8f7-222">ユーザー定義関数の定義を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd8f7-222">Describes how to view the definition of a user-defined function.</span></span>|[<span data-ttu-id="bd8f7-223">ユーザー定義関数の表示</span><span class="sxs-lookup"><span data-stu-id="bd8f7-223">View User-defined Functions</span></span>](view-user-defined-functions.md)|  
  
  
