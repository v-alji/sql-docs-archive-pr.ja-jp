---
title: パフォーマンスのベースラインの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0cb85ae8ad370b816c6240b58aabd247c7593c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713061"
---
# <a name="establish-a-performance-baseline"></a><span data-ttu-id="3ffe8-102">パフォーマンスのベースラインの設定</span><span class="sxs-lookup"><span data-stu-id="3ffe8-102">Establish a Performance Baseline</span></span>
  <span data-ttu-id="3ffe8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムが最適に実行されているかどうかを判断するには、たとえ問題が発生しなくても、長期にわたって定期的にパフォーマンスを測定し、サーバーのパフォーマンス ベースラインを設定します。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-103">To determine whether your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system is performing optimally, take performance measurements at regular intervals over time, even when no problems occur, to establish a server performance baseline.</span></span> <span data-ttu-id="3ffe8-104">各新規測定値セットを以前の測定値と比較します。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-104">Compare each new set of measurements with those taken earlier.</span></span>  
  
 <span data-ttu-id="3ffe8-105">次の要素が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-105">The following areas affect the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="3ffe8-106">システム リソース (ハードウェア)</span><span class="sxs-lookup"><span data-stu-id="3ffe8-106">System resources (hardware)</span></span>  
  
-   <span data-ttu-id="3ffe8-107">ネットワーク アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="3ffe8-107">Network architecture</span></span>  
  
-   <span data-ttu-id="3ffe8-108">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="3ffe8-108">The operating system</span></span>  
  
-   <span data-ttu-id="3ffe8-109">データベース アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3ffe8-109">Database applications</span></span>  
  
-   <span data-ttu-id="3ffe8-110">クライアント アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3ffe8-110">Client applications</span></span>  
  
 <span data-ttu-id="3ffe8-111">少なくとも、ベースライン測定値を使用して次のことを判断します。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-111">At a minimum, use baseline measurements to determine:</span></span>  
  
-   <span data-ttu-id="3ffe8-112">操作のピーク時間とオフピーク時間</span><span class="sxs-lookup"><span data-stu-id="3ffe8-112">Peak and off-peak hours of operation.</span></span>  
  
-   <span data-ttu-id="3ffe8-113">実稼働クエリまたはバッチ コマンドの応答時間。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-113">Production-query or batch-command response times.</span></span>  
  
-   <span data-ttu-id="3ffe8-114">データベースのバックアップと復元の終了までにかかる時間</span><span class="sxs-lookup"><span data-stu-id="3ffe8-114">Database backup and restore completion times.</span></span>  
  
 <span data-ttu-id="3ffe8-115">サーバーのパフォーマンス ベースラインを設定したら、ベースライン統計と現在のサーバーのパフォーマンスを比較します。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-115">After you establish a server performance baseline, compare the baseline statistics to current server performance.</span></span> <span data-ttu-id="3ffe8-116">ベースラインと比べて極端に大きいまたは小さい数値は、詳細な調査の対象となります。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-116">Numbers far above or far below your baseline are candidates for further investigation.</span></span> <span data-ttu-id="3ffe8-117">これらはチューニングや再構成が必要な要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-117">They may indicate areas in need of tuning or reconfiguration.</span></span> <span data-ttu-id="3ffe8-118">たとえば、クエリ セットの実行時間が増える場合、クエリを調べて、クエリの再作成が可能かどうか、列統計または新しいインデックスを追加する必要があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="3ffe8-118">For example, if the amount of time to execute a set of queries increases, examine the queries to determine if they can be rewritten, or if column statistics or new indexes must be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ffe8-119">参照</span><span class="sxs-lookup"><span data-stu-id="3ffe8-119">See Also</span></span>  
 [<span data-ttu-id="3ffe8-120">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3ffe8-120">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
