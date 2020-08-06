---
title: 一括挿入タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.f1
helpviewer_keywords:
- Bulk Insert task
- copying data [Integration Services]
ms.assetid: c5166156-6b4c-4369-81ed-27c4ce7040ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8f0b306af7a067e4dbd46bc8df7ca689770a3ce2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633259"
---
# <a name="bulk-insert-task"></a><span data-ttu-id="ab558-102">一括挿入タスク</span><span class="sxs-lookup"><span data-stu-id="ab558-102">Bulk Insert Task</span></span>
  <span data-ttu-id="ab558-103">一括挿入タスクは、大量のデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルまたはビューにコピーするための効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="ab558-103">The Bulk Insert task provides an efficient way to copy large amounts of data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span> <span data-ttu-id="ab558-104">たとえば、会社で 100 万行の製品リストをメインフレーム システムに格納し、電子商取引システムで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して Web ページを構成しているとします。</span><span class="sxs-lookup"><span data-stu-id="ab558-104">For example, suppose your company stores its million-row product list on a mainframe system, but the company's e-commerce system uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to populate Web pages.</span></span> <span data-ttu-id="ab558-105">また、メインフレームにあるマスター製品リストを使用して、夜間に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の製品テーブルを更新する必要があるものとします。</span><span class="sxs-lookup"><span data-stu-id="ab558-105">You must update the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product table nightly with the master product list from the mainframe.</span></span> <span data-ttu-id="ab558-106">このテーブルを更新するには、製品リストをタブ区切り形式で保存し、一括挿入タスクを使用してデータを直接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ab558-106">To update the table, you save the product list in a tab-delimited format and use the Bulk Insert task to copy the data directly into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="ab558-107">高速なデータ コピーを確実に行うため、コピー元ファイルからテーブルまたはビューへのデータ移動時に、データ変換を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="ab558-107">To ensure high-speed data copying, transformations cannot be performed on the data while it is moving from the source file to the table or view.</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="ab558-108">使用に関する注意点</span><span class="sxs-lookup"><span data-stu-id="ab558-108">Usage Considerations</span></span>  
 <span data-ttu-id="ab558-109">一括挿入タスクを使用する前に、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ab558-109">Before you use the Bulk Insert task, consider the following:</span></span>  
  
-   <span data-ttu-id="ab558-110">一括挿入タスクで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはビューに転送できるのは、テキスト ファイルのデータのみです。</span><span class="sxs-lookup"><span data-stu-id="ab558-110">The Bulk Insert task can transfer data only from a text file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span> <span data-ttu-id="ab558-111">一括挿入タスクを使用して他のデータベース管理システム (DBMS) からデータを転送するには、データをコピー元からテキスト ファイルにエクスポートし、そのテキスト ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはビューにインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab558-111">To use the Bulk Insert task to transfer data from other database management systems (DBMSs), you must export the data from the source to a text file and then import the data from the text file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
-   <span data-ttu-id="ab558-112">コピー先は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのテーブルまたはビューである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab558-112">The destination must be a table or view in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="ab558-113">コピー先のテーブルまたはビューに既にデータがある場合、一括挿入タスクが実行されると新しいデータが既存のデータに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ab558-113">If the destination table or view already contains data, the new data is appended to the existing data when the Bulk Insert task runs.</span></span> <span data-ttu-id="ab558-114">データを置換する場合は、一括挿入タスクを実行する前に、DELETE または TRUNCATE ステートメントを実行する SQL 実行タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab558-114">If you want to replace the data, run an Execute SQL task that runs a DELETE or TRUNCATE statement before you run the Bulk Insert task.</span></span> <span data-ttu-id="ab558-115">詳細については、「 [SQL 実行タスク](execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab558-115">For more information, see [Execute SQL Task](execute-sql-task.md).</span></span>  
  
-   <span data-ttu-id="ab558-116">一括挿入タスク オブジェクトではフォーマット ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab558-116">You can use a format file in the Bulk Insert task object.</span></span> <span data-ttu-id="ab558-117">**bcp** ユーティリティを使用して作成したフォーマット ファイルを使用する場合、一括挿入タスクでフォーマット ファイルのパスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ab558-117">If you have a format file that was created by the **bcp** utility, you can specify its path in the Bulk Insert task.</span></span> <span data-ttu-id="ab558-118">一括挿入タスクでは、XML および XML 以外のフォーマット ファイルの両方がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ab558-118">The Bulk Insert task supports both XML and nonXML format files.</span></span> <span data-ttu-id="ab558-119">フォーマット ファイルの使用方法の詳細は、「[データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab558-119">For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ab558-120">一括挿入タスクが含まれるパッケージを実行できるのは、固定サーバー ロール sysadmin のメンバーのみです。</span><span class="sxs-lookup"><span data-stu-id="ab558-120">Only members of the sysadmin fixed server role can run a package that contains a Bulk Insert task.</span></span>  
  
## <a name="bulk-insert-task-with-transactions"></a><span data-ttu-id="ab558-121">トランザクションでの一括挿入タスク</span><span class="sxs-lookup"><span data-stu-id="ab558-121">Bulk Insert Task with Transactions</span></span>  
 <span data-ttu-id="ab558-122">バッチ サイズが設定されていないときは、一括コピー操作全体が 1 つのトランザクションとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="ab558-122">If a batch size is not set, the complete bulk copy operation is treated as one transaction.</span></span> <span data-ttu-id="ab558-123">バッチ サイズが **0** の場合は、データが 1 つのバッチに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="ab558-123">A batch size of **0** indicates that the data is inserted in one batch.</span></span> <span data-ttu-id="ab558-124">バッチ サイズが設定されているときは、各バッチはバッチの実行終了時にコミットされるトランザクションを示します。</span><span class="sxs-lookup"><span data-stu-id="ab558-124">If a batch size is set, each batch represents a transaction that is committed when the batch finishes running.</span></span>  
  
 <span data-ttu-id="ab558-125">一括挿入タスクがトランザクションに関連付けられている場合、その動作は、パッケージ トランザクションに結合されているかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ab558-125">The behavior of the Bulk Insert task, as it relates to transactions, depends on whether the task joins the package transaction.</span></span> <span data-ttu-id="ab558-126">一括挿入タスクがパッケージ トランザクションに結合する場合、エラーのない各バッチは次のバッチが実行されるまで 1 つの単位としてコミットされます。</span><span class="sxs-lookup"><span data-stu-id="ab558-126">If the Bulk Insert task does not join the package transaction, each error-free batch is committed as a unit before the next batch is tried.</span></span> <span data-ttu-id="ab558-127">一括挿入タスクがパッケージ トランザクションに結合する場合、タスクの実行終了時にエラーのないバッチはそのままトランザクション内に残ります。</span><span class="sxs-lookup"><span data-stu-id="ab558-127">If the Bulk Insert task joins the package transaction, error-free batches remain in the transaction at the conclusion of the task.</span></span> <span data-ttu-id="ab558-128">これらのバッチは、パッケージのコミットまたはロールバック操作の対象となります。</span><span class="sxs-lookup"><span data-stu-id="ab558-128">These batches are subject to the commit or rollback operation of the package.</span></span>  
  
 <span data-ttu-id="ab558-129">一括挿入タスクに失敗した場合、正しく読み込まれたバッチは自動的にロールバックされません。同様に、一括挿入タスクが成功した場合でも、これらのバッチは自動的にコミットされません。</span><span class="sxs-lookup"><span data-stu-id="ab558-129">A failure in the Bulk Insert task does not automatically roll back successfully loaded batches; similarly, if the task succeeds, batches are not automatically committed.</span></span> <span data-ttu-id="ab558-130">コミットとロールバックの各操作は、パッケージおよびワークフローのプロパティ設定で指定されている場合に限り発生します。</span><span class="sxs-lookup"><span data-stu-id="ab558-130">Commit and rollback operations occur only in response to package and workflow property settings.</span></span>  
  
## <a name="source-and-destination"></a><span data-ttu-id="ab558-131">コピー元とコピー先</span><span class="sxs-lookup"><span data-stu-id="ab558-131">Source and Destination</span></span>  
 <span data-ttu-id="ab558-132">コピー元のテキスト ファイルの場所を指定するときは、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ab558-132">When you specify the location of the text source file, consider the following:</span></span>  
  
-   <span data-ttu-id="ab558-133">サーバーには、コピー元ファイルおよびコピー先データベースの両方にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ab558-133">The server must have permission to access both the file and the destination database.</span></span>  
  
-   <span data-ttu-id="ab558-134">一括挿入タスクはサーバーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ab558-134">The server runs the Bulk Insert task.</span></span> <span data-ttu-id="ab558-135">したがって、タスクが使用するすべてのフォーマット ファイルは、そのサーバー上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab558-135">Therefore, any format file that the task uses must be located on the server.</span></span>  
  
-   <span data-ttu-id="ab558-136">一括挿入タスクが読み込むコピー元ファイルの場所は、データ挿入先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースと同じサーバー上でも、リモート サーバー上でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="ab558-136">The source file that the Bulk Insert task loads can be on the same server as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database into which data is inserted, or on a remote server.</span></span> <span data-ttu-id="ab558-137">コピー元ファイルがリモート サーバー上にある場合、汎用名前付け規則 (UNC) を使用して、ファイル名をパスで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab558-137">If the file is on a remote server, you must specify the file name using the Universal Naming Convention (UNC) name in the path.</span></span>  
  
## <a name="performance-optimization"></a><span data-ttu-id="ab558-138">パフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="ab558-138">Performance Optimization</span></span>  
 <span data-ttu-id="ab558-139">パフォーマンスを最適化するには、次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ab558-139">To optimize performance, consider the following:</span></span>  
  
-   <span data-ttu-id="ab558-140">テキスト ファイルがデータの挿入先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースと同じコンピューター上にある場合、データがネットワーク経由で転送されないため、コピー操作の実行速度がいっそう速くなります。</span><span class="sxs-lookup"><span data-stu-id="ab558-140">If the text file is located on the same computer as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database into which data is inserted, the copy operation occurs at an even faster rate because the data is not moved over the network.</span></span>  
  
-   <span data-ttu-id="ab558-141">一括挿入タスクでは、エラーが発生した行はログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="ab558-141">The Bulk Insert task does not log error-causing rows.</span></span> <span data-ttu-id="ab558-142">この情報を取得する必要がある場合は、データ フロー コンポーネントのエラー出力を使用すれば、エラーが発生した行を例外ファイルにキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="ab558-142">If you must capture this information, use the error outputs of data flow components to capture error-causing rows in an exception file.</span></span>  
  
## <a name="custom-log-entries-available-on-the-bulk-insert-task"></a><span data-ttu-id="ab558-143">一括挿入タスクで使用できるカスタム ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="ab558-143">Custom Log Entries Available on the Bulk Insert Task</span></span>  
 <span data-ttu-id="ab558-144">次の表は、一括挿入タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ab558-144">The following table lists the custom log entries for the Bulk Insert task.</span></span> <span data-ttu-id="ab558-145">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ab558-145">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="ab558-146">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="ab558-146">Log entry</span></span>|<span data-ttu-id="ab558-147">説明</span><span class="sxs-lookup"><span data-stu-id="ab558-147">Description</span></span>|  
|---------------|-----------------|  
|`BulkInsertTaskBegin`|<span data-ttu-id="ab558-148">一括挿入が開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="ab558-148">Indicates that the bulk insert began.</span></span>|  
|`BulkInsertTaskEnd`|<span data-ttu-id="ab558-149">一括挿入が終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ab558-149">Indicates that the bulk insert finished.</span></span>|  
|`BulkInsertTaskInfos`|<span data-ttu-id="ab558-150">タスクに関する説明情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab558-150">Provides descriptive information about the task.</span></span>|  
  
## <a name="bulk-insert-task-configuration"></a><span data-ttu-id="ab558-151">一括挿入タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ab558-151">Bulk Insert Task Configuration</span></span>  
 <span data-ttu-id="ab558-152">一括挿入タスクは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="ab558-152">You can configure the Bulk Insert task in the following ways:</span></span>  
  
-   <span data-ttu-id="ab558-153">コピー先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース、およびデータを挿入するテーブルまたはビューに接続する OLE DB 接続マネージャーを指定します。</span><span class="sxs-lookup"><span data-stu-id="ab558-153">Specify the OLE DB connection manager to connect to the destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and the table or view into which data is inserted.</span></span> <span data-ttu-id="ab558-154">一括挿入タスクでは、コピー先データベースに対して OLE DB 接続のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="ab558-154">The Bulk Insert task supports only OLE DB connections for the destination database.</span></span>  
  
-   <span data-ttu-id="ab558-155">ファイルまたはフラット ファイル接続マネージャーを指定して、コピー元ファイルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ab558-155">Specify the File or Flat File connection manager to access the source file.</span></span> <span data-ttu-id="ab558-156">一括挿入タスクは、コピー元ファイルの場所にのみ接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab558-156">The Bulk Insert task uses the connection manager only for the location of the source file.</span></span> <span data-ttu-id="ab558-157">接続マネージャー エディターでその他のオプションを選択しても、一括挿入タスクでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="ab558-157">The task ignores other options that you select in the connection manager editor.</span></span>  
  
-   <span data-ttu-id="ab558-158">フォーマット ファイルを使用するか、またはコピー元データの列区切り記号と行区切り記号を定義して、一括挿入タスクで使用するフォーマットを定義します。</span><span class="sxs-lookup"><span data-stu-id="ab558-158">Define the format that is used by the Bulk Insert task, either by using a format file or by defining the column and row delimiters of the source data.</span></span> <span data-ttu-id="ab558-159">フォーマット ファイルを使用する場合は、フォーマット ファイルにアクセスするファイル接続マネージャーを指定します。</span><span class="sxs-lookup"><span data-stu-id="ab558-159">If using a format file, specify the File connection manager to access the format file.</span></span>  
  
-   <span data-ttu-id="ab558-160">タスクでデータを挿入する場合、挿入先のテーブルまたはビューで実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ab558-160">Specify actions to perform on the destination table or view when the task inserts the data.</span></span> <span data-ttu-id="ab558-161">オプションとして、CHECK 制約の有効化、ID 挿入の許可、NULL の保持、トリガーの起動、またはテーブルのロックを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ab558-161">The options include whether to check constraints, enable identity inserts, keep nulls, fire triggers, or lock the table.</span></span>  
  
-   <span data-ttu-id="ab558-162">挿入するデータのバッチに関する情報を設定します。たとえば、バッチ サイズ、挿入するファイルの先頭行と最終行、行の挿入を停止せずにタスクを実行できる挿入エラーの最大数、並べ替えの対象となる列の名前などです。</span><span class="sxs-lookup"><span data-stu-id="ab558-162">Provide information about the batch of data to insert, such as the batch size, the first and last row from the file to insert, the number of insert errors that can occur before the task stops inserting rows, and the names of the columns that will be sorted.</span></span>  
  
 <span data-ttu-id="ab558-163">一括挿入タスクでフラット ファイル接続マネージャーを使用してコピー元ファイルにアクセスする場合、タスクはフラット ファイル接続マネージャーで指定されたフォーマットを使用しません。</span><span class="sxs-lookup"><span data-stu-id="ab558-163">If the Bulk Insert task uses a Flat File connection manager to access the source file, the task does not use the format specified in the Flat File connection manager.</span></span> <span data-ttu-id="ab558-164">その代わり、フォーマット ファイルに指定されたフォーマットか、またはタスクの RowDelimiter プロパティおよび ColumnDelimiter プロパティの値が一括挿入タスクで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ab558-164">Instead, the Bulk Insert task uses either the format specified in a format file, or the values of the RowDelimiter and ColumnDelimiter properties of the task.</span></span>  
  
 <span data-ttu-id="ab558-165">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="ab558-165">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ab558-166">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab558-166">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="ab558-167">[一括挿入タスク エディター &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="ab558-167">[Bulk Insert Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="ab558-168">[一括挿入タスク エディター &#40;[接続] ページ&#41;](../bulk-insert-task-editor-connection-page.md)</span><span class="sxs-lookup"><span data-stu-id="ab558-168">[Bulk Insert Task Editor &#40;Connection Page&#41;](../bulk-insert-task-editor-connection-page.md)</span></span>  
  
-   <span data-ttu-id="ab558-169">[一括挿入タスク エディター &#40;[オプション] ページ&#41;](../bulk-insert-task-editor-options-page.md)</span><span class="sxs-lookup"><span data-stu-id="ab558-169">[Bulk Insert Task Editor &#40;Options Page&#41;](../bulk-insert-task-editor-options-page.md)</span></span>  
  
-   <span data-ttu-id="ab558-170">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="ab558-170">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="ab558-171">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab558-171">For more information about how to setthese properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="ab558-172">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="ab558-172">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="programmatic-configuration-of-the-bulk-insert-task"></a><span data-ttu-id="ab558-173">プログラムによる一括挿入タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ab558-173">Programmatic Configuration of the Bulk Insert Task</span></span>  
 <span data-ttu-id="ab558-174">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab558-174">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="ab558-175">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ab558-175">Related Tasks</span></span>  
 [<span data-ttu-id="ab558-176">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="ab558-176">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="ab558-177">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ab558-177">Related Content</span></span>  
  
-   <span data-ttu-id="ab558-178">support.microsoft.com の技術記事: [UAC 対応システムで "データを挿入するための SSIS 一括挿入を準備できません" というエラーが発生することがある](https://go.microsoft.com/fwlink/?LinkId=233693)</span><span class="sxs-lookup"><span data-stu-id="ab558-178">Technical article, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=233693), on support.microsoft.com.</span></span>  
  
-   <span data-ttu-id="ab558-179">msdn.microsoft.com の技術記事: [Integration Services のパフォーマンス チューニング技法](https://go.microsoft.com/fwlink/?LinkId=233700)</span><span class="sxs-lookup"><span data-stu-id="ab558-179">Technical article, [The Data Loading Performance Guide](https://go.microsoft.com/fwlink/?LinkId=233700), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="ab558-180">simple-talk.com の技術記事: [SQL Server Integration Services を使用してデータの一括読み込みを行う](https://go.microsoft.com/fwlink/?LinkId=233701)</span><span class="sxs-lookup"><span data-stu-id="ab558-180">Technical article, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), on simple-talk.com.</span></span>  
  
  
