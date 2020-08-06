---
title: MSSQLSERVER_5250 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5250 (Database Engine error)
ms.assetid: f4a1d0e8-f27f-4cb8-a25d-040b40555dcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ace26b88aca5b00c23aff3fe48f7c1d04ef35245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718170"
---
# <a name="mssqlserver_5250"></a><span data-ttu-id="67aa8-102">MSSQLSERVER_5250</span><span class="sxs-lookup"><span data-stu-id="67aa8-102">MSSQLSERVER_5250</span></span>
    
## <a name="details"></a><span data-ttu-id="67aa8-103">詳細</span><span class="sxs-lookup"><span data-stu-id="67aa8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67aa8-104">製品名</span><span class="sxs-lookup"><span data-stu-id="67aa8-104">Product Name</span></span>|<span data-ttu-id="67aa8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="67aa8-105">SQL Server</span></span>|  
|<span data-ttu-id="67aa8-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="67aa8-106">Event ID</span></span>|<span data-ttu-id="67aa8-107">5250</span><span class="sxs-lookup"><span data-stu-id="67aa8-107">5250</span></span>|  
|<span data-ttu-id="67aa8-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="67aa8-108">Event Source</span></span>|<span data-ttu-id="67aa8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="67aa8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="67aa8-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="67aa8-110">Component</span></span>|<span data-ttu-id="67aa8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="67aa8-111">SQLEngine</span></span>|  
|<span data-ttu-id="67aa8-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="67aa8-112">Symbolic Name</span></span>|<span data-ttu-id="67aa8-113">DBCC4_CRITICAL_DATABASE_PAGE_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="67aa8-113">DBCC4_CRITICAL_DATABASE_PAGE_CORRUPT</span></span>|  
|<span data-ttu-id="67aa8-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="67aa8-114">Message Text</span></span>|<span data-ttu-id="67aa8-115">データベース エラー:データベース 'NAME' (データベース ID DB_ID) の PAGE_TYPE ページ P_ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="67aa8-115">Database error: PAGE_TYPE page P_ID for database 'NAME' (database ID DB_ID) is invalid.</span></span> <span data-ttu-id="67aa8-116">このエラーを修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="67aa8-116">This error cannot be repaired.</span></span> <span data-ttu-id="67aa8-117">バックアップから復元してください。</span><span class="sxs-lookup"><span data-stu-id="67aa8-117">You must restore from backup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="67aa8-118">説明</span><span class="sxs-lookup"><span data-stu-id="67aa8-118">Explanation</span></span>  
 <span data-ttu-id="67aa8-119">示されているデータベースのファイル ヘッダー ページまたはブート ページが破損しています。</span><span class="sxs-lookup"><span data-stu-id="67aa8-119">A file header page or boot page in the specified database is corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="67aa8-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="67aa8-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="67aa8-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="67aa8-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="67aa8-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="67aa8-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="67aa8-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="67aa8-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="67aa8-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="67aa8-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="67aa8-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="67aa8-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="67aa8-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="67aa8-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="67aa8-127">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="67aa8-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="67aa8-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="67aa8-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="67aa8-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="67aa8-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="67aa8-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="67aa8-130">Restore from Backup</span></span>  
 <span data-ttu-id="67aa8-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="67aa8-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="67aa8-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="67aa8-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="67aa8-133">適用不可。</span><span class="sxs-lookup"><span data-stu-id="67aa8-133">Not applicable.</span></span> <span data-ttu-id="67aa8-134">このエラーを修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="67aa8-134">This error cannot be repaired.</span></span> <span data-ttu-id="67aa8-135">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="67aa8-135">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
