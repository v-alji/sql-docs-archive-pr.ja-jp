---
title: SQL Server の Plan Cache オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Plan Cache object
- SQLServer:Plan Cache
ms.assetid: 225e2b02-8d2f-4f29-9eba-f5847c36ea99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 002cbe261c531c18bdbb2170da9694cc8abde89d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713085"
---
# <a name="sql-server-plan-cache-object"></a><span data-ttu-id="44f89-102">SQL Server の Plan Cache オブジェクト</span><span class="sxs-lookup"><span data-stu-id="44f89-102">SQL Server, Plan Cache Object</span></span>
  <span data-ttu-id="44f89-103">**Plan Cache** オブジェクトには、ストアド プロシージャ、アドホックおよび準備済みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメント、トリガーなどのオブジェクトを保存するために、 [!INCLUDE[tsql](../../includes/tsql-md.md)] がどのようにメモリを使用しているかを監視するためのカウンターがあります。</span><span class="sxs-lookup"><span data-stu-id="44f89-103">The **Plan Cache** object provides counters to monitor how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses memory to store objects such as stored procedures, ad hoc and prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, and triggers.</span></span> <span data-ttu-id="44f89-104">**Plan Cache** オブジェクトの複数のインスタンスを同時に監視できます。各インスタンスは、監視される異なる種類のクエリ プランを表します。</span><span class="sxs-lookup"><span data-stu-id="44f89-104">Multiple instances of the **Plan Cache** object can be monitored at the same time, with each instance representing a different type of plan to monitor.</span></span>  
  
 <span data-ttu-id="44f89-105">次の表では、 **SQLServer:Plan Cache**カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="44f89-105">This table describes are the **SQLServer:Plan Cache**counters.</span></span>  
  
|<span data-ttu-id="44f89-106">SQL Server Plan Cache のカウンター</span><span class="sxs-lookup"><span data-stu-id="44f89-106">SQL Server Plan Cache counters</span></span>|<span data-ttu-id="44f89-107">説明</span><span class="sxs-lookup"><span data-stu-id="44f89-107">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="44f89-108">**Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="44f89-108">**Cache Hit Ratio**</span></span>|<span data-ttu-id="44f89-109">キャッシュ ヒットとキャッシュ参照の比率。</span><span class="sxs-lookup"><span data-stu-id="44f89-109">Ratio between cache hits and lookups.</span></span>|  
|<span data-ttu-id="44f89-110">**Cache Object Counts**</span><span class="sxs-lookup"><span data-stu-id="44f89-110">**Cache Object Counts**</span></span>|<span data-ttu-id="44f89-111">キャッシュ内にあるキャッシュ オブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="44f89-111">Number of cache objects in the cache.</span></span>|  
|<span data-ttu-id="44f89-112">**Cache Pages**</span><span class="sxs-lookup"><span data-stu-id="44f89-112">**Cache Pages**</span></span>|<span data-ttu-id="44f89-113">キャッシュ オブジェクトによって使用される 8 KB ページの数。</span><span class="sxs-lookup"><span data-stu-id="44f89-113">Number of 8-kilobyte (KB) pages used by cache objects.</span></span>|  
|<span data-ttu-id="44f89-114">**Cache Objects in use**</span><span class="sxs-lookup"><span data-stu-id="44f89-114">**Cache Objects in use**</span></span>|<span data-ttu-id="44f89-115">使用中のキャッシュ オブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="44f89-115">Number of cache objects in use.</span></span>|  
  
 <span data-ttu-id="44f89-116">オブジェクトの各カウンターには、次のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="44f89-116">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="44f89-117">Plan Cache インスタンス</span><span class="sxs-lookup"><span data-stu-id="44f89-117">Plan Cache instance</span></span>|<span data-ttu-id="44f89-118">説明</span><span class="sxs-lookup"><span data-stu-id="44f89-118">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="44f89-119">**_Total**</span><span class="sxs-lookup"><span data-stu-id="44f89-119">**_Total**</span></span>|<span data-ttu-id="44f89-120">すべての種類のキャッシュ インスタンスの情報。</span><span class="sxs-lookup"><span data-stu-id="44f89-120">Information for all types of cache instances.</span></span>|  
|<span data-ttu-id="44f89-121">**Sql Plans**</span><span class="sxs-lookup"><span data-stu-id="44f89-121">**Sql Plans**</span></span>|<span data-ttu-id="44f89-122">自動パラメーター化クエリを含むアドホック [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリから作成されたクエリ プランか、 [!INCLUDE[tsql](../../includes/tsql-md.md)] sp_prepare **または** sp_cursorprepare **を使用して準備された**ステートメントから作成されたクエリ プラン。</span><span class="sxs-lookup"><span data-stu-id="44f89-122">Query plans produced from an ad hoc [!INCLUDE[tsql](../../includes/tsql-md.md)] query, including auto-parameterized queries, or from [!INCLUDE[tsql](../../includes/tsql-md.md)] statements prepared using **sp_prepare** or **sp_cursorprepare**.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="44f89-123">では、後で同一の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが実行された場合の再利用に備えて、アドホック [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのプランをキャッシュに格納します。</span><span class="sxs-lookup"><span data-stu-id="44f89-123">caches the plans for ad hoc [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for later reuse if the identical [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is later executed.</span></span> <span data-ttu-id="44f89-124">ユーザーによるパラメーター化クエリも、明示的に準備されていない場合も含めて Prepared SQL Plans として監視されます。</span><span class="sxs-lookup"><span data-stu-id="44f89-124">User-parameterized queries (even if not explicitly prepared) are also monitored as Prepared SQL Plans.</span></span>|  
|<span data-ttu-id="44f89-125">**Object Plans**</span><span class="sxs-lookup"><span data-stu-id="44f89-125">**Object Plans**</span></span>|<span data-ttu-id="44f89-126">ストアド プロシージャ、関数、またはトリガーの作成によって生成されたクエリ プラン。</span><span class="sxs-lookup"><span data-stu-id="44f89-126">Query plans generated by creating a stored procedure, function, or trigger.</span></span>|  
|<span data-ttu-id="44f89-127">**Bound Trees**</span><span class="sxs-lookup"><span data-stu-id="44f89-127">**Bound Trees**</span></span>|<span data-ttu-id="44f89-128">ビュー、規則、計算済みの列、および CHECK 制約のための正規化ツリー。</span><span class="sxs-lookup"><span data-stu-id="44f89-128">Normalized trees for views, rules, computed columns, and check constraints.</span></span>|  
|<span data-ttu-id="44f89-129">**拡張ストアド プロシージャ**</span><span class="sxs-lookup"><span data-stu-id="44f89-129">**Extended Stored Procedures**</span></span>|<span data-ttu-id="44f89-130">拡張ストアド プロシージャのカタログ情報。</span><span class="sxs-lookup"><span data-stu-id="44f89-130">Catalog information for extended stores procedures.</span></span>|  
|<span data-ttu-id="44f89-131">**Temporary Tables & Table Variables**</span><span class="sxs-lookup"><span data-stu-id="44f89-131">**Temporary Tables & Table Variables**</span></span>|<span data-ttu-id="44f89-132">一時テーブルおよびテーブル変数に関連するキャッシュ情報。</span><span class="sxs-lookup"><span data-stu-id="44f89-132">Cache information related to temporary tables and table variables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44f89-133">参照</span><span class="sxs-lookup"><span data-stu-id="44f89-133">See Also</span></span>  
 <span data-ttu-id="44f89-134">[サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="44f89-134">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="44f89-135">[SQL Server: Buffer Manager オブジェクト](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="44f89-135">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="44f89-136">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="44f89-136">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
