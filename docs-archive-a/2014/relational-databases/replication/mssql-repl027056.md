---
title: MSSQL_REPL027056 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027056 error
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44fb130321ec54c39559d52e493cc8f3424172fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721345"
---
# <a name="mssql_repl027056"></a><span data-ttu-id="a0091-102">MSSQL_REPL027056</span><span class="sxs-lookup"><span data-stu-id="a0091-102">MSSQL_REPL027056</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a0091-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="a0091-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0091-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a0091-104">Product Name</span></span>|<span data-ttu-id="a0091-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a0091-105">SQL Server</span></span>|  
|<span data-ttu-id="a0091-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a0091-106">Event ID</span></span>|<span data-ttu-id="a0091-107">27056</span><span class="sxs-lookup"><span data-stu-id="a0091-107">27056</span></span>|  
|<span data-ttu-id="a0091-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a0091-108">Event Source</span></span>|<span data-ttu-id="a0091-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a0091-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a0091-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a0091-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a0091-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a0091-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a0091-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a0091-112">Message Text</span></span>|<span data-ttu-id="a0091-113">マージ プロセスが、'%1' で生成履歴を変更できませんでした。</span><span class="sxs-lookup"><span data-stu-id="a0091-113">The merge process was unable to change generation history at the '%1'.</span></span> <span data-ttu-id="a0091-114">トラブルシューティングを行うには、詳細な履歴ログとの同期を再開して、書き込み先の出力ファイルを指定してください。</span><span class="sxs-lookup"><span data-stu-id="a0091-114">When troubleshooting, restart the synchronization with verbose history logging and specify an output file to which to write.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a0091-115">説明</span><span class="sxs-lookup"><span data-stu-id="a0091-115">Explanation</span></span>  
 <span data-ttu-id="a0091-116">通常このエラーは、極端に大きくなったマージ レプリケーション システム テーブルにおける競合の結果として発生します。</span><span class="sxs-lookup"><span data-stu-id="a0091-116">This error is typically raised as a result of contention in merge replication system tables that have grown excessively large.</span></span> <span data-ttu-id="a0091-117">一般的にシステム テーブルは、パブリケーションの保有期間が長いと大きくなります。これは、保有期間が終了するまでメタデータを格納しておく必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="a0091-117">Large system tables are typically caused by a long publication retention period, because metadata must be stored in these tables until the retention period is reached.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a0091-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a0091-118">User Action</span></span>  
 <span data-ttu-id="a0091-119">**問題を解決するには、以下の操作を実行します。**</span><span class="sxs-lookup"><span data-stu-id="a0091-119">**To resolve the issue:**</span></span>  
  
1.  <span data-ttu-id="a0091-120">マージ エージェントの**DownloadGenerationsPerBatch** パラメーターと **UploadGenerationsPerBatch** パラメーターの値を小さくし、エラーの原因となっている根本的な問題に対処する間、処理を継続できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a0091-120">Decrease the value of the -**DownloadGenerationsPerBatch** and **-UploadGenerationsPerBatch** parameters for the Merge Agent to allow processing to continue while you address the underlying issue causing the error.</span></span> <span data-ttu-id="a0091-121">エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a0091-121">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="a0091-122">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0091-122">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="a0091-123">レプリケーション エージェント プロファイルの操作</span><span class="sxs-lookup"><span data-stu-id="a0091-123">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="a0091-124">レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a0091-124">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="a0091-125">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)に割り当てるメモリの最大容量と最小容量を設定する。</span><span class="sxs-lookup"><span data-stu-id="a0091-125">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
2.  <span data-ttu-id="a0091-126">パブリケーションの保有期間をできるだけ短く設定します。</span><span class="sxs-lookup"><span data-stu-id="a0091-126">Specify the lowest setting possible for the publication retention period.</span></span> <span data-ttu-id="a0091-127">詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0091-127">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
3.  <span data-ttu-id="a0091-128">マージ レプリケーションのメンテナンスの一環として、マージ レプリケーションに関連付けられたシステム テーブル **MSmerge_contents**、 **MSmerge_genhistory**、 **MSmerge_tombstone**、 **MSmerge_current_partition_mappings**、および **MSmerge_past_partition_mappings**の増大を必要に応じて確認します。</span><span class="sxs-lookup"><span data-stu-id="a0091-128">As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge_contents**, **MSmerge_genhistory**, and **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, and **MSmerge_past_partition_mappings**.</span></span> <span data-ttu-id="a0091-129">定期的にこれらのテーブルのインデックスを再設定します。</span><span class="sxs-lookup"><span data-stu-id="a0091-129">Periodically re-index these tables.</span></span> <span data-ttu-id="a0091-130">詳細については、「 [インデックスの再編成と再構築](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0091-130">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0091-131">参照</span><span class="sxs-lookup"><span data-stu-id="a0091-131">See Also</span></span>  
 [<span data-ttu-id="a0091-132">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="a0091-132">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
