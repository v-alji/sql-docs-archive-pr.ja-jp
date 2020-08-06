---
title: MSSQLSERVER_701 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 701 (Database Engine error)
ms.assetid: 3b975000-63a1-43c2-a40f-89d0a8a36bef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 542535223d3e394c72079092411add143de61545
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634540"
---
# <a name="mssqlserver_701"></a><span data-ttu-id="be70a-102">MSSQLSERVER_701</span><span class="sxs-lookup"><span data-stu-id="be70a-102">MSSQLSERVER_701</span></span>
    
## <a name="details"></a><span data-ttu-id="be70a-103">詳細</span><span class="sxs-lookup"><span data-stu-id="be70a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be70a-104">製品名</span><span class="sxs-lookup"><span data-stu-id="be70a-104">Product Name</span></span>|<span data-ttu-id="be70a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="be70a-105">SQL Server</span></span>|  
|<span data-ttu-id="be70a-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="be70a-106">Event ID</span></span>|<span data-ttu-id="be70a-107">701</span><span class="sxs-lookup"><span data-stu-id="be70a-107">701</span></span>|  
|<span data-ttu-id="be70a-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="be70a-108">Event Source</span></span>|<span data-ttu-id="be70a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="be70a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="be70a-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="be70a-110">Component</span></span>|<span data-ttu-id="be70a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="be70a-111">SQLEngine</span></span>|  
|<span data-ttu-id="be70a-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="be70a-112">Symbolic Name</span></span>|<span data-ttu-id="be70a-113">NOSYSMEM</span><span class="sxs-lookup"><span data-stu-id="be70a-113">NOSYSMEM</span></span>|  
|<span data-ttu-id="be70a-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="be70a-114">Message Text</span></span>|<span data-ttu-id="be70a-115">システム メモリが不足しているため、このクエリを実行できません。</span><span class="sxs-lookup"><span data-stu-id="be70a-115">There is insufficient system memory to run this query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="be70a-116">説明</span><span class="sxs-lookup"><span data-stu-id="be70a-116">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="be70a-117">は、クエリを実行するために必要なメモリを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="be70a-117">has failed to allocate sufficient memory to run the query.</span></span> <span data-ttu-id="be70a-118">この原因としては、オペレーティング システムの設定、物理メモリの可用性、現在のワークロードのメモリ制限など、さまざまなことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="be70a-118">This can be caused by a variety of reasons including operating system settings, physical memory availability, or memory limits on the current workload.</span></span> <span data-ttu-id="be70a-119">ほとんどの場合、トランザクションが失敗しても、このエラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="be70a-119">In most cases, the transaction that failed is not the cause of this error.</span></span>  
  
 <span data-ttu-id="be70a-120">サーバーに十分なメモリがないので、DBCC ステートメントなどの診断クエリは失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="be70a-120">Diagnostic queries, such as DBCC statements, may fail because server the does not have sufficient memory.</span></span>  
  
 <span data-ttu-id="be70a-121">リソース プール 'default' でクエリ実行のためのメモリ リソースを待機中にタイムアウトが発生しました。</span><span class="sxs-lookup"><span data-stu-id="be70a-121">A timeout occurred while waiting for memory resources to execute the query in the resource pool 'default'.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="be70a-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="be70a-122">User Action</span></span>  
 <span data-ttu-id="be70a-123">リソース ガバナーを使用していない場合は、サーバーの全体的な状態と読み込みを検証するか、リソース プールまたはワークロード グループの設定を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="be70a-123">If you are not using Resource Governor, we recommend that you verify the overall server state and load, or check the resource pool or workload group settings.</span></span>  
  
 <span data-ttu-id="be70a-124">メモリ エラーのトラブルシューティングに役立つ一般的な手順の概略を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be70a-124">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="be70a-125">このサーバー上で、他のアプリケーションやサービスによってメモリが消費されていないか確認します。</span><span class="sxs-lookup"><span data-stu-id="be70a-125">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="be70a-126">重要度の低いアプリケーションやサービスのメモリ消費量が少なくなるように、構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="be70a-126">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="be70a-127">次のパフォーマンス モニター カウンターの収集を開始します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **:Buffer Manager**、**SQL Server:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="be70a-127">Start collecting performance monitor counters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="be70a-128">次に示す SQL Server メモリ構成パラメーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="be70a-128">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="be70a-129">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="be70a-129">**max server memory**</span></span>  
  
    -   <span data-ttu-id="be70a-130">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="be70a-130">**min server memory**</span></span>  
  
    -   <span data-ttu-id="be70a-131">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="be70a-131">**min memory per query**</span></span>  
  
     <span data-ttu-id="be70a-132">通常とは異なる設定がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="be70a-132">Notice unusual settings.</span></span> <span data-ttu-id="be70a-133">必要に応じて、これらを修正します。</span><span class="sxs-lookup"><span data-stu-id="be70a-133">Correct them as necessary.</span></span> <span data-ttu-id="be70a-134">高くなったメモリ要件を把握しておきます。</span><span class="sxs-lookup"><span data-stu-id="be70a-134">Account for increased memory requirements.</span></span> <span data-ttu-id="be70a-135">既定の設定については、SQL Server オンライン ブックの「サーバー構成オプションの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be70a-135">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="be70a-136">DBCC MEMORYSTATUS 出力を監視し、エラー メッセージが表示された場合にどのように変化するかを調べます。</span><span class="sxs-lookup"><span data-stu-id="be70a-136">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="be70a-137">ワークロード (同時セッション数や現在実行中のクエリ数など) をチェックします。</span><span class="sxs-lookup"><span data-stu-id="be70a-137">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="be70a-138">次のアクションを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やせる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="be70a-138">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="be70a-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションの実行を停止するか、別のサーバーで実行することを検討します。</span><span class="sxs-lookup"><span data-stu-id="be70a-139">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="be70a-140">これにより、外部的なメモリ負荷を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="be70a-140">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="be70a-141">**max server memory** を構成した場合は、設定値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="be70a-141">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="be70a-142">次の DBCC コマンドを実行して、いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ キャッシュを解放します。</span><span class="sxs-lookup"><span data-stu-id="be70a-142">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="be70a-143">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="be70a-143">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="be70a-144">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="be70a-144">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="be70a-145">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="be70a-145">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="be70a-146">問題が解決しない場合は、さらに調査します。ワークロードの軽減が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="be70a-146">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
