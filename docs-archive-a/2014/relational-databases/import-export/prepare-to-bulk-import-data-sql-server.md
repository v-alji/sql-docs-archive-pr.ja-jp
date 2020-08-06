---
title: データの一括インポートの準備 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], about bulk importing
- BULK INSERT statement, guidelines
- BULK INSERT statement, restrictions
- bcp utility [SQL Server], guidelines
- bcp utility [SQL Server], restrictions
- hidden characters
- OPENROWSET function, BCP guidelines
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 03d45d9c79082b255e9b8b0e4804c50855a3ad7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741046"
---
# <a name="prepare-to-bulk-import-data-sql-server"></a><span data-ttu-id="45b60-102">データの一括インポートの準備 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="45b60-102">Prepare to Bulk Import Data (SQL Server)</span></span>
  <span data-ttu-id="45b60-103">データ ファイルのみからデータを一括インポートするには、 **bcp** コマンド、BULK INSERT ステートメント、または OPENROWSET(BULK) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="45b60-103">You can use the **bcp** command, BULK INSERT statement, or OPENROWSET(BULK) function to bulk import data from a data file only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45b60-104">テキスト ファイル以外のオブジェクトからデータを一括インポートするカスタム アプリケーションを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="45b60-104">It is possible to write a custom application that bulk imports data from objects other than a text file.</span></span> <span data-ttu-id="45b60-105">メモリ バッファーからデータを一括インポートするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC) アプリケーション プログラミング インターフェイス (API) または OLE DB **IRowsetFastLoad** インターフェイスのいずれかの bcp 拡張機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="45b60-105">To bulk import data from memory buffers, use either the bcp extensions to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC) application programming interface (API) or the OLE DB **IRowsetFastLoad** interface.</span></span>  <span data-ttu-id="45b60-106">C# のデータ テーブルからデータを一括インポートするには、ADO.NET 一括コピー API ( **SqlBulkCopy**) を使用します。</span><span class="sxs-lookup"><span data-stu-id="45b60-106">To bulk import data from a C# data table, use the ADO.NET bulk-copy API, **SqlBulkCopy**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45b60-107">リモート テーブルへのデータの一括インポートはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="45b60-107">Bulk importing data into a remote table is not supported.</span></span>  
  
 <span data-ttu-id="45b60-108">データ ファイルから [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータを一括インポートするときは、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="45b60-108">Use the following guidelines when you bulk import data from a data file to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="45b60-109">使用しているユーザー アカウントに必要な権限を取得する。</span><span class="sxs-lookup"><span data-stu-id="45b60-109">Obtain required permissions for your user account.</span></span>  
  
     <span data-ttu-id="45b60-110">**bcp** ユーティリティ、BULK INSERT ステートメント、INSERT ...SELECT \* FROM OPENROWSET(BULK...) ステートメントのいずれかで使用するユーザー アカウントには、テーブル操作に必要な権限がテーブルの所有者によって割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="45b60-110">The user account in which you use the **bcp** utility, the BULK INSERT statement, or the INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement must have the required permissions on the table, which are assigned by the table owner.</span></span> <span data-ttu-id="45b60-111">各方法に必要な権限の詳細については、「 [bcp ユーティリティ](../../tools/bcp-utility.md)」、「 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)」、および「 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)) を使用します。</span><span class="sxs-lookup"><span data-stu-id="45b60-111">For more information about permissions that are required by each method, see [bcp Utility](../../tools/bcp-utility.md), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
-   <span data-ttu-id="45b60-112">一括ログ復旧モデルを使用する。</span><span class="sxs-lookup"><span data-stu-id="45b60-112">Use the bulk-logged recovery model.</span></span>  
  
     <span data-ttu-id="45b60-113">このガイドラインは、完全復旧モデルを使用するデータベースに関するものです。</span><span class="sxs-lookup"><span data-stu-id="45b60-113">This guideline is for a database that uses the full recovery model.</span></span> <span data-ttu-id="45b60-114">一括ログ復旧モデルは、インデックスなしテーブル ( *ヒープ*) に対して一括操作を実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="45b60-114">The bulk-logged recovery model is useful when performing bulk operations into an unindexed table (a *heap*).</span></span> <span data-ttu-id="45b60-115">一括ログ復旧では行の挿入がログに記録されないため、一括ログ復旧モデルを使用することで、トランザクション ログの領域が不足する状況を回避できます。</span><span class="sxs-lookup"><span data-stu-id="45b60-115">Using bulk-logged recovery helps prevent the transaction log from running out of space because bulk-logged recovery does not perform log row inserts.</span></span> <span data-ttu-id="45b60-116">一括ログ復旧モデルの詳細については、「[復旧モデル &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45b60-116">For more information about the bulk-logged recovery model, see [Recovery Models &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md).</span></span>  
  
     <span data-ttu-id="45b60-117">一括インポート操作の直前に一括ログ復旧モデルが使用されるようにデータベースを変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="45b60-117">We recommend that you change the database to use the bulk-logged recovery model immediately before the bulk import operation.</span></span> <span data-ttu-id="45b60-118">一括インポート操作が終了したらすぐに、データベースを完全復旧モデルに戻します。</span><span class="sxs-lookup"><span data-stu-id="45b60-118">Immediately afterwards, you should reset the database to the full recovery model.</span></span> <span data-ttu-id="45b60-119">詳細については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45b60-119">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45b60-120">一括インポート操作時のログ記録を最小限にする方法の詳細については、「 [一括インポートで最小ログ記録を行うための前提条件](prerequisites-for-minimal-logging-in-bulk-import.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45b60-120">more information about how to minimize logging during bulk import operations, see [Prerequisites for Minimal Logging in Bulk Import](prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
-   <span data-ttu-id="45b60-121">データの一括インポート後にバックアップを行う。</span><span class="sxs-lookup"><span data-stu-id="45b60-121">Back up after bulk importing data.</span></span>  
  
     <span data-ttu-id="45b60-122">単純復旧モデルを使用するデータベースの場合は、一括インポート操作後に完全バックアップまたは差分バックアップを行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="45b60-122">For a database that uses the simple recovery model, we recommend that you take a full or differential backup after the bulk-import operation finishes.</span></span> <span data-ttu-id="45b60-123">詳細については、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)」または「[データベースの差分バックアップの作成 &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45b60-123">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) or [Create a Differential Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md).</span></span>  
  
     <span data-ttu-id="45b60-124">一括ログ復旧モデルまたは完全復旧モデルの場合、ログ バックアップで十分です。</span><span class="sxs-lookup"><span data-stu-id="45b60-124">For the bulk-logged recovery model or full recovery model, a log backup is enough.</span></span> <span data-ttu-id="45b60-125">詳細については、「[トランザクション ログ バックアップ &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45b60-125">For more information, see [Transaction Log Backups &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="45b60-126">大量一括インポートのパフォーマンスを向上するために、テーブル インデックスを削除する。</span><span class="sxs-lookup"><span data-stu-id="45b60-126">Drop table indexes to improve performance for large bulk imports.</span></span>  
  
     <span data-ttu-id="45b60-127">このガイドラインは、テーブル内の既存のデータ量に比べて大量のデータをインポートするときに関するものです。</span><span class="sxs-lookup"><span data-stu-id="45b60-127">This guideline is for when you are importing a large amount of data compared to the amount of data that is already in the table.</span></span> <span data-ttu-id="45b60-128">この場合、一括インポート操作を実行する前にテーブルからインデックスを削除すると、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="45b60-128">In this case, dropping the indexes from the table before you perform the bulk-import operation can significantly increase performance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45b60-129">テーブル内の既存のデータ量に比べて少量のデータを読み込む場合は、インデックスを削除すると逆効果です。</span><span class="sxs-lookup"><span data-stu-id="45b60-129">If you are loading a small amount of data compared to the amount of data already in the table, dropping the indexes is counterproductive.</span></span> <span data-ttu-id="45b60-130">インデックスの再構築に必要な時間が、一括インポート操作で節約される時間よりも長くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="45b60-130">The time required to rebuild the indexes might be longer than the time saved during the bulk-import operation.</span></span>  
  
-   <span data-ttu-id="45b60-131">データ ファイルにある隠し文字を検索して取り除く。</span><span class="sxs-lookup"><span data-stu-id="45b60-131">Find and remove hidden characters in the data file.</span></span>  
  
     <span data-ttu-id="45b60-132">多くのユーティリティやテキスト エディターで隠し文字を表示できます。隠し文字は、通常データ ファイルの末尾にあります。</span><span class="sxs-lookup"><span data-stu-id="45b60-132">Many utilities and text editors display hidden characters, which are usually at the end of the data file.</span></span> <span data-ttu-id="45b60-133">一括インポート操作のとき、ASCII データ ファイルに隠し文字があると、"予期しない NULL が見つかりました" というエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="45b60-133">During a bulk-import operation, hidden characters in an ASCII data file can cause problems that cause an error of "unexpected null found".</span></span> <span data-ttu-id="45b60-134">隠し文字をすべて検索して削除することにより、この問題を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="45b60-134">Finding and removing all the hidden characters should help prevent this problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b60-135">参照</span><span class="sxs-lookup"><span data-stu-id="45b60-135">See Also</span></span>  
 <span data-ttu-id="45b60-136">[bcp ユーティリティを使用した一括データのインポートとエクスポート &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="45b60-136">[Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) </span></span>  
 <span data-ttu-id="45b60-137">[BULK INSERT または OPENROWSET&#40;BULK...&#41; を使用した一括データのインポート &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="45b60-137">[Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span></span>  
 <span data-ttu-id="45b60-138">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="45b60-138">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="45b60-139">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="45b60-139">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="45b60-140">[一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="45b60-140">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 [<span data-ttu-id="45b60-141">OPENROWSET &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="45b60-141">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
