---
title: MSSQLSERVER_2574 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2574 (Database Engine error)
ms.assetid: efba507a-b5ad-4f1d-b0c8-f73b663a0562
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44fd103f8c651ca968ae997ae9c3d544b41cbf3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713190"
---
# <a name="mssqlserver_2574"></a><span data-ttu-id="b2ee1-102">MSSQLSERVER_2574</span><span class="sxs-lookup"><span data-stu-id="b2ee1-102">MSSQLSERVER_2574</span></span>
    
## <a name="details"></a><span data-ttu-id="b2ee1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="b2ee1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2ee1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="b2ee1-104">Product Name</span></span>|<span data-ttu-id="b2ee1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b2ee1-105">SQL Server</span></span>|  
|<span data-ttu-id="b2ee1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="b2ee1-106">Event ID</span></span>|<span data-ttu-id="b2ee1-107">2574</span><span class="sxs-lookup"><span data-stu-id="b2ee1-107">2574</span></span>|  
|<span data-ttu-id="b2ee1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="b2ee1-108">Event Source</span></span>|<span data-ttu-id="b2ee1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b2ee1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b2ee1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b2ee1-110">Component</span></span>|<span data-ttu-id="b2ee1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b2ee1-111">SQLEngine</span></span>|  
|<span data-ttu-id="b2ee1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="b2ee1-112">Symbolic Name</span></span>|<span data-ttu-id="b2ee1-113">DBCC_EMPTY_INDEX_TREE_LEVEL_PAGE</span><span class="sxs-lookup"><span data-stu-id="b2ee1-113">DBCC_EMPTY_INDEX_TREE_LEVEL_PAGE</span></span>|  
|<span data-ttu-id="b2ee1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="b2ee1-114">Message Text</span></span>|<span data-ttu-id="b2ee1-115">テーブル エラー:オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) のページ P_ID が空です。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-115">Table error: Page P_ID is empty in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="b2ee1-116">これは、B-Tree のレベル LEVEL では許可されません。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-116">This is not permitted at level LEVEL of the B-tree.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b2ee1-117">説明</span><span class="sxs-lookup"><span data-stu-id="b2ee1-117">Explanation</span></span>  
 <span data-ttu-id="b2ee1-118">指定されたインデックスのリーフ レベルより上位の B-Tree ページが空であり、行がありません。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-118">A B-tree page above the leaf level of the specified index is empty, that is it has no rows.</span></span> <span data-ttu-id="b2ee1-119">この動作は、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] のリーフ レベル ページでは可能ですが、各ツリー レベルでは一切許可されていません。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-119">This behavior is possible for leaf-level pages in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], but has never been possible in tree levels.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b2ee1-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="b2ee1-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="b2ee1-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="b2ee1-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="b2ee1-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="b2ee1-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="b2ee1-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="b2ee1-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="b2ee1-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="b2ee1-127">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="b2ee1-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="b2ee1-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="b2ee1-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="b2ee1-130">Restore from Backup</span></span>  
 <span data-ttu-id="b2ee1-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="b2ee1-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="b2ee1-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="b2ee1-133">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="b2ee1-134">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="b2ee1-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="b2ee1-135">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b2ee1-136">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="b2ee1-137">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="b2ee1-138">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="b2ee1-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="b2ee1-139">DBCC により、インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="b2ee1-139">DBCC will rebuild the index.</span></span>  
  
  
