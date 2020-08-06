---
title: Integration Services (SSIS) のクエリ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Query Builder [Integration Services]
- queries [Integration Services]
- statements [Integration Services]
- queries [Integration Services], about queries in packages
ms.assetid: 8822bd29-4575-46c8-92a0-1a39bc2604c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5119ff27606ce4e43f65cc129f3caac764e78e0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641123"
---
# <a name="integration-services-ssis-queries"></a><span data-ttu-id="34097-102">Integration Services (SSIS) のクエリ</span><span class="sxs-lookup"><span data-stu-id="34097-102">Integration Services (SSIS) Queries</span></span>
  <span data-ttu-id="34097-103">SQL 実行タスク、OLE DB ソース、OLE DB 変換先、および参照変換では、SQL クエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="34097-103">The Execute SQL task, the OLE DB source, the OLE DB destination, and the Lookup transformation can use SQL queries.</span></span> <span data-ttu-id="34097-104">SQL 実行タスクでは、SQL ステートメントによってデータベース オブジェクトとデータを作成、更新、および削除したり、ストアド プロシージャを実行したり、SELECT ステートメントを実行したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="34097-104">In the Execute SQL task, the SQL statements can create, update, and delete database objects and data; run stored procedures; and perform SELECT statements.</span></span> <span data-ttu-id="34097-105">OLE DB ソースと参照変換の場合、通常 SQL ステートメントは SELECT ステートメントまたは EXEC ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="34097-105">In the OLE DB source and the Lookup transformation, the SQL statements are typically SELECT statements or EXEC statements.</span></span> <span data-ttu-id="34097-106">EXEC ステートメントで最もよく実行するのは、結果セットを返すストアド プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="34097-106">The latter most frequently run stored procedures that return result sets.</span></span>  
  
 <span data-ttu-id="34097-107">クエリを解析して、有効かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="34097-107">A query can be parsed to establish whether it is valid.</span></span> <span data-ttu-id="34097-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]への接続を使用するクエリを解析すると、クエリは解析後に実行されて、実行結果 (成功または失敗) が解析結果に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="34097-108">When parsing a query that uses a connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the query is parsed, executed, and the execution outcome (success or failure) is assigned to the parsing outcome.</span></span> <span data-ttu-id="34097-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]以外のデータへの接続をクエリで使用する場合、ステートメントは解析されるだけです。</span><span class="sxs-lookup"><span data-stu-id="34097-109">If the query uses a connection to a data other than [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the statement is parsed only.</span></span>  
  
 <span data-ttu-id="34097-110">SQL ステートメントを定義するには、デザイナーに直接入力するか、ステートメントを含むファイル接続または変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="34097-110">The SQL statement can be defined either by entering it directly in the designer, or by specifying a file connection or a variable that contains the statement.</span></span>  
  
## <a name="direct-input-sql"></a><span data-ttu-id="34097-111">直接入力 SQL</span><span class="sxs-lookup"><span data-stu-id="34097-111">Direct Input SQL</span></span>  
 <span data-ttu-id="34097-112">クエリ ビルダーは、SQL 実行タスク、OLE DB ソース、OLE DB 変換先、および参照変換のユーザー インターフェイスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="34097-112">Query Builder is available in the user interface for the Execute SQL task, the OLE DB source, the OLE DB destination, and the Lookup transformation.</span></span> <span data-ttu-id="34097-113">クエリ ビルダーを使用すると次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="34097-113">Query Builder offers the following advantages:</span></span>  
  
-   <span data-ttu-id="34097-114">視覚的な作業、または SQL コマンドを使用した作業</span><span class="sxs-lookup"><span data-stu-id="34097-114">Work visually or with SQL commands.</span></span>  
  
     <span data-ttu-id="34097-115">クエリ ビルダーには、クエリを視覚的に構成するグラフィカル ペインと、クエリの SQL テキストを表示するテキスト ペインがあります。</span><span class="sxs-lookup"><span data-stu-id="34097-115">Query Builder includes graphical panes that compose your query visually and a text pane that displays the SQL text of your query.</span></span> <span data-ttu-id="34097-116">グラフィカル ペインとテキスト ペインのどちらでも作業ができます。</span><span class="sxs-lookup"><span data-stu-id="34097-116">You can work in either the graphical or text panes.</span></span> <span data-ttu-id="34097-117">これらの表示はクエリ ビルダーによって同期されるため、クエリのテキストとグラフィカルな表示は常に一致します。</span><span class="sxs-lookup"><span data-stu-id="34097-117">Query Builder synchronizes the views so that the query text and graphical representation always match.</span></span>  
  
-   <span data-ttu-id="34097-118">関係付けられたテーブルの結合</span><span class="sxs-lookup"><span data-stu-id="34097-118">Join related tables.</span></span>  
  
     <span data-ttu-id="34097-119">クエリに複数のテーブルを追加する場合、クエリ ビルダーでは自動的にテーブル間の関係を認識し、適切な結合コマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="34097-119">If you add more than one table to your query, Query Builder automatically determines how the tables are related and constructs the appropriate join command.</span></span>  
  
-   <span data-ttu-id="34097-120">データベースのクエリまたは更新</span><span class="sxs-lookup"><span data-stu-id="34097-120">Query or update databases.</span></span>  
  
     <span data-ttu-id="34097-121">クエリ ビルダーでは、Transact-SQL SELECT ステートメントを使用してデータを返すことができます。また、データベースのレコードの更新、追加、削除を行うクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="34097-121">You can use Query Builder to return data using Transact-SQL SELECT statements, or to create queries that update, add, or delete records in a database.</span></span>  
  
-   <span data-ttu-id="34097-122">結果の即時の表示と変更</span><span class="sxs-lookup"><span data-stu-id="34097-122">View and edit results immediately.</span></span>  
  
     <span data-ttu-id="34097-123">クエリを実行したり、グリッドのレコードセットを使用して、データベースのレコードのスクロールや編集ができます。</span><span class="sxs-lookup"><span data-stu-id="34097-123">You can execute your query and work with a recordset in a grid that lets you scroll through and edit records in the database.</span></span>  
  
 <span data-ttu-id="34097-124">クエリ ビルダーの視覚的な作業で作成できるのは SELECT クエリだけですが、テキスト ペインには DELETE や UPDATE ステートメントなど他の種類の SQL ステートメントを入力できます。</span><span class="sxs-lookup"><span data-stu-id="34097-124">Although Query Builder is visually limited to creating SELECT queries, you can type the SQL for other types of statements such as DELETE and UPDATE statements in the text pane.</span></span> <span data-ttu-id="34097-125">入力した SQL ステートメントに合わせて、グラフィカル ペインも自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="34097-125">The graphical pane is automatically updated to reflect the SQL statement that you typed.</span></span>  
  
 <span data-ttu-id="34097-126">また、直接入力は、タスクやデータ フロー コンポーネントのダイアログ ボックス、またはプロパティ ウィンドウにクエリを入力しても行えます。</span><span class="sxs-lookup"><span data-stu-id="34097-126">You can also provide direct input by typing the query in the task or data flow component dialog box or the Properties window.</span></span>  
  
 <span data-ttu-id="34097-127">詳細については、「 [クエリ ビルダー](../../2014/integration-services/query-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34097-127">For more information, see [Query Builder](../../2014/integration-services/query-builder.md).</span></span>  
  
## <a name="sql-in-files"></a><span data-ttu-id="34097-128">ファイルの SQL</span><span class="sxs-lookup"><span data-stu-id="34097-128">SQL in Files</span></span>  
 <span data-ttu-id="34097-129">SQL 実行タスクの SQL ステートメントを、別のファイルに格納しておくことも可能です。</span><span class="sxs-lookup"><span data-stu-id="34097-129">The SQL statement for the Execute SQL task can also reside in a separate file.</span></span> <span data-ttu-id="34097-130">たとえば、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のクエリ エディターのようなツールを使用してクエリを記述し、ファイルに保存して、パッケージを実行するときにファイルからクエリを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="34097-130">For example, you can write queries using tools such as the Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], save the query to a file, and then read the query from the file when running a package.</span></span> <span data-ttu-id="34097-131">ファイルには、実行する SQL ステートメントとコメントのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="34097-131">The file can contain only the SQL statements to run and comments.</span></span> <span data-ttu-id="34097-132">ファイルに格納された SQL ステートメントを使用するには、ファイル名とファイルの場所を指定するファイル接続を用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34097-132">To use a SQL statement stored in a file, you must provide a file connection that specifies the file name and location.</span></span> <span data-ttu-id="34097-133">詳しくは「 [File Connection Manager](connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34097-133">For more information, see [File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="sql-in-variables"></a><span data-ttu-id="34097-134">変数の SQL</span><span class="sxs-lookup"><span data-stu-id="34097-134">SQL in Variables</span></span>  
 <span data-ttu-id="34097-135">SQL 実行タスクの SQL ステートメントのソースが変数の場合、クエリが格納されている変数の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="34097-135">If the source of the SQL statement in the Execute SQL task is a variable, you provide the name of the variable that contains the query.</span></span> <span data-ttu-id="34097-136">変数の Value プロパティにクエリのテキストを格納します。</span><span class="sxs-lookup"><span data-stu-id="34097-136">The Value property of the variable contains the query text.</span></span> <span data-ttu-id="34097-137">変数の ValueType プロパティを文字列データ型に設定し、Value プロパティに SQL ステートメントを入力またはコピーします。</span><span class="sxs-lookup"><span data-stu-id="34097-137">You set the ValueType property of the variable to a string data type and then type or copy the SQL statement into the Value property.</span></span> <span data-ttu-id="34097-138">詳細については、「[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34097-138">For more information, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
  
