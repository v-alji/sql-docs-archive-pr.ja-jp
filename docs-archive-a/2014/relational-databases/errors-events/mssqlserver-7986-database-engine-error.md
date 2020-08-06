---
title: MSSQLSERVER_7986 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7986 (Database Engine error)
ms.assetid: ae64276c-4e1e-4ef3-9ee9-ebeb2f61e565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f7d312987a2692c95f2cf6dbe0c86a4b2acbe6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718152"
---
# <a name="mssqlserver_7986"></a><span data-ttu-id="4ce25-102">MSSQLSERVER_7986</span><span class="sxs-lookup"><span data-stu-id="4ce25-102">MSSQLSERVER_7986</span></span>
    
## <a name="details"></a><span data-ttu-id="4ce25-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4ce25-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ce25-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4ce25-104">Product Name</span></span>|<span data-ttu-id="4ce25-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4ce25-105">SQL Server</span></span>|  
|<span data-ttu-id="4ce25-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4ce25-106">Event ID</span></span>|<span data-ttu-id="4ce25-107">7986</span><span class="sxs-lookup"><span data-stu-id="4ce25-107">7986</span></span>|  
|<span data-ttu-id="4ce25-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4ce25-108">Event Source</span></span>|<span data-ttu-id="4ce25-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4ce25-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4ce25-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4ce25-110">Component</span></span>|<span data-ttu-id="4ce25-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4ce25-111">SQLEngine</span></span>|  
|<span data-ttu-id="4ce25-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4ce25-112">Symbolic Name</span></span>|<span data-ttu-id="4ce25-113">DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE</span><span class="sxs-lookup"><span data-stu-id="4ce25-113">DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE</span></span>|  
|<span data-ttu-id="4ce25-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4ce25-114">Message Text</span></span>|<span data-ttu-id="4ce25-115">システム テーブルの事前チェック:オブジェクト ID O_ID には、オブジェクト間のチェーン リンケージがあります。</span><span class="sxs-lookup"><span data-stu-id="4ce25-115">System table pre-checks: Object ID O_ID has cross-object chain linkage.</span></span> <span data-ttu-id="4ce25-116">ページ P_ID1 は、アロケーション ユニット ID A_ID1 の P_ID2 を指しています (A_ID2 の必要があります)。</span><span class="sxs-lookup"><span data-stu-id="4ce25-116">Page P_ID1 points to P_ID2 in alloc unit ID A_ID1 (should be A_ID2).</span></span> <span data-ttu-id="4ce25-117">修復できないエラーにより、Check ステートメントが終了しました。</span><span class="sxs-lookup"><span data-stu-id="4ce25-117">Check statement terminated due to unrepairable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4ce25-118">説明</span><span class="sxs-lookup"><span data-stu-id="4ce25-118">Explanation</span></span>  
 <span data-ttu-id="4ce25-119">DBCC CHECKDB の最初のフェーズで行われるのは、重要なシステム テーブルのデータ ページに対する初期チェックです。</span><span class="sxs-lookup"><span data-stu-id="4ce25-119">The first phase of a DBCC CHECKDB is to do primitive checks on the data pages of critical system tables.</span></span> <span data-ttu-id="4ce25-120">この時点でエラーが検出されても修正できないので、DBCC CHECKDB は直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="4ce25-120">If any errors are found, they cannot be repaired; therefore, the DBCC CHECKDB terminates immediately.</span></span> <span data-ttu-id="4ce25-121">指定のオブジェクトのデータ レベルで、ページ *P_ID1* の次ページ ポインターは、別のオブジェクトのページ *P_ID2* を指しています。</span><span class="sxs-lookup"><span data-stu-id="4ce25-121">The next page pointer of page *P_ID1* in the data level of the specified object points to a page, *P_ID2*, in a different object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4ce25-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4ce25-122">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="4ce25-123">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="4ce25-123">Look for Hardware Failure</span></span>  
 <span data-ttu-id="4ce25-124">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="4ce25-124">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="4ce25-125">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ce25-125">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="4ce25-126">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="4ce25-126">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="4ce25-127">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4ce25-127">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="4ce25-128">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ce25-128">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="4ce25-129">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4ce25-129">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="4ce25-130">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="4ce25-130">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="4ce25-131">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4ce25-131">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="4ce25-132">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="4ce25-132">Restore from Backup</span></span>  
 <span data-ttu-id="4ce25-133">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="4ce25-133">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="4ce25-134">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="4ce25-134">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="4ce25-135">適用不可。</span><span class="sxs-lookup"><span data-stu-id="4ce25-135">Not applicable.</span></span> <span data-ttu-id="4ce25-136">このエラーを自動的に修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="4ce25-136">This error cannot be repaired automatically.</span></span> <span data-ttu-id="4ce25-137">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="4ce25-137">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
