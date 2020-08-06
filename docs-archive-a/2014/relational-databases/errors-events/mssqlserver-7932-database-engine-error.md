---
title: MSSQLSERVER_7932 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7932 (Database Engine error)
ms.assetid: e2ad218a-3249-4f18-8b32-09f0030765a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 237d9be3e0f22664adb061d3bba526c9878d3bfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641668"
---
# <a name="mssqlserver_7932"></a><span data-ttu-id="10df4-102">MSSQLSERVER_7932</span><span class="sxs-lookup"><span data-stu-id="10df4-102">MSSQLSERVER_7932</span></span>
    
## <a name="details"></a><span data-ttu-id="10df4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="10df4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10df4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="10df4-104">Product Name</span></span>|<span data-ttu-id="10df4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="10df4-105">SQL Server</span></span>|  
|<span data-ttu-id="10df4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="10df4-106">Event ID</span></span>|<span data-ttu-id="10df4-107">7932</span><span class="sxs-lookup"><span data-stu-id="10df4-107">7932</span></span>|  
|<span data-ttu-id="10df4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="10df4-108">Event Source</span></span>|<span data-ttu-id="10df4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="10df4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="10df4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="10df4-110">Component</span></span>|<span data-ttu-id="10df4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="10df4-111">SQLEngine</span></span>|  
|<span data-ttu-id="10df4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="10df4-112">Symbolic Name</span></span>|<span data-ttu-id="10df4-113">DBCC2_FS_ROWSET_IN_WRONG_FILEGROUP</span><span class="sxs-lookup"><span data-stu-id="10df4-113">DBCC2_FS_ROWSET_IN_WRONG_FILEGROUP</span></span>|  
|<span data-ttu-id="10df4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="10df4-114">Message Text</span></span>|<span data-ttu-id="10df4-115">テーブル エラー:オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID の FileStream ディレクトリ ID F_ID はファイル グループ FG_ID1 に存在しますが、ファイル グループ FG_ID2 に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10df4-115">Table error: The FileStream directory ID F_ID for object ID O_ID, index ID I_ID, partition ID PN_ID is in filegroup FG_ID1, but should be in filegroup FG_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="10df4-116">説明</span><span class="sxs-lookup"><span data-stu-id="10df4-116">Explanation</span></span>  
 <span data-ttu-id="10df4-117">DBCC CHECKDB の実行中に、指定されたオブジェクトの FILESTREAM ストレージが、間違ったファイル グループ内で検出されました。</span><span class="sxs-lookup"><span data-stu-id="10df4-117">During DBCC CHECKDB, the FILESTREAM storage for the specified object was detected in the wrong filegroup.</span></span> <span data-ttu-id="10df4-118">オブジェクトのメタデータが破損している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="10df4-118">This could be a corruption in the metadata of the object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10df4-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="10df4-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="10df4-120">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="10df4-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="10df4-121">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="10df4-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="10df4-122">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="10df4-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="10df4-123">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="10df4-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="10df4-124">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="10df4-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="10df4-125">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="10df4-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="10df4-126">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="10df4-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="10df4-127">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="10df4-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="10df4-128">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="10df4-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="10df4-129">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="10df4-129">Restore from Backup</span></span>  
 <span data-ttu-id="10df4-130">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="10df4-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="10df4-131">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="10df4-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="10df4-132">適用不可。</span><span class="sxs-lookup"><span data-stu-id="10df4-132">Not applicable.</span></span> <span data-ttu-id="10df4-133">このエラーを自動的に修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="10df4-133">This error cannot be repaired automatically.</span></span> <span data-ttu-id="10df4-134">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="10df4-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
