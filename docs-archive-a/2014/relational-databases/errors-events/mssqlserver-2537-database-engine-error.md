---
title: MSSQLSERVER_2537 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2537 (Database Engine error)
ms.assetid: 0af6ff69-d75a-4c39-8da2-9bd0695277c6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c227867bac5a0ea5789ba653414444d011e5910d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643879"
---
# <a name="mssqlserver_2537"></a><span data-ttu-id="19acd-102">MSSQLSERVER_2537</span><span class="sxs-lookup"><span data-stu-id="19acd-102">MSSQLSERVER_2537</span></span>
    
## <a name="details"></a><span data-ttu-id="19acd-103">詳細</span><span class="sxs-lookup"><span data-stu-id="19acd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19acd-104">製品名</span><span class="sxs-lookup"><span data-stu-id="19acd-104">Product Name</span></span>|<span data-ttu-id="19acd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="19acd-105">SQL Server</span></span>|  
|<span data-ttu-id="19acd-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="19acd-106">Event ID</span></span>|<span data-ttu-id="19acd-107">2537</span><span class="sxs-lookup"><span data-stu-id="19acd-107">2537</span></span>|  
|<span data-ttu-id="19acd-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="19acd-108">Event Source</span></span>|<span data-ttu-id="19acd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="19acd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="19acd-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="19acd-110">Component</span></span>|<span data-ttu-id="19acd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="19acd-111">SQLEngine</span></span>|  
|<span data-ttu-id="19acd-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="19acd-112">Symbolic Name</span></span>|<span data-ttu-id="19acd-113">DBCC_RECORD_CHECK_FAILED</span><span class="sxs-lookup"><span data-stu-id="19acd-113">DBCC_RECORD_CHECK_FAILED</span></span>|  
|<span data-ttu-id="19acd-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="19acd-114">Message Text</span></span>|<span data-ttu-id="19acd-115">テーブル エラー:オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE)、ページ P_ID、行 ROW_ID。</span><span class="sxs-lookup"><span data-stu-id="19acd-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), page P_ID, row ROW_ID.</span></span> <span data-ttu-id="19acd-116">レコード チェック (CHECK_TEXT) が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="19acd-116">Record check (CHECK_TEXT) failed.</span></span> <span data-ttu-id="19acd-117">値は VALUE1 および VALUE2 です。</span><span class="sxs-lookup"><span data-stu-id="19acd-117">Values are VALUE1 and VALUE2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="19acd-118">説明</span><span class="sxs-lookup"><span data-stu-id="19acd-118">Explanation</span></span>  
 <span data-ttu-id="19acd-119">行 ROW_ID (または行内の列) が、CHECK_TEXT に記述されているテストまたは条件をクリアできませんでした。</span><span class="sxs-lookup"><span data-stu-id="19acd-119">The row ROW_ID (or a column in the row) failed the test or condition described by CHECK_TEXT.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="19acd-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="19acd-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="19acd-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="19acd-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="19acd-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="19acd-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="19acd-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="19acd-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="19acd-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="19acd-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="19acd-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="19acd-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="19acd-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="19acd-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="19acd-127">書き込みキャッシュが問題であると思われる場合は、ハードウェアの製造元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="19acd-127">If you suspect that write-caching is the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="19acd-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="19acd-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="19acd-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="19acd-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="19acd-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="19acd-130">Restore from Backup</span></span>  
 <span data-ttu-id="19acd-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="19acd-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="19acd-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="19acd-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="19acd-133">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="19acd-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="19acd-134">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="19acd-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="19acd-135">その REPAIR 句を付けて DBCC CHECKDB を実行します。</span><span class="sxs-lookup"><span data-stu-id="19acd-135">Then, run DBCC CHECKDB with the recommended REPAIR clause.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="19acd-136">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="19acd-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="19acd-137">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="19acd-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="19acd-138">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="19acd-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="19acd-139">インデックスが存在する場合は、REPAIR によりインデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="19acd-139">REPAIR will rebuild the index if an index exists.</span></span>  
  
 <span data-ttu-id="19acd-140">**注意** この修復を実行すると、データが失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="19acd-140">**Caution** This repair may cause data loss.</span></span>  
  
  
