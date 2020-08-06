---
title: MSSQLSERVER_8645 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8645 (Database Engine error)
ms.assetid: 63d6d6d7-3850-4061-8e96-b1fa665e3180
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7be9774452e2008c34ecb52d228a0123992c5368
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642817"
---
# <a name="mssqlserver_8645"></a><span data-ttu-id="3f04f-102">MSSQLSERVER_8645</span><span class="sxs-lookup"><span data-stu-id="3f04f-102">MSSQLSERVER_8645</span></span>
    
## <a name="details"></a><span data-ttu-id="3f04f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="3f04f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f04f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="3f04f-104">Product Name</span></span>|<span data-ttu-id="3f04f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3f04f-105">SQL Server</span></span>|  
|<span data-ttu-id="3f04f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3f04f-106">Event ID</span></span>|<span data-ttu-id="3f04f-107">8645</span><span class="sxs-lookup"><span data-stu-id="3f04f-107">8645</span></span>|  
|<span data-ttu-id="3f04f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="3f04f-108">Event Source</span></span>|<span data-ttu-id="3f04f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3f04f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3f04f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3f04f-110">Component</span></span>|<span data-ttu-id="3f04f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3f04f-111">SQLEngine</span></span>|  
|<span data-ttu-id="3f04f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="3f04f-112">Symbolic Name</span></span>|<span data-ttu-id="3f04f-113">MEMTIMEDOUT_ERR</span><span class="sxs-lookup"><span data-stu-id="3f04f-113">MEMTIMEDOUT_ERR</span></span>|  
|<span data-ttu-id="3f04f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="3f04f-114">Message Text</span></span>|<span data-ttu-id="3f04f-115">クエリ実行のためのメモリ リソースを待機中にタイムアウトが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3f04f-115">A time out occurred while waiting for memory resources to execute the query.</span></span> <span data-ttu-id="3f04f-116">クエリを再実行してください。</span><span class="sxs-lookup"><span data-stu-id="3f04f-116">Rerun the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3f04f-117">説明</span><span class="sxs-lookup"><span data-stu-id="3f04f-117">Explanation</span></span>  
 <span data-ttu-id="3f04f-118">リソース プール 'default' でクエリ実行のためのメモリ リソースを待機中にタイムアウトが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3f04f-118">A timeout occurred while waiting for memory resources to execute the query in the resource pool 'default'.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3f04f-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="3f04f-119">User Action</span></span>  
 <span data-ttu-id="3f04f-120">リソース ガバナーを使用していない場合は、サーバーの全体的な状態と読み込みを検証するか、リソース プールまたはワークロード グループの設定を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3f04f-120">If you are not using Resource Governor, we recommend that you verify the overall server state and load, or check the resource pool or workload group settings.</span></span>  
  
 <span data-ttu-id="3f04f-121">メモリ エラーのトラブルシューティングに役立つ一般的な手順の概略を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3f04f-121">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="3f04f-122">このサーバー上で、他のアプリケーションやサービスによってメモリが消費されていないか確認します。</span><span class="sxs-lookup"><span data-stu-id="3f04f-122">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="3f04f-123">重要度の低いアプリケーションやサービスのメモリ消費量が少なくなるように、構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="3f04f-123">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="3f04f-124">次のパフォーマンス モニター カウンターの収集を開始します。**SQL Server:Buffer Manager**、**SQL Server:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="3f04f-124">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="3f04f-125">次に示す SQL Server メモリ構成パラメーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f04f-125">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="3f04f-126">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="3f04f-126">**max server memory**</span></span>  
  
    -   <span data-ttu-id="3f04f-127">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="3f04f-127">**min server memory**</span></span>  
  
    -   <span data-ttu-id="3f04f-128">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="3f04f-128">**min memory per query**</span></span>  
  
     <span data-ttu-id="3f04f-129">通常とは異なる設定がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="3f04f-129">Notice unusual settings.</span></span> <span data-ttu-id="3f04f-130">必要に応じて、これらを修正します。</span><span class="sxs-lookup"><span data-stu-id="3f04f-130">Correct them as necessary.</span></span> <span data-ttu-id="3f04f-131">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で増加した必要なメモリの要件を把握しておきます。</span><span class="sxs-lookup"><span data-stu-id="3f04f-131">Account for increased memory requirements for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3f04f-132">既定の設定については、SQL Server オンライン ブックの「サーバー構成オプションの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f04f-132">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="3f04f-133">DBCC MEMORYSTATUS 出力を監視し、エラー メッセージが表示された場合にどのように変化するかを調べます。</span><span class="sxs-lookup"><span data-stu-id="3f04f-133">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="3f04f-134">ワークロード (同時セッション数や現在実行中のクエリ数など) をチェックします。</span><span class="sxs-lookup"><span data-stu-id="3f04f-134">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="3f04f-135">次のアクションを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やせる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f04f-135">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="3f04f-136">SQL Server 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションの実行を停止するか、別のサーバーで実行することを検討します。</span><span class="sxs-lookup"><span data-stu-id="3f04f-136">If applications besides SQL Server are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="3f04f-137">これにより、外部的なメモリ負荷を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="3f04f-137">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="3f04f-138">**max server memory** を構成した場合は、設定値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="3f04f-138">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="3f04f-139">次の DBCC コマンドを実行して、いくつかの SQL Server メモリ キャッシュを解放します。</span><span class="sxs-lookup"><span data-stu-id="3f04f-139">Run the following DBCC commands to free several SQL Server memory caches.</span></span>  
  
-   <span data-ttu-id="3f04f-140">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="3f04f-140">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="3f04f-141">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="3f04f-141">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="3f04f-142">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="3f04f-142">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="3f04f-143">問題が解決しない場合は、さらに調査します。ワークロードの軽減が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="3f04f-143">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
