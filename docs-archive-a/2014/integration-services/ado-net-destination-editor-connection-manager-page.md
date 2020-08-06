---
title: '[ADO NET 変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.connection.f1
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78851d5bbad18d2d1076eaa87200dd73e6962a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631209"
---
# <a name="ado-net-destination-editor-connection-manager-page"></a><span data-ttu-id="55278-102">[ADO NET 変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="55278-102">ADO NET Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="55278-103">**[ADO NET 変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、変換先の [!INCLUDE[vstecado](../includes/vstecado-md.md)] 接続を選択できます。</span><span class="sxs-lookup"><span data-stu-id="55278-103">Use the **Connection Manager** page of the **ADO NET Destination Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection for the destination.</span></span> <span data-ttu-id="55278-104">さらにこのページを使用して、データベースのテーブルやビューを選択できます。</span><span class="sxs-lookup"><span data-stu-id="55278-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="55278-105">ADO NET 変換先の詳細については、「 [ADO NET Destination](data-flow/ado-net-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55278-105">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="55278-106">**[接続マネージャー] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="55278-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="55278-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換先を含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="55278-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="55278-108">**[データ フロー]** タブで、ADO NET 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="55278-108">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="55278-109">**[ADO NET 変換先エディター]** で、 **[接続マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55278-109">In the **ADO NET Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="55278-110">静的オプション</span><span class="sxs-lookup"><span data-stu-id="55278-110">Static Options</span></span>  
 <span data-ttu-id="55278-111">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="55278-111">**Connection manager**</span></span>  
 <span data-ttu-id="55278-112">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="55278-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="55278-113">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="55278-113">**New**</span></span>  
 <span data-ttu-id="55278-114">**[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="55278-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="55278-115">**[テーブルまたはビューを使用する]**</span><span class="sxs-lookup"><span data-stu-id="55278-115">**Use a table or view**</span></span>  
 <span data-ttu-id="55278-116">既存のテーブルまたはビューを一覧から選択するか、 **[新規作成]** をクリックして新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="55278-116">Select an existing table or view from the list, or create a new table by clicking **New**..</span></span>  
  
 <span data-ttu-id="55278-117">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="55278-117">**New**</span></span>  
 <span data-ttu-id="55278-118">**[テーブルの作成]** ダイアログ ボックスを使用して、新しいテーブルまたはビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="55278-118">Create a new table or view by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55278-119">**[新規作成]** をクリックすると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="55278-119">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="55278-120">基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。</span><span class="sxs-lookup"><span data-stu-id="55278-120">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="55278-121">FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。</span><span class="sxs-lookup"><span data-stu-id="55278-121">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="55278-122">次に、 **[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="55278-122">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="55278-123">詳細については、「[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55278-123">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="55278-124">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="55278-124">**Preview**</span></span>  
 <span data-ttu-id="55278-125">**[クエリ結果のプレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="55278-125">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="55278-126">プレビューでは、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="55278-126">Preview can display up to 200 rows.</span></span>  
  
 <span data-ttu-id="55278-127">**[使用可能な場合は一括挿入を使用する]**</span><span class="sxs-lookup"><span data-stu-id="55278-127">**Use bulk insert when available**</span></span>  
 <span data-ttu-id="55278-128">一括挿入操作のパフォーマンスを向上させるために <xref:System.Data.SqlClient.SqlBulkCopy> インターフェイスを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="55278-128">Specify whether to use the <xref:System.Data.SqlClient.SqlBulkCopy> interface to improve the performance of bulk insert operations.</span></span>  
  
 <span data-ttu-id="55278-129"><xref:System.Data.SqlClient.SqlConnection> オブジェクトを返す ADO.NET プロバイダーのみが <xref:System.Data.SqlClient.SqlBulkCopy> インターフェイスの使用をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="55278-129">Only ADO.NET providers that return a <xref:System.Data.SqlClient.SqlConnection> object support the use of the <xref:System.Data.SqlClient.SqlBulkCopy> interface.</span></span> <span data-ttu-id="55278-130">.NET Data Provider for SQL Server (SqlClient) は <xref:System.Data.SqlClient.SqlConnection> オブジェクトを返し、カスタム プロバイダーは <xref:System.Data.SqlClient.SqlConnection> オブジェクトを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55278-130">The .NET Data Provider for SQL Server (SqlClient) returns a <xref:System.Data.SqlClient.SqlConnection> object, and a custom provider may return a <xref:System.Data.SqlClient.SqlConnection> object.</span></span>  
  
 <span data-ttu-id="55278-131">.NET Data Provider for SQL Server (SqlClient) を使用して [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]に接続できます。</span><span class="sxs-lookup"><span data-stu-id="55278-131">You can use the .NET Data Provider for SQL Server (SqlClient) to connect to [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span></span>  
  
 <span data-ttu-id="55278-132">**[使用可能な場合は一括挿入を使用する]** を選択し、 **[エラー]** オプションを **[行をリダイレクトする]** に設定した場合、変換先によってエラー出力にリダイレクトされるデータのバッチに問題のない行が含まれる可能性があります。一括操作でのエラー処理の詳細については、「 [データのエラー処理](data-flow/error-handling-in-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55278-132">If you select **Use bulk insert when available**, and set the **Error** option to **Redirect the row**, the batch of data that the destination redirects to the error output may include good rows.For more information about handling errors in bulk operations, see [Error Handling in Data](data-flow/error-handling-in-data.md).</span></span> <span data-ttu-id="55278-133">**[エラー]** オプションの詳細については、「[[ADO NET 変換先エディター] &#40;[エラー出力] ページ&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55278-133">For more information about the **Error** option, see [ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55278-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] または Sybase のソース テーブルに ID 列が含まれている場合は、ADO NET 変換先の前と後に SQL 実行タスクを使用して SET IDENTITY_INSERT ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55278-134">If a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or Sybase source table includes an identity column, you must use Execute SQL tasks to run a SET IDENTITY_INSERT statement before and after the ADO NET destination.</span></span> <span data-ttu-id="55278-135">ID 列プロパティは、列の増分値を指定します。</span><span class="sxs-lookup"><span data-stu-id="55278-135">The identity column property specifies an incremental value for the column.</span></span> <span data-ttu-id="55278-136">SET IDENTITY_INSERT ステートメントを使用することで、ID 列に明示的な値を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="55278-136">The SET IDENTITY_INSERT statement enables explicit values to be inserted into the identity column.</span></span> <span data-ttu-id="55278-137">同じデータベース接続で CREATE TABLE ステートメントと SET IDENTITY ステートメントを実行するには、[!INCLUDE[vstecado](../includes/vstecado-md.md)] 接続マネージャーの `RetainSameConnection` プロパティを `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="55278-137">To run the CREATE TABLE and SET IDENTITY statements on the same database connection, set the `RetainSameConnection` property of the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager to `True`.</span></span> <span data-ttu-id="55278-138">また、SQL 実行タスクと ADO NET 変換先に同じ [!INCLUDE[vstecado](../includes/vstecado-md.md)] 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="55278-138">Also, use the same [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the Execute SQL tasks and the ADO NET destination.</span></span>  
>   
>  <span data-ttu-id="55278-139">詳細については、「[SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql)」および「[IDENTITY &#40;プロパティ&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55278-139">For more information, see [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) and [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="55278-140">外部リソース</span><span class="sxs-lookup"><span data-stu-id="55278-140">External Resources</span></span>  
 <span data-ttu-id="55278-141">sqlcat.com の技術記事「[Azure SQL Database へのデータの高速な読み込み](https://go.microsoft.com/fwlink/?LinkId=244333)」</span><span class="sxs-lookup"><span data-stu-id="55278-141">Technical article, [Loading data to Azure SQL Database the fast way](https://go.microsoft.com/fwlink/?LinkId=244333), on sqlcat.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55278-142">参照</span><span class="sxs-lookup"><span data-stu-id="55278-142">See Also</span></span>  
 <span data-ttu-id="55278-143">[[ADO NET 変換先エディター &#40;マッピング] ページ&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="55278-143">[ADO NET Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="55278-144">[[ADO NET 変換先エディター] &#40;エラー出力ページ&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="55278-144">[ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="55278-145">[ADO.NET 接続マネージャー](connection-manager/ado-net-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="55278-145">[ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md) </span></span>  
 [<span data-ttu-id="55278-146">SQL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="55278-146">Execute SQL Task</span></span>](control-flow/execute-sql-task.md)  
  
  
