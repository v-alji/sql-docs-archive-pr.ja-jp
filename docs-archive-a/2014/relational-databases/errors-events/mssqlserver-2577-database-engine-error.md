---
title: MSSQLSERVER_2577 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2577 (Database Engine error)
ms.assetid: f53256a2-2fb0-47fd-9ed9-c45389104145
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9e4b7b85f59ba721eae6b4a0ac8db1b2d288422d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643871"
---
# <a name="mssqlserver_2577"></a><span data-ttu-id="d29d8-102">MSSQLSERVER_2577</span><span class="sxs-lookup"><span data-stu-id="d29d8-102">MSSQLSERVER_2577</span></span>
    
## <a name="details"></a><span data-ttu-id="d29d8-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d29d8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d29d8-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d29d8-104">Product Name</span></span>|<span data-ttu-id="d29d8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d29d8-105">SQL Server</span></span>|  
|<span data-ttu-id="d29d8-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d29d8-106">Event ID</span></span>|<span data-ttu-id="d29d8-107">2577</span><span class="sxs-lookup"><span data-stu-id="d29d8-107">2577</span></span>|  
|<span data-ttu-id="d29d8-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d29d8-108">Event Source</span></span>|<span data-ttu-id="d29d8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d29d8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d29d8-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d29d8-110">Component</span></span>|<span data-ttu-id="d29d8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d29d8-111">SQLEngine</span></span>|  
|<span data-ttu-id="d29d8-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d29d8-112">Symbolic Name</span></span>|<span data-ttu-id="d29d8-113">DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER</span><span class="sxs-lookup"><span data-stu-id="d29d8-113">DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER</span></span>|  
|<span data-ttu-id="d29d8-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d29d8-114">Message Text</span></span>|<span data-ttu-id="d29d8-115">オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) の IAM (Index Allocation Map) チェーン内のチェーン シーケンス番号が間違っています。</span><span class="sxs-lookup"><span data-stu-id="d29d8-115">Chain sequence numbers out of order in the Index Allocation Map (IAM) chain for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="d29d8-116">シーケンス番号 SEQUENCE1 のページ P_ID1 がシーケンス番号 SEQUENCE2 のページ P_ID2 を指しています。</span><span class="sxs-lookup"><span data-stu-id="d29d8-116">Page P_ID1 with sequence number SEQUENCE1 points to page P_ID2 with sequence number SEQUENCE2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d29d8-117">説明</span><span class="sxs-lookup"><span data-stu-id="d29d8-117">Explanation</span></span>  
 <span data-ttu-id="d29d8-118">個々の IAM (Index Allocation Map) ページにはすべて、シーケンス番号が付けられています。</span><span class="sxs-lookup"><span data-stu-id="d29d8-118">Every Index Allocation Map (IAM) page has a sequence number.</span></span> <span data-ttu-id="d29d8-119">シーケンス番号は、IAM チェーン内における IAM ページの位置を表します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-119">The sequence number is the position of the IAM page within the IAM chain.</span></span> <span data-ttu-id="d29d8-120">シーケンス番号には、IAM ページごとに値が 1 ずつ増加するという規則があります。</span><span class="sxs-lookup"><span data-stu-id="d29d8-120">The rule is that sequence numbers increase by one for each IAM page.</span></span> <span data-ttu-id="d29d8-121">IAM ページ *P_ID2* には、この規則に従わないシーケンス番号が付けられています。</span><span class="sxs-lookup"><span data-stu-id="d29d8-121">IAM page, *P_ID2*, has a sequence number that does not follow this rule.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d29d8-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d29d8-122">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="d29d8-123">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="d29d8-123">Look for Hardware Failure</span></span>  
 <span data-ttu-id="d29d8-124">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-124">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="d29d8-125">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-125">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="d29d8-126">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-126">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d29d8-127">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d29d8-127">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="d29d8-128">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-128">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="d29d8-129">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d29d8-129">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="d29d8-130">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="d29d8-130">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="d29d8-131">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d29d8-131">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="d29d8-132">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="d29d8-132">Restore from Backup</span></span>  
 <span data-ttu-id="d29d8-133">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-133">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="d29d8-134">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="d29d8-134">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="d29d8-135">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="d29d8-135">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="d29d8-136">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="d29d8-136">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="d29d8-137">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-137">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d29d8-138">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d29d8-138">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="d29d8-139">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d29d8-139">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="d29d8-140">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="d29d8-140">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="d29d8-141">REPAIR を実行すると、IAM チェーンが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="d29d8-141">Running REPAIR will rebuild the IAM chain.</span></span> <span data-ttu-id="d29d8-142">REPAIR はまず、既存の IAM チェーンを半分ずつに分割します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-142">REPAIR first splits the existing IAM chain in two halves.</span></span> <span data-ttu-id="d29d8-143">チェーンの前半は IAM ページ *P_ID1* で終わります。</span><span class="sxs-lookup"><span data-stu-id="d29d8-143">The first half of the chain will end with IAM page, *P_ID1*.</span></span> <span data-ttu-id="d29d8-144">*P_ID1* ページの次ページ ポインターは、(0:0) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d29d8-144">The next page pointer of the *P_ID1* page will be set to (0:0).</span></span> <span data-ttu-id="d29d8-145">チェーンの後半は IAM ページ *P_ID2* から始まります。</span><span class="sxs-lookup"><span data-stu-id="d29d8-145">The second half of the chain will start with IAM page, *P_ID2*.</span></span> <span data-ttu-id="d29d8-146">*P_ID2* ページの前ページ ポインターは、(0:0) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d29d8-146">The previous page pointer of the *P_ID2* page will be set to (0:0).</span></span>  
  
 <span data-ttu-id="d29d8-147">次に REPAIR は、この 2 つのチェーンを接続し、IAM チェーンのシーケンス番号を再生成します。</span><span class="sxs-lookup"><span data-stu-id="d29d8-147">REPAIR will then connect the two haves of the chain together and regenerate the sequence numbers for the IAM chain.</span></span> <span data-ttu-id="d29d8-148">修復できない IAM ページがあれば、その割り当ては解除されます。</span><span class="sxs-lookup"><span data-stu-id="d29d8-148">Any IAM pages that cannot be repaired will be deallocated.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d29d8-149">この修復を実行すると、データが失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="d29d8-149">This repair may cause data loss.</span></span>  
  
  
