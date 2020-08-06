---
title: MSSQLSERVER_847 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 847 (Database Engine error)
ms.assetid: 67208b7c-bd8d-48a1-9f70-a6488e0f5f9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b2d5c0a35533700606a44867d2a51cf9087e399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642825"
---
# <a name="mssqlserver_847"></a><span data-ttu-id="5b05b-102">MSSQLSERVER_847</span><span class="sxs-lookup"><span data-stu-id="5b05b-102">MSSQLSERVER_847</span></span>
    
## <a name="details"></a><span data-ttu-id="5b05b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="5b05b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b05b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="5b05b-104">Product Name</span></span>|<span data-ttu-id="5b05b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5b05b-105">SQL Server</span></span>|  
|<span data-ttu-id="5b05b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5b05b-106">Event ID</span></span>|<span data-ttu-id="5b05b-107">847</span><span class="sxs-lookup"><span data-stu-id="5b05b-107">847</span></span>|  
|<span data-ttu-id="5b05b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="5b05b-108">Event Source</span></span>|<span data-ttu-id="5b05b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5b05b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5b05b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5b05b-110">Component</span></span>|<span data-ttu-id="5b05b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5b05b-111">SQLEngine</span></span>|  
|<span data-ttu-id="5b05b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="5b05b-112">Symbolic Name</span></span>|<span data-ttu-id="5b05b-113">該当なし</span><span class="sxs-lookup"><span data-stu-id="5b05b-113">N/A</span></span>|  
|<span data-ttu-id="5b05b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="5b05b-114">Message Text</span></span>|<span data-ttu-id="5b05b-115">ラッチを待機中にタイムアウトが発生しました。クラス '%ls'、ID %p、型 %d、タスク 0x%p : %d、待機時間 %d、フラグ 0x%I64x、所有しているタスク 0x%p。</span><span class="sxs-lookup"><span data-stu-id="5b05b-115">Time-out occurred while waiting for latch: class '%ls', id %p, type %d, Task 0x%p : %d, waittime %d, flags 0x%I64x, owning task 0x%p.</span></span> <span data-ttu-id="5b05b-116">待機を続行します。</span><span class="sxs-lookup"><span data-stu-id="5b05b-116">Continuing to wait.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5b05b-117">説明</span><span class="sxs-lookup"><span data-stu-id="5b05b-117">Explanation</span></span>  
 <span data-ttu-id="5b05b-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってバッファー ラッチ エラーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに書き込まれるのと同時に、コンピューターが応答を停止するか、タイムアウトなどにより通常の操作が中断される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5b05b-118">A computer might stop responding, or a time-out or some other disruption of regular operations might occur at the same time that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] writes buffer latch errors to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
 <span data-ttu-id="5b05b-119">メッセージの状態フィールドの値 0x04 がオンの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は I/O 操作を待機しています。</span><span class="sxs-lookup"><span data-stu-id="5b05b-119">If the stat field in the message has the value of 0x04 on, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is waiting for an I/O operation.</span></span> <span data-ttu-id="5b05b-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログにメッセージ [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md) を受信する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5b05b-120">You may also receive message [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
 <span data-ttu-id="5b05b-121">メッセージの状態フィールドの値 0x04 がオフの場合、ページに対して多数の競合が存在します。</span><span class="sxs-lookup"><span data-stu-id="5b05b-121">If the stat field in the message has the value 0x04 off, there is heavy contention for a page.</span></span> <span data-ttu-id="5b05b-122">オブジェクトがデータ ページの場合、非効率なコード デザインに起因している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5b05b-122">If the object is a data page, this can be caused by inefficient code design.</span></span> <span data-ttu-id="5b05b-123">データ以外のページの場合、ハードウェア リソースの不足など、サーバーのボトルネックによってエラーが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5b05b-123">If the page is nondata, the error might be caused by server bottlenecks, such as insufficient hardware resources.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5b05b-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="5b05b-124">User Action</span></span>  
 <span data-ttu-id="5b05b-125">この問題を回避するには、環境に応じて次の 1 つ以上の手順を実行します。これにより、エラー メッセージの発生を回避または減らすことができる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5b05b-125">To work around this problem, depending on your environment, one or more of the following steps might reduce or eliminate the error messages:</span></span>  
  
-   <span data-ttu-id="5b05b-126">ハードウェアにボトルネックがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5b05b-126">Determine whether you have any hardware bottlenecks.</span></span> <span data-ttu-id="5b05b-127">必要な場合、使用している環境の構成、クエリ、および負荷要件がサポートされるように、ハードウェアをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="5b05b-127">If it is necessary, upgrade your hardware so that it can support the configuration, query, and load requirements of your environment.</span></span> <span data-ttu-id="5b05b-128">ボトルネックの詳細については、「[Identify Bottlenecks](../performance/identify-bottlenecks.md)」 (ボトルネックの特定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b05b-128">For more information about bottlenecks, see [Identify Bottlenecks](../performance/identify-bottlenecks.md).</span></span>  
  
-   <span data-ttu-id="5b05b-129">記録されたエラーを確認し、ハードウェア ベンダーの提供する診断を実行します。</span><span class="sxs-lookup"><span data-stu-id="5b05b-129">Check for any logged errors and run any diagnostics provided by your hardware vendor.</span></span>  
  
-   <span data-ttu-id="5b05b-130">ディスク ドライブが圧縮されていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5b05b-130">Make sure that your disk drives are not compressed.</span></span> <span data-ttu-id="5b05b-131">データ ファイルやログ ファイルを圧縮ドライブに格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="5b05b-131">Storing data or log files on compressed drives is not supported.</span></span> <span data-ttu-id="5b05b-132">物理的ファイルの詳細については、「[Database Files and Filegroups](../databases/database-files-and-filegroups.md)」 (データベース ファイルとファイル グループ) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5b05b-132">For more information about physical files, see [Database Files and Filegroups](../databases/database-files-and-filegroups.md).</span></span>  
  
-   <span data-ttu-id="5b05b-133">次のオプションをオフに設定して、エラー メッセージが消えるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="5b05b-133">See whether the error messages disappear when you set the following options to off:</span></span>  
  
    -   <span data-ttu-id="5b05b-134">SQL Server の priority boost 構成オプション</span><span class="sxs-lookup"><span data-stu-id="5b05b-134">SQL Server priority boost configuration option</span></span>  
  
    -   <span data-ttu-id="5b05b-135">簡易プーリング (ファイバー モード) オプション</span><span class="sxs-lookup"><span data-stu-id="5b05b-135">Lightweight pooling (fiber mode) option</span></span>  
  
    -   <span data-ttu-id="5b05b-136">set working set size オプション</span><span class="sxs-lookup"><span data-stu-id="5b05b-136">Set working set size option</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b05b-137">これらの設定を既定のオフから変更すると、多くの場合、効率が悪化します。</span><span class="sxs-lookup"><span data-stu-id="5b05b-137">The previous settings can frequently be counter-productive if you change them from their default setting of OFF.</span></span> <span data-ttu-id="5b05b-138">詳細については、「[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)」 (サーバー構成オプション (SQL Server)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b05b-138">For more information about the settings, see [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
-   <span data-ttu-id="5b05b-139">クエリをチューニングして、システムで使用するリソースを削減します。</span><span class="sxs-lookup"><span data-stu-id="5b05b-139">Tune queries to reduce resources used on the system.</span></span> <span data-ttu-id="5b05b-140">パフォーマンス チューニングは、システム負荷の削減と、個々のクエリの応答時間改善に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5b05b-140">Performance tuning will help reduce the stress on a system and improve response time for individual queries.</span></span>  
  
-   <span data-ttu-id="5b05b-141">AUTO_SHRINK オプションをオフにして、データベース サイズに対する変更のオーバーヘッドを軽減します。</span><span class="sxs-lookup"><span data-stu-id="5b05b-141">Set the AUTO_SHRINK option to OFF to reduce the overhead of changes to the database size.</span></span>  
  
-   <span data-ttu-id="5b05b-142">FILEGROWTH オプションに、頻繁になりすぎないように十分な大きさを持った増分値を設定するようにします。</span><span class="sxs-lookup"><span data-stu-id="5b05b-142">Make sure that you set the FILEGROWTH option to increments that are large enough to be infrequent.</span></span> <span data-ttu-id="5b05b-143">データベース内で使用可能な領域を確認するジョブをスケジュールし、ピーク時以外にデータベース サイズを大きくします。</span><span class="sxs-lookup"><span data-stu-id="5b05b-143">Schedule a job to check the available space in the databases, and then increase the database size during nonpeak hours.</span></span>  
  
  
