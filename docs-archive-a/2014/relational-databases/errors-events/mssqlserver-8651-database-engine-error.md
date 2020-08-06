---
title: MSSQLSERVER_8651 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a385350a05edee3759ab83d318e365f5b4f3e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714377"
---
# <a name="mssqlserver_8651"></a><span data-ttu-id="b1205-102">MSSQLSERVER_8651</span><span class="sxs-lookup"><span data-stu-id="b1205-102">MSSQLSERVER_8651</span></span>
    
## <a name="details"></a><span data-ttu-id="b1205-103">詳細</span><span class="sxs-lookup"><span data-stu-id="b1205-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1205-104">製品名</span><span class="sxs-lookup"><span data-stu-id="b1205-104">Product Name</span></span>|<span data-ttu-id="b1205-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b1205-105">SQL Server</span></span>|  
|<span data-ttu-id="b1205-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="b1205-106">Event ID</span></span>|<span data-ttu-id="b1205-107">8651</span><span class="sxs-lookup"><span data-stu-id="b1205-107">8651</span></span>|  
|<span data-ttu-id="b1205-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="b1205-108">Event Source</span></span>|<span data-ttu-id="b1205-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b1205-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b1205-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b1205-110">Component</span></span>|<span data-ttu-id="b1205-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b1205-111">SQLEngine</span></span>|  
|<span data-ttu-id="b1205-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="b1205-112">Symbolic Name</span></span>|<span data-ttu-id="b1205-113">MEMGRANT_ERR</span><span class="sxs-lookup"><span data-stu-id="b1205-113">MEMGRANT_ERR</span></span>|  
|<span data-ttu-id="b1205-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="b1205-114">Message Text</span></span>|<span data-ttu-id="b1205-115">最小クエリ メモリが使用できないので、要求された操作を実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="b1205-115">Could not perform the requested operation because the minimum query memory is not available.</span></span> <span data-ttu-id="b1205-116">'min memory per query' サーバー構成オプションの設定値を減らしてください。</span><span class="sxs-lookup"><span data-stu-id="b1205-116">Decrease the configured value for the 'min memory per query' server configuration option.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b1205-117">説明</span><span class="sxs-lookup"><span data-stu-id="b1205-117">Explanation</span></span>  
 <span data-ttu-id="b1205-118">他のプロセスによってサーバー メモリが消費されています (サーバーにメモリ負荷がかかっています)。</span><span class="sxs-lookup"><span data-stu-id="b1205-118">Other processes are consuming server memory (exerting memory pressure in the server).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b1205-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="b1205-119">User Action</span></span>  
 <span data-ttu-id="b1205-120">'min memory per query' サーバー構成オプションの設定値を小さくするか、サーバーに対するクエリ負荷を軽減します。</span><span class="sxs-lookup"><span data-stu-id="b1205-120">Either decrease the configured value for the min memory per query' server configuration option or reduce the query load to the server.</span></span>  
  
 <span data-ttu-id="b1205-121">メモリ エラーのトラブルシューティングに役立つ一般的な手順の概略を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b1205-121">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="b1205-122">このサーバー上で、他のアプリケーションやサービスによってメモリが消費されていないか確認します。</span><span class="sxs-lookup"><span data-stu-id="b1205-122">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="b1205-123">重要度の低いアプリケーションやサービスのメモリ消費量が少なくなるように、構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="b1205-123">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="b1205-124">次のパフォーマンス モニター カウンターの収集を開始します。**SQL Server:Buffer Manager**、**SQL Server:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="b1205-124">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="b1205-125">次に示す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ構成パラメーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="b1205-125">Check the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="b1205-126">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="b1205-126">**max server memory**</span></span>  
  
    -   <span data-ttu-id="b1205-127">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="b1205-127">**min server memory**</span></span>  
  
    -   <span data-ttu-id="b1205-128">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="b1205-128">**min memory per query**</span></span>  
  
     <span data-ttu-id="b1205-129">通常とは異なる設定がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="b1205-129">Notice unusual settings.</span></span> <span data-ttu-id="b1205-130">必要に応じて、これらを修正します。</span><span class="sxs-lookup"><span data-stu-id="b1205-130">Correct them as necessary.</span></span> <span data-ttu-id="b1205-131">既定の設定については、SQL Server オンライン ブックの「サーバー構成オプションの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1205-131">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="b1205-132">ワークロード (同時セッション数や現在実行中のクエリ数など) をチェックします。</span><span class="sxs-lookup"><span data-stu-id="b1205-132">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="b1205-133">次のアクションを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やせる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b1205-133">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="b1205-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションの実行を停止するか、別のサーバーで実行することを検討します。</span><span class="sxs-lookup"><span data-stu-id="b1205-134">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="b1205-135">これにより、外部的なメモリ負荷を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="b1205-135">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="b1205-136">**max server memory** を構成した場合は、設定値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="b1205-136">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="b1205-137">次の DBCC コマンドを実行して、いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ キャッシュを解放します。</span><span class="sxs-lookup"><span data-stu-id="b1205-137">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="b1205-138">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="b1205-138">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="b1205-139">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="b1205-139">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="b1205-140">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="b1205-140">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="b1205-141">問題が解決しない場合は、さらに調査します。ワークロードの軽減が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b1205-141">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1205-142">参照</span><span class="sxs-lookup"><span data-stu-id="b1205-142">See Also</span></span>  
 <span data-ttu-id="b1205-143">[DBCC FREESYSTEMCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1205-143">[DBCC FREESYSTEMCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql) </span></span>  
 <span data-ttu-id="b1205-144">[DBCC FREESESSIONCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1205-144">[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql) </span></span>  
 <span data-ttu-id="b1205-145">[DBCC FREEべきキャッシュ &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1205-145">[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql) </span></span>  
 <span data-ttu-id="b1205-146">[サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b1205-146">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="b1205-147">[SQL Server: Buffer Manager オブジェクト](../performance-monitor/sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="b1205-147">[SQL Server, Buffer Manager Object](../performance-monitor/sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="b1205-148">SQL Server の Memory Manager オブジェクト</span><span class="sxs-lookup"><span data-stu-id="b1205-148">SQL Server, Memory Manager Object</span></span>](../performance-monitor/sql-server-memory-manager-object.md)  
  
  
