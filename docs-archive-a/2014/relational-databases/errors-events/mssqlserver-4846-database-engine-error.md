---
title: MSSQLSERVER_4846 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4846 (Database Engine error)
ms.assetid: a455e809-1883-4c7d-b3e3-835ee5bfe258
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 923137645aae72476fb4b2ae33f0cbbf3e81c2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714382"
---
# <a name="mssqlserver_4846"></a><span data-ttu-id="22288-102">MSSQLSERVER_4846</span><span class="sxs-lookup"><span data-stu-id="22288-102">MSSQLSERVER_4846</span></span>
    
## <a name="details"></a><span data-ttu-id="22288-103">詳細</span><span class="sxs-lookup"><span data-stu-id="22288-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22288-104">製品名</span><span class="sxs-lookup"><span data-stu-id="22288-104">Product Name</span></span>|<span data-ttu-id="22288-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="22288-105">SQL Server</span></span>|  
|<span data-ttu-id="22288-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="22288-106">Event ID</span></span>|<span data-ttu-id="22288-107">4846</span><span class="sxs-lookup"><span data-stu-id="22288-107">4846</span></span>|  
|<span data-ttu-id="22288-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="22288-108">Event Source</span></span>|<span data-ttu-id="22288-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="22288-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="22288-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="22288-110">Component</span></span>|<span data-ttu-id="22288-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="22288-111">SQLEngine</span></span>|  
|<span data-ttu-id="22288-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="22288-112">Symbolic Name</span></span>|<span data-ttu-id="22288-113">BULKPROV_MEMORY</span><span class="sxs-lookup"><span data-stu-id="22288-113">BULKPROV_MEMORY</span></span>|  
|<span data-ttu-id="22288-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="22288-114">Message Text</span></span>|<span data-ttu-id="22288-115">一括データ ソース プロバイダーがメモリの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="22288-115">The bulk data provider failed to allocate memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="22288-116">説明</span><span class="sxs-lookup"><span data-stu-id="22288-116">Explanation</span></span>  
 <span data-ttu-id="22288-117">メモリの割り当てが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="22288-117">Memory allocation failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22288-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="22288-118">User Action</span></span>  
 <span data-ttu-id="22288-119">メモリ エラーのトラブルシューティングを行うための一般的な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="22288-119">Follow these general steps to troubleshoot memory errors:</span></span>  
  
1.  <span data-ttu-id="22288-120">このサーバー上で、他のアプリケーションやサービスによってメモリが消費されていないか確認します。</span><span class="sxs-lookup"><span data-stu-id="22288-120">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="22288-121">重要度の低いアプリケーションやサービスのメモリ消費量が少なくなるように、構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="22288-121">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="22288-122">次のパフォーマンス モニター カウンターの収集を開始します。**SQL Server:Buffer Manager**、**SQL Server:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="22288-122">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="22288-123">次に示す SQL Server メモリ構成パラメーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="22288-123">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="22288-124">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="22288-124">**max server memory**</span></span>  
  
    -   <span data-ttu-id="22288-125">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="22288-125">**min server memory**</span></span>  
  
    -   <span data-ttu-id="22288-126">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="22288-126">**min memory per query**</span></span>  
  
     <span data-ttu-id="22288-127">通常とは異なる設定がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="22288-127">Notice any unusual settings.</span></span> <span data-ttu-id="22288-128">必要に応じて、これらを修正します。</span><span class="sxs-lookup"><span data-stu-id="22288-128">Correct them as necessary.</span></span> <span data-ttu-id="22288-129">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で必要なメモリの要件を把握しておきます。</span><span class="sxs-lookup"><span data-stu-id="22288-129">Account for memory requirements for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="22288-130">既定の設定については、SQL Server オンライン ブックの「サーバー構成オプションの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22288-130">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="22288-131">DBCC MEMORYSTATUS 出力を監視し、エラー メッセージが表示された場合にどのように変化するかを調べます。</span><span class="sxs-lookup"><span data-stu-id="22288-131">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="22288-132">ワークロード (同時セッション数や現在実行中のクエリ数など) をチェックします。</span><span class="sxs-lookup"><span data-stu-id="22288-132">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="22288-133">次のアクションを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やせる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22288-133">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="22288-134">SQL Server 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションの実行を停止するか、別のサーバーで実行することを検討します。</span><span class="sxs-lookup"><span data-stu-id="22288-134">If applications besides SQL Server are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="22288-135">これにより、外部的なメモリ負荷を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="22288-135">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="22288-136">**max server memory** を構成した場合は、設定値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="22288-136">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="22288-137">次の DBCC コマンドを実行して、いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ キャッシュを解放します。</span><span class="sxs-lookup"><span data-stu-id="22288-137">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="22288-138">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="22288-138">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="22288-139">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="22288-139">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="22288-140">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="22288-140">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="22288-141">問題が解決しない場合は、さらに調査します。ワークロードの軽減が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="22288-141">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
