---
title: MSSQLSERVER_3313 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3313 (Database Engine error)
ms.assetid: a244227b-8553-42df-9435-034f906c4c74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 94de98c248713927790efb0d04c4e1358df30e2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640018"
---
# <a name="mssqlserver_3313"></a><span data-ttu-id="73961-102">MSSQLSERVER_3313</span><span class="sxs-lookup"><span data-stu-id="73961-102">MSSQLSERVER_3313</span></span>
    
## <a name="details"></a><span data-ttu-id="73961-103">詳細</span><span class="sxs-lookup"><span data-stu-id="73961-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73961-104">製品名</span><span class="sxs-lookup"><span data-stu-id="73961-104">Product Name</span></span>|<span data-ttu-id="73961-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="73961-105">SQL Server</span></span>|  
|<span data-ttu-id="73961-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="73961-106">Event ID</span></span>|<span data-ttu-id="73961-107">3313</span><span class="sxs-lookup"><span data-stu-id="73961-107">3313</span></span>|  
|<span data-ttu-id="73961-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="73961-108">Event Source</span></span>|<span data-ttu-id="73961-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="73961-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="73961-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="73961-110">Component</span></span>|<span data-ttu-id="73961-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="73961-111">SQLEngine</span></span>|  
|<span data-ttu-id="73961-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="73961-112">Symbolic Name</span></span>|<span data-ttu-id="73961-113">ERR_LOG_RID1</span><span class="sxs-lookup"><span data-stu-id="73961-113">ERR_LOG_RID1</span></span>|  
|<span data-ttu-id="73961-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="73961-114">Message Text</span></span>|<span data-ttu-id="73961-115">データベース '%.\*ls' でログに記録された操作をやり直しているときにエラーが発生しました。エラーが発生したログ レコード ID は %S_LSN です。</span><span class="sxs-lookup"><span data-stu-id="73961-115">During redoing of a logged operation in database '%.\*ls', an error occurred at log record ID %S_LSN.</span></span> <span data-ttu-id="73961-116">通常、この前に特定のエラーが Windows イベント ログ サービスにログ記録されます。</span><span class="sxs-lookup"><span data-stu-id="73961-116">Typically, the specific failure is previously logged as an error in the Windows Event Log service.</span></span> <span data-ttu-id="73961-117">完全バックアップからデータベースを復元するか、データベースを修復してください。</span><span class="sxs-lookup"><span data-stu-id="73961-117">Restore the database from a full backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="73961-118">説明</span><span class="sxs-lookup"><span data-stu-id="73961-118">Explanation</span></span>  
 <span data-ttu-id="73961-119">これは、再実行の復旧のロールアップ エラーです。</span><span class="sxs-lookup"><span data-stu-id="73961-119">This is a roll-up error for redo recovery.</span></span> <span data-ttu-id="73961-120">このエラーによって、データベースは SUSPECT 状態になっています。</span><span class="sxs-lookup"><span data-stu-id="73961-120">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="73961-121">プライマリ ファイル グループ、また場合によってはその他のファイル グループには、問題があり、損傷している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73961-121">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="73961-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動中はデータベースを復旧できないため、データベースを使用できません。</span><span class="sxs-lookup"><span data-stu-id="73961-122">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="73961-123">問題を解決するには、ユーザーによる操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="73961-123">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="73961-124">このエラーが **tempdb**で発生した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスはシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="73961-124">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="73961-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="73961-125">User Action</span></span>  
 <span data-ttu-id="73961-126">このエラーは、サーバー インスタンスの起動またはデータベースの復旧を試行したときのシステム上の一時的な状態が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73961-126">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="73961-127">また、データベースを起動しようとするたびに発生する永続的なエラーが原因である可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="73961-127">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="73961-128">原因の詳細については、Windows イベント ログで、具体的な問題点を示しているこれより前のエラーを調べてください。</span><span class="sxs-lookup"><span data-stu-id="73961-128">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="73961-129">このエラー状態が発生すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、通常、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **LOG** フォルダーに 3 つのファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="73961-129">Note that when this error condition is encountered, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] typically generates three files in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **LOG** folder.</span></span> <span data-ttu-id="73961-130">SQLDump*nnnn*.txt ファイルには、問題が発生したトランザクションやページの詳細など、エラーに関する詳しい診断情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="73961-130">The SQLDump*nnnn*.txt file contains advanced diagnostic information relating to the failures, including the details about the transaction and the page that encountered the problem.</span></span> <span data-ttu-id="73961-131">この情報は、通常、失敗の理由を分析するために製品サポート チームが使用します。</span><span class="sxs-lookup"><span data-stu-id="73961-131">This information is typically used by the Product Support team to analyze the reason for the failure.</span></span>  
  
 <span data-ttu-id="73961-132">このエラー 3313 の発生の原因については、Windows イベント ログをさかのぼって、具体的な問題点を示すエラーを調べてください。</span><span class="sxs-lookup"><span data-stu-id="73961-132">For information about the cause of this occurrence of error 3313, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="73961-133">ユーザーに求められる適切な対処は、Windows イベント ログが示している情報、つまり、その [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーが一時的な状態によって引き起こされたのか、永続的なエラーが原因で引き起こされたのかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="73961-133">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="73961-134">エラー 3313 をトラブルシューティングするためのユーザー操作の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="73961-134">For information about the user actions for troubleshooting error 3313, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73961-135">参照</span><span class="sxs-lookup"><span data-stu-id="73961-135">See Also</span></span>  
 <span data-ttu-id="73961-136">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73961-136">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="73961-137">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73961-137">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="73961-138">[データベースの全体復元 &#40;単純復旧モデル&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="73961-138">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="73961-139">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="73961-139">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="73961-140">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73961-140">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
