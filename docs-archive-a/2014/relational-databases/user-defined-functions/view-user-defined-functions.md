---
title: ユーザー定義関数の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.udfproperties.general.f1
- sql12.swb.functionproperties.general.f1
helpviewer_keywords:
- displaying user-defined functions
- viewing user-defined functions
- user-defined functions [SQL Server], viewing
- status information [SQL Server], user-defined functions
ms.assetid: a45dfab5-6384-4311-b935-2e23a70c5c10
author: rothja
ms.author: jroth
ms.openlocfilehash: 5248f75540b72b489a7605b2cca34144dfcfedbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630847"
---
# <a name="view-user-defined-functions"></a><span data-ttu-id="90eb4-102">ユーザー定義関数の表示</span><span class="sxs-lookup"><span data-stu-id="90eb4-102">View User-defined Functions</span></span>
  <span data-ttu-id="90eb4-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のユーザー定義関数の定義またはプロパティに関する情報は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="90eb4-103">You can gain information about the definition or properties of a user-defined function in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="90eb4-104">関数のデータが元のテーブルからどのように抽出されているのかを理解したり、関数で定義されているデータを確認するために、関数の定義を調べたい場合があります。</span><span class="sxs-lookup"><span data-stu-id="90eb4-104">You may need to see the definition of the function to understand how its data is derived from the source tables or to see the data defined by the function.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="90eb4-105">関数から参照しているオブジェクトの名前を変更する場合は、関数のテキストに新しいオブジェクト名が反映されるように関数を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90eb4-105">If you change the name of an object referenced by a function, you must modify that function so that its text reflects the new name.</span></span> <span data-ttu-id="90eb4-106">したがって、オブジェクトの名前を変更する前に、まずオブジェクトの依存関係を表示して、オブジェクト名の変更により影響を受ける関数があるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90eb4-106">Therefore, before renaming an object, display the dependencies of the object first to determine if any functions are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="90eb4-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="90eb4-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="90eb4-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="90eb4-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="90eb4-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="90eb4-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="90eb4-110">**関数に関する情報を取得するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="90eb4-110">**To get information about a function, using:**</span></span>  
  
     [<span data-ttu-id="90eb4-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="90eb4-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="90eb4-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="90eb4-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="90eb4-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="90eb4-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="90eb4-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="90eb4-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="90eb4-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="90eb4-115">Permissions</span></span>  
 <span data-ttu-id="90eb4-116">**sys.sql_expression_dependencies** を使用して関数のすべての依存関係を検索するには、データベースに対する VIEW DEFINITION 権限とデータベースの **sys.sql_expression_dependencies** に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-116">Using **sys.sql_expression_dependencies** to find all the dependencies on a function requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database.</span></span> <span data-ttu-id="90eb4-117">OBJECT_DEFINITION で返されるようなシステム オブジェクトの定義は公開されます。</span><span class="sxs-lookup"><span data-stu-id="90eb4-117">System object definitions, like the ones returned in OBJECT_DEFINITION, are publicly visible.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="90eb4-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="90eb4-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-show-a-user-defined-functions-properties"></a><span data-ttu-id="90eb4-119">ユーザー定義関数のプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="90eb4-119">To show a user-defined function's properties</span></span>  
  
1.  <span data-ttu-id="90eb4-120">**オブジェクト エクスプローラー**で、プロパティを表示する関数を含むデータベースの横にあるプラス記号をクリックします。次に、プラス記号をクリックして **[プログラミング]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-120">In **Object Explorer**, click the plus sign next to the database that contains the function to which you want to view the properties, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="90eb4-121">プラス記号をクリックして **[関数]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-121">Click the plus sign to expand the **Functions** folder.</span></span>  
  
3.  <span data-ttu-id="90eb4-122">プロパティを表示する関数を含むフォルダーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-122">Click the plus sign to expand the folder that contains the function to which you want to view the properties:</span></span>  
  
    -   <span data-ttu-id="90eb4-123">Table-valued Function</span><span class="sxs-lookup"><span data-stu-id="90eb4-123">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="90eb4-124">スカラー値関数</span><span class="sxs-lookup"><span data-stu-id="90eb4-124">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="90eb4-125">集計関数</span><span class="sxs-lookup"><span data-stu-id="90eb4-125">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="90eb4-126">プロパティを表示する関数を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-126">Right-click the function of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="90eb4-127">**[関数のプロパティ -** function_name _]_ ダイアログ ボックスに、次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90eb4-127">The following properties appear in the **Function Properties -** _function_name_ dialog box.</span></span>  
  
     <span data-ttu-id="90eb4-128">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-128">**Database**</span></span>  
     <span data-ttu-id="90eb4-129">この関数を含むデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-129">The name of the database containing this function.</span></span>  
  
     <span data-ttu-id="90eb4-130">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-130">**Server**</span></span>  
     <span data-ttu-id="90eb4-131">現在のサーバー インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-131">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="90eb4-132">**User**</span><span class="sxs-lookup"><span data-stu-id="90eb4-132">**User**</span></span>  
     <span data-ttu-id="90eb4-133">この接続のユーザーの名前です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-133">The name of the user of this connection.</span></span>  
  
     <span data-ttu-id="90eb4-134">**[作成日]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-134">**Created date**</span></span>  
     <span data-ttu-id="90eb4-135">関数が作成された日付を表示します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-135">Displays the date the function was created.</span></span>  
  
     <span data-ttu-id="90eb4-136">**[実行時の権限]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-136">**Execute As**</span></span>  
     <span data-ttu-id="90eb4-137">関数の実行コンテキストです。</span><span class="sxs-lookup"><span data-stu-id="90eb4-137">Execution context for the function.</span></span>  
  
     <span data-ttu-id="90eb4-138">**Name**</span><span class="sxs-lookup"><span data-stu-id="90eb4-138">**Name**</span></span>  
     <span data-ttu-id="90eb4-139">現在の関数の名前です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-139">The name of the current function.</span></span>  
  
     <span data-ttu-id="90eb4-140">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-140">**Schema**</span></span>  
     <span data-ttu-id="90eb4-141">関数を所有するスキーマを表示します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-141">Displays the schema that owns the function.</span></span>  
  
     <span data-ttu-id="90eb4-142">**[システム オブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-142">**System object**</span></span>  
     <span data-ttu-id="90eb4-143">関数がシステム オブジェクトかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-143">Indicates whether the function is a system object.</span></span> <span data-ttu-id="90eb4-144">値は True と False です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-144">Values are True and False.</span></span>  
  
     <span data-ttu-id="90eb4-145">**[ANSI NULL]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-145">**ANSI NULLs**</span></span>  
     <span data-ttu-id="90eb4-146">オブジェクトが ANSI NULL オプションで作成されたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-146">Indicates if the object was created with the ANSI NULLs option.</span></span>  
  
     <span data-ttu-id="90eb4-147">**Encrypted**</span><span class="sxs-lookup"><span data-stu-id="90eb4-147">**Encrypted**</span></span>  
     <span data-ttu-id="90eb4-148">関数が暗号化されているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-148">Indicates whether the function is encrypted.</span></span> <span data-ttu-id="90eb4-149">値は True と False です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-149">Values are True and False.</span></span>  
  
     <span data-ttu-id="90eb4-150">**[関数の種類]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-150">**Function Type**</span></span>  
     <span data-ttu-id="90eb4-151">ユーザー定義関数の種類です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-151">The type of user defined function.</span></span>  
  
     <span data-ttu-id="90eb4-152">**[引用符で囲まれた識別子]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-152">**Quoted identifier**</span></span>  
     <span data-ttu-id="90eb4-153">オブジェクトが引用符で囲まれた識別子オプションで作成されたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-153">Indicates if the object was created with the quoted identifier option.</span></span>  
  
     <span data-ttu-id="90eb4-154">**[スキーマ バインド]**</span><span class="sxs-lookup"><span data-stu-id="90eb4-154">**Schema bound**</span></span>  
     <span data-ttu-id="90eb4-155">関数がスキーマ バインドされているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-155">Indicates whether the function is schema-bound.</span></span> <span data-ttu-id="90eb4-156">値は True と False です。</span><span class="sxs-lookup"><span data-stu-id="90eb4-156">Values are True and False.</span></span> <span data-ttu-id="90eb4-157">スキーマ バインド関数の詳細については、「[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)」の SCHEMABINDING のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90eb4-157">For information about schema-bound functions, see the SCHEMABINDING section of [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="90eb4-158">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="90eb4-158">Using Transact-SQL</span></span>  
  
#### <a name="to-get-the-definition-and-properties-of-a-function"></a><span data-ttu-id="90eb4-159">関数の定義およびプロパティを取得するには</span><span class="sxs-lookup"><span data-stu-id="90eb4-159">To get the definition and properties of a function</span></span>  
  
1.  <span data-ttu-id="90eb4-160">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="90eb4-161">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90eb4-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="90eb4-162">次のいずれかの例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90eb4-162">Copy and paste one of the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get the function name, definition, and relevant properties  
    SELECT sm.object_id,   
       OBJECT_NAME(sm.object_id) AS object_name,   
       o.type,   
       o.type_desc,   
       sm.definition,  
       sm.uses_ansi_nulls,  
       sm.uses_quoted_identifier,  
       sm.is_schema_bound,  
       sm.execute_as_principal_id  
    -- using the two system tables sys.sql_modules and sys.objects  
    FROM sys.sql_modules AS sm  
    JOIN sys.objects AS o ON sm.object_id = o.object_id  
    -- from the function 'dbo.ufnGetProductDealerPrice'  
    WHERE sm.object_id = OBJECT_ID('dbo.ufnGetProductDealerPrice')  
    ORDER BY o.type;  
    GO  
  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get the definition of the function dbo.ufnGetProductDealerPrice  
    SELECT OBJECT_DEFINITION (OBJECT_ID('dbo.ufnGetProductDealerPrice')) AS ObjectDefinition;  
    GO  
    ```  
  
 <span data-ttu-id="90eb4-163">詳細については、「[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)」および「[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90eb4-163">For more information, see [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) and [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql).</span></span>  
  
#### <a name="to-get-the-dependencies-of-a-function"></a><span data-ttu-id="90eb4-164">関数の依存関係を取得するには</span><span class="sxs-lookup"><span data-stu-id="90eb4-164">To get the dependencies of a function</span></span>  
  
1.  <span data-ttu-id="90eb4-165">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="90eb4-165">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="90eb4-166">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90eb4-166">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="90eb4-167">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90eb4-167">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get all of the dependency information  
    SELECT OBJECT_NAME(sed.referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(sed.referencing_id, sed.referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        sed.referencing_class_desc, sed.referenced_class_desc,  
        sed.referenced_server_name, sed.referenced_database_name, sed.referenced_schema_name,  
        sed.referenced_entity_name,   
        COALESCE(COL_NAME(sed.referenced_id, sed.referenced_minor_id), '(n/a)') AS referenced_column_name,  
        sed.is_caller_dependent, sed.is_ambiguous  
    -- from the two system tables sys.sql_expression_dependencies and sys.object  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    -- on the function dbo.ufnGetProductDealerPrice  
    WHERE sed.referencing_id = OBJECT_ID('dbo.ufnGetProductDealerPrice');  
    GO  
    ```  
  
 <span data-ttu-id="90eb4-168">詳細については、「[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)」および「[sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90eb4-168">For more information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
  
