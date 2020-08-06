---
title: MSSQLSERVER_7935 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7935 (Database Engine error)
ms.assetid: 45ab21a3-024a-4523-9bd9-1175d01f9c8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a798438213fecf7a6867056c5fe1db033bc6beb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641657"
---
# <a name="mssqlserver_7935"></a><span data-ttu-id="73372-102">MSSQLSERVER_7935</span><span class="sxs-lookup"><span data-stu-id="73372-102">MSSQLSERVER_7935</span></span>
    
## <a name="details"></a><span data-ttu-id="73372-103">詳細</span><span class="sxs-lookup"><span data-stu-id="73372-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73372-104">製品名</span><span class="sxs-lookup"><span data-stu-id="73372-104">Product Name</span></span>|<span data-ttu-id="73372-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="73372-105">SQL Server</span></span>|  
|<span data-ttu-id="73372-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="73372-106">Event ID</span></span>|<span data-ttu-id="73372-107">7935</span><span class="sxs-lookup"><span data-stu-id="73372-107">7935</span></span>|  
|<span data-ttu-id="73372-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="73372-108">Event Source</span></span>|<span data-ttu-id="73372-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="73372-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="73372-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="73372-110">Component</span></span>|<span data-ttu-id="73372-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="73372-111">SQLEngine</span></span>|  
|<span data-ttu-id="73372-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="73372-112">Symbolic Name</span></span>|<span data-ttu-id="73372-113">DBCC2_FS_MISSING_COLUMN</span><span class="sxs-lookup"><span data-stu-id="73372-113">DBCC2_FS_MISSING_COLUMN</span></span>|  
|<span data-ttu-id="73372-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="73372-114">Message Text</span></span>|<span data-ttu-id="73372-115">テーブル エラー:FILESTREAM ディレクトリ ID F_ID は、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID の列に存在しますが、その列はパーティションに存在しません。</span><span class="sxs-lookup"><span data-stu-id="73372-115">Table error: A Filestream directory ID F_ID exists for a column of object ID O_ID, index ID I_ID, partition ID PN_ID, but that column does not exist in the partition.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="73372-116">説明</span><span class="sxs-lookup"><span data-stu-id="73372-116">Explanation</span></span>  
 <span data-ttu-id="73372-117">DBCC CHECKDB の実行中に、指定されたオブジェクト内の列に対応する FILESTREAM ディレクトリが検出されましたが、この列はパーティションの対応するメタデータでは検出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="73372-117">During DBCC CHECKDB, a FILESTREAM directory was found for a column in the specified object; however, the column was not found in the corresponding metadata of the partition.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="73372-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="73372-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="73372-119">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="73372-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="73372-120">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="73372-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="73372-121">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="73372-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="73372-122">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="73372-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="73372-123">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="73372-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="73372-124">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="73372-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="73372-125">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="73372-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="73372-126">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="73372-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="73372-127">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="73372-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="73372-128">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="73372-128">Restore from Backup</span></span>  
 <span data-ttu-id="73372-129">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="73372-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="73372-130">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="73372-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="73372-131">適用不可。</span><span class="sxs-lookup"><span data-stu-id="73372-131">Not applicable.</span></span> <span data-ttu-id="73372-132">このエラーを自動的に修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="73372-132">This error cannot be repaired automatically.</span></span> <span data-ttu-id="73372-133">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="73372-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
