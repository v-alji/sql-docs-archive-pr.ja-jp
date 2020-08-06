---
title: MSSQLSERVER_2534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2534 (Database Engine error)
ms.assetid: 121cf99d-0722-494c-be24-3369c1a0badc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 409c429f961cd8357bfa2e40663c33f3c1f2e36d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643884"
---
# <a name="mssqlserver_2534"></a><span data-ttu-id="31d36-102">MSSQLSERVER_2534</span><span class="sxs-lookup"><span data-stu-id="31d36-102">MSSQLSERVER_2534</span></span>
    
## <a name="details"></a><span data-ttu-id="31d36-103">詳細</span><span class="sxs-lookup"><span data-stu-id="31d36-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31d36-104">製品名</span><span class="sxs-lookup"><span data-stu-id="31d36-104">Product Name</span></span>|<span data-ttu-id="31d36-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="31d36-105">SQL Server</span></span>|  
|<span data-ttu-id="31d36-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="31d36-106">Event ID</span></span>|<span data-ttu-id="31d36-107">2534</span><span class="sxs-lookup"><span data-stu-id="31d36-107">2534</span></span>|  
|<span data-ttu-id="31d36-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="31d36-108">Event Source</span></span>|<span data-ttu-id="31d36-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="31d36-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="31d36-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="31d36-110">Component</span></span>|<span data-ttu-id="31d36-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="31d36-111">SQLEngine</span></span>|  
|<span data-ttu-id="31d36-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="31d36-112">Symbolic Name</span></span>|<span data-ttu-id="31d36-113">DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="31d36-113">DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT</span></span>|  
|<span data-ttu-id="31d36-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="31d36-114">Message Text</span></span>|<span data-ttu-id="31d36-115">テーブル エラー:ページ P_ID が別のオブジェクトによって割り当てられています。このページのヘッダーは、ページがオブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) に割り当てられていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="31d36-115">Table error: Page P_ID, whose header indicates it as being allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), is allocated by another object.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="31d36-116">説明</span><span class="sxs-lookup"><span data-stu-id="31d36-116">Explanation</span></span>  
 <span data-ttu-id="31d36-117">ページのヘッダーにはアロケーション ユニット ID、*A_ID* が含まれていますが、このアロケーション ユニットのどの IAM (Index Allocation Map) ページにもこのページが割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="31d36-117">The header of the page contains the allocation unit ID, *A_ID*, but none of the Index Allocation Map (IAM) pages of that allocation unit allocates the page.</span></span> <span data-ttu-id="31d36-118">ページのヘッダーに含まれているアロケーション ユニット ID は誤りであり、ページが実際に割り当てられているアロケーション ユニット ID に対応した MSSQLServer_2533 エラーがこのページで生じます。</span><span class="sxs-lookup"><span data-stu-id="31d36-118">Therefore, the header of the page contains the wrong allocation unit ID, and the page will have a matching MSSQLServer_2533 error that corresponds to the allocation unit ID to which the page is actually allocated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="31d36-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="31d36-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="31d36-120">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="31d36-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="31d36-121">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="31d36-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="31d36-122">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="31d36-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="31d36-123">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="31d36-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="31d36-124">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="31d36-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="31d36-125">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="31d36-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="31d36-126">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="31d36-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="31d36-127">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="31d36-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="31d36-128">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="31d36-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="31d36-129">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="31d36-129">Restore from Backup</span></span>  
 <span data-ttu-id="31d36-130">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="31d36-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="31d36-131">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="31d36-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="31d36-132">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="31d36-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="31d36-133">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="31d36-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="31d36-134">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="31d36-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="31d36-135">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="31d36-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="31d36-136">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="31d36-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="31d36-137">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="31d36-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="31d36-138">インデックスが存在する場合は、REPAIR によりインデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="31d36-138">REPAIR will rebuild the index if an index exists.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="31d36-139">対応する [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) エラーに対して REPAIR を実行すると、再構築の前にページの割り当てが解除されます。</span><span class="sxs-lookup"><span data-stu-id="31d36-139">Running REPAIR for the matching [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) error deallocates the page before the rebuild.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="31d36-140">この修復を実行すると、データが失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="31d36-140">This repair may cause data loss.</span></span>  
  
  
