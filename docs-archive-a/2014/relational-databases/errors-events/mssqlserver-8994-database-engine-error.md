---
title: MSSQLSERVER_8994 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8994 (Database Engine error)
ms.assetid: 8f4b0e2f-04c0-46e4-9208-20a7085d7a1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0bcc0b1db100b70390c09e9c825dbfd068d968af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631973"
---
# <a name="mssqlserver_8994"></a><span data-ttu-id="18f15-102">MSSQLSERVER_8994</span><span class="sxs-lookup"><span data-stu-id="18f15-102">MSSQLSERVER_8994</span></span>
    
## <a name="details"></a><span data-ttu-id="18f15-103">詳細</span><span class="sxs-lookup"><span data-stu-id="18f15-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18f15-104">製品名</span><span class="sxs-lookup"><span data-stu-id="18f15-104">Product Name</span></span>|<span data-ttu-id="18f15-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="18f15-105">SQL Server</span></span>|  
|<span data-ttu-id="18f15-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="18f15-106">Event ID</span></span>|<span data-ttu-id="18f15-107">8994</span><span class="sxs-lookup"><span data-stu-id="18f15-107">8994</span></span>|  
|<span data-ttu-id="18f15-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="18f15-108">Event Source</span></span>|<span data-ttu-id="18f15-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="18f15-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="18f15-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="18f15-110">Component</span></span>|<span data-ttu-id="18f15-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="18f15-111">SQLEngine</span></span>|  
|<span data-ttu-id="18f15-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="18f15-112">Symbolic Name</span></span>|<span data-ttu-id="18f15-113">DBCC3_MISSING_FORWARDING_ROW</span><span class="sxs-lookup"><span data-stu-id="18f15-113">DBCC3_MISSING_FORWARDING_ROW</span></span>|  
|<span data-ttu-id="18f15-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="18f15-114">Message Text</span></span>|<span data-ttu-id="18f15-115">オブジェクト ID O_ID、転送先の行のページ P_ID2、スロット S_ID2 は、転送元の行のページ P_ID1、スロット S_ID1 を指す必要があります。</span><span class="sxs-lookup"><span data-stu-id="18f15-115">Object ID O_ID, forwarded row page P_ID1, slot S_ID1 should be pointed to by forwarding row page P_ID2, slot S_ID2.</span></span> <span data-ttu-id="18f15-116">転送先の行が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="18f15-116">Did not encounter forwarding row.</span></span> <span data-ttu-id="18f15-117">アロケーション エラーが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18f15-117">Possible allocation error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="18f15-118">説明</span><span class="sxs-lookup"><span data-stu-id="18f15-118">Explanation</span></span>  
 <span data-ttu-id="18f15-119">ヒープ内の転送先の行を指しているはずの転送元の行がありません。</span><span class="sxs-lookup"><span data-stu-id="18f15-119">A forwarded row in a heap is missing the forwarding row that should point to it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="18f15-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="18f15-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="18f15-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="18f15-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="18f15-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="18f15-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="18f15-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f15-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="18f15-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="18f15-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="18f15-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="18f15-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="18f15-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f15-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="18f15-127">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="18f15-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="18f15-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="18f15-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="18f15-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="18f15-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="18f15-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="18f15-130">Restore from Backup</span></span>  
 <span data-ttu-id="18f15-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="18f15-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="18f15-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="18f15-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="18f15-133">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="18f15-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="18f15-134">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="18f15-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="18f15-135">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="18f15-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="18f15-136">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="18f15-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="18f15-137">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="18f15-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="18f15-138">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="18f15-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="18f15-139">転送された行は、通常のデータ行に変換されます。</span><span class="sxs-lookup"><span data-stu-id="18f15-139">The forwarded row will be converted to a regular data row.</span></span>  
  
  
