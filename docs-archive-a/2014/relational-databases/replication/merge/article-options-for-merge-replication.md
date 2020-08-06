---
title: マージ レプリケーションのアーティクルのオプション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], article options
- articles [SQL Server replication], merge replication options
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4f9e6391962d5755983322073f738ba84f02633
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630968"
---
# <a name="article-options-for-merge-replication"></a><span data-ttu-id="495e1-102">マージ レプリケーションのアーティクルのオプション</span><span class="sxs-lookup"><span data-stu-id="495e1-102">Article Options for Merge Replication</span></span>
  <span data-ttu-id="495e1-103">アプリケーションのニーズに合わせてレプリケーション動作をカスタマイズするためのマージ テーブル アーティクルには多くのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="495e1-103">There are many options for merge table articles that enable you to customize replication behavior to the needs of your applications.</span></span> <span data-ttu-id="495e1-104">マージ レプリケーションを使用すると、以下のようなことが可能です。</span><span class="sxs-lookup"><span data-stu-id="495e1-104">By using merge replication, you can do the following:</span></span>  
  
-   <span data-ttu-id="495e1-105">行フィルター、結合フィルター、および列フィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="495e1-105">Use row filters, join filters, and column filters.</span></span> <span data-ttu-id="495e1-106">テーブル アーティクルをフィルター選択すると、パブリッシュされるデータのパーティションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="495e1-106">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="495e1-107">詳細については、「[パブリッシュされたデータのフィルター選択](../publish/filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="495e1-107">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
-   <span data-ttu-id="495e1-108">サブスクライバーでの変更をパブリッシャーにアップロードするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="495e1-108">Specify whether changes at the Subscriber are uploaded to the Publisher.</span></span> <span data-ttu-id="495e1-109">サブスクライバーでデータの一部またはすべてが読み取り専用であるアプリケーションでは、アーティクルをダウンロード専用にすることにより、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="495e1-109">For applications in which some or all data should be read-only at the Subscriber, download-only articles provide a performance benefit.</span></span> <span data-ttu-id="495e1-110">詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="495e1-110">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
-   <span data-ttu-id="495e1-111">1 つまたは複数のアーティクルに対する削除をレプリケーション トリガーおよびシステム テーブルによって追跡しないように指定します。</span><span class="sxs-lookup"><span data-stu-id="495e1-111">Specify that deletes for one or more articles should not be tracked by replication triggers and system tables.</span></span> <span data-ttu-id="495e1-112">このオプションは多くのアプリケーション シナリオで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="495e1-112">This option can be useful in many application scenarios.</span></span> <span data-ttu-id="495e1-113">レプリケートする必要のないバッチ削除を使用するシナリオなどがあります。</span><span class="sxs-lookup"><span data-stu-id="495e1-113">These include scenarios that use batch deletes that do not need to be replicated.</span></span> <span data-ttu-id="495e1-114">詳細については、「[Optimize Merge Replication Performance with Conditional Delete Tracking](optimize-merge-replication-performance-with-conditional-delete-tracking.md)」 (条件付き削除の追跡によるマージ レプリケーションのパフォーマンスの最適化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="495e1-114">For more information, see [Optimize Merge Replication Performance with Conditional Delete Tracking](optimize-merge-replication-performance-with-conditional-delete-tracking.md).</span></span>  
  
-   <span data-ttu-id="495e1-115">アーティクルの処理順序を指定し、アプリケーションが要求する順序でアーティクルが処理されるようにします。</span><span class="sxs-lookup"><span data-stu-id="495e1-115">Specify the processing order of articles to make sure that articles are processed in the order required by your application.</span></span> <span data-ttu-id="495e1-116">詳細については、「[Specify Merge Replication properties](../publish/specify-merge-replication-properties.md)」 (マージ レプリケーションのプロパティの指定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="495e1-116">For more information, see [Specify Merge Replication properties](../publish/specify-merge-replication-properties.md).</span></span>  
  
-   <span data-ttu-id="495e1-117">関連するレコードのセットを 1 つの単位として処理するように指定します (既定では、マージ レプリケーションはテーブルへの変更を行単位で処理します)。</span><span class="sxs-lookup"><span data-stu-id="495e1-117">Specify that a set of related records should be processed as a unit (by default, merge replication processes changes to tables on a row-by-row basis).</span></span> <span data-ttu-id="495e1-118">詳細については、「[Group Changes to Related Rows with Logical Records](group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="495e1-118">For more information, see [Group Changes to Related Rows with Logical Records](group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
-   <span data-ttu-id="495e1-119">トポロジの複数のノードで同じデータが変更される可能性がある場合に、競合の検出と解決を使用します。</span><span class="sxs-lookup"><span data-stu-id="495e1-119">Use conflict detection and resolution for cases in which the same data could be changed at more than one node in a topology.</span></span> <span data-ttu-id="495e1-120">詳細については、「 [マージ レプリケーションの競合の検出および解決](advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="495e1-120">For more information, see [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
-   <span data-ttu-id="495e1-121">制約やトリガーをサブスクライバーにコピーするかどうかなど、スキーマ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="495e1-121">Specify schema options, such as whether constraints and triggers are copied to the Subscriber.</span></span> <span data-ttu-id="495e1-122">詳細については、「[スキーマ オプションの指定](../publish/specify-schema-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="495e1-122">For more information, see [Specify Schema Options](../publish/specify-schema-options.md).</span></span>  
  
-   <span data-ttu-id="495e1-123">ビジネス ロジック ハンドラーを使用して、同期中に発生するさまざまな状況に対処します。</span><span class="sxs-lookup"><span data-stu-id="495e1-123">Use a business logic handler to respond to many conditions during synchronization.</span></span> <span data-ttu-id="495e1-124">たとえば、データの変更、競合、エラーに対処します。</span><span class="sxs-lookup"><span data-stu-id="495e1-124">These include data changes, conflicts, and errors.</span></span> <span data-ttu-id="495e1-125">詳細については、「[Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md)」(マージ同期中のビジネス ロジックの実行) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="495e1-125">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495e1-126">参照</span><span class="sxs-lookup"><span data-stu-id="495e1-126">See Also</span></span>  
 [<span data-ttu-id="495e1-127">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="495e1-127">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
