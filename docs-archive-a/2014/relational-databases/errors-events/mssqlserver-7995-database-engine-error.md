---
title: MSSQLSERVER_7995 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7995 (Database Engine error)
ms.assetid: af6d6322-3cba-43d8-be97-e6ef15f8c933
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c65cf2b16c4d7a0dcf40272f8280205a111d08e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641655"
---
# <a name="mssqlserver_7995"></a><span data-ttu-id="a30e6-102">MSSQLSERVER_7995</span><span class="sxs-lookup"><span data-stu-id="a30e6-102">MSSQLSERVER_7995</span></span>
    
## <a name="details"></a><span data-ttu-id="a30e6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a30e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a30e6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a30e6-104">Product Name</span></span>|<span data-ttu-id="a30e6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a30e6-105">SQL Server</span></span>|  
|<span data-ttu-id="a30e6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a30e6-106">Event ID</span></span>|<span data-ttu-id="a30e6-107">7995</span><span class="sxs-lookup"><span data-stu-id="a30e6-107">7995</span></span>|  
|<span data-ttu-id="a30e6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a30e6-108">Event Source</span></span>|<span data-ttu-id="a30e6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a30e6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a30e6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a30e6-110">Component</span></span>|<span data-ttu-id="a30e6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a30e6-111">SQLEngine</span></span>|  
|<span data-ttu-id="a30e6-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a30e6-112">Symbolic Name</span></span>|<span data-ttu-id="a30e6-113">DBCC2_SYSTEM_CATALOGS_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="a30e6-113">DBCC2_SYSTEM_CATALOGS_CORRUPT</span></span>|  
|<span data-ttu-id="a30e6-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a30e6-114">Message Text</span></span>|<span data-ttu-id="a30e6-115">データベース 'DBNAME' : システム カタログの一貫性エラーにより、DBCC CHECKNAME 処理を続行できません。</span><span class="sxs-lookup"><span data-stu-id="a30e6-115">Database 'DBNAME': consistency errors in system catalogs prevent further DBCC CHECKNAME processing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a30e6-116">説明</span><span class="sxs-lookup"><span data-stu-id="a30e6-116">Explanation</span></span>  
 <span data-ttu-id="a30e6-117">DBCC CHECKDB のプロセスは、次の 3 つのステージで構成されています。</span><span class="sxs-lookup"><span data-stu-id="a30e6-117">The DBCC CHECKDB process consists of the following three stages:</span></span>  
  
1.  <span data-ttu-id="a30e6-118">割り当てチェック。</span><span class="sxs-lookup"><span data-stu-id="a30e6-118">Allocation checks.</span></span> <span data-ttu-id="a30e6-119">これは、DBCC CHECKALLOC の実行に相当します。</span><span class="sxs-lookup"><span data-stu-id="a30e6-119">This is equivalent to running DBCC CHECKALLOC.</span></span>  
  
2.  <span data-ttu-id="a30e6-120">システム テーブルの一貫性チェック。</span><span class="sxs-lookup"><span data-stu-id="a30e6-120">System tables consistency checks.</span></span> <span data-ttu-id="a30e6-121">これは、少数の不可欠なシステム ベース テーブルに対して DBCC CHECKTABLE を実行することに相当します。</span><span class="sxs-lookup"><span data-stu-id="a30e6-121">This is equivalent to running DBCC CHECKTABLE on a small list of necessary system base tables.</span></span>  
  
3.  <span data-ttu-id="a30e6-122">データベース全体の一貫性チェック。</span><span class="sxs-lookup"><span data-stu-id="a30e6-122">Complete database consistency checks.</span></span>  
  
 <span data-ttu-id="a30e6-123">ステージ 2 で MSSQLEngine_7995 が発行されました。このメッセージは、DBCC CHECKDB コマンドで修復できないエラーが検出されたか、REPAIR が指定されていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="a30e6-123">MSSQLEngine_7995 is raised in stage 2 to indicate that DBCC CHECKDB has found errors that the command cannot repair or that REPAIR has not been specified.</span></span> <span data-ttu-id="a30e6-124">問題のシステム ベース テーブルにデータベース内のすべてのオブジェクトのメタデータが格納されているか、システム ベース テーブルが破損しているため、DBCC CHECKDB はステージ 3 に進むことができません。</span><span class="sxs-lookup"><span data-stu-id="a30e6-124">DBCC CHECKDB cannot continue with stage 3 because either the system base tables in question store the metadata for all objects in the database or the system base tables are corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a30e6-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a30e6-125">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="a30e6-126">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="a30e6-126">Look for Hardware Failure</span></span>  
 <span data-ttu-id="a30e6-127">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="a30e6-127">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="a30e6-128">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a30e6-128">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="a30e6-129">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="a30e6-129">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="a30e6-130">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a30e6-130">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="a30e6-131">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a30e6-131">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="a30e6-132">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="a30e6-132">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="a30e6-133">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="a30e6-133">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="a30e6-134">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a30e6-134">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="a30e6-135">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="a30e6-135">Restore from Backup</span></span>  
 <span data-ttu-id="a30e6-136">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="a30e6-136">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="a30e6-137">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="a30e6-137">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="a30e6-138">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="a30e6-138">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="a30e6-139">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="a30e6-139">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="a30e6-140">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="a30e6-140">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a30e6-141">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="a30e6-141">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="a30e6-142">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="a30e6-142">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="a30e6-143">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="a30e6-143">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="a30e6-144">エラーの一覧を調べて、REPAIR によって個々のエラーに対して何が行われるかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a30e6-144">Examine the list of errors to see what REPAIR will do for each.</span></span>  
  
  
