---
title: MSSQLSERVER_2512 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2512 (Database Engine error)
ms.assetid: 989b527f-5b02-403c-9b7f-51580f4e7688
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da121c8b49ab8290c494d33f0f2a0ba6fded9e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714393"
---
# <a name="mssqlserver_2512"></a><span data-ttu-id="ba6d4-102">MSSQLSERVER_2512</span><span class="sxs-lookup"><span data-stu-id="ba6d4-102">MSSQLSERVER_2512</span></span>
    
## <a name="details"></a><span data-ttu-id="ba6d4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="ba6d4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba6d4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ba6d4-104">Product Name</span></span>|<span data-ttu-id="ba6d4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ba6d4-105">SQL Server</span></span>|  
|<span data-ttu-id="ba6d4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ba6d4-106">Event ID</span></span>|<span data-ttu-id="ba6d4-107">2512</span><span class="sxs-lookup"><span data-stu-id="ba6d4-107">2512</span></span>|  
|<span data-ttu-id="ba6d4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ba6d4-108">Event Source</span></span>|<span data-ttu-id="ba6d4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ba6d4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ba6d4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ba6d4-110">Component</span></span>|<span data-ttu-id="ba6d4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ba6d4-111">SQLEngine</span></span>|  
|<span data-ttu-id="ba6d4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ba6d4-112">Symbolic Name</span></span>|<span data-ttu-id="ba6d4-113">DBCC_DUPLICATE_KEYS</span><span class="sxs-lookup"><span data-stu-id="ba6d4-113">DBCC_DUPLICATE_KEYS</span></span>|  
|<span data-ttu-id="ba6d4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ba6d4-114">Message Text</span></span>|<span data-ttu-id="ba6d4-115">テーブル エラー:オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE)。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="ba6d4-116">ページ P_ID1 スロット SLOT1 とページ P_ID2 スロット SLOT2 でキーが重複しています。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-116">Duplicate keys on page P_ID1 slot SLOT1 and page P_ID2 slot SLOT2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ba6d4-117">説明</span><span class="sxs-lookup"><span data-stu-id="ba6d4-117">Explanation</span></span>  
 <span data-ttu-id="ba6d4-118">`uniqueifiers` を含めて、示されている 2 つのスロットのキーが同じです。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-118">The two specified slots have identical keys, including any `uniqueifiers`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ba6d4-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ba6d4-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="ba6d4-120">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="ba6d4-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="ba6d4-121">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="ba6d4-122">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="ba6d4-123">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="ba6d4-124">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="ba6d4-125">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="ba6d4-126">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="ba6d4-127">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="ba6d4-128">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="ba6d4-129">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="ba6d4-129">Restore from Backup</span></span>  
 <span data-ttu-id="ba6d4-130">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="ba6d4-131">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="ba6d4-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="ba6d4-132">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="ba6d4-133">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="ba6d4-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="ba6d4-134">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ba6d4-135">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="ba6d4-136">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="ba6d4-137">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="ba6d4-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="ba6d4-138">レコードが非実体レコードである場合またはインデックスが一意でない場合は、DBCC によるインデックスの再構築でこの問題を修復できます。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-138">If either record is a ghost or the index is nonunique, DBCC can repair this problem by rebuilding the index.</span></span> <span data-ttu-id="ba6d4-139">これ以外の場合、REPAIR により、必要に応じてページ *P_ID2* のスロット *SLOT2* を削除するか、非実体スロットとして設定するか、いずれかの処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="ba6d4-139">Otherwise, if necessary, REPAIR will delete slot *SLOT2* on page *P_ID2* or mark the slot as a ghost.</span></span>  
  
  
