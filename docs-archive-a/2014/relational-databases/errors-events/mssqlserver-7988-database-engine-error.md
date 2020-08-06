---
title: MSSQLSERVER_7988 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7988 (Database Engine error)
ms.assetid: 29b967b8-de30-4618-99a8-8b1155e69026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 984cb03aeb5feaa230762e200304f16cd8c5df08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715298"
---
# <a name="mssqlserver_7988"></a><span data-ttu-id="fa797-102">MSSQLSERVER_7988</span><span class="sxs-lookup"><span data-stu-id="fa797-102">MSSQLSERVER_7988</span></span>
    
## <a name="details"></a><span data-ttu-id="fa797-103">詳細</span><span class="sxs-lookup"><span data-stu-id="fa797-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa797-104">製品名</span><span class="sxs-lookup"><span data-stu-id="fa797-104">Product Name</span></span>|<span data-ttu-id="fa797-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fa797-105">SQL Server</span></span>|  
|<span data-ttu-id="fa797-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="fa797-106">Event ID</span></span>|<span data-ttu-id="fa797-107">7988</span><span class="sxs-lookup"><span data-stu-id="fa797-107">7988</span></span>|  
|<span data-ttu-id="fa797-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="fa797-108">Event Source</span></span>|<span data-ttu-id="fa797-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fa797-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fa797-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="fa797-110">Component</span></span>|<span data-ttu-id="fa797-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fa797-111">SQLEngine</span></span>|  
|<span data-ttu-id="fa797-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="fa797-112">Symbolic Name</span></span>|<span data-ttu-id="fa797-113">DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED</span><span class="sxs-lookup"><span data-stu-id="fa797-113">DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED</span></span>|  
|<span data-ttu-id="fa797-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="fa797-114">Message Text</span></span>|<span data-ttu-id="fa797-115">システム テーブルの事前チェック:オブジェクト ID O_ID。</span><span class="sxs-lookup"><span data-stu-id="fa797-115">System table pre-checks: Object ID O_ID.</span></span> <span data-ttu-id="fa797-116">データ チェーンでのループが P_ID で検出されました。</span><span class="sxs-lookup"><span data-stu-id="fa797-116">Loop in data chain detected at P_ID.</span></span> <span data-ttu-id="fa797-117">修復できないエラーにより、Check ステートメントが終了しました。</span><span class="sxs-lookup"><span data-stu-id="fa797-117">Check statement terminated because of an irreparable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fa797-118">説明</span><span class="sxs-lookup"><span data-stu-id="fa797-118">Explanation</span></span>  
 <span data-ttu-id="fa797-119">DBCC CHECKDB の最初のフェーズで行われるのは、重要なシステム テーブルのデータ ページに対する初期チェックです。</span><span class="sxs-lookup"><span data-stu-id="fa797-119">The first phase of a DBCC CHECKDB is to do primitive checks on the data pages of critical system tables.</span></span> <span data-ttu-id="fa797-120">この時点でエラーが検出されても修正できないので、DBCC CHECKDB は直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="fa797-120">If any errors are found, they cannot be repaired; therefore, DBCC CHECKDB terminates immediately.</span></span> <span data-ttu-id="fa797-121">*P_ID* ページで、ページ リンケージ ループが検出されています。</span><span class="sxs-lookup"><span data-stu-id="fa797-121">A page linkage loop has been detected on page *P_ID*.</span></span> <span data-ttu-id="fa797-122">ページ リンケージ ループとは、あるページからの次ページ ポインターが最終的にそのページに戻ってくる状態です。</span><span class="sxs-lookup"><span data-stu-id="fa797-122">A page linkage loop occurs when the next page pointers from a page eventually return to the page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fa797-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="fa797-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="fa797-124">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="fa797-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="fa797-125">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="fa797-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="fa797-126">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="fa797-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="fa797-127">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="fa797-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="fa797-128">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="fa797-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="fa797-129">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="fa797-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="fa797-130">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="fa797-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="fa797-131">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="fa797-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="fa797-132">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fa797-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="fa797-133">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="fa797-133">Restore from Backup</span></span>  
 <span data-ttu-id="fa797-134">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="fa797-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="fa797-135">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="fa797-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="fa797-136">適用不可。</span><span class="sxs-lookup"><span data-stu-id="fa797-136">Not applicable.</span></span> <span data-ttu-id="fa797-137">このエラーを自動的に修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa797-137">This error cannot be repaired automatically.</span></span> <span data-ttu-id="fa797-138">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="fa797-138">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service and Support (CSS).</span></span>  
  
  
