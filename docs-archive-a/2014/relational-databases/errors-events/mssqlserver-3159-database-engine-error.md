---
title: MSSQLSERVER_3159 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3159 (Database Engine error)
ms.assetid: c93c1003-0e3a-40aa-9873-44a0f5b8b57e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b469842b2aab15980c72ea01e46270c55ef29e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640988"
---
# <a name="mssqlserver_3159"></a><span data-ttu-id="1654f-102">MSSQLSERVER_3159</span><span class="sxs-lookup"><span data-stu-id="1654f-102">MSSQLSERVER_3159</span></span>
    
## <a name="details"></a><span data-ttu-id="1654f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="1654f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1654f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="1654f-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="1654f-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1654f-105">Event ID</span></span>|<span data-ttu-id="1654f-106">3159</span><span class="sxs-lookup"><span data-stu-id="1654f-106">3159</span></span>|  
|<span data-ttu-id="1654f-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="1654f-107">Event Source</span></span>|<span data-ttu-id="1654f-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1654f-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1654f-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1654f-109">Component</span></span>|<span data-ttu-id="1654f-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1654f-110">SQLEngine</span></span>|  
|<span data-ttu-id="1654f-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="1654f-111">Symbolic Name</span></span>|<span data-ttu-id="1654f-112">LDDB_LOGNOTBACKEDUP</span><span class="sxs-lookup"><span data-stu-id="1654f-112">LDDB_LOGNOTBACKEDUP</span></span>|  
|<span data-ttu-id="1654f-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="1654f-113">Message Text</span></span>|<span data-ttu-id="1654f-114">データベース "%ls" のログの末尾がバックアップされませんでした。</span><span class="sxs-lookup"><span data-stu-id="1654f-114">The tail of the log for the database "%ls" has not been backed up.</span></span> <span data-ttu-id="1654f-115">この部分の作業を保存しておく場合は BACKUP LOG WITH NORECOVERY を使用してログをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="1654f-115">Use BACKUP LOG WITH NORECOVERY to back up the log if it contains work that you do not want to lose.</span></span> <span data-ttu-id="1654f-116">ログのコンテンツを上書きするだけの場合は、RESTORE ステートメントで WITH REPLACE 句または WITH STOPAT 句を使用してください。</span><span class="sxs-lookup"><span data-stu-id="1654f-116">Use the WITH REPLACE or WITH STOPAT clause of the RESTORE statement to just overwrite the contents of the log.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1654f-117">説明</span><span class="sxs-lookup"><span data-stu-id="1654f-117">Explanation</span></span>  
 <span data-ttu-id="1654f-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で完全復旧モデルまたは一括ログ復旧モデルを使用するほとんどの場合は、まだバックアップされていないログ レコードをキャプチャするため、ログの末尾をバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1654f-118">In most cases, under the full or bulk-logged recovery models, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires that you back up the tail of the log to capture the log records that have not yet been backed up.</span></span> <span data-ttu-id="1654f-119">復元操作直前のログの末尾から取ったログ バックアップをログ末尾のバックアップといいます。</span><span class="sxs-lookup"><span data-stu-id="1654f-119">A log backup taken of the tail of the log just before a restore operation is called a tail-log backup.</span></span>  
  
 <span data-ttu-id="1654f-120">データベースを障害発生時点に復旧するとき、ログ末尾のバックアップは復旧計画の対象になる最後のバックアップです。</span><span class="sxs-lookup"><span data-stu-id="1654f-120">When you are recovering a database to the point of a failure, the tail-log backup is the last backup of interest in the recovery plan.</span></span> <span data-ttu-id="1654f-121">ログの末尾をバックアップできない場合、障害の前に作成した最後のバックアップの末尾までしかデータベースを復旧できません。</span><span class="sxs-lookup"><span data-stu-id="1654f-121">If you cannot back up the tail of the log, you can recover a database only to the end of the last backup that was created before the failure.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1654f-122">では通常、データベースの復元を開始する前に、ログ末尾のバックアップを取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="1654f-122">usually requires that you take a tail-log backup before you start to restore a database.</span></span> <span data-ttu-id="1654f-123">ログ末尾のバックアップを取ることで、作業の損失を防ぎ、ログ チェーンを完全な状態で保持することができます。</span><span class="sxs-lookup"><span data-stu-id="1654f-123">The tail-log backup prevents work loss and keeps the log chain intact.</span></span> <span data-ttu-id="1654f-124">ただし、ログ末尾のバックアップは、すべての復元シナリオで必要となるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1654f-124">However, not all restore scenarios require a tail-log backup.</span></span> <span data-ttu-id="1654f-125">復元ポイントが以前のログ バックアップに含まれている場合、またはデータベースを移動するか置き換えて (上書きして) いる場合、ログ末尾のバックアップは不要であり、最新のバックアップ以降の特定の時点に復元する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="1654f-125">You do not have to have a tail-log backup if the recovery point is included in an earlier log backup, or if you are moving or replacing (overwriting) the database and do not need to restore it to a point of time after the most recent backup.</span></span> <span data-ttu-id="1654f-126">また、ログ ファイルが破損し、ログ末尾のバックアップを作成できない場合、ログ末尾のバックアップを使用することなくデータベースを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1654f-126">Also, if the log files are damaged and a tail-log backup cannot be created, you must restore the database without using a tail-log backup.</span></span> <span data-ttu-id="1654f-127">最新のログ バックアップの後にコミットされたトランザクションは失われます。</span><span class="sxs-lookup"><span data-stu-id="1654f-127">Any transactions committed after the latest log backup are lost.</span></span> <span data-ttu-id="1654f-128">詳細については、後の「ログ末尾のバックアップを使用しない復元」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1654f-128">For more information, see "Restoring Without Using a Tail-Log Backup," later in this topic.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="1654f-129">REPLACE は頻繁に使用するのではなく、十分に検討した後で必要と判断される場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="1654f-129">REPLACE should be used rarely, and only after careful consideration.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1654f-130">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="1654f-130">User Action</span></span>  
 <span data-ttu-id="1654f-131">ログ末尾のバックアップを行い、復元操作を再試行します。</span><span class="sxs-lookup"><span data-stu-id="1654f-131">Take a tail-log backup, and retry the restore operation.</span></span>  
  
 <span data-ttu-id="1654f-132">ログ末尾をバックアップできない場合は、RESTORE ステートメントで WITH STOPAT または WITH REPLACE を使用します。</span><span class="sxs-lookup"><span data-stu-id="1654f-132">If you cannot back up the tail of the log, use WITH STOPAT or WITH REPLACE in your RESTORE statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1654f-133">参照</span><span class="sxs-lookup"><span data-stu-id="1654f-133">See Also</span></span>  
 <span data-ttu-id="1654f-134">[SQL Server データベースを特定の時点に復元する方法 &#40;完全復旧モデル&#41;](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="1654f-134">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="1654f-135">[データベースが破損したときにトランザクションログをバックアップ &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1654f-135">[Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md) </span></span>  
 <span data-ttu-id="1654f-136">[トランザクション ログのバックアップ &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1654f-136">[Back Up a Transaction Log &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="1654f-137">ログ末尾のバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1654f-137">Tail-Log Backups &#40;SQL Server&#41;</span></span>](../backup-restore/tail-log-backups-sql-server.md)  
  
  
