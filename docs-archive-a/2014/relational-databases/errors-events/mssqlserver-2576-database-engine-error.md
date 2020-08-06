---
title: MSSQLSERVER_2576 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2576 (Database Engine error)
ms.assetid: b727cc2f-c76c-46f8-bbbe-5e7a05a6eabf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f378051c7844bf08d617db56666d69b22ecf732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634541"
---
# <a name="mssqlserver_2576"></a><span data-ttu-id="ac4b6-102">MSSQLSERVER_2576</span><span class="sxs-lookup"><span data-stu-id="ac4b6-102">MSSQLSERVER_2576</span></span>
    
## <a name="details"></a><span data-ttu-id="ac4b6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="ac4b6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ac4b6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ac4b6-104">Product Name</span></span>|<span data-ttu-id="ac4b6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ac4b6-105">SQL Server</span></span>|  
|<span data-ttu-id="ac4b6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ac4b6-106">Event ID</span></span>|<span data-ttu-id="ac4b6-107">2576</span><span class="sxs-lookup"><span data-stu-id="ac4b6-107">2576</span></span>|  
|<span data-ttu-id="ac4b6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ac4b6-108">Event Source</span></span>|<span data-ttu-id="ac4b6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ac4b6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ac4b6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ac4b6-110">Component</span></span>|<span data-ttu-id="ac4b6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ac4b6-111">SQLEngine</span></span>|  
|<span data-ttu-id="ac4b6-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ac4b6-112">Symbolic Name</span></span>|<span data-ttu-id="ac4b6-113">DBCC_IAM_PARENT_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="ac4b6-113">DBCC_IAM_PARENT_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="ac4b6-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ac4b6-114">Message Text</span></span>|<span data-ttu-id="ac4b6-115">オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) の IAM ページ P_ID2 の前のポインターは、IAM (Index Allocation Map) ページ P_ID1 を指していますが、スキャンでは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-115">The Index Allocation Map (IAM) page P_ID1 is pointed to by the previous pointer of IAM page P_ID2 in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) but was not detected in the scan.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ac4b6-116">説明</span><span class="sxs-lookup"><span data-stu-id="ac4b6-116">Explanation</span></span>  
 <span data-ttu-id="ac4b6-117">Index Allocation Map (IAM) ページへの参照が、IAM チェーン内の別の IAM ページに前ページ リンクとして存在しますが、この IAM ページまたはメタデータのエントリが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-117">An Index Allocation Map (IAM) page or metadata entry was not located, even though a reference to the page exists as the previous page link on another IAM page in an IAM chain.</span></span> <span data-ttu-id="ac4b6-118">*P_ID1* ページが (0:0) であれば、IAM ページ *P_ID2* が IAM チェーンの開始であり、この IAM チェーンのメタデータ エントリがありません。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-118">If the *P_ID1* page is (0:0), the IAM page, *P_ID2*, is the start of an IAM chain, and the metadata entry for the IAM chain is missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ac4b6-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ac4b6-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="ac4b6-120">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="ac4b6-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="ac4b6-121">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="ac4b6-122">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="ac4b6-123">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="ac4b6-124">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="ac4b6-125">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="ac4b6-126">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="ac4b6-127">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="ac4b6-128">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="ac4b6-129">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="ac4b6-129">Restore from Backup</span></span>  
 <span data-ttu-id="ac4b6-130">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="ac4b6-131">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="ac4b6-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="ac4b6-132">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="ac4b6-133">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="ac4b6-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="ac4b6-134">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ac4b6-135">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="ac4b6-136">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="ac4b6-137">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="ac4b6-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="ac4b6-138">REPAIR を実行すると、*P_ID2* ページを含んでいる IAM チェーンの再構築が試行されます。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-138">REPAIR will try to rebuild the IAM chain involving the *P_ID2* page.</span></span> <span data-ttu-id="ac4b6-139">チェーンの再構築時には、チェーンからページが削除される場合や、メタデータが破損していればチェーン全体が削除される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-139">Rebuilding the chain may involve removing pages from the chain, or removing the whole chain if the metadata is corrupted.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ac4b6-140">この修復を実行すると、データが失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="ac4b6-140">This repair may cause data loss.</span></span>  
  
  
