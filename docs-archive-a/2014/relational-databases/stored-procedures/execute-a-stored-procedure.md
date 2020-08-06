---
title: ストアド プロシージャの実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.executeprocedure.f1
- sql12.swb.executeprocedure.general.f1
helpviewer_keywords:
- stored procedures [SQL Server], parameters
- extended stored procedures [SQL Server], executing
- system stored procedures [SQL Server], executing
- stored procedures [SQL Server], executing
- user-defined stored procedures [SQL Server]
ms.assetid: a0b1337d-2059-4872-8c62-3f967d8b170f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c679ba7af3ac9f60d312b33c0346e50687387476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644363"
---
# <a name="execute-a-stored-procedure"></a><span data-ttu-id="9a6c9-102">ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="9a6c9-102">Execute a Stored Procedure</span></span>
  <span data-ttu-id="9a6c9-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でストアド プロシージャを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-103">This topic describes how to execute a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9a6c9-104">ストアド プロシージャを実行するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-104">There are two different ways to execute a stored procedure.</span></span> <span data-ttu-id="9a6c9-105">1 つ目の最も一般的な方法は、アプリケーションまたはユーザーがプロシージャを呼び出す方法です。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-105">The first and most common approach is for an application or user to call the procedure.</span></span> <span data-ttu-id="9a6c9-106">2 番目の方法は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの起動時にプロシージャが自動的に実行されるように設定する方法です。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-106">The second approach is to set the procedure to run automatically when an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="9a6c9-107">アプリケーションまたはユーザーによってプロシージャが呼び出される場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] の EXECUTE または EXEC キーワードが呼び出しの中に明示的に指定されています。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-107">When a procedure is called by an application or user, the [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE or EXEC keyword is explicitly stated in the call.</span></span> <span data-ttu-id="9a6c9-108">または、プロシージャが [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ内の最初のステートメントである場合は、このキーワードを使用せずにストアド プロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-108">Alternatively, the procedure can be called and executed without the keyword if the procedure is the first statement in the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch.</span></span>  
  
 <span data-ttu-id="9a6c9-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9a6c9-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9a6c9-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9a6c9-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9a6c9-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9a6c9-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9a6c9-112">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="9a6c9-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="9a6c9-113">Security</span><span class="sxs-lookup"><span data-stu-id="9a6c9-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9a6c9-114">**ストアド プロシージャを実行するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="9a6c9-114">**To execute a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="9a6c9-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9a6c9-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9a6c9-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9a6c9-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9a6c9-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="9a6c9-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9a6c9-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9a6c9-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9a6c9-119">システム プロシージャ名を照合するときに、呼び出し元のデータベースの照合順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-119">The calling database collation is used when matching system procedure names.</span></span> <span data-ttu-id="9a6c9-120">そのため、プロシージャの呼び出しでは、システム プロシージャ名の大文字と小文字を常に区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-120">Therefore, always use the exact case of system procedure names in procedure calls.</span></span> <span data-ttu-id="9a6c9-121">たとえば、次のコードは、大文字と小文字を区別する照合順序が指定されたデータベースのコンテキストで実行された場合は失敗します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-121">For example, this code will fail if it is executed in the context of a database that has a case-sensitive collation:</span></span>  
  
    ```sql  
    EXEC SP_heLP; -- Will fail to resolve because SP_heLP does not equal sp_help  
    ```  
  
     <span data-ttu-id="9a6c9-122">正確なシステム ストアド プロシージャ名を表示するには、 [sys.system_objects](/sql/relational-databases/system-catalog-views/sys-system-objects-transact-sql) カタログ ビューおよび [sys.system_parameters](/sql/relational-databases/system-catalog-views/sys-system-parameters-transact-sql) カタログ ビューをクエリします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-122">To display the exact system procedure names, query the [sys.system_objects](/sql/relational-databases/system-catalog-views/sys-system-objects-transact-sql) and [sys.system_parameters](/sql/relational-databases/system-catalog-views/sys-system-parameters-transact-sql) catalog views.</span></span>  
  
-   <span data-ttu-id="9a6c9-123">システム プロシージャと同じ名前を持つユーザー定義プロシージャは、実行されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-123">If a user-defined procedure has the same name as a system procedure, the user-defined procedure might not ever execute.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="9a6c9-124">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9a6c9-124">Recommendations</span></span>  
  
-   <span data-ttu-id="9a6c9-125">システム ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="9a6c9-125">Executing System Stored Procedures</span></span>  
  
     <span data-ttu-id="9a6c9-126">システム ストアド プロシージャは、 **sp_** というプレフィックスで始まります。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-126">System procedures begin with the prefix **sp_**.</span></span> <span data-ttu-id="9a6c9-127">システム ストアド プロシージャは、論理的にすべてのユーザー定義データベースおよびシステム定義データベースに表示されるため、プロシージャ名を完全修飾する必要なく、任意のデータベースから実行できます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-127">Because they logically appear in all user- and system- defined databases, they can be executed from any database without having to fully quality the procedure name.</span></span> <span data-ttu-id="9a6c9-128">ただし、名前の競合を回避するためには、すべてのシステム プロシージャ名を **sys** スキーマ名でスキーマ修飾することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-128">However, we recommend schema-qualifying all system procedure names with the **sys** schema name to prevent name conflicts.</span></span> <span data-ttu-id="9a6c9-129">次の例は、システム ストアド プロシージャの呼び出しに関して推奨されている方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-129">The following example demonstrates the recommended method of calling a system procedure.</span></span>  
  
    ```sql  
    EXEC sys.sp_who;  
    ```  
  
-   <span data-ttu-id="9a6c9-130">ユーザー定義のストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="9a6c9-130">Executing User-defined Stored Procedures</span></span>  
  
     <span data-ttu-id="9a6c9-131">ユーザー定義のプロシージャを実行する場合は、プロシージャ名をスキーマ名で修飾することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-131">When executing a user-defined procedure, we recommend qualifying the procedure name with the schema name.</span></span> <span data-ttu-id="9a6c9-132">これにより、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] が複数のスキーマに対して検索を実行する必要がなくなるため、パフォーマンスが多少向上します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-132">This practice gives a small performance boost because the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] does not have to search multiple schemas.</span></span> <span data-ttu-id="9a6c9-133">また、複数のスキーマに同じ名前のプロシージャがあるデータベースで誤ったプロシージャが実行されることを防止できます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-133">It also prevents executing the wrong procedure if a database has procedures with the same name in multiple schemas.</span></span>  
  
     <span data-ttu-id="9a6c9-134">次の例は、ユーザー定義のプロシージャを実行するために推奨されている方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-134">The following example demonstrates the recommended method to execute a user-defined procedure.</span></span> <span data-ttu-id="9a6c9-135">このプロシージャは 1 つの入力パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-135">Notice that the procedure accepts one input parameter.</span></span> <span data-ttu-id="9a6c9-136">入力パラメーターと出力パラメーターを指定する方法の詳細については、「 [パラメーターの指定](specify-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-136">For information about specifying input and output parameters, see [Specify Parameters](specify-parameters.md).</span></span>  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    EXEC dbo.uspGetEmployeeManagers @BusinessEntityID = 50;  
    ```  
  
     <span data-ttu-id="9a6c9-137">または</span><span class="sxs-lookup"><span data-stu-id="9a6c9-137">-Or-</span></span>  
  
    ```sql  
    EXEC AdventureWorks2012.dbo.uspGetEmployeeManagers 50;  
    GO  
    ```  
  
     <span data-ttu-id="9a6c9-138">修飾されていないユーザー定義のプロシージャを指定した場合、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] では次の順序でプロシージャが検索されます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-138">If a nonqualified user-defined procedure is specified, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] searches for the procedure in the following order:</span></span>  
  
    1.  <span data-ttu-id="9a6c9-139">現在のデータベースの **sys** スキーマ。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-139">The **sys** schema of the current database.</span></span>  
  
    2.  <span data-ttu-id="9a6c9-140">バッチまたは動的 SQL で実行された場合は、呼び出し側の既定のスキーマ。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-140">The caller's default schema if it is executed in a batch or in dynamic SQL.</span></span> <span data-ttu-id="9a6c9-141">または、別のプロシージャ定義の本文の中に非修飾型プロシージャ名がある場合は、そのプロシージャを含んでいるスキーマが次に検索されます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-141">Or, if the nonqualified procedure name appears inside the body of another procedure definition, the schema that contains this other procedure is searched next.</span></span>  
  
    3.  <span data-ttu-id="9a6c9-142">現在のデータベースの **dbo** スキーマ。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-142">The **dbo** schema in the current database.</span></span>  
  
-   <span data-ttu-id="9a6c9-143">ストアド プロシージャの自動実行</span><span class="sxs-lookup"><span data-stu-id="9a6c9-143">Executing Stored Procedures Automatically</span></span>  
  
     <span data-ttu-id="9a6c9-144">自動実行用にマークされたプロシージャは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を起動するたびに実行されます。スタートアップ プロセス中に、 **master** データベースが復旧されます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-144">Procedures marked for automatic execution are executed every time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts and the **master** database is recovered during that startup process.</span></span> <span data-ttu-id="9a6c9-145">データベースのメンテナンス操作を実行する場合や、バックグラウンド プロセスとしてプロシージャを連続実行する場合は、自動実行するようにプロシージャを設定すると便利です。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-145">Setting up procedures to execute automatically can be useful for performing database maintenance operations or for having procedures run continuously as background processes.</span></span> <span data-ttu-id="9a6c9-146">プロシージャの自動実行は、グローバル一時テーブルの作成など、 **tempdb**のシステム タスクまたはメンテナンス タスクを行う場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-146">Another use for automatic execution is to have the procedure perform system or maintenance tasks in **tempdb**, such as creating a global temporary table.</span></span> <span data-ttu-id="9a6c9-147">このようにすると、 **のスタートアップ時に** tempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再作成されても、一時テーブルの存在が保証されます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-147">This makes sure that such a temporary table will always exist when **tempdb** is re-created during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span>  
  
     <span data-ttu-id="9a6c9-148">自動実行されるプロシージャは、固定サーバー ロール **sysadmin** と同じ権限で操作を行います。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-148">A procedure that is automatically executed operates with the same permissions as members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="9a6c9-149">これらのプロシージャが生成するエラー メッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-149">Any error messages generated by the procedure are written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
     <span data-ttu-id="9a6c9-150">スタートアップ プロシージャの数に制限はありませんが、実行中、プロシージャ 1 つにつき 1 つのワーカー スレッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-150">There is no limit to the number of startup procedures you can have, but be aware that each consumes one worker thread while executing.</span></span> <span data-ttu-id="9a6c9-151">スタートアップ時に複数のプロシージャを実行する場合でも、並列に実行する必要がないときは 1 つのプロシージャをスタートアップ プロシージャとし、そのプロシージャが残りのプロシージャを呼び出すようにします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-151">If you must execute multiple procedures at startup but do not need to execute them in parallel, make one procedure the startup procedure and have that procedure call the other procedures.</span></span> <span data-ttu-id="9a6c9-152">この場合は、全体で 1 つのワーカー スレッドしか使用されません。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-152">This uses only one worker thread.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="9a6c9-153">自動実行されるプロシージャからは、結果セットを返さないでください。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-153">Do not return any result sets from a procedure that is executed automatically.</span></span> <span data-ttu-id="9a6c9-154">自動実行されるプロシージャは、アプリケーションやユーザーではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行するので、結果セットを返す先がないためです。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-154">Because the procedure is being executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instead of an application or user, there is nowhere for the result sets to go.</span></span>  
  
-   <span data-ttu-id="9a6c9-155">自動実行の設定、解除、および制御</span><span class="sxs-lookup"><span data-stu-id="9a6c9-155">Setting, Clearing, and Controlling Automatic Execution</span></span>  
  
     <span data-ttu-id="9a6c9-156">自動実行されるようにプロシージャを設定できるのは、システム管理者 (**sa**) だけです。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-156">Only the system administrator (**sa**) can mark a procedure to execute automatically.</span></span> <span data-ttu-id="9a6c9-157">また、このプロシージャは、 **master** データベースに格納されていて、 **sa**により所有されている必要があり、入出力パラメーターを受け渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-157">In addition, the procedure must be in the **master** database, owned by **sa**, and cannot have input or output parameters.</span></span>  
  
     <span data-ttu-id="9a6c9-158">次の操作を実行するには、 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-158">Use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to:</span></span>  
  
    1.  <span data-ttu-id="9a6c9-159">既存のプロシージャをスタートアップ プロシージャとして指定する。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-159">Designate an existing procedure as a startup procedure.</span></span>  
  
    2.  <span data-ttu-id="9a6c9-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタートアップ時にプロシージャが実行されないようにする。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-160">Stop a procedure from executing at [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9a6c9-161">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9a6c9-161">Security</span></span>  
 <span data-ttu-id="9a6c9-162">詳細については、「[EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql)」および「[EXECUTE AS 句 &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-162">For more information, see [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql) and [EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9a6c9-163">Permissions</span><span class="sxs-lookup"><span data-stu-id="9a6c9-163">Permissions</span></span>  
 <span data-ttu-id="9a6c9-164">詳細については、「 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)でストアド プロシージャを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-164">For more information, see the "Permissions" section in [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9a6c9-165">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9a6c9-165">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-execute-a-stored-procedure"></a><span data-ttu-id="9a6c9-166">ストアド プロシージャを実行するには</span><span class="sxs-lookup"><span data-stu-id="9a6c9-166">To execute a stored procedure</span></span>  
  
1.  <span data-ttu-id="9a6c9-167">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続して、そのインスタンスを展開します。次に、 **[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-167">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="9a6c9-168">目的のデータベースを展開し、 **[プログラミング]** を展開します。次に、 **[ストアド プロシージャ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-168">Expand the database that you want, expand **Programmability**, and then expand **Stored Procedures**.</span></span>  
  
3.  <span data-ttu-id="9a6c9-169">目的のユーザー定義のストアド プロシージャを右クリックし、 **[ストアド プロシージャの実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-169">Right-click the user-defined stored procedure that you want and click **Execute Stored Procedure**.</span></span>  
  
4.  <span data-ttu-id="9a6c9-170">**[プロシージャの実行]** ダイアログ ボックスで、各パラメーターの値と、null 値を渡すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-170">In the **Execute Procedure** dialog box, specify a value for each parameter and whether it should pass a null value.</span></span>  
  
     <span data-ttu-id="9a6c9-171">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="9a6c9-171">**Parameter**</span></span>  
     <span data-ttu-id="9a6c9-172">パラメーターの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-172">Indicates the name of the parameter.</span></span>  
  
     <span data-ttu-id="9a6c9-173">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="9a6c9-173">**Data Type**</span></span>  
     <span data-ttu-id="9a6c9-174">パラメーターのデータ型を示します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-174">Indicates the data type of the parameter.</span></span>  
  
     <span data-ttu-id="9a6c9-175">**[出力パラメーター]**</span><span class="sxs-lookup"><span data-stu-id="9a6c9-175">**Output Parameter**</span></span>  
     <span data-ttu-id="9a6c9-176">これが出力パラメーターかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-176">Indicates if this is an output parameter.</span></span>  
  
     <span data-ttu-id="9a6c9-177">**[NULL 値を渡す]**</span><span class="sxs-lookup"><span data-stu-id="9a6c9-177">**Pass Null Value**</span></span>  
     <span data-ttu-id="9a6c9-178">パラメーターの値として NULL を渡します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-178">Pass a NULL as the value of the parameter.</span></span>  
  
     <span data-ttu-id="9a6c9-179">**Value**</span><span class="sxs-lookup"><span data-stu-id="9a6c9-179">**Value**</span></span>  
     <span data-ttu-id="9a6c9-180">プロシージャを呼び出すときのパラメーターの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-180">Type the value for the parameter when calling the procedure.</span></span>  
  
5.  <span data-ttu-id="9a6c9-181">ストアド プロシージャを実行するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-181">To execute the stored procedure, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9a6c9-182">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9a6c9-182">Using Transact-SQL</span></span>  
  
#### <a name="to-execute-a-stored-procedure"></a><span data-ttu-id="9a6c9-183">ストアド プロシージャを実行するには</span><span class="sxs-lookup"><span data-stu-id="9a6c9-183">To execute a stored procedure</span></span>  
  
1.  <span data-ttu-id="9a6c9-184">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-184">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9a6c9-185">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-185">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9a6c9-186">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-186">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9a6c9-187">この例は、1 つのパラメーターを受け取るストアド プロシージャを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-187">This example shows how to execute a stored procedure that expects one parameter.</span></span> <span data-ttu-id="9a6c9-188">この例では、 `uspGetEmployeeManagers` パラメーター値として値  `6` を指定して、 `@EmployeeID` ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-188">The example executes the `uspGetEmployeeManagers` stored procedure with the value  `6` specified as the `@EmployeeID` parameter.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC dbo.uspGetEmployeeManagers 6;  
GO  
```  
  
#### <a name="to-set-or-clear-a-procedure-for-executing-automatically"></a><span data-ttu-id="9a6c9-189">プロシージャの自動実行を設定または解除するには</span><span class="sxs-lookup"><span data-stu-id="9a6c9-189">To set or clear a procedure for executing automatically</span></span>  
  
1.  <span data-ttu-id="9a6c9-190">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-190">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9a6c9-191">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-191">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9a6c9-192">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-192">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9a6c9-193">この例は、 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) を使用してプロシージャの自動実行を設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-193">This example shows how to use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to set a procedure for automatic execution.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';  
```  
  
#### <a name="to-stop-a-procedure-from-executing-automatically"></a><span data-ttu-id="9a6c9-194">プロシージャの自動実行を解除するには</span><span class="sxs-lookup"><span data-stu-id="9a6c9-194">To stop a procedure from executing automatically</span></span>  
  
1.  <span data-ttu-id="9a6c9-195">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-195">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9a6c9-196">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-196">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9a6c9-197">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-197">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9a6c9-198">この例は、 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) を使用して、プロシージャの自動実行を解除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9a6c9-198">This example shows how to use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to stop a procedure from executing automatically.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';  
```  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="9a6c9-199">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9a6c9-199">Example (Transact-SQL)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6c9-200">参照</span><span class="sxs-lookup"><span data-stu-id="9a6c9-200">See Also</span></span>  
 <span data-ttu-id="9a6c9-201">[パラメーターの指定](specify-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="9a6c9-201">[Specify Parameters](specify-parameters.md) </span></span>  
 <span data-ttu-id="9a6c9-202">[scan for startup procs サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="9a6c9-202">[Configure the scan for startup procs Server Configuration Option](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md) </span></span>  
 <span data-ttu-id="9a6c9-203">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9a6c9-203">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span></span>  
 <span data-ttu-id="9a6c9-204">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9a6c9-204">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 [<span data-ttu-id="9a6c9-205">ストアド プロシージャ &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="9a6c9-205">Stored Procedures &#40;Database Engine&#41;</span></span>](stored-procedures-database-engine.md)  
  
  
