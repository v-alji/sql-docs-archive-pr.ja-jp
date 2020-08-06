---
title: MSSQLSERVER_8996 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8996 (Database Engine error)
ms.assetid: 4e655cdc-945a-4a18-95dd-75f050563d26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d0cb5f0294ea471a6e300adbabc0f7b55632994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643840"
---
# <a name="mssqlserver_8996"></a><span data-ttu-id="518e2-102">MSSQLSERVER_8996</span><span class="sxs-lookup"><span data-stu-id="518e2-102">MSSQLSERVER_8996</span></span>
    
## <a name="details"></a><span data-ttu-id="518e2-103">詳細</span><span class="sxs-lookup"><span data-stu-id="518e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="518e2-104">製品名</span><span class="sxs-lookup"><span data-stu-id="518e2-104">Product Name</span></span>|<span data-ttu-id="518e2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="518e2-105">SQL Server</span></span>|  
|<span data-ttu-id="518e2-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="518e2-106">Event ID</span></span>|<span data-ttu-id="518e2-107">8996</span><span class="sxs-lookup"><span data-stu-id="518e2-107">8996</span></span>|  
|<span data-ttu-id="518e2-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="518e2-108">Event Source</span></span>|<span data-ttu-id="518e2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="518e2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="518e2-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="518e2-110">Component</span></span>|<span data-ttu-id="518e2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="518e2-111">SQLEngine</span></span>|  
|<span data-ttu-id="518e2-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="518e2-112">Symbolic Name</span></span>|<span data-ttu-id="518e2-113">DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP</span><span class="sxs-lookup"><span data-stu-id="518e2-113">DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP</span></span>|  
|<span data-ttu-id="518e2-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="518e2-114">Message Text</span></span>|<span data-ttu-id="518e2-115">オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) の IAM ページ P_ID は、ファイル グループ FG_ID1 のページを制御しています。このページは、正しくはファイル グループ FG_ID2 に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="518e2-115">IAM page P_ID for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) controls pages in filegroup FG_ID1, that should be in filegroup FG_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="518e2-116">説明</span><span class="sxs-lookup"><span data-stu-id="518e2-116">Explanation</span></span>  
 <span data-ttu-id="518e2-117">ファイル グループ *FG_ID1* の IAM (Index Allocation Map) ページ *P_ID* に、誤ってファイル グループ *FG_ID2* のエクステントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="518e2-117">The index allocation map (IAM) page *P_ID* in filegroup *FG_ID1* incorrectly includes extents from filegroup *FG_ID2*.</span></span> <span data-ttu-id="518e2-118">同じ IAM ページ内のエクステントはすべて、その IAM ページと同じファイル グループに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="518e2-118">All extents for an IAM page should be in the same filegroup as the IAM page itself.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="518e2-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="518e2-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="518e2-120">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="518e2-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="518e2-121">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="518e2-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="518e2-122">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="518e2-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="518e2-123">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="518e2-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="518e2-124">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="518e2-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="518e2-125">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="518e2-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="518e2-126">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="518e2-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="518e2-127">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="518e2-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="518e2-128">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="518e2-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="518e2-129">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="518e2-129">Restore from Backup</span></span>  
 <span data-ttu-id="518e2-130">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="518e2-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="518e2-131">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="518e2-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="518e2-132">適用不可。</span><span class="sxs-lookup"><span data-stu-id="518e2-132">Not applicable.</span></span> <span data-ttu-id="518e2-133">このエラーを修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="518e2-133">This error cannot be repaired.</span></span> <span data-ttu-id="518e2-134">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="518e2-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
