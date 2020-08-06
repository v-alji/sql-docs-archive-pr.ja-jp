---
title: MSSQLSERVER_7984 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7984 (Database Engine error)
ms.assetid: e3192f56-e4e2-41da-b132-65f1e7540b1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7f92fe4f3751621e0cc636ffcd2d4de73b348d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643387"
---
# <a name="mssqlserver_7984"></a><span data-ttu-id="d65d1-102">MSSQLSERVER_7984</span><span class="sxs-lookup"><span data-stu-id="d65d1-102">MSSQLSERVER_7984</span></span>
    
## <a name="details"></a><span data-ttu-id="d65d1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d65d1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d65d1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d65d1-104">Product Name</span></span>|<span data-ttu-id="d65d1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d65d1-105">SQL Server</span></span>|  
|<span data-ttu-id="d65d1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d65d1-106">Event ID</span></span>|<span data-ttu-id="d65d1-107">7984</span><span class="sxs-lookup"><span data-stu-id="d65d1-107">7984</span></span>|  
|<span data-ttu-id="d65d1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d65d1-108">Event Source</span></span>|<span data-ttu-id="d65d1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d65d1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d65d1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d65d1-110">Component</span></span>|<span data-ttu-id="d65d1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d65d1-111">SQLEngine</span></span>|  
|<span data-ttu-id="d65d1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d65d1-112">Symbolic Name</span></span>|<span data-ttu-id="d65d1-113">DBCC2_PRE_CHECKS_BAD_PAGE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d65d1-113">DBCC2_PRE_CHECKS_BAD_PAGE_TYPE</span></span>|  
|<span data-ttu-id="d65d1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d65d1-114">Message Text</span></span>|<span data-ttu-id="d65d1-115">システム テーブルの事前チェック:オブジェクト ID O_ID。</span><span class="sxs-lookup"><span data-stu-id="d65d1-115">System table pre-checks: Object ID O_ID.</span></span> <span data-ttu-id="d65d1-116">ページ P_ID に予期しないページ型 PAGETYPE が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d65d1-116">Page P_ID has unexpected page type PAGETYPE.</span></span> <span data-ttu-id="d65d1-117">修復できないエラーにより、Check ステートメントが終了しました。</span><span class="sxs-lookup"><span data-stu-id="d65d1-117">Check statement terminated because of an irreparable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d65d1-118">説明</span><span class="sxs-lookup"><span data-stu-id="d65d1-118">Explanation</span></span>  
 <span data-ttu-id="d65d1-119">示されているオブジェクトのデータ レベルで、DATA_PAGE 以外の型のページが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="d65d1-119">A page with a type other than DATA_PAGE was found in the data level of the specified object.</span></span> <span data-ttu-id="d65d1-120">このエラーは、DBCC CHECKDB コマンドによるチェックの第 1 フェーズで生成されます。</span><span class="sxs-lookup"><span data-stu-id="d65d1-120">This error is raised during the first phase of the DBCC CHECKDB command checks.</span></span> <span data-ttu-id="d65d1-121">DBCC CHECKDB のこのフェーズで行われるのは、重要なシステム ベース テーブルのデータ ページに対する初期チェックです。</span><span class="sxs-lookup"><span data-stu-id="d65d1-121">During this phase, DBCC CHECKDB performs primitive checks on the data pages of critical system base tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d65d1-122">システム テーブルでエラーが検出されても修正できないので、DBCC CHECKDB コマンドは直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="d65d1-122">If any errors are found in the system tables, the errors cannot be repaired; therefore, the DBCC CHECKDB command ends immediately.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d65d1-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d65d1-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="d65d1-124">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="d65d1-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="d65d1-125">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="d65d1-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="d65d1-126">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d65d1-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="d65d1-127">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="d65d1-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d65d1-128">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d65d1-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="d65d1-129">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d65d1-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="d65d1-130">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d65d1-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="d65d1-131">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="d65d1-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="d65d1-132">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d65d1-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="d65d1-133">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="d65d1-133">Restore from Backup</span></span>  
 <span data-ttu-id="d65d1-134">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="d65d1-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="d65d1-135">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="d65d1-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="d65d1-136">適用不可。</span><span class="sxs-lookup"><span data-stu-id="d65d1-136">Not applicable.</span></span> <span data-ttu-id="d65d1-137">このエラーを自動的に修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="d65d1-137">This error cannot be repaired automatically.</span></span> <span data-ttu-id="d65d1-138">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="d65d1-138">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service and Support (CSS).</span></span>  
  
  
