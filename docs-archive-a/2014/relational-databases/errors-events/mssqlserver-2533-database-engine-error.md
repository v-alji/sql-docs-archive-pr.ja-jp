---
title: MSSQLSERVER_2533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2533 (Database Engine error)
ms.assetid: 0418352c-0ab2-4dc7-b8b9-5c3bad94560c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1eb3e2780693a3a0ffed21ce7b9d7887615536c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715310"
---
# <a name="mssqlserver_2533"></a><span data-ttu-id="12e25-102">MSSQLSERVER_2533</span><span class="sxs-lookup"><span data-stu-id="12e25-102">MSSQLSERVER_2533</span></span>
    
## <a name="details"></a><span data-ttu-id="12e25-103">詳細</span><span class="sxs-lookup"><span data-stu-id="12e25-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12e25-104">製品名</span><span class="sxs-lookup"><span data-stu-id="12e25-104">Product Name</span></span>|<span data-ttu-id="12e25-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="12e25-105">SQL Server</span></span>|  
|<span data-ttu-id="12e25-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="12e25-106">Event ID</span></span>|<span data-ttu-id="12e25-107">2533</span><span class="sxs-lookup"><span data-stu-id="12e25-107">2533</span></span>|  
|<span data-ttu-id="12e25-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="12e25-108">Event Source</span></span>|<span data-ttu-id="12e25-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="12e25-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="12e25-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="12e25-110">Component</span></span>|<span data-ttu-id="12e25-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="12e25-111">SQLEngine</span></span>|  
|<span data-ttu-id="12e25-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="12e25-112">Symbolic Name</span></span>|<span data-ttu-id="12e25-113">DBCC_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="12e25-113">DBCC_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="12e25-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="12e25-114">Message Text</span></span>|<span data-ttu-id="12e25-115">テーブル エラー:オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) に割り当てられたページ P_ID が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="12e25-115">Table error: Page P_ID allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) was not seen.</span></span> <span data-ttu-id="12e25-116">このページが無効であるか、ページのヘッダー内に不適切なアロケーション ユニット ID がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="12e25-116">Page may be invalid or have incorrect alloc unit ID in its header.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="12e25-117">説明</span><span class="sxs-lookup"><span data-stu-id="12e25-117">Explanation</span></span>  
 <span data-ttu-id="12e25-118">アロケーション ユニット ID、*A_ID* にページが割り当てられましたが、このアロケーション ユニット ID がページのヘッダー内にありません。</span><span class="sxs-lookup"><span data-stu-id="12e25-118">A page is allocated to the allocation unit ID, *A_ID*, but this allocation unit ID is not in the header of the page.</span></span> <span data-ttu-id="12e25-119">ヘッダー内には別のアロケーション ユニット ID があります。</span><span class="sxs-lookup"><span data-stu-id="12e25-119">The header has a different allocation unit ID.</span></span> <span data-ttu-id="12e25-120">ページのヘッダー内にあるアロケーション ユニット ID が有効なオブジェクトに対するものであれば、対応する MSSQLEngine_2534 エラーがこのページで生じている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="12e25-120">If the allocation unit ID in the header of the page is for a valid object, the page may have a matching MSSQLEngine_2534 error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="12e25-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="12e25-121">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="12e25-122">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="12e25-122">Look for Hardware Failure</span></span>  
 <span data-ttu-id="12e25-123">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="12e25-123">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="12e25-124">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="12e25-124">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="12e25-125">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="12e25-125">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="12e25-126">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="12e25-126">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="12e25-127">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="12e25-127">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="12e25-128">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="12e25-128">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="12e25-129">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="12e25-129">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="12e25-130">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="12e25-130">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="12e25-131">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="12e25-131">Restore from Backup</span></span>  
 <span data-ttu-id="12e25-132">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="12e25-132">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="12e25-133">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="12e25-133">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="12e25-134">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="12e25-134">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="12e25-135">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="12e25-135">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="12e25-136">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="12e25-136">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="12e25-137">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="12e25-137">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="12e25-138">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="12e25-138">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="12e25-139">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="12e25-139">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="12e25-140">REPAIR により、このページの割り当てが解除されます。</span><span class="sxs-lookup"><span data-stu-id="12e25-140">REPAIR will deallocate the page.</span></span> <span data-ttu-id="12e25-141">このページが行内データ アロケーション ユニットのものであれば、(インデックスが存在する場合は) インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="12e25-141">If the page was from an in-row data allocation unit, the index, if one exists, will be rebuilt.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="12e25-142">この修復を実行すると、データが失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="12e25-142">This repair may cause data loss.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e25-143">参照</span><span class="sxs-lookup"><span data-stu-id="12e25-143">See Also</span></span>  
 [<span data-ttu-id="12e25-144">MSSQLSERVER_2534</span><span class="sxs-lookup"><span data-stu-id="12e25-144">MSSQLSERVER_2534</span></span>](mssqlserver-2534-database-engine-error.md)  
  
  
