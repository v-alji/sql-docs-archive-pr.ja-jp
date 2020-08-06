---
title: SQL Server 拡張イベント エンジン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], engine
ms.assetid: d74642a5-42b9-4a15-aa3d-f98bfe695050
author: rothja
ms.author: jroth
ms.openlocfilehash: ef11ac8e2cfaf39d2bca90f1d5d52439989ee327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631916"
---
# <a name="sql-server-extended-events-engine"></a><span data-ttu-id="fcab8-102">SQL Server 拡張イベント エンジン</span><span class="sxs-lookup"><span data-stu-id="fcab8-102">SQL Server Extended Events Engine</span></span>
  <span data-ttu-id="fcab8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張イベント エンジンは、次の役割を持った各種のサービスおよびオブジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events engine is a collection of services and objects that:</span></span>  
  
-   <span data-ttu-id="fcab8-104">イベントの定義を有効にする。</span><span class="sxs-lookup"><span data-stu-id="fcab8-104">Enable the definition of events.</span></span>  
  
-   <span data-ttu-id="fcab8-105">イベント データの処理を有効にする。</span><span class="sxs-lookup"><span data-stu-id="fcab8-105">Enable processing event data.</span></span>  
  
-   <span data-ttu-id="fcab8-106">システム内の拡張イベント サービスとオブジェクトを管理する。</span><span class="sxs-lookup"><span data-stu-id="fcab8-106">Manage Extended Events services and objects in the system.</span></span>  
  
-   <span data-ttu-id="fcab8-107">拡張イベント セッションのリストを保持し、そのリストへのアクセスを管理する。</span><span class="sxs-lookup"><span data-stu-id="fcab8-107">Maintain a list of Extended Events sessions and manage access to that list.</span></span>  
  
 <span data-ttu-id="fcab8-108">拡張イベント エンジンそのものは、イベントまたはイベント発生時のアクションを一切提供しません。</span><span class="sxs-lookup"><span data-stu-id="fcab8-108">The Extended Events engine itself does not provide any events or actions to take when an event fires.</span></span> <span data-ttu-id="fcab8-109">拡張イベント エンジンとの対話は、エンジンを使用するプロセスによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-109">The processes that use the Extended Events engine define interaction with the engine.</span></span> <span data-ttu-id="fcab8-110">これらのプロセスによって、イベント ポイントが追加され、イベントの発生時に実行されるアクションが指定されます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-110">These processes add event points and supply the actions to take in response to event firing.</span></span>  
  
 <span data-ttu-id="fcab8-111">拡張イベント セッションの概略図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fcab8-111">The following illustration shows a simplified view of an Extended Events session.</span></span> <span data-ttu-id="fcab8-112">詳細については、「 [SQL Server 拡張イベント セッション](sql-server-extended-events-sessions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcab8-112">For more information, see [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).</span></span>  
  
 <span data-ttu-id="fcab8-113">![拡張イベントのアーキテクチャの詳細](../../database-engine/media/xearchitecturedetailed.gif "拡張イベントのアーキテクチャの詳細")</span><span class="sxs-lookup"><span data-stu-id="fcab8-113">![Detailed extended events architecture](../../database-engine/media/xearchitecturedetailed.gif "Detailed extended events architecture")</span></span>  
  
 <span data-ttu-id="fcab8-114">次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="fcab8-114">Note the following:</span></span>  
  
-   <span data-ttu-id="fcab8-115">各 Windows プロセスは、1 つまたは複数のモジュール (**Win32 プロセス**、 **Win32 モジュール**) を持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="fcab8-115">Each Windows process can have one or more modules (**Win32 process**, **Win32 module**).</span></span> <span data-ttu-id="fcab8-116">これらは、 *バイナリ* または *実行可能モジュール*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-116">These are also known as *binaries* or *executable modules*.</span></span>  
  
-   <span data-ttu-id="fcab8-117">各 Windows プロセス モジュールには、1 つまたは複数の拡張イベント パッケージ (**Package**) が含まれる場合があります。拡張イベント パッケージには、1 つまたは複数の拡張イベント オブジェクト (**Type**、 **Target**、 **Action**、 **Map**、 **Predicate**、および **Event**) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-117">Each of the Windows process modules can contain one or more Extended Events packages (**Package**), which contain one or more Extended Events objects (**Type**, **Target**, **Action**, **Map**, **Predicate**, and **Event**).</span></span>  
  
-   <span data-ttu-id="fcab8-118">ホスト プロセス内に存在できる拡張イベント エンジン (**Extended event engine**) のインスタンスは 1 つだけです。拡張イベント エンジンのインスタンスは次の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="fcab8-118">Inside a host process there can only be one instance of the Extended Events engine (**Extended event engine**), which:</span></span>  
  
    -   <span data-ttu-id="fcab8-119">セッション関連の処理を管理する (セッションの列挙など)。</span><span class="sxs-lookup"><span data-stu-id="fcab8-119">Manages some aspects of the session (for example, enumerating sessions).</span></span>  
  
    -   <span data-ttu-id="fcab8-120">ディスパッチを処理する (**Dispatcher**)。</span><span class="sxs-lookup"><span data-stu-id="fcab8-120">Handles dispatching (**Dispatcher**).</span></span> <span data-ttu-id="fcab8-121">これはスレッド プールに似ています。</span><span class="sxs-lookup"><span data-stu-id="fcab8-121">This is similar to a thread pool.</span></span>  
  
    -   <span data-ttu-id="fcab8-122">イベントのメモリ バッファー (**Buffer**) を処理する。</span><span class="sxs-lookup"><span data-stu-id="fcab8-122">Handles memory buffers (**Buffer**) for events.</span></span> <span data-ttu-id="fcab8-123">バッファーがいっぱいになると、そのバッファーがターゲットにディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-123">When buffers are filled, the buffers are dispatched to targets.</span></span>  
  
-   <span data-ttu-id="fcab8-124">セッションが作成された後、イベントは必要に応じてセッション (**Session context**) にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-124">After a session is created and events are optionally bound to the session (**Session context**):</span></span>  
  
    -   <span data-ttu-id="fcab8-125">場合によっては、ターゲットのインスタンス (**Target instance**) も作成されてセッションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-125">Instances of targets (**Target instance**) may be also be created and added to the session.</span></span>  
  
    -   <span data-ttu-id="fcab8-126">バッファーがいっぱいになると、そのバッファーがターゲットにディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="fcab8-126">When buffers are filled, those buffers are dispatched to targets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcab8-127">参照</span><span class="sxs-lookup"><span data-stu-id="fcab8-127">See Also</span></span>  
 [<span data-ttu-id="fcab8-128">拡張イベント</span><span class="sxs-lookup"><span data-stu-id="fcab8-128">Extended Events</span></span>](extended-events.md)  
  
  
