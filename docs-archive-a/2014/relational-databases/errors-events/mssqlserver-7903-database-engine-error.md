---
title: MSSQLSERVER_7903 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7903 (Database Engine error)
ms.assetid: 991a86df-42cd-435e-85b3-f42e4cb13039
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e30247c5c858cf8ce6dcd75e41f1fb567e974201
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640970"
---
# <a name="mssqlserver_7903"></a><span data-ttu-id="0d6c1-102">MSSQLSERVER_7903</span><span class="sxs-lookup"><span data-stu-id="0d6c1-102">MSSQLSERVER_7903</span></span>
    
## <a name="details"></a><span data-ttu-id="0d6c1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="0d6c1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d6c1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="0d6c1-104">Product Name</span></span>|<span data-ttu-id="0d6c1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0d6c1-105">SQL Server</span></span>|  
|<span data-ttu-id="0d6c1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0d6c1-106">Event ID</span></span>|<span data-ttu-id="0d6c1-107">7903</span><span class="sxs-lookup"><span data-stu-id="0d6c1-107">7903</span></span>|  
|<span data-ttu-id="0d6c1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="0d6c1-108">Event Source</span></span>|<span data-ttu-id="0d6c1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0d6c1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0d6c1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0d6c1-110">Component</span></span>|<span data-ttu-id="0d6c1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0d6c1-111">SQLEngine</span></span>|  
|<span data-ttu-id="0d6c1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="0d6c1-112">Symbolic Name</span></span>|<span data-ttu-id="0d6c1-113">DBCC2_FS_ORPHANED_FILE</span><span class="sxs-lookup"><span data-stu-id="0d6c1-113">DBCC2_FS_ORPHANED_FILE</span></span>|  
|<span data-ttu-id="0d6c1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="0d6c1-114">Message Text</span></span>|<span data-ttu-id="0d6c1-115">テーブル エラー:孤立したファイル 'FILE' が、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、列 ID C_ID の Filestream ディレクトリに見つかりました。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-115">Table error: The orphaned file 'FILE' was found in the Filestream directory for object ID O_ID, index ID I_ID, partition ID PN_ID, column ID C_ID.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d6c1-116">説明</span><span class="sxs-lookup"><span data-stu-id="0d6c1-116">Explanation</span></span>  
 <span data-ttu-id="0d6c1-117">FILESTREAM 列ディレクトリ内で FILESTREAM ファイルが検出されましたが、パーティション内の対応する列値がありません。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-117">A FILESTREAM file was found in a FILESTREAM column directory; however, the corresponding column value in the partition is missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d6c1-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="0d6c1-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="0d6c1-119">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="0d6c1-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="0d6c1-120">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="0d6c1-121">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="0d6c1-122">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="0d6c1-123">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="0d6c1-124">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="0d6c1-125">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="0d6c1-126">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="0d6c1-127">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="0d6c1-128">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="0d6c1-128">Restore from Backup</span></span>  
 <span data-ttu-id="0d6c1-129">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="0d6c1-130">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="0d6c1-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="0d6c1-131">適用不可。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-131">Not applicable.</span></span> <span data-ttu-id="0d6c1-132">このエラーを修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-132">This error cannot be repaired.</span></span> <span data-ttu-id="0d6c1-133">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="0d6c1-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
