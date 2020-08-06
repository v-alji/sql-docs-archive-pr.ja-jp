---
title: MSSQLSERVER_2575 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2575 (Database Engine error)
ms.assetid: 92dfe449-a122-4730-942b-e1d319862d20
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 461d2b57b5ace98ca624f8dc3717c98f3e9e4d67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631982"
---
# <a name="mssqlserver_2575"></a><span data-ttu-id="4ef1f-102">MSSQLSERVER_2575</span><span class="sxs-lookup"><span data-stu-id="4ef1f-102">MSSQLSERVER_2575</span></span>
    
## <a name="details"></a><span data-ttu-id="4ef1f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4ef1f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ef1f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4ef1f-104">Product Name</span></span>|<span data-ttu-id="4ef1f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4ef1f-105">SQL Server</span></span>|  
|<span data-ttu-id="4ef1f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4ef1f-106">Event ID</span></span>|<span data-ttu-id="4ef1f-107">2575</span><span class="sxs-lookup"><span data-stu-id="4ef1f-107">2575</span></span>|  
|<span data-ttu-id="4ef1f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4ef1f-108">Event Source</span></span>|<span data-ttu-id="4ef1f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4ef1f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4ef1f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4ef1f-110">Component</span></span>|<span data-ttu-id="4ef1f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4ef1f-111">SQLEngine</span></span>|  
|<span data-ttu-id="4ef1f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4ef1f-112">Symbolic Name</span></span>|<span data-ttu-id="4ef1f-113">DBCC_IAM_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="4ef1f-113">DBCC_IAM_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="4ef1f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4ef1f-114">Message Text</span></span>|<span data-ttu-id="4ef1f-115">オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) の IAM ページ P_ID2 の次のポインターは、IAM ページ P_ID1 を指していますが、スキャンでは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-115">IAM page P_ID1 is pointed to by the next pointer of IAM page P_ID2 in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) but was not detected in the scan.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4ef1f-116">説明</span><span class="sxs-lookup"><span data-stu-id="4ef1f-116">Explanation</span></span>  
 <span data-ttu-id="4ef1f-117">指定されたインデックスに対応する IAM (Index Allocation Map) ページは見つかりましたが、次ページ ポインターに対応する IAM ページが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-117">An Index Allocation Map (IAM) page was found for the specified index; however, the IAM page for its next-page pointer was not found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4ef1f-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4ef1f-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="4ef1f-119">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="4ef1f-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="4ef1f-120">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="4ef1f-121">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="4ef1f-122">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="4ef1f-123">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="4ef1f-124">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="4ef1f-125">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="4ef1f-126">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="4ef1f-127">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="4ef1f-128">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="4ef1f-128">Restore from Backup</span></span>  
 <span data-ttu-id="4ef1f-129">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="4ef1f-130">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="4ef1f-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="4ef1f-131">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-131">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="4ef1f-132">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="4ef1f-132">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="4ef1f-133">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-133">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="4ef1f-134">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-134">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="4ef1f-135">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-135">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="4ef1f-136">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="4ef1f-136">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="4ef1f-137">DBCC により、インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="4ef1f-137">DBCC will rebuild the index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef1f-138">参照</span><span class="sxs-lookup"><span data-stu-id="4ef1f-138">See Also</span></span>  
 [<span data-ttu-id="4ef1f-139">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4ef1f-139">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
