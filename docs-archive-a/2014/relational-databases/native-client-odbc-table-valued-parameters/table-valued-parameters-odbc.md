---
title: テーブル値パラメーター (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC)
- ODBC, table-valued parameters
ms.assetid: ef06cd13-18e2-4c65-8ede-c3955d820e54
author: rothja
ms.author: jroth
ms.openlocfilehash: fedfd63f7cbafd68d39aeb62dd29c046df8ab100
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631852"
---
# <a name="table-valued-parameters-odbc"></a><span data-ttu-id="d33ae-102">テーブル値パラメーター (ODBC)</span><span class="sxs-lookup"><span data-stu-id="d33ae-102">Table-Valued Parameters (ODBC)</span></span>
  <span data-ttu-id="d33ae-103">ODBC のテーブル値パラメーターのサポートにより、クライアント アプリケーションは、1 回の呼び出しで複数の行をサーバーに送信することで、パラメーター化されたデータをサーバーに効率的に送信できます。</span><span class="sxs-lookup"><span data-stu-id="d33ae-103">ODBC support for table-valued parameters lets a client application send parameterized data to the server more efficiently, by sending multiple rows to the server with one call.</span></span>  
  
 <span data-ttu-id="d33ae-104">サーバー上のテーブル値パラメーターの詳細については、「[テーブル値パラメーターの使用 &#40;データベースエンジン&#41;](../tables/use-table-valued-parameters-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d33ae-104">For information about table-valued parameters on the server, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
 <span data-ttu-id="d33ae-105">ODBC でテーブル値パラメーターをサーバーに送信するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="d33ae-105">In ODBC, there are two ways that you can send table-valued parameters to the server:</span></span>  
  
-   <span data-ttu-id="d33ae-106">SQLExecDirect または SQLExecute が呼び出されたときに、すべてのテーブル値パラメーターデータをメモリ内に配置できます。</span><span class="sxs-lookup"><span data-stu-id="d33ae-106">All the table-valued parameter data can be in memory at the time SQLExecDirect or SQLExecute is called.</span></span> <span data-ttu-id="d33ae-107">テーブル値に複数の行がある場合、このデータを配列に格納します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-107">This data is stored in arrays if there are multiple rows in the table-value.</span></span>  
  
-   <span data-ttu-id="d33ae-108">アプリケーションでは、SQLExecDirect または SQLExecute が呼び出されたときに、テーブル値パラメーターの実行時データを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d33ae-108">An application can specify data-at-execution for a table-valued parameter when SQLExecDirect or SQLExecute is called.</span></span> <span data-ttu-id="d33ae-109">この場合、テーブル値のデータの行をバッチ内で指定するか、必要なメモリ量を減らすために 1 つずつ指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d33ae-109">In this case, rows of data for the table-value can be provided in batches, or one at a time to reduce memory requirements.</span></span>  
  
 <span data-ttu-id="d33ae-110">1 つ目の方法では、より多くのビジネス ロジックをストアド プロシージャにカプセル化できます。</span><span class="sxs-lookup"><span data-stu-id="d33ae-110">The first option enables stored procedures to encapsulate more business logic.</span></span> <span data-ttu-id="d33ae-111">たとえば、発注品目をテーブル値パラメーターとして渡す場合、注文入力のトランザクション全体を 1 つのストアド プロシージャにカプセル化することができます。</span><span class="sxs-lookup"><span data-stu-id="d33ae-111">For example, a single stored procedure could encapsulate a whole order entry transaction when the order items are passed as a table-valued parameter.</span></span> <span data-ttu-id="d33ae-112">サーバーとのやり取りが 1 回で済むため、この方法は非常に効率的です。</span><span class="sxs-lookup"><span data-stu-id="d33ae-112">This option is very efficient, because only a single round trip to the server is required.</span></span> <span data-ttu-id="d33ae-113">また、異なるプロシージャを使用して、注文ヘッダーと発注品目を個別に処理することもできます。この場合、必要なコードが多くなり、クライアントとサーバー間のコントラクトが複雑になります。</span><span class="sxs-lookup"><span data-stu-id="d33ae-113">Alternatively, you could use different procedures to handle the order header and order items separately, which would require more code and a more complex contract between the client and server.</span></span>  
  
 <span data-ttu-id="d33ae-114">2 つ目の方法は、膨大な量のデータを使用する一括操作のときに効率の良いメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="d33ae-114">The second method provides an efficient mechanism for bulk operations with very large amounts of data.</span></span> <span data-ttu-id="d33ae-115">この方法では、アプリケーションで最初にデータ行をメモリ内のバッファーに格納しなくても、データ行をサーバーにストリーム送信できます。</span><span class="sxs-lookup"><span data-stu-id="d33ae-115">This enables an application to stream rows of data to the server without having to buffer them all in memory first.</span></span>  
  
 <span data-ttu-id="d33ae-116">テーブル変数を作成するときに、制約と主キーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d33ae-116">You can create constraints and primary keys when you create the table variable.</span></span> <span data-ttu-id="d33ae-117">制約は、テーブル内のデータが特定の要件を満たしていることを確認するのに優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="d33ae-117">Constraints are a good way to ensure that the data in a table meets specific requirements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d33ae-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d33ae-118">In This Section</span></span>  
 [<span data-ttu-id="d33ae-119">ODBC テーブル値パラメーターの使用</span><span class="sxs-lookup"><span data-stu-id="d33ae-119">Uses of ODBC Table-Valued Parameters</span></span>](uses-of-odbc-table-valued-parameters.md)  
 <span data-ttu-id="d33ae-120">テーブル値パラメーターと ODBC の主なユーザー シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-120">Describes the primary user scenarios for table-valued parameters and ODBC.</span></span>  
  
 [<span data-ttu-id="d33ae-121">テーブル値パラメーター用の ODBC SQL 型</span><span class="sxs-lookup"><span data-stu-id="d33ae-121">ODBC SQL Type for Table-Valued Parameters</span></span>](odbc-sql-type-for-table-valued-parameters.md)  
 <span data-ttu-id="d33ae-122">SQL_SS_TABLE 型について説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-122">Describes the SQL_SS_TABLE type.</span></span> <span data-ttu-id="d33ae-123">この型は、テーブル値パラメーターをサポートする新しい ODBC SQL 型です。</span><span class="sxs-lookup"><span data-stu-id="d33ae-123">This is a new ODBC SQL type that supports table-valued parameters.</span></span>  
  
 [<span data-ttu-id="d33ae-124">テーブル値パラメーターの記述子フィールド</span><span class="sxs-lookup"><span data-stu-id="d33ae-124">Table-Valued Parameter Descriptor Fields</span></span>](table-valued-parameter-descriptor-fields.md)  
 <span data-ttu-id="d33ae-125">テーブル値パラメーターをサポートする記述子フィールドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-125">Describes descriptor fields that support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="d33ae-126">テーブル値パラメーターを構成する列の記述子フィールド</span><span class="sxs-lookup"><span data-stu-id="d33ae-126">Descriptor Fields for Table-Valued Parameter Constituent Columns</span></span>](descriptor-fields-for-table-valued-parameter-constituent-columns.md)  
 <span data-ttu-id="d33ae-127">テーブル値パラメーターで意味を持つ記述子フィールドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-127">Describes descriptor fields that have meaning for table-valued parameters.</span></span>  
  
 [<span data-ttu-id="d33ae-128">テーブル値パラメーターの診断レコードのフィールド</span><span class="sxs-lookup"><span data-stu-id="d33ae-128">Table-Valued Parameter Diagnostic Record Fields</span></span>](table-valued-parameter-diagnostic-record-fields.md)  
 <span data-ttu-id="d33ae-129">テーブル値パラメーターをサポートするために診断レコードに追加された 2 つの診断フィールドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-129">Describes two diagnostic fields that have been added to diagnostic records to support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="d33ae-130">テーブル値パラメーターに影響を与えるステートメント属性</span><span class="sxs-lookup"><span data-stu-id="d33ae-130">Statement Attributes that Affect Table-Valued Parameters</span></span>](statement-attributes-that-affect-table-valued-parameters.md)  
 <span data-ttu-id="d33ae-131">テーブル値パラメーター列に対処できるようにする記述子の新しいヘッダー フィールドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-131">Describes a new descriptor header field that enables table-valued parameters columns to be addressed.</span></span>  
  
 [<span data-ttu-id="d33ae-132">テーブル値パラメーターおよび列の値のバインドとデータ転送</span><span class="sxs-lookup"><span data-stu-id="d33ae-132">Binding and Data Transfer of Table-Valued Parameters and Column Values</span></span>](binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)  
 <span data-ttu-id="d33ae-133">パラメーター バインドと、テーブル値パラメーターをサーバーに渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-133">Describes parameter binding and how to pass a table-valued parameter to the server.</span></span>  
  
 [<span data-ttu-id="d33ae-134">準備されたステートメント用のテーブル値パラメーターのメタデータ</span><span class="sxs-lookup"><span data-stu-id="d33ae-134">Table-Valued Parameter Metadata for Prepared Statements</span></span>](table-valued-parameter-metadata-for-prepared-statements.md)  
 <span data-ttu-id="d33ae-135">アプリケーションから、準備されたプロシージャ呼び出しのメタデータを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-135">Describes how an application can obtain metadata for a prepared procedure call.</span></span>  
  
 [<span data-ttu-id="d33ae-136">テーブル値パラメーターの追加メタデータ</span><span class="sxs-lookup"><span data-stu-id="d33ae-136">Additional Table-Valued Parameter Metadata</span></span>](additional-table-valued-parameter-metadata.md)  
 <span data-ttu-id="d33ae-137">SQLProcedureColumns、SQLTables、および Sqltables を使用して、テーブル値パラメーターのメタデータを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-137">Describes how to use SQLProcedureColumns, SQLTables, and SQLColumns to retrieve metadata for a table-valued parameter.</span></span>  
  
 [<span data-ttu-id="d33ae-138">テーブル値パラメーターのデータ変換およびその他のエラーと警告</span><span class="sxs-lookup"><span data-stu-id="d33ae-138">Table-Valued Parameter Data Conversion and Other Errors and Warnings</span></span>](table-valued-parameter-data-conversion-and-other-errors-and-warnings.md)  
 <span data-ttu-id="d33ae-139">テーブル値パラメーターの列値に関するエラーを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-139">Describes how to process errors on table-valued parameter column values.</span></span>  
  
 [<span data-ttu-id="d33ae-140">複数バージョン間の互換性</span><span class="sxs-lookup"><span data-stu-id="d33ae-140">Cross-Version Compatibility</span></span>](cross-version-compatibility.md)  
 <span data-ttu-id="d33ae-141">テーブル値パラメーターが、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のバージョンのクライアントまたはサーバーで使用されるときに発生する可能性がある競合について説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-141">Describes conflicts that can occur when table-valued parameters are used by a client or server of a version earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 [<span data-ttu-id="d33ae-142">ODBC テーブル値パラメーター API の概要</span><span class="sxs-lookup"><span data-stu-id="d33ae-142">ODBC Table-Valued Parameter API Summary</span></span>](odbc-table-valued-parameter-api-summary.md)  
 <span data-ttu-id="d33ae-143">テーブル値パラメーターをサポートする、ODBC 関数の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-143">Lists the ODBC functions that support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="d33ae-144">ODBC テーブル値パラメーターのプログラミング例</span><span class="sxs-lookup"><span data-stu-id="d33ae-144">ODBC Table-Valued Parameter Programming Examples</span></span>](../../database-engine/dev-guide/odbc-table-valued-parameter-programming-examples.md)  
 <span data-ttu-id="d33ae-145">一般的なタスクの実行方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ae-145">Describes how to perform common tasks.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33ae-146">参照</span><span class="sxs-lookup"><span data-stu-id="d33ae-146">See Also</span></span>  
 <span data-ttu-id="d33ae-147">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="d33ae-147">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="d33ae-148">テーブル値パラメーター &#40;SQL Server Native Client&#41;</span><span class="sxs-lookup"><span data-stu-id="d33ae-148">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](../native-client/features/table-valued-parameters-sql-server-native-client.md)  
  
  
