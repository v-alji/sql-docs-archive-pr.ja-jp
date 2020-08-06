---
title: MSSQLSERVER_802 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9edcdda1410d7651f7c7531ef98c64c85741f15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646175"
---
# <a name="mssqlserver_802"></a><span data-ttu-id="49ee1-102">MSSQLSERVER_802</span><span class="sxs-lookup"><span data-stu-id="49ee1-102">MSSQLSERVER_802</span></span>
    
## <a name="details"></a><span data-ttu-id="49ee1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="49ee1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49ee1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="49ee1-104">Product Name</span></span>|<span data-ttu-id="49ee1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="49ee1-105">SQL Server</span></span>|  
|<span data-ttu-id="49ee1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="49ee1-106">Event ID</span></span>|<span data-ttu-id="49ee1-107">802</span><span class="sxs-lookup"><span data-stu-id="49ee1-107">802</span></span>|  
|<span data-ttu-id="49ee1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="49ee1-108">Event Source</span></span>|<span data-ttu-id="49ee1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="49ee1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="49ee1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="49ee1-110">Component</span></span>|<span data-ttu-id="49ee1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="49ee1-111">SQLEngine</span></span>|  
|<span data-ttu-id="49ee1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="49ee1-112">Symbolic Name</span></span>|<span data-ttu-id="49ee1-113">NO_BUFS</span><span class="sxs-lookup"><span data-stu-id="49ee1-113">NO_BUFS</span></span>|  
|<span data-ttu-id="49ee1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="49ee1-114">Message Text</span></span>|<span data-ttu-id="49ee1-115">バッファー プールで使用できるメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="49ee1-115">There is insufficient memory available in the buffer pool.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="49ee1-116">説明</span><span class="sxs-lookup"><span data-stu-id="49ee1-116">Explanation</span></span>  
 <span data-ttu-id="49ee1-117">この問題は、バッファー プールがいっぱいになり、それ以上バッファー プールのサイズを大きくできない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="49ee1-117">This is caused when the buffer pool is full and the buffer pool can not grow any larger.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="49ee1-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="49ee1-118">User Action</span></span>  
 <span data-ttu-id="49ee1-119">メモリ エラーのトラブルシューティングに役立つ一般的な手順の概略を次に示します。</span><span class="sxs-lookup"><span data-stu-id="49ee1-119">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="49ee1-120">このサーバー上で、他のアプリケーションやサービスによってメモリが消費されていないか確認します。</span><span class="sxs-lookup"><span data-stu-id="49ee1-120">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="49ee1-121">重要度の低いアプリケーションやサービスのメモリ消費量が少なくなるように、構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="49ee1-121">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="49ee1-122">次のパフォーマンス モニター カウンターの収集を開始します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **:Buffer Manager**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="49ee1-122">Start collecting performance monitor counters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="49ee1-123">次に示す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ構成パラメーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="49ee1-123">Check the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="49ee1-124">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="49ee1-124">**max server memory**</span></span>  
  
    -   <span data-ttu-id="49ee1-125">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="49ee1-125">**min server memory**</span></span>  
  
    -   <span data-ttu-id="49ee1-126">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="49ee1-126">**min memory per query**</span></span>  
  
     <span data-ttu-id="49ee1-127">通常とは異なる設定がないか確認し、必要に応じて修正します。</span><span class="sxs-lookup"><span data-stu-id="49ee1-127">Notice any unusual settings and correct them as necessary.</span></span> <span data-ttu-id="49ee1-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で増加した必要なメモリの要件を把握しておきます。</span><span class="sxs-lookup"><span data-stu-id="49ee1-128">Account for increased memory requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="49ee1-129">既定の設定については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「サーバー構成オプションの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49ee1-129">Default settings are listed in "Setting Server Configuration Options" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="49ee1-130">DBCC MEMORYSTATUS 出力を監視し、エラー メッセージが表示された場合にどのように変化するかを調べます。</span><span class="sxs-lookup"><span data-stu-id="49ee1-130">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="49ee1-131">ワークロード (同時セッション数や現在実行中のクエリ数など) をチェックします。</span><span class="sxs-lookup"><span data-stu-id="49ee1-131">Check the workload (number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="49ee1-132">次のアクションを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やせる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="49ee1-132">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="49ee1-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションを停止するか、別のサーバーで実行します。</span><span class="sxs-lookup"><span data-stu-id="49ee1-133">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping these applications or running them on a separate server.</span></span>  
  
-   <span data-ttu-id="49ee1-134">**max server memory** を構成した場合は、設定値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="49ee1-134">If you have configured **max server memory,** increase the setting.</span></span>  
  
 <span data-ttu-id="49ee1-135">次の DBCC コマンドを実行して、いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ キャッシュを解放します。</span><span class="sxs-lookup"><span data-stu-id="49ee1-135">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="49ee1-136">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="49ee1-136">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="49ee1-137">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="49ee1-137">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="49ee1-138">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="49ee1-138">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="49ee1-139">問題が解決しない場合は、さらに調査します。ワークロードの軽減が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="49ee1-139">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
