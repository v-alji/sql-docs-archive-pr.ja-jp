---
title: MSSQLSERVER_3414 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3414 (Database Engine error)
ms.assetid: f25852f9-b91c-4356-b817-78bec9ec8db4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aecaf2a920552b8ea66804600fa8bd4168175e53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643862"
---
# <a name="mssqlserver_3414"></a><span data-ttu-id="45a1c-102">MSSQLSERVER_3414</span><span class="sxs-lookup"><span data-stu-id="45a1c-102">MSSQLSERVER_3414</span></span>
    
## <a name="details"></a><span data-ttu-id="45a1c-103">詳細</span><span class="sxs-lookup"><span data-stu-id="45a1c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45a1c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="45a1c-104">Product Name</span></span>|<span data-ttu-id="45a1c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="45a1c-105">SQL Server</span></span>|  
|<span data-ttu-id="45a1c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="45a1c-106">Event ID</span></span>|<span data-ttu-id="45a1c-107">3414</span><span class="sxs-lookup"><span data-stu-id="45a1c-107">3414</span></span>|  
|<span data-ttu-id="45a1c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="45a1c-108">Event Source</span></span>|<span data-ttu-id="45a1c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="45a1c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="45a1c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="45a1c-110">Component</span></span>|<span data-ttu-id="45a1c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="45a1c-111">SQLEngine</span></span>|  
|<span data-ttu-id="45a1c-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="45a1c-112">Symbolic Name</span></span>|<span data-ttu-id="45a1c-113">REC_GIVEUP</span><span class="sxs-lookup"><span data-stu-id="45a1c-113">REC_GIVEUP</span></span>|  
|<span data-ttu-id="45a1c-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="45a1c-114">Message Text</span></span>|<span data-ttu-id="45a1c-115">復元中にエラーが発生したので、データベース '%.\*ls' (データベース ID %d) は再開されません。</span><span class="sxs-lookup"><span data-stu-id="45a1c-115">An error occurred during recovery, preventing the database '%.\*ls' (database ID %d) from restarting.</span></span> <span data-ttu-id="45a1c-116">復元エラーを診断して修正するか、既知の適切なバックアップから復元してください。</span><span class="sxs-lookup"><span data-stu-id="45a1c-116">Diagnose the recovery errors and fix them, or restore from a known good backup.</span></span> <span data-ttu-id="45a1c-117">エラーが修正されない場合は、ご購入元に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="45a1c-117">If errors are not corrected or expected, contact Technical Support.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="45a1c-118">説明</span><span class="sxs-lookup"><span data-stu-id="45a1c-118">Explanation</span></span>  
 <span data-ttu-id="45a1c-119">示されているデータベースは復旧されましたが、復旧中にエラーが発生したために起動できませんでした。</span><span class="sxs-lookup"><span data-stu-id="45a1c-119">The specified database was recovered, but failed to start, because errors occurred during recovery.</span></span> <span data-ttu-id="45a1c-120">このエラーによって、データベースは SUSPECT 状態になっています。</span><span class="sxs-lookup"><span data-stu-id="45a1c-120">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="45a1c-121">プライマリ ファイル グループ、また場合によってはその他のファイル グループには、問題があり、損傷している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="45a1c-121">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="45a1c-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動中はデータベースを復旧できないため、データベースを使用できません。</span><span class="sxs-lookup"><span data-stu-id="45a1c-122">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="45a1c-123">問題を解決するには、ユーザーによる操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="45a1c-123">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="45a1c-124">このエラーが **tempdb**で発生した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスはシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="45a1c-124">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="45a1c-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="45a1c-125">User Action</span></span>  
 <span data-ttu-id="45a1c-126">このエラーは、サーバー インスタンスの起動またはデータベースの復旧を試行したときのシステム上の一時的な状態が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="45a1c-126">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="45a1c-127">また、データベースを起動しようとするたびに発生する永続的なエラーが原因である可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="45a1c-127">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="45a1c-128">原因の詳細については、Windows イベント ログで、具体的な問題点を示しているこれより前のエラーを調べてください。</span><span class="sxs-lookup"><span data-stu-id="45a1c-128">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="45a1c-129">このエラー 3414 の発生の原因については、Windows イベント ログをさかのぼって、具体的な問題点を示すエラーを調べてください。</span><span class="sxs-lookup"><span data-stu-id="45a1c-129">For information about the cause of this occurrence of error 3414, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="45a1c-130">ユーザーに求められる適切な対処は、Windows イベント ログが示している情報、つまり、その [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーが一時的な状態によって引き起こされたのか、永続的なエラーが原因で引き起こされたのかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="45a1c-130">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="45a1c-131">エラー 3414 をトラブルシューティングするためのユーザー操作の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="45a1c-131">For information about the user actions for troubleshooting error 3414, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a1c-132">参照</span><span class="sxs-lookup"><span data-stu-id="45a1c-132">See Also</span></span>  
 <span data-ttu-id="45a1c-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="45a1c-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="45a1c-134">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="45a1c-134">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="45a1c-135">[データベースの全体復元 &#40;単純復旧モデル&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="45a1c-135">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="45a1c-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="45a1c-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="45a1c-137">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="45a1c-137">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
