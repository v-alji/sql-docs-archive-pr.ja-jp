---
title: データの再パブリッシュ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- republishing data
- publishing [SQL Server replication], Subscribers
- Subscribers [SQL Server replication], republishing data
ms.assetid: a1485cf4-b1c4-49e9-ab06-8ccfaad998f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1e4213266121b3bf55bf2857e15f71f1e94e301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631774"
---
# <a name="republish-data"></a><span data-ttu-id="94a27-102">データの再パブリッシュ</span><span class="sxs-lookup"><span data-stu-id="94a27-102">Republish Data</span></span>
  <span data-ttu-id="94a27-103">再パブリッシュ モデルでは、パブリッシャーがデータをサブスクライバーに送信し、このサブスクライバーがそのデータを任意の数の他のサブスクライバーに再パブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="94a27-103">In a republishing model, the Publisher sends data to a Subscriber, which then republishes the data to any number of other Subscribers.</span></span> <span data-ttu-id="94a27-104">これは、パブリッシャーが、低速、またはコストが高い通信リンクを使用してサブスクライバーにデータを送信する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="94a27-104">This is useful when a Publisher must send data to Subscribers over a slow or expensive communications link.</span></span> <span data-ttu-id="94a27-105">多数のサブスクライバーがそのリンクの端末に接続されている場合には、リパブリッシャーの使用によりディストリビューションの負荷の大部分がそのリンク側に移ります。</span><span class="sxs-lookup"><span data-stu-id="94a27-105">If there are a number of Subscribers on the far side of that link, using a republisher shifts the bulk of the distribution load to that side of the link.</span></span>  
  
 <span data-ttu-id="94a27-106">データの再パブリッシュを行うには、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="94a27-106">Republishing data involves the following steps:</span></span>  
  
1.  <span data-ttu-id="94a27-107">パブリッシャーでパブリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="94a27-107">Create a publication at the Publisher.</span></span>  
  
2.  <span data-ttu-id="94a27-108">再パブリッシュ サブスクライバーのパブリケーションに対してサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="94a27-108">Create a subscription to the publication for the republishing Subscriber.</span></span>  
  
3.  <span data-ttu-id="94a27-109">サブスクリプションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="94a27-109">Initialize the subscription.</span></span> <span data-ttu-id="94a27-110">サブスクリプションは、再パブリッシュ サブスクライバーでパブリケーションが作成される前に、初期化する必要があります。この初期化を行わなかった場合、レプリケーションは失敗します。</span><span class="sxs-lookup"><span data-stu-id="94a27-110">The subscription must be initialized before the publication is created at the republishing Subscriber, or replication will fail.</span></span>  
  
4.  <span data-ttu-id="94a27-111">再パブリッシュ サブスクライバーで、サブスクリプション データベース内にパブリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="94a27-111">Create a publication in the subscription database at the republishing Subscriber.</span></span>  
  
5.  <span data-ttu-id="94a27-112">他のサブスクライバーへの再パブリッシュ サブスクライバーで、パブリケーションに対するサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="94a27-112">Create subscriptions to the publication at the republishing Subscriber for the other Subscribers.</span></span>  
  
6.  <span data-ttu-id="94a27-113">サブスクリプションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="94a27-113">Initialize the subscriptions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94a27-114">再パブリッシュ トポロジでマージ レプリケーションを使用する場合、すべての再パブリッシュ サブスクライバーはサーバー サブスクリプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94a27-114">If you use merge replication in a republishing topology, all republishing Subscribers must use server subscriptions.</span></span> <span data-ttu-id="94a27-115">サブスクリプションの種類の詳細については、「[パブリケーションのサブスクライブ](subscribe-to-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94a27-115">For more information about subscription types, see [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
 <span data-ttu-id="94a27-116">以下の図では、パブリッシャーとリパブリッシャーの両方が、各自のローカル ディストリビューターとして動作します。</span><span class="sxs-lookup"><span data-stu-id="94a27-116">In the following illustration, both the Publisher and the republisher are acting as their own local Distributors.</span></span> <span data-ttu-id="94a27-117">それぞれがリモート ディストリビューターを使用するように設定された場合は、各ディストリビューターは、低速またはコストが高い通信リンクの、それぞれのパブリッシャーと同じ側に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="94a27-117">If each were set up to use a remote Distributor, each Distributor would need to be on the same side of the slow or expensive communications link as its Publisher.</span></span> <span data-ttu-id="94a27-118">パブリッシャーとリモート ディストリビューターは、信頼性の高い、高速通信リンクで接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94a27-118">Publishers must be connected to remote Distributors by reliable, high-speed communications links.</span></span>  
  
 <span data-ttu-id="94a27-119">![データの再パブリッシュ](media/repl-06a.gif "データの再パブリッシュ")</span><span class="sxs-lookup"><span data-stu-id="94a27-119">![Republishing data](media/repl-06a.gif "Republishing data")</span></span>  
  
 <span data-ttu-id="94a27-120">どのサーバーも、パブリッシャーとサブスクライバーの両方として動作できます。</span><span class="sxs-lookup"><span data-stu-id="94a27-120">Any server can act as both a Publisher and Subscriber.</span></span> <span data-ttu-id="94a27-121">たとえば、以下の図では、ロンドンにあるテーブルを、シカゴ、ニューヨーク、サンディエゴ、シアトルの 4 つの米国の都市に配信する必要がある場合のパブリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="94a27-121">For example, consider the following diagram in which a publication of a table exists in London and must be distributed to four different cities in the United States: Chicago, New York, San Diego, and Seattle.</span></span> <span data-ttu-id="94a27-122">この場合は、ニューヨークのサイトが以下の条件を満たしているので、ロンドンでパブリッシュされたテーブルをニューヨークにあるサーバーがサブスクライブするように選択します。</span><span class="sxs-lookup"><span data-stu-id="94a27-122">The server in New York is chosen to subscribe to the published table originating in London, because the New York site meets these conditions:</span></span>  
  
-   <span data-ttu-id="94a27-123">ロンドンとのネットワーク リンクが比較的信頼できること。</span><span class="sxs-lookup"><span data-stu-id="94a27-123">The network link back to London is relatively reliable.</span></span>  
  
-   <span data-ttu-id="94a27-124">ロンドンとニューヨークの通信コストが妥当であること。</span><span class="sxs-lookup"><span data-stu-id="94a27-124">The London-to-New York communication costs are acceptable.</span></span>  
  
-   <span data-ttu-id="94a27-125">ニューヨークと他の 3 つの米国のサブスクライバー サイトが適切なネットワーク通信回線で結ばれていること。</span><span class="sxs-lookup"><span data-stu-id="94a27-125">There are good network communications lines from New York to all other Subscriber sites in the United States.</span></span>  
  
     <span data-ttu-id="94a27-126">![分散した場所へのデータの再パブリッシュ](media/repl-06.gif "分散した場所へのデータの再パブリッシュ")</span><span class="sxs-lookup"><span data-stu-id="94a27-126">![Republishing data to dispersed locations](media/repl-06.gif "Republishing data to dispersed locations")</span></span>  
  
 <span data-ttu-id="94a27-127">レプリケーションでは、次の表に示す再パブリッシュのシナリオがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="94a27-127">Replication supports the republishing scenarios shown in the following table.</span></span>  
  
|<span data-ttu-id="94a27-128">Publisher</span><span class="sxs-lookup"><span data-stu-id="94a27-128">Publisher</span></span>|<span data-ttu-id="94a27-129">パブリッシュ元のサブスクライバー</span><span class="sxs-lookup"><span data-stu-id="94a27-129">Publishing Subscriber</span></span>|<span data-ttu-id="94a27-130">サブスクライバー (Subscriber)</span><span class="sxs-lookup"><span data-stu-id="94a27-130">Subscriber</span></span>|  
|---------------|---------------------------|----------------|  
|<span data-ttu-id="94a27-131">トランザクション パブリケーション</span><span class="sxs-lookup"><span data-stu-id="94a27-131">Transactional publication</span></span>|<span data-ttu-id="94a27-132">トランザクション サブスクリプション/トランザクション パブリケーション</span><span class="sxs-lookup"><span data-stu-id="94a27-132">Transactional subscription/transactional publication</span></span>|<span data-ttu-id="94a27-133">トランザクション サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="94a27-133">Transactional subscription</span></span>|  
|<span data-ttu-id="94a27-134">トランザクション パブリケーション</span><span class="sxs-lookup"><span data-stu-id="94a27-134">Transactional publication</span></span>|<span data-ttu-id="94a27-135">トランザクションサブスクリプション/マージパブリケーション<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="94a27-135">Transactional subscription/merge publication<sup>1</sup></span></span>|<span data-ttu-id="94a27-136">マージ サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="94a27-136">Merge subscription</span></span>|  
|<span data-ttu-id="94a27-137">マージ パブリケーション</span><span class="sxs-lookup"><span data-stu-id="94a27-137">Merge publication</span></span>|<span data-ttu-id="94a27-138">マージ サブスクリプション/マージ パブリケーション</span><span class="sxs-lookup"><span data-stu-id="94a27-138">Merge subscription/merge publication</span></span>|<span data-ttu-id="94a27-139">マージ サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="94a27-139">Merge subscription</span></span>|  
|<span data-ttu-id="94a27-140">マージ パブリケーション</span><span class="sxs-lookup"><span data-stu-id="94a27-140">Merge publication</span></span>|<span data-ttu-id="94a27-141">マージ サブスクリプション/トランザクション パブリケーション</span><span class="sxs-lookup"><span data-stu-id="94a27-141">Merge subscription/transactional publication</span></span>|<span data-ttu-id="94a27-142">トランザクション サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="94a27-142">Transactional subscription</span></span>|  
  
 <span data-ttu-id="94a27-143"><sup>1</sup>マージパブリケーションのプロパティを設定する必要があり `@published_in_tran_pub` ます。</span><span class="sxs-lookup"><span data-stu-id="94a27-143"><sup>1</sup>You should set the `@published_in_tran_pub` property on the merge publication.</span></span> <span data-ttu-id="94a27-144">既定では、トランザクション レプリケーションにより、サブスクライバーでテーブルが読み取り専用として処理されることが予測されます。</span><span class="sxs-lookup"><span data-stu-id="94a27-144">By default, transactional replication expects tables at the Subscriber to be treated as read-only.</span></span> <span data-ttu-id="94a27-145">マージ レプリケーションにより、トランザクション サブスクリプションのテーブルでデータの変更が行われる場合、データが集約できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="94a27-145">If merge replication makes data changes to a table in a transactional subscription, non-convergence of data can occur.</span></span> <span data-ttu-id="94a27-146">このリスクを回避するため、マージ パブリケーションではこのようなテーブルをダウンロードのみとして指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="94a27-146">To avoid this risk, we recommend that any such table be specified as download-only in the merge publication.</span></span> <span data-ttu-id="94a27-147">これはマージ サブスクライバーがテーブルにデータの変更をアップロードすることを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="94a27-147">This prevents a merge Subscriber from uploading data changes to the table.</span></span> <span data-ttu-id="94a27-148">詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](merge/optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94a27-148">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a27-149">参照</span><span class="sxs-lookup"><span data-stu-id="94a27-149">See Also</span></span>  
 <span data-ttu-id="94a27-150">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="94a27-150">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="94a27-151">[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="94a27-151">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="94a27-152">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="94a27-152">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="94a27-153">[サブスクリプションの初期化](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="94a27-153">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="94a27-154">データの同期</span><span class="sxs-lookup"><span data-stu-id="94a27-154">Synchronize Data</span></span>](synchronize-data.md)  
  
  
