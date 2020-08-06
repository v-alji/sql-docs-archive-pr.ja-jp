---
title: MSSQLSERVER_2020 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2020 (Database Engine error)
ms.assetid: 4a8bf90f-a083-4c53-84f0-d23c711c8081
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5939267c37e90e7b8456dc01a4af79545e775656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643886"
---
# <a name="mssqlserver_2020"></a><span data-ttu-id="baf04-102">MSSQLSERVER_2020</span><span class="sxs-lookup"><span data-stu-id="baf04-102">MSSQLSERVER_2020</span></span>
    
## <a name="details"></a><span data-ttu-id="baf04-103">詳細</span><span class="sxs-lookup"><span data-stu-id="baf04-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="baf04-104">製品名</span><span class="sxs-lookup"><span data-stu-id="baf04-104">Product Name</span></span>|<span data-ttu-id="baf04-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="baf04-105">SQL Server</span></span>|  
|<span data-ttu-id="baf04-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="baf04-106">Event ID</span></span>|<span data-ttu-id="baf04-107">2020</span><span class="sxs-lookup"><span data-stu-id="baf04-107">2020</span></span>|  
|<span data-ttu-id="baf04-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="baf04-108">Event Source</span></span>|<span data-ttu-id="baf04-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="baf04-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="baf04-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="baf04-110">Component</span></span>|<span data-ttu-id="baf04-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="baf04-111">SQLEngine</span></span>|  
|<span data-ttu-id="baf04-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="baf04-112">Symbolic Name</span></span>||  
|<span data-ttu-id="baf04-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="baf04-113">Message Text</span></span>|<span data-ttu-id="baf04-114">エンティティ "%.\*ls" に対してレポートされた依存関係に、列への参照が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="baf04-114">The dependencies reported for entity "%.\*ls" do not include references to columns.</span></span> <span data-ttu-id="baf04-115">この原因としては、存在しないオブジェクトがエンティティによって参照されていること、またはエンティティの 1 つ以上のステートメントにエラーがあることが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="baf04-115">This is either because the entity references an object that does not exist or because of an error in one or more statements in the entity.</span></span>  <span data-ttu-id="baf04-116">クエリを再実行する前に、エンティティにエラーがないこと、およびエンティティによって参照されているすべてのオブジェクトが存在することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="baf04-116">Before rerunning the query, ensure that there are no errors in the entity and that all objects referenced by the entity exist.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="baf04-117">説明</span><span class="sxs-lookup"><span data-stu-id="baf04-117">Explanation</span></span>  
 <span data-ttu-id="baf04-118">**sys.dm_sql_referenced_entities** システム関数では、スキーマ バインド参照の列レベルの依存関係が報告されます。</span><span class="sxs-lookup"><span data-stu-id="baf04-118">The **sys.dm_sql_referenced_entities** system function will report any column-level dependency for schema-bound references.</span></span> <span data-ttu-id="baf04-119">たとえば、インデックス付きビューの列レベルの依存関係がすべて報告されます。これは、インデックス付きビューがスキーマ バインドを必要とするためです。</span><span class="sxs-lookup"><span data-stu-id="baf04-119">For example, the function will report all column-level dependencies for an indexed view because an indexed view requires schema binding.</span></span> <span data-ttu-id="baf04-120">ただし、参照先エンティティがスキーマにバインドされていない場合は、列が参照されているすべてのステートメントをバインドできる場合にのみ、列の依存関係が報告されます。</span><span class="sxs-lookup"><span data-stu-id="baf04-120">However, when the referenced entity is not schema-bound, column dependencies are reported only when all statements in which the columns are referenced can be bound.</span></span> <span data-ttu-id="baf04-121">ステートメントをバインドできるのは、ステートメント解析時にすべてのオブジェクトが存在している場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="baf04-121">Statements can be successfully bound only if all objects exist at the time the statements are parsed.</span></span> <span data-ttu-id="baf04-122">エンティティに定義されているステートメントを 1 つでもバインドできない場合は、列の依存関係が報告されず、**referenced_minor_id** 列で 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="baf04-122">If any statement defined in the entity fails to bind, column dependencies will not be reported and the **referenced_minor_id** column will return 0.</span></span> <span data-ttu-id="baf04-123">列の依存関係を解決できない場合は、エラー 2020 が発生します。</span><span class="sxs-lookup"><span data-stu-id="baf04-123">When column dependencies cannot be resolved, error 2020 is raised.</span></span> <span data-ttu-id="baf04-124">このエラーによって、クエリからオブジェクト レベルの依存関係が返されなくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="baf04-124">This error does not prevent the query from returning object-level dependencies.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="baf04-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="baf04-125">User Action</span></span>  
 <span data-ttu-id="baf04-126">エラー 2020 発生前のメッセージで確認されたエラーをすべて修正します。</span><span class="sxs-lookup"><span data-stu-id="baf04-126">Correct any errors identified in the message before error 2020.</span></span> <span data-ttu-id="baf04-127">たとえば次のコード例では、`Production.ApprovedDocuments` テーブルの `Title`、`ChangeNumber`、`Status` の各列で、ビュー `Production.Document` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="baf04-127">For example, in the following code example the view `Production.ApprovedDocuments` is defined on the columns `Title`, `ChangeNumber`, and `Status` in the `Production.Document` table.</span></span> <span data-ttu-id="baf04-128">**sys.dm_sql_referenced_entities** システム関数で、`ApprovedDocuments` ビューが依存するオブジェクトと列がクエリされます。</span><span class="sxs-lookup"><span data-stu-id="baf04-128">The **sys.dm_sql_referenced_entities** system function is queried for the objects and columns on which the `ApprovedDocuments` view depends.</span></span> <span data-ttu-id="baf04-129">このビューの作成には WITH SCHEMA_BINDING 句が使用されていないため、ビューで参照されている列が参照先テーブルで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="baf04-129">Because the view is not created using the WITH SCHEMA_BINDING clause, the columns referenced in the view can be modified in the referenced table.</span></span> <span data-ttu-id="baf04-130">この例では、`ChangeNumber` テーブルの `Production.Document` 列の名前が `TrackingNumber` に変更されています。</span><span class="sxs-lookup"><span data-stu-id="baf04-130">The example alters the column `ChangeNumber` in the `Production.Document` table by renaming it to `TrackingNumber`.</span></span> <span data-ttu-id="baf04-131">カタログ ビューに対して `ApprovedDocuments` ビューに関するクエリが再度実行されますが、ビューに定義されているどの列にもバインドできません。</span><span class="sxs-lookup"><span data-stu-id="baf04-131">The catalog view is queried again for the `ApprovedDocuments` view; however it cannot bind to all the columns defined in the view.</span></span> <span data-ttu-id="baf04-132">この問題を示すエラー 207 と 2020 が返されます。</span><span class="sxs-lookup"><span data-stu-id="baf04-132">Errors 207 and 2020 are returned identifying the problem.</span></span> <span data-ttu-id="baf04-133">問題を解決するには、列の新しい名前が反映されるようにビューを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="baf04-133">To resolve the problem, the view must be altered to reflect the new name of the column.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `CREATE VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title, ChangeNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 `EXEC sp_rename 'Production.Document.ChangeNumber', 'TrackingNumber', 'COLUMN';`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 <span data-ttu-id="baf04-134">このクエリでは、次のエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="baf04-134">The query returns the following error messages.</span></span>  
  
 `Msg 207, Level 16, State 1, Procedure ApprovedDocuments, Line 3`  
  
 `Invalid column name 'ChangeNumber'.`  
  
 `Msg 2020, Level 16, State 1, Line 1`  
  
 `The dependencies reported for entity`  
  
 `"Production.ApprovedDocuments" do not include references to`  
  
 `columns. This is either because the entity references an`  
  
 `object that does not exist or because of an error in one or`  
  
 `more statements in the entity. Before rerunning the query,`  
  
 `ensure that there are no errors in the entity and that all`  
  
 `objects referenced by the entity exist.`  
  
 <span data-ttu-id="baf04-135">次の例では、ビュー内の列名を修正しています。</span><span class="sxs-lookup"><span data-stu-id="baf04-135">The following example corrects the column name in the view.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `ALTER VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title,TrackingNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
## <a name="see-also"></a><span data-ttu-id="baf04-136">参照</span><span class="sxs-lookup"><span data-stu-id="baf04-136">See Also</span></span>  
 [<span data-ttu-id="baf04-137">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="baf04-137">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
  
