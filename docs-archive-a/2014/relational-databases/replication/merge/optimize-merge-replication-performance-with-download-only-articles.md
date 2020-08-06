---
title: ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 8851faa6-e6df-4ea5-a6ea-2a3471680fa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8414174971792f8a2c256cd564dd1ea224527463
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630941"
---
# <a name="optimize-merge-replication-performance-with-download-only-articles"></a><span data-ttu-id="54d44-102">ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化</span><span class="sxs-lookup"><span data-stu-id="54d44-102">Optimize Merge Replication Performance with Download-Only Articles</span></span>
  <span data-ttu-id="54d44-103">マージ レプリケーションには、異なるアプリケーション ニーズに対応する 2 種類のアーティクルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="54d44-103">Merge replication offers two different article types to address different application needs.</span></span> <span data-ttu-id="54d44-104">アプリケーションでの必要に応じて、パブリケーションにはこれら 2 種類のアーティクルを 1 つ以上格納できます。</span><span class="sxs-lookup"><span data-stu-id="54d44-104">Publications can contain one or more of each of these article types as appropriate for the application:</span></span>  
  
-   <span data-ttu-id="54d44-105">標準アーティクル</span><span class="sxs-lookup"><span data-stu-id="54d44-105">Standard articles</span></span>  
  
-   <span data-ttu-id="54d44-106">ダウンロード専用アーティクル</span><span class="sxs-lookup"><span data-stu-id="54d44-106">Download-only articles</span></span>  
  
 <span data-ttu-id="54d44-107">ダウンロード専用アーティクルは、パフォーマンス面で標準アーティクルよりも優れています。必要に応じて、ダウンロード専用アーティクルを使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="54d44-107">Download-only articles provide performance advantages over standard articles and should be used where appropriate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54d44-108">ダウンロード専用アーティクルを使用するためには、90RTM 以上の互換性レベルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="54d44-108">To use download-only articles, the compatibility level of the publication must be at least 90RTM.</span></span>  
  
## <a name="standard-articles"></a><span data-ttu-id="54d44-109">標準アーティクル</span><span class="sxs-lookup"><span data-stu-id="54d44-109">Standard Articles</span></span>  
 <span data-ttu-id="54d44-110">標準アーティクルは既定のアーティクルであり、強力な競合検出および競合解決機能など、マージ レプリケーションに必要なすべての機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="54d44-110">Standard articles are the default, offering the full range of merge replication features, including rich conflict detection and resolution.</span></span> <span data-ttu-id="54d44-111">標準アーティクルは、複数のサブスクライバーによって更新されるテーブルに適しています。また、ストアド プロシージャやビューなどのテーブル以外のオブジェクトは、常に標準アーティクルとしてパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="54d44-111">Standard articles are appropriate for tables that are updated by multiple Subscribers; objects other than tables, such as stored procedures and views, are always published as standard articles.</span></span>  
  
## <a name="download-only-articles"></a><span data-ttu-id="54d44-112">ダウンロード専用アーティクル</span><span class="sxs-lookup"><span data-stu-id="54d44-112">Download-Only Articles</span></span>  
 <span data-ttu-id="54d44-113">ダウンロード専用アーティクルは、製品カタログに格納される一連のアーティクルなど、サブスクライバーで更新されないデータを処理するアプリケーション向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="54d44-113">Download-only articles are designed for applications with data that is not updated at Subscribers, such as a set of articles that are contained in a product catalog.</span></span> <span data-ttu-id="54d44-114">通常の場合、製品カタログはサブスクライバーではなくパブリッシャーで更新されます。</span><span class="sxs-lookup"><span data-stu-id="54d44-114">A product catalog is typically updated at the Publisher, but not at the Subscribers.</span></span> <span data-ttu-id="54d44-115">ダウンロード専用アーティクルはサブスクライバーで更新されないため、追跡メタデータがサブスクライバーに送信されることはありません。</span><span class="sxs-lookup"><span data-stu-id="54d44-115">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="54d44-116">これによってサブスクライバーの記憶域が節約されると共に、特に低速なネットワーク接続ではパフォーマンスの向上にもつながります。</span><span class="sxs-lookup"><span data-stu-id="54d44-116">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span>  
  
 <span data-ttu-id="54d44-117">ダウンロード専用アーティクルはクライアント サブスクリプションと併用されます。アーティクルがダウンロード専用に作成されている場合、クライアント サブスクリプションを使用するサブスクライバーでは、このアーティクルに対して行の挿入、更新、および削除を行うことができません。</span><span class="sxs-lookup"><span data-stu-id="54d44-117">Download-only articles work in conjunction with client subscriptions: if an article is designated as download-only, rows for that article cannot be inserted, updated, or deleted at Subscribers who use client subscriptions.</span></span> <span data-ttu-id="54d44-118">サーバー サブスクリプションを使用するパブリッシャーおよびサブスクライバー (通常は、他のサブスクライバーにデータを再パブリッシュするサブスクライバー) では、行の挿入、更新、および削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="54d44-118">Publishers and Subscribers that use the server subscription type (typically Subscribers that republish data to other Subscribers) can insert, update, and delete data.</span></span> <span data-ttu-id="54d44-119">クライアント サブスクリプションの詳細については、「[パブリケーションのサブスクライブ](../subscribe-to-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54d44-119">For more information about client subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>  
  
 <span data-ttu-id="54d44-120">アーティクルをダウンロード専用に指定するには、「 [マージ テーブル アーティクルをダウンロード専用に指定する](../publish/specify-merge-replication-properties.md#download-only)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54d44-120">To specify that an article is download-only, see [Specify That a Merge Table Article is Download-Only](../publish/specify-merge-replication-properties.md#download-only).</span></span>  
  
## <a name="using-different-article-types-in-your-applications"></a><span data-ttu-id="54d44-121">アプリケーションに応じた各種アーティクルの使い分け</span><span class="sxs-lookup"><span data-stu-id="54d44-121">Using Different Article Types in Your Applications</span></span>  
 <span data-ttu-id="54d44-122">アプリケーションの要件を理解することにより、柔軟性の最大化とパフォーマンスの最適化の間でアプリケーションを調整できます。</span><span class="sxs-lookup"><span data-stu-id="54d44-122">By understanding the requirements of your application, you can make tradeoffs between maximum flexibility and optimal performance.</span></span> <span data-ttu-id="54d44-123">たとえば、パブリッシャーとサブスクライバーの両方で多数の競合と変更が発生するアプリケーションでは、標準アーティクルから構成されるパブリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="54d44-123">For example, applications with numerous conflicts and changes at both the Publisher and Subscribers will use a publication made up of standard articles.</span></span> <span data-ttu-id="54d44-124">セールス フォース オートメーションなど一部のアプリケーションでは、競合の可能性のあるアーティクルと、それ以外にダウンロード専用に指定できる参照テーブル用のアーティクルが使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="54d44-124">Some applications, such as a sales force automation application, might have articles with a potential for conflicts, and other articles that function as lookup tables, which can be specified as download-only.</span></span> <span data-ttu-id="54d44-125">POS システムやフィールド フォース オートメーションなどのデータ入力アプリケーションでは、競合を排除するように厳密にデータがパーティション分割されている場合が多く、あるサブスクライバーから他のサブスクライバーにデータが送信されることは決してありません。</span><span class="sxs-lookup"><span data-stu-id="54d44-125">Data entry applications, such as point of sales systems and field force automation applications, often strictly partition data in a way that conflicts are eliminated, and data from one Subscriber never goes to another.</span></span> <span data-ttu-id="54d44-126">このような状況では、重複しないパーティション、ダウンロード専用アーティクル、および事前計算済みパーティションを組み合わせて使用することで、パフォーマンスとスケーラビリティを最大化することができます。</span><span class="sxs-lookup"><span data-stu-id="54d44-126">In these situations, a combination of nonoverlapping partitions, download-only articles and precomputed partitions provides maximum performance and scalability.</span></span> <span data-ttu-id="54d44-127">重複しないパーティションおよび事前計算済みパーティションの詳細については、「 [パラメータ化された行フィルタ](parameterized-filters-parameterized-row-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54d44-127">For more information about nonoverlapping partitions and precomputed partitions, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d44-128">参照</span><span class="sxs-lookup"><span data-stu-id="54d44-128">See Also</span></span>  
 <span data-ttu-id="54d44-129">[マージレプリケーションのアーティクルオプション](article-options-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="54d44-129">[Article Options for Merge Replication](article-options-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="54d44-130">条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="54d44-130">Optimize Merge Replication Performance with Conditional Delete Tracking</span></span>](optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
