---
title: MSSQLSERVER_8993 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8993 (Database Engine error)
ms.assetid: 06aac110-a41c-4853-bc8e-a83e8535b8be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5ee9497e9c4484fd885803c0feff20362a159ff2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631974"
---
# <a name="mssqlserver_8993"></a><span data-ttu-id="4f4d8-102">MSSQLSERVER_8993</span><span class="sxs-lookup"><span data-stu-id="4f4d8-102">MSSQLSERVER_8993</span></span>
    
## <a name="details"></a><span data-ttu-id="4f4d8-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4f4d8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f4d8-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4f4d8-104">Product Name</span></span>|<span data-ttu-id="4f4d8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4f4d8-105">SQL Server</span></span>|  
|<span data-ttu-id="4f4d8-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4f4d8-106">Event ID</span></span>|<span data-ttu-id="4f4d8-107">8993</span><span class="sxs-lookup"><span data-stu-id="4f4d8-107">8993</span></span>|  
|<span data-ttu-id="4f4d8-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4f4d8-108">Event Source</span></span>|<span data-ttu-id="4f4d8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4f4d8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4f4d8-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4f4d8-110">Component</span></span>|<span data-ttu-id="4f4d8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4f4d8-111">SQLEngine</span></span>|  
|<span data-ttu-id="4f4d8-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4f4d8-112">Symbolic Name</span></span>|<span data-ttu-id="4f4d8-113">DBCC3_MISSING_FORWARDED_ROW</span><span class="sxs-lookup"><span data-stu-id="4f4d8-113">DBCC3_MISSING_FORWARDED_ROW</span></span>|  
|<span data-ttu-id="4f4d8-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4f4d8-114">Message Text</span></span>|<span data-ttu-id="4f4d8-115">オブジェクト ID O_ID、転送元の行のページ P_ID1、スロット S_ID1 は、ページ P_ID2、スロット S_ID2 を指しています。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-115">Object ID O_ID, forwarding row page P_ID1, slot S_ID1 points to page P_ID2, slot S_ID2.</span></span> <span data-ttu-id="4f4d8-116">転送先の行が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-116">Did not encounter forwarded row.</span></span> <span data-ttu-id="4f4d8-117">アロケーション エラーが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-117">Possible allocation error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4f4d8-118">説明</span><span class="sxs-lookup"><span data-stu-id="4f4d8-118">Explanation</span></span>  
 <span data-ttu-id="4f4d8-119">ヒープ内の転送元の行が、存在しない転送先の行を指しています。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-119">A forwarding row in a heap points to a nonexistent forwarded row.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4f4d8-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4f4d8-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="4f4d8-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="4f4d8-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="4f4d8-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="4f4d8-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="4f4d8-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="4f4d8-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="4f4d8-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="4f4d8-127">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="4f4d8-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="4f4d8-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="4f4d8-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="4f4d8-130">Restore from Backup</span></span>  
 <span data-ttu-id="4f4d8-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="4f4d8-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="4f4d8-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="4f4d8-133">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="4f4d8-134">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="4f4d8-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="4f4d8-135">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="4f4d8-136">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="4f4d8-137">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="4f4d8-138">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="4f4d8-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="4f4d8-139">転送元の行は削除され、非クラスター化インデックスはすべて再構築されます。</span><span class="sxs-lookup"><span data-stu-id="4f4d8-139">The forwarding row will be deleted and any nonclustered indexes will be rebuilt.</span></span>  
  
  
