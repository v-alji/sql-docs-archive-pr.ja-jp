---
title: MSSQLSERVER_2522 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2522 (Database Engine error)
ms.assetid: 19b9b00c-330f-4dd3-9052-9d88bce83849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60446c21599c02ee9c4bc96789b106b49b71582a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631985"
---
# <a name="mssqlserver_2522"></a><span data-ttu-id="ded8b-102">MSSQLSERVER_2522</span><span class="sxs-lookup"><span data-stu-id="ded8b-102">MSSQLSERVER_2522</span></span>
    
## <a name="details"></a><span data-ttu-id="ded8b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="ded8b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ded8b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ded8b-104">Product Name</span></span>|<span data-ttu-id="ded8b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ded8b-105">SQL Server</span></span>|  
|<span data-ttu-id="ded8b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ded8b-106">Event ID</span></span>|<span data-ttu-id="ded8b-107">2522</span><span class="sxs-lookup"><span data-stu-id="ded8b-107">2522</span></span>|  
|<span data-ttu-id="ded8b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ded8b-108">Event Source</span></span>|<span data-ttu-id="ded8b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ded8b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ded8b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ded8b-110">Component</span></span>|<span data-ttu-id="ded8b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ded8b-111">SQLEngine</span></span>|  
|<span data-ttu-id="ded8b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ded8b-112">Symbolic Name</span></span>|<span data-ttu-id="ded8b-113">DBCC_INDEX_FILEGROUP_IS_INVALID</span><span class="sxs-lookup"><span data-stu-id="ded8b-113">DBCC_INDEX_FILEGROUP_IS_INVALID</span></span>|  
|<span data-ttu-id="ded8b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ded8b-114">Message Text</span></span>|<span data-ttu-id="ded8b-115">テーブル O_NAME のインデックス I_NAME を処理できません。ファイル グループ F_NAME が無効です。</span><span class="sxs-lookup"><span data-stu-id="ded8b-115">Unable to process index I_NAME of table O_NAME because filegroup F_NAME is invalid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ded8b-116">説明</span><span class="sxs-lookup"><span data-stu-id="ded8b-116">Explanation</span></span>  
 <span data-ttu-id="ded8b-117">この情報メッセージは、インデックスのメタデータに格納されているファイル グループ ID の 1 つが存在しないので、インデックスをチェックできないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="ded8b-117">This informational message indicates that the index cannot be checked because one of the filegroup IDs that is stored in the metadata of the index does not exist.</span></span> <span data-ttu-id="ded8b-118">有効でないファイル グループ ID は、データそのものに関係している場合も、ラージ オブジェクト (LOB) または行オーバーフロー データに関係している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ded8b-118">The filegroup ID that is not valid might pertain to the data itself, or to the large object (LOB) data, or to the row-overflow data.</span></span>  
  
 <span data-ttu-id="ded8b-119">問題がなければ、同じオブジェクトの他のインデックスはすべてチェックされます。</span><span class="sxs-lookup"><span data-stu-id="ded8b-119">If there are no problems, all other indexes of the same object will be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ded8b-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ded8b-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="ded8b-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="ded8b-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="ded8b-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="ded8b-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="ded8b-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ded8b-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="ded8b-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="ded8b-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="ded8b-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ded8b-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="ded8b-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ded8b-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="ded8b-127">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ded8b-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="ded8b-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="ded8b-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="ded8b-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ded8b-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="ded8b-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="ded8b-130">Restore from Backup</span></span>  
 <span data-ttu-id="ded8b-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="ded8b-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="ded8b-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="ded8b-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="ded8b-133">適用不可。</span><span class="sxs-lookup"><span data-stu-id="ded8b-133">Not applicable.</span></span> <span data-ttu-id="ded8b-134">このエラーを自動的に修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="ded8b-134">This error cannot be repaired automatically.</span></span>  
  
  
