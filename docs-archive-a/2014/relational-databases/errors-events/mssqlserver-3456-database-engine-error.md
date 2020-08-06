---
title: MSSQLSERVER_3456 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3456 (Database Engine error)
ms.assetid: d11b2b2c-3ae4-4023-b82f-05b561bfacce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f13316bdd3147bb0ad63c8d4a2fb18f1fce74006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716385"
---
# <a name="mssqlserver_3456"></a><span data-ttu-id="f806f-102">MSSQLSERVER_3456</span><span class="sxs-lookup"><span data-stu-id="f806f-102">MSSQLSERVER_3456</span></span>
    
## <a name="details"></a><span data-ttu-id="f806f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f806f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f806f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f806f-104">Product Name</span></span>|<span data-ttu-id="f806f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f806f-105">SQL Server</span></span>|  
|<span data-ttu-id="f806f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f806f-106">Event ID</span></span>|<span data-ttu-id="f806f-107">3456</span><span class="sxs-lookup"><span data-stu-id="f806f-107">3456</span></span>|  
|<span data-ttu-id="f806f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f806f-108">Event Source</span></span>|<span data-ttu-id="f806f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f806f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f806f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f806f-110">Component</span></span>|<span data-ttu-id="f806f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f806f-111">SQLEngine</span></span>|  
|<span data-ttu-id="f806f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f806f-112">Symbolic Name</span></span>|<span data-ttu-id="f806f-113">REC_REDOLSNMISMATCH</span><span class="sxs-lookup"><span data-stu-id="f806f-113">REC_REDOLSNMISMATCH</span></span>|  
|<span data-ttu-id="f806f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f806f-114">Message Text</span></span>|<span data-ttu-id="f806f-115">トランザクション ID %S_XID、ページ %S_PGID、データベース '%.\*ls' (データベース ID %d) のログ レコード %S_LSN を再実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f806f-115">Could not redo log record %S_LSN, for transaction ID %S_XID, on page %S_PGID, database '%.\*ls' (database ID %d).</span></span> <span data-ttu-id="f806f-116">ページ:LSN = %S_LSN、型 = %ld。</span><span class="sxs-lookup"><span data-stu-id="f806f-116">Page: LSN = %S_LSN, type = %ld.</span></span> <span data-ttu-id="f806f-117">Log:OpCode = %ld、コンテキスト %ld、PrevPageLSN: %S_LSN。</span><span class="sxs-lookup"><span data-stu-id="f806f-117">Log: OpCode = %ld, context %ld, PrevPageLSN: %S_LSN.</span></span> <span data-ttu-id="f806f-118">データベースをバックアップから復元するか、データベースを修復してください。</span><span class="sxs-lookup"><span data-stu-id="f806f-118">Restore from a backup of the database, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f806f-119">説明</span><span class="sxs-lookup"><span data-stu-id="f806f-119">Explanation</span></span>  
 <span data-ttu-id="f806f-120">復元操作で、トランザクション ログを再実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f806f-120">The restore operation was unable to redo the transaction log.</span></span> <span data-ttu-id="f806f-121">このエラーによって、データベースは SUSPECT 状態になっています。</span><span class="sxs-lookup"><span data-stu-id="f806f-121">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="f806f-122">プライマリ ファイル グループ、また場合によってはその他のファイル グループには、問題があり、損傷している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f806f-122">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="f806f-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動中はデータベースを復旧できないため、データベースを使用できません。</span><span class="sxs-lookup"><span data-stu-id="f806f-123">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="f806f-124">問題を解決するには、ユーザーによる操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="f806f-124">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="f806f-125">このエラーが **tempdb**で発生した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスはシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="f806f-125">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f806f-126">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f806f-126">User Action</span></span>  
 <span data-ttu-id="f806f-127">このエラーは、サーバー インスタンスの起動またはデータベースの復旧を試行したときのシステム上の一時的な状態が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f806f-127">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="f806f-128">また、データベースを起動しようとするたびに発生する永続的なエラーが原因である可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="f806f-128">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="f806f-129">原因の詳細については、Windows イベント ログで、具体的な問題点を示しているこれより前のエラーを調べてください。</span><span class="sxs-lookup"><span data-stu-id="f806f-129">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="f806f-130">このエラー 3456 の発生の原因については、Windows イベント ログをさかのぼって、具体的な問題点を示すエラーを調べてください。</span><span class="sxs-lookup"><span data-stu-id="f806f-130">For information about the cause of this occurrence of error 3456, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="f806f-131">ユーザーに求められる適切な対処は、Windows イベント ログが示している情報、つまり、その [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーが一時的な状態によって引き起こされたのか、永続的なエラーが原因で引き起こされたのかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f806f-131">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="f806f-132">エラー 3456 をトラブルシューティングするためのユーザー操作の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f806f-132">For information about the user actions for troubleshooting error 3456, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f806f-133">参照</span><span class="sxs-lookup"><span data-stu-id="f806f-133">See Also</span></span>  
 <span data-ttu-id="f806f-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f806f-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="f806f-135">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f806f-135">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="f806f-136">[データベースの全体復元 &#40;単純復旧モデル&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="f806f-136">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="f806f-137">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="f806f-137">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="f806f-138">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f806f-138">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
