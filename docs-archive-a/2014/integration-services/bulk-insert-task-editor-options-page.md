---
title: '[一括挿入タスクエディター] ([オプション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.options.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1751d1e0ac01d5459a8c76e6a48626c2ad6deafd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738641"
---
# <a name="bulk-insert-task-editor-options-page"></a><span data-ttu-id="92f50-102">[一括挿入タスク エディター] ([オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="92f50-102">Bulk Insert Task Editor (Options Page)</span></span>
  <span data-ttu-id="92f50-103">**[一括挿入タスク エディター]** ダイアログ ボックスの **[オプション]** ページを使用すると、一括挿入操作のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="92f50-103">Use the **Options** page of the **Bulk Insert Task Editor** dialog box to set properties for the bulk insert operation.</span></span> <span data-ttu-id="92f50-104">一括挿入タスクにより、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のテーブルまたはビューに大量のデータがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="92f50-104">The Bulk Insert task copies large amounts of data into a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 <span data-ttu-id="92f50-105">一括挿入タスクについては、「[一括挿入タスク](control-flow/bulk-insert-task.md)」および「[「BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92f50-105">To learn about working with bulk inserts, see [Bulk Insert Task](control-flow/bulk-insert-task.md) and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="92f50-106">Options</span><span class="sxs-lookup"><span data-stu-id="92f50-106">Options</span></span>  
 <span data-ttu-id="92f50-107">**CodePage**</span><span class="sxs-lookup"><span data-stu-id="92f50-107">**CodePage**</span></span>  
 <span data-ttu-id="92f50-108">データ ファイル内のデータのコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="92f50-108">Specify the code page of the data in the data file.</span></span>  
  
 <span data-ttu-id="92f50-109">**[DataFileType]**</span><span class="sxs-lookup"><span data-stu-id="92f50-109">**DataFileType**</span></span>  
 <span data-ttu-id="92f50-110">読み込み操作で使用するデータ型の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="92f50-110">Specify the data-type value to use in the load operation.</span></span>  
  
 <span data-ttu-id="92f50-111">**BatchSize**</span><span class="sxs-lookup"><span data-stu-id="92f50-111">**BatchSize**</span></span>  
 <span data-ttu-id="92f50-112">バッチ内の行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92f50-112">Specify the number of rows in a batch.</span></span> <span data-ttu-id="92f50-113">既定では、データ ファイル全体です。</span><span class="sxs-lookup"><span data-stu-id="92f50-113">The default is the entire data file.</span></span> <span data-ttu-id="92f50-114">**[BatchSize]** を 0 に設定すると、データは単一のバッチに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="92f50-114">If you set **BatchSize** to zero, the data is loaded in a single batch.</span></span>  
  
 <span data-ttu-id="92f50-115">**[LastRow]**</span><span class="sxs-lookup"><span data-stu-id="92f50-115">**LastRow**</span></span>  
 <span data-ttu-id="92f50-116">コピーする最後の行を指定します。</span><span class="sxs-lookup"><span data-stu-id="92f50-116">Specify the last row to copy.</span></span>  
  
 <span data-ttu-id="92f50-117">**[FirstRow]**</span><span class="sxs-lookup"><span data-stu-id="92f50-117">**FirstRow**</span></span>  
 <span data-ttu-id="92f50-118">コピーを開始する最初の行を指定します。</span><span class="sxs-lookup"><span data-stu-id="92f50-118">Specify the first row from which to start copying.</span></span>  
  
 <span data-ttu-id="92f50-119">**[オプション]**</span><span class="sxs-lookup"><span data-stu-id="92f50-119">**Options**</span></span>  
 |<span data-ttu-id="92f50-120">期間</span><span class="sxs-lookup"><span data-stu-id="92f50-120">Term</span></span>|<span data-ttu-id="92f50-121">定義</span><span class="sxs-lookup"><span data-stu-id="92f50-121">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="92f50-122">**CHECK 制約**</span><span class="sxs-lookup"><span data-stu-id="92f50-122">**Check constraints**</span></span>|<span data-ttu-id="92f50-123">テーブルおよび列に対する制約をチェックします。</span><span class="sxs-lookup"><span data-stu-id="92f50-123">Select to check the table and column constraints.</span></span>|  
|<span data-ttu-id="92f50-124">**[NULL を保持する]**</span><span class="sxs-lookup"><span data-stu-id="92f50-124">**Keep nulls**</span></span>|<span data-ttu-id="92f50-125">空の列に任意の既定値を挿入する代わりに、一括挿入操作中に NULL 値を保持します。</span><span class="sxs-lookup"><span data-stu-id="92f50-125">Select to retain null values during the bulk insert operation, instead of inserting any default values for empty columns.</span></span>|  
|<span data-ttu-id="92f50-126">**ID 挿入を許可する**</span><span class="sxs-lookup"><span data-stu-id="92f50-126">**Enable identity insert**</span></span>|<span data-ttu-id="92f50-127">ID 列に既存の値を挿入します。</span><span class="sxs-lookup"><span data-stu-id="92f50-127">Select to insert existing values into an identity column.</span></span>|  
|<span data-ttu-id="92f50-128">**[テーブル ロック]**</span><span class="sxs-lookup"><span data-stu-id="92f50-128">**Table lock**</span></span>|<span data-ttu-id="92f50-129">一括挿入中にテーブルをロックします。</span><span class="sxs-lookup"><span data-stu-id="92f50-129">Select to lock the table during the bulk insert.</span></span>|  
|<span data-ttu-id="92f50-130">**[トリガーを起動する]**</span><span class="sxs-lookup"><span data-stu-id="92f50-130">**Fire triggers**</span></span>|<span data-ttu-id="92f50-131">テーブル上のすべての挿入トリガー、更新トリガー、および削除トリガーを起動します。</span><span class="sxs-lookup"><span data-stu-id="92f50-131">Select to fire any insert, update, or delete triggers on the table.</span></span>|  
  
 <span data-ttu-id="92f50-132">**SortedData**</span><span class="sxs-lookup"><span data-stu-id="92f50-132">**SortedData**</span></span>  
 <span data-ttu-id="92f50-133">一括挿入ステートメントに ORDER BY 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="92f50-133">Specify the ORDER BY clause in the bulk insert statement.</span></span> <span data-ttu-id="92f50-134">指定する列名は、挿入先テーブル内の有効な列でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="92f50-134">The column name that you supply must be a valid column in the destination table.</span></span> <span data-ttu-id="92f50-135">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="92f50-135">The default is `false`.</span></span> <span data-ttu-id="92f50-136">これは、データが ORDER BY 句によって並べ替えられないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="92f50-136">This means that the data is not sorted by an ORDER BY clause.</span></span>  
  
 <span data-ttu-id="92f50-137">**[MaxErrors]**</span><span class="sxs-lookup"><span data-stu-id="92f50-137">**MaxErrors**</span></span>  
 <span data-ttu-id="92f50-138">一括挿入操作が取り消されるまでに発生が許可される最大エラー数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92f50-138">Specify the maximum number of errors that can occur before the bulk insert operation is canceled.</span></span> <span data-ttu-id="92f50-139">0 の値は、許可されるエラー数が無制限であることを示します。</span><span class="sxs-lookup"><span data-stu-id="92f50-139">A value of 0 indicates that an infinite number of errors are allowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92f50-140">一括読み込み操作でインポートできない行は、1 つのエラーとしてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="92f50-140">Each row that cannot be imported by the bulk load operation is counted as one error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f50-141">参照</span><span class="sxs-lookup"><span data-stu-id="92f50-141">See Also</span></span>  
 <span data-ttu-id="92f50-142">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="92f50-142">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="92f50-143">[一括挿入タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="92f50-143">[Bulk Insert Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="92f50-144">[[一括挿入タスクエディター] &#40;接続ページ&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="92f50-144">[Bulk Insert Task Editor &#40;Connection Page&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md) </span></span>  
 <span data-ttu-id="92f50-145">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="92f50-145">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="92f50-146">制御フロー</span><span class="sxs-lookup"><span data-stu-id="92f50-146">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
