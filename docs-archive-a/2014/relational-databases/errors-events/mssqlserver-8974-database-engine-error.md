---
title: MSSQLSERVER_8974 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8974 (Database Engine error)
ms.assetid: 52098678-0858-4a14-ad07-37ebbafca5fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff3107f5b62caf04e232532c2d2b93d5da19fb53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646161"
---
# <a name="mssqlserver_8974"></a><span data-ttu-id="a61cd-102">MSSQLSERVER_8974</span><span class="sxs-lookup"><span data-stu-id="a61cd-102">MSSQLSERVER_8974</span></span>
    
## <a name="details"></a><span data-ttu-id="a61cd-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a61cd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a61cd-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a61cd-104">Product Name</span></span>|<span data-ttu-id="a61cd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a61cd-105">SQL Server</span></span>|  
|<span data-ttu-id="a61cd-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a61cd-106">Event ID</span></span>|<span data-ttu-id="a61cd-107">8974</span><span class="sxs-lookup"><span data-stu-id="a61cd-107">8974</span></span>|  
|<span data-ttu-id="a61cd-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a61cd-108">Event Source</span></span>|<span data-ttu-id="a61cd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a61cd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a61cd-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a61cd-110">Component</span></span>|<span data-ttu-id="a61cd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a61cd-111">SQLEngine</span></span>|  
|<span data-ttu-id="a61cd-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a61cd-112">Symbolic Name</span></span>|<span data-ttu-id="a61cd-113">DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS</span><span class="sxs-lookup"><span data-stu-id="a61cd-113">DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS</span></span>|  
|<span data-ttu-id="a61cd-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a61cd-114">Message Text</span></span>|<span data-ttu-id="a61cd-115">テーブル エラー:オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE)。</span><span class="sxs-lookup"><span data-stu-id="a61cd-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="a61cd-116">ページ P_ID1、スロット S_ID1、テキスト ID TEXT_ID の行以外のデータ ノードが、ページ P_ID2、スロット S_ID2 とページ P_ID3、スロット P_ID3 によって指されています。</span><span class="sxs-lookup"><span data-stu-id="a61cd-116">The off-row data node at page P_ID1, slot S_ID1, text ID TEXT_ID is pointed to by page P_ID2, slot S_ID2 and by page P_ID3, slot P_ID3.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a61cd-117">説明</span><span class="sxs-lookup"><span data-stu-id="a61cd-117">Explanation</span></span>  
 <span data-ttu-id="a61cd-118">行外のデータ ノードが、2 件のデータ レコードまたはインデックス レコードで、子ノードの一覧に含まれています。</span><span class="sxs-lookup"><span data-stu-id="a61cd-118">An off-row data node has two data or index records that list it as a child node.</span></span> <span data-ttu-id="a61cd-119">各ノードに対して可能な親ノードは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="a61cd-119">A node can have only one parent node.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a61cd-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a61cd-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="a61cd-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="a61cd-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="a61cd-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="a61cd-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="a61cd-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a61cd-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="a61cd-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="a61cd-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="a61cd-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a61cd-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="a61cd-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a61cd-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="a61cd-127">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="a61cd-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="a61cd-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="a61cd-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="a61cd-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a61cd-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="a61cd-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="a61cd-130">Restore from Backup</span></span>  
 <span data-ttu-id="a61cd-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="a61cd-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="a61cd-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="a61cd-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="a61cd-133">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="a61cd-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="a61cd-134">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="a61cd-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="a61cd-135">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="a61cd-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a61cd-136">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="a61cd-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="a61cd-137">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="a61cd-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="a61cd-138">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="a61cd-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="a61cd-139">ページ *P_ID1* にある行以外のデータ ノードが削除され、ページ *P_ID2* および *P_ID3* にある参照がどちらも削除されます。</span><span class="sxs-lookup"><span data-stu-id="a61cd-139">The off-row data node on page *P_ID1* will be deleted and both references on pages *P_ID2* and *P_ID3* will be deleted.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a61cd-140">この修復を実行すると、データが失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="a61cd-140">This repair might cause data loss.</span></span>  
  
  
