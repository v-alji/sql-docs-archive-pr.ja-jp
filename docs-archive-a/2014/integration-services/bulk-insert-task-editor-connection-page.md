---
title: '[一括挿入タスクエディター] ([接続] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2cd722fd8520ff011c0d57040a55d624178e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738658"
---
# <a name="bulk-insert-task-editor-connection-page"></a><span data-ttu-id="7db10-102">[一括挿入タスク エディター] ([接続] ページ)</span><span class="sxs-lookup"><span data-stu-id="7db10-102">Bulk Insert Task Editor (Connection Page)</span></span>
  <span data-ttu-id="7db10-103">**[一括挿入タスク エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、一括挿入操作の挿入元と挿入先、および使用するフォーマットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7db10-103">Use the **Connection** page of the **Bulk Insert Task Editor** dialog box to specify the source and destination of the bulk insert operation and the format to use.</span></span>  
  
 <span data-ttu-id="7db10-104">一括挿入操作の詳細については、「[Bulk Insert Task](control-flow/bulk-insert-task.md)」(一括挿入タスク) と「[データのインポートまたはエクスポート用のフォーマット ファイル (SQL Server)](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7db10-104">To learn about working with bulk inserts, see [Bulk Insert Task](control-flow/bulk-insert-task.md) and [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7db10-105">Options</span><span class="sxs-lookup"><span data-stu-id="7db10-105">Options</span></span>  
 <span data-ttu-id="7db10-106">**接続**</span><span class="sxs-lookup"><span data-stu-id="7db10-106">**Connection**</span></span>  
 <span data-ttu-id="7db10-107">OLE DB 接続マネージャーを一覧から選択するか、[\<**New connection...**>] をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7db10-107">Select an OLE DB connection manager in the list, or click \<**New connection...**> to create a new connection.</span></span>  
  
 <span data-ttu-id="7db10-108">**関連トピック:** [OLE DB 接続マネージャー](connection-manager/ole-db-connection-manager.md)、 [OLE DB 接続マネージャーの構成](../../2014/integration-services/configure-ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="7db10-108">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [Configure OLE DB Connection Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="7db10-109">**[DestinationTable]**</span><span class="sxs-lookup"><span data-stu-id="7db10-109">**DestinationTable**</span></span>  
 <span data-ttu-id="7db10-110">挿入先のテーブルまたはビューの名前を入力するか、テーブルまたはビューを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="7db10-110">Type the name of the destination table or view or select a table or view in the list.</span></span>  
  
 <span data-ttu-id="7db10-111">**形式**</span><span class="sxs-lookup"><span data-stu-id="7db10-111">**Format**</span></span>  
 <span data-ttu-id="7db10-112">一括挿入のフォーマットの挿入元を選択します。</span><span class="sxs-lookup"><span data-stu-id="7db10-112">Select the source of the format for the bulk insert.</span></span> <span data-ttu-id="7db10-113">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7db10-113">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="7db10-114">値</span><span class="sxs-lookup"><span data-stu-id="7db10-114">Value</span></span>|<span data-ttu-id="7db10-115">説明</span><span class="sxs-lookup"><span data-stu-id="7db10-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7db10-116">**[ファイルを使用]**</span><span class="sxs-lookup"><span data-stu-id="7db10-116">**Use File**</span></span>|<span data-ttu-id="7db10-117">フォーマット指定が格納されているファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7db10-117">Select a file containing the format specification.</span></span> <span data-ttu-id="7db10-118">このオプションを選択すると、動的オプションの **[FormatFile]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7db10-118">Selecting this option displays the dynamic option, **FormatFile**.</span></span>|  
|<span data-ttu-id="7db10-119">**[指定]**</span><span class="sxs-lookup"><span data-stu-id="7db10-119">**Specify**</span></span>|<span data-ttu-id="7db10-120">フォーマットを指定します。</span><span class="sxs-lookup"><span data-stu-id="7db10-120">Specify the format.</span></span> <span data-ttu-id="7db10-121">このオプションを選択すると、動的オプションとが表示され `RowDelimiter` `ColumnDelimiter` ます。</span><span class="sxs-lookup"><span data-stu-id="7db10-121">Selecting this option displays the dynamic options, `RowDelimiter` and `ColumnDelimiter`.</span></span>|  
  
 <span data-ttu-id="7db10-122">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="7db10-122">**File**</span></span>  
 <span data-ttu-id="7db10-123">ファイル接続マネージャーまたはフラット ファイル接続マネージャーを一覧から選択するか、[\<**New connection...**>] をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7db10-123">Select a File or Flat File connection manager in the list, or click \<**New connection...**> to create a new connection.</span></span>  
  
 <span data-ttu-id="7db10-124">このファイルの場所は、このタスクの接続マネージャーに指定されている SQL Server データベース エンジンを基準とする相対パスです。</span><span class="sxs-lookup"><span data-stu-id="7db10-124">The file location is relative to the SQL Server Database Engine specified in the connection manager for this task.</span></span> <span data-ttu-id="7db10-125">SQL Server データベース エンジンは、サーバーのローカル ハード ドライブ、共有、または SQL Server にマップされたドライブでこのテキスト ファイルにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7db10-125">The text file must be accessible by the SQL Server Database Engine either on a local hard drive on the server, or via a share or mapped drive to the SQL Server.</span></span> <span data-ttu-id="7db10-126">SSIS ランタイムはこのファイルにアクセスしません。</span><span class="sxs-lookup"><span data-stu-id="7db10-126">The file is not accessed by the SSIS Runtime.</span></span>  
  
 <span data-ttu-id="7db10-127">フラット ファイル接続マネージャーを使用してソース ファイルにアクセスした場合、フラット ファイル接続マネージャーに指定されたフォーマットは一括挿入タスクで使用されません。</span><span class="sxs-lookup"><span data-stu-id="7db10-127">If you access the source file by using a Flat File connection manager, the Bulk Insert task does not use the format specified in the Flat File connection manager.</span></span> <span data-ttu-id="7db10-128">その代わり、フォーマット ファイルに指定されたフォーマットか、またはタスクの RowDelimiter プロパティおよび ColumnDelimiter プロパティの値が一括挿入タスクで使用されます。</span><span class="sxs-lookup"><span data-stu-id="7db10-128">Instead, the Bulk Insert task uses either the format specified in a format file or the values of the RowDelimiter and ColumnDelimiter properties of the task.</span></span>  
  
 <span data-ttu-id="7db10-129">**関連トピック: 「** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)」、「[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)」、「[フラット ファイル接続マネージャー](connection-manager/flat-file-connection-manager.md)」、「[フラット ファイル接続マネージャー エディター ([全般] ページ)](general-page-of-integration-services-designers-options.md)」、「[フラット ファイル接続マネージャー エディター ([列] ページ)](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)」、「[フラット ファイル接続マネージャー エディター ([詳細設定] ページ)](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)」</span><span class="sxs-lookup"><span data-stu-id="7db10-129">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md), [Flat File Connection Manager](connection-manager/flat-file-connection-manager.md), [Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md), [Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="7db10-130">**[テーブルの更新]**</span><span class="sxs-lookup"><span data-stu-id="7db10-130">**Refresh Tables**</span></span>  
 <span data-ttu-id="7db10-131">データベースおよびビューの一覧を更新します。</span><span class="sxs-lookup"><span data-stu-id="7db10-131">Refresh the list of tables and views.</span></span>  
  
## <a name="format-dynamic-options"></a><span data-ttu-id="7db10-132">[Format] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="7db10-132">Format Dynamic Options</span></span>  
  
### <a name="format--use-file"></a><span data-ttu-id="7db10-133">[Format] = [ファイルを使用]</span><span class="sxs-lookup"><span data-stu-id="7db10-133">Format = Use File</span></span>  
 <span data-ttu-id="7db10-134">**[FormatFile]**</span><span class="sxs-lookup"><span data-stu-id="7db10-134">**FormatFile**</span></span>  
 <span data-ttu-id="7db10-135">フォーマット ファイルのパスを入力します。または、参照ボタン **[...]** をクリックし、フォーマット ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7db10-135">Type the path of the format file or click the ellipsis button **(...)** to locate the format file.</span></span>  
  
### <a name="format--specify"></a><span data-ttu-id="7db10-136">[Format] = [指定]</span><span class="sxs-lookup"><span data-stu-id="7db10-136">Format = Specify</span></span>  
 `RowDelimiter`  
 <span data-ttu-id="7db10-137">ソース ファイルの行区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="7db10-137">Specify the row delimiter in the source file.</span></span> <span data-ttu-id="7db10-138">既定値は **{CR}{LF}** です。</span><span class="sxs-lookup"><span data-stu-id="7db10-138">The default value is **{CR}{LF}**.</span></span>  
  
 `ColumnDelimiter`  
 <span data-ttu-id="7db10-139">ソース ファイルの列区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="7db10-139">Specify the column delimiter in the source file.</span></span> <span data-ttu-id="7db10-140">既定値は **[タブ]** です。</span><span class="sxs-lookup"><span data-stu-id="7db10-140">The default is **Tab**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db10-141">参照</span><span class="sxs-lookup"><span data-stu-id="7db10-141">See Also</span></span>  
 <span data-ttu-id="7db10-142">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7db10-142">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="7db10-143">[一括挿入タスクエディター &#40;[全般] ページ&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md) </span><span class="sxs-lookup"><span data-stu-id="7db10-143">[Bulk Insert Task Editor &#40;General Page&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md) </span></span>  
 <span data-ttu-id="7db10-144">[一括挿入タスクエディター &#40;オプションページ&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="7db10-144">[Bulk Insert Task Editor &#40;Options Page&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md) </span></span>  
 <span data-ttu-id="7db10-145">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="7db10-145">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="7db10-146">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7db10-146">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="7db10-147">制御フロー</span><span class="sxs-lookup"><span data-stu-id="7db10-147">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
