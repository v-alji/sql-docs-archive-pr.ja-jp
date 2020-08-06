---
title: MSSQLSERVER_2515 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2515 (Database Engine error)
ms.assetid: af93aa29-70c9-4923-90af-aafadb20c1c6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73b2d8b8ff01b97428ba6149f537d96044c6ae3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713198"
---
# <a name="mssqlserver_2515"></a><span data-ttu-id="1cf6d-102">MSSQLSERVER_2515</span><span class="sxs-lookup"><span data-stu-id="1cf6d-102">MSSQLSERVER_2515</span></span>
    
## <a name="details"></a><span data-ttu-id="1cf6d-103">詳細</span><span class="sxs-lookup"><span data-stu-id="1cf6d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1cf6d-104">製品名</span><span class="sxs-lookup"><span data-stu-id="1cf6d-104">Product Name</span></span>|<span data-ttu-id="1cf6d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1cf6d-105">SQL Server</span></span>|  
|<span data-ttu-id="1cf6d-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1cf6d-106">Event ID</span></span>|<span data-ttu-id="1cf6d-107">2515</span><span class="sxs-lookup"><span data-stu-id="1cf6d-107">2515</span></span>|  
|<span data-ttu-id="1cf6d-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="1cf6d-108">Event Source</span></span>|<span data-ttu-id="1cf6d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1cf6d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1cf6d-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1cf6d-110">Component</span></span>|<span data-ttu-id="1cf6d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1cf6d-111">SQLEngine</span></span>|  
|<span data-ttu-id="1cf6d-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="1cf6d-112">Symbolic Name</span></span>|<span data-ttu-id="1cf6d-113">DBCC_DIFF_MAP_OUT_OF_SYNC</span><span class="sxs-lookup"><span data-stu-id="1cf6d-113">DBCC_DIFF_MAP_OUT_OF_SYNC</span></span>|  
|<span data-ttu-id="1cf6d-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="1cf6d-114">Message Text</span></span>|<span data-ttu-id="1cf6d-115">ページ P_ID、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) は変更されていますが、差分バックアップ ビットマップでは変更が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-115">Page P_ID, object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID type TYPE has been modified but is not marked modified in the differential backup bitmap.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1cf6d-116">説明</span><span class="sxs-lookup"><span data-stu-id="1cf6d-116">Explanation</span></span>  
 <span data-ttu-id="1cf6d-117">指定のページにあるログ シーケンス番号 (LSN) の値が、データベースの BackupManager 内の差分参照 LSN か、ファイルのファイル制御ブロック内の差分ベース LSN のうち、新しい方の値より大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-117">The page specified has a log sequence number (LSN) that is higher than the differential reference LSN in the BackupManager of the database, or the differential base LSN in the file control block of the file, whichever is more recent.</span></span> <span data-ttu-id="1cf6d-118">ところが、差分バックアップ ビットマップでは、このページに変更が行われたことが記録されていません。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-118">However, the page is not marked as changed in the differential backup bitmap.</span></span>  
  
 <span data-ttu-id="1cf6d-119">このチェックは、差分ビットマップにエラーがないとわかっている場合にのみ実行されるので、報告されるのは各データベースにつき 1 ページのみです。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-119">Only one page per database will be reported, because this check is only performed when the differential bitmap is known to be error free.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1cf6d-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="1cf6d-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="1cf6d-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="1cf6d-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="1cf6d-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="1cf6d-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="1cf6d-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="1cf6d-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="1cf6d-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="1cf6d-127">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="1cf6d-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="1cf6d-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="1cf6d-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="1cf6d-130">Restore from Backup</span></span>  
 <span data-ttu-id="1cf6d-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="1cf6d-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="1cf6d-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="1cf6d-133">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="1cf6d-134">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="1cf6d-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="1cf6d-135">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="1cf6d-136">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="1cf6d-137">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="1cf6d-138">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="1cf6d-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="1cf6d-139">REPAIR を実行すると、差分ビットマップが無効になります。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-139">Running REPAIR will invalidate the differential bitmap.</span></span> <span data-ttu-id="1cf6d-140">データベースの完全バックアップを作成するまで、差分バックアップは実行できません。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-140">You cannot perform a differential backup until a full database backup is taken.</span></span> <span data-ttu-id="1cf6d-141">データベースの完全バックアップにより、差分ビットマップを再構築するためのベースラインが提供されます。</span><span class="sxs-lookup"><span data-stu-id="1cf6d-141">The full database backup provides a baseline for the differential bitmap to be rebuilt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf6d-142">参照</span><span class="sxs-lookup"><span data-stu-id="1cf6d-142">See Also</span></span>  
 <span data-ttu-id="1cf6d-143">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1cf6d-143">[Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="1cf6d-144">MSSQLSERVER_2516</span><span class="sxs-lookup"><span data-stu-id="1cf6d-144">MSSQLSERVER_2516</span></span>](mssqlserver-2516-database-engine-error.md)  
  
  
