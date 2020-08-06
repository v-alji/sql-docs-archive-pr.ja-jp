---
title: optimize for ad hoc workloads サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b217e48d6e4b0ffa0f687ff170f16d4d77ad17d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713482"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a><span data-ttu-id="8018b-102">optimize for ad hoc workloads サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="8018b-102">optimize for ad hoc workloads Server Configuration Option</span></span>
  <span data-ttu-id="8018b-103">**optimize for ad hoc workloads** オプションを使用すると、1 回のみ使用するアドホック バッチが多数含まれているワークロードのプラン キャッシュの効率を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="8018b-103">The **optimize for ad hoc workloads** option is used to improve the efficiency of the plan cache for workloads that contain many single use ad hoc batches.</span></span> <span data-ttu-id="8018b-104">このオプションを 1 に設定すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では、バッチが初めてコンパイルされるときに、完全なコンパイル済みプランではなく、コンパイル済みプランの小さいスタブをプラン キャッシュに格納します。</span><span class="sxs-lookup"><span data-stu-id="8018b-104">When this option is set to 1, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores a small compiled plan stub in the plan cache when a batch is compiled for the first time, instead of the full compiled plan.</span></span> <span data-ttu-id="8018b-105">これにより、再利用されないコンパイル済みプランでプラン キャッシュがいっぱいにならないようにして、メモリの負荷を下げることができます。</span><span class="sxs-lookup"><span data-stu-id="8018b-105">This helps to relieve memory pressure by not allowing the plan cache to become filled with compiled plans that are not reused.</span></span>  
  
 <span data-ttu-id="8018b-106">コンパイル済みプランのスタブを使用すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、このアドホック バッチが既にコンパイルされているが、コンパイル済みプランのスタブしか格納していないと認識します。そのため、このバッチが再度呼び出される (コンパイルまたは実行される) と、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では、バッチがコンパイルされ、コンパイル済みプランのスタブがプラン キャッシュから削除され、完全なコンパイル済みプランがプラン キャッシュに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8018b-106">The compiled plan stub allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to recognize that this ad hoc batch has been compiled before but has only stored a compiled plan stub, so when this batch is invoked (compiled or executed) again, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] compiles the batch, removes the compiled plan stub from the plan cache, and adds the full compiled plan to the plan cache.</span></span>  
  
 <span data-ttu-id="8018b-107">**optimize for ad hoc workloads** を 1 に設定すると、新しいプランのみに影響します。プラン キャッシュ内の既存のプランには影響しません。</span><span class="sxs-lookup"><span data-stu-id="8018b-107">Setting the **optimize for ad hoc workloads** to 1 affects only new plans; plans that are already in the plan cache are unaffected.</span></span>  
  
 <span data-ttu-id="8018b-108">コンパイル済みプランのスタブは、sys.dm_exec_cached_plans カタログ ビューによって表示される cacheobjtype の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="8018b-108">The compiled plan stub is one of the cacheobjtypes displayed by the sys.dm_exec_cached_plans catalog view.</span></span> <span data-ttu-id="8018b-109">これには、一意の SQL ハンドルとプラン ハンドルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8018b-109">It has a unique sql handle and plan handle.</span></span> <span data-ttu-id="8018b-110">コンパイル済みプランのスタブには、関連付けられた実行プランがないため、プラン ハンドルに対してクエリを実行しても、XML プラン表示は返されません。</span><span class="sxs-lookup"><span data-stu-id="8018b-110">The compiled plan stub does not have an execution plan associated with it and querying for the plan handle will not return an XML Showplan.</span></span>  
  
 <span data-ttu-id="8018b-111">トレース フラグ 8032 は、キャッシュ制限パラメーターを [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] RTM の設定に戻します。これにより、一般に、より大きいキャッシュに対応できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8018b-111">Trace flag 8032 reverts the cache limit parameters to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] RTM setting which in general allows caches to be larger.</span></span> <span data-ttu-id="8018b-112">この設定は、頻繁に再利用されるキャッシュ エントリがキャッシュに収まらない場合や、サーバー構成オプション *[アドホック ワークロードの最適化]* でプラン キャッシュの問題を解決できない場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="8018b-112">Use this setting when frequently reused cache entries do not fit into the cache and when the *optimize for ad hoc workloads Server Configuration Option* has failed to resolve the problem with plan cache.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8018b-113">トレース フラグ 8032 を使用した場合、キャッシュが大きいために他のメモリ コンシューマー (バッファー プールなど) で利用できるメモリが少なくなると、パフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="8018b-113">Trace flag 8032 can cause poor performance if large caches make less memory available for other memory consumers, such as the buffer pool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8018b-114">参照</span><span class="sxs-lookup"><span data-stu-id="8018b-114">See Also</span></span>  
 <span data-ttu-id="8018b-115">[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8018b-115">[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql) </span></span>  
 [<span data-ttu-id="8018b-116">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8018b-116">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
