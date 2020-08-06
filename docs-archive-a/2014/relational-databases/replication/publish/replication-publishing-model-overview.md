---
title: レプリケーションのパブリッシング モデルの概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], publishing model
- subscriptions [SQL Server replication], about subscriptions
- articles [SQL Server replication]
- publications [SQL Server replication]
- Publishers [SQL Server replication], about Publishers
- Subscribers [SQL Server replication]
- Distributors [SQL Server replication], about Distributors
- Subscribers [SQL Server replication], about Subscribers
- articles [SQL Server replication], about articles
- publications [SQL Server replication], about publications
- Distributors [SQL Server replication]
ms.assetid: b9567832-e6a8-45b2-a3ed-ea12aa002f4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a6b6bd555cf87a8dcb334db2c44e17ed99aa845d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641616"
---
# <a name="replication-publishing-model-overview"></a><span data-ttu-id="dcd46-102">レプリケーションのパブリッシング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="dcd46-102">Replication Publishing Model Overview</span></span>
  <span data-ttu-id="dcd46-103">レプリケーションでは、パブリッシャー (出版社)、ディストリビューター (流通業者)、サブスクライバー (購読者)、パブリケーション (出版物)、アーティクル (記事)、サブスクリプション (定期購読物) など、レプリケーション トポロジ内のコンポーネントを出版業界にたとえて表しています。</span><span class="sxs-lookup"><span data-stu-id="dcd46-103">Replication uses a publishing industry metaphor to represent the components in a replication topology, which include Publisher, Distributor, Subscribers, publications, articles, and subscriptions.</span></span> <span data-ttu-id="dcd46-104">雑誌を例にとって考えると、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレプリケーションを理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="dcd46-104">It is helpful to think of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication in terms of a magazine:</span></span>

-   <span data-ttu-id="dcd46-105">雑誌のパブリッシャー (出版社) は、1 つ以上のパブリケーション (出版物) を発行します。</span><span class="sxs-lookup"><span data-stu-id="dcd46-105">A magazine publisher produces one or more publications</span></span>

-   <span data-ttu-id="dcd46-106">パブリケーションにはアーティクル (記事) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dcd46-106">A publication contains articles</span></span>

-   <span data-ttu-id="dcd46-107">パブリッシャーは、雑誌を直接または、ディストリビューター (流通業者) を使用して配布します。</span><span class="sxs-lookup"><span data-stu-id="dcd46-107">The publisher either distributes the magazine directly or uses a distributor</span></span>

-   <span data-ttu-id="dcd46-108">サブスクライバー (購読者) は、サブスクライブする (定期購読する) パブリケーションを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="dcd46-108">Subscribers receive publications to which they have subscribed</span></span>

 <span data-ttu-id="dcd46-109">雑誌にたとえると、レプリケーションを理解する上で役に立ちますが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレプリケーションには、この例で表されない機能 (特に、サブスクライバーが更新を行ったり、パブリッシャーがパブリケーション内のアーティクルに増分変更を送信する機能など) もあるので注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="dcd46-109">Although the magazine metaphor is useful for understanding replication, it is important to note that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication includes functionality that is not represented in this metaphor, particularly the ability for a Subscriber to make updates and for a Publisher to send out incremental changes to the articles in a publication.</span></span>

 <span data-ttu-id="dcd46-110">*レプリケーション トポロジ* は、サーバーとデータのコピー間のリレーションシップを定義し、サーバー間のデータ フローを決定する論理を明白にします。</span><span class="sxs-lookup"><span data-stu-id="dcd46-110">A *replication topology* defines the relationship between servers and copies of data and clarifies the logic that determines how data flows between servers.</span></span> <span data-ttu-id="dcd46-111">パブリッシャーとサブスクライバーの間でデータのコピーや移動を行ういくつかのレプリケーション処理 ( *エージェント*) があります。</span><span class="sxs-lookup"><span data-stu-id="dcd46-111">There are several replication processes (referred to as *agents*) that are responsible for copying and moving data between the Publisher and Subscribers.</span></span> <span data-ttu-id="dcd46-112">次の図は、レプリケーションに関係するコンポーネントと処理の概要を表しています。</span><span class="sxs-lookup"><span data-stu-id="dcd46-112">The following illustration is an overview of the components and processes involved in replication.</span></span>

 <span data-ttu-id="dcd46-113">![レプリケーション コンポーネントとデータ フロー](../media/replintro1.gif "レプリケーション コンポーネントとデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="dcd46-113">![Replication components and data flow](../media/replintro1.gif "Replication components and data flow")</span></span>

## <a name="publisher"></a><span data-ttu-id="dcd46-114">Publisher</span><span class="sxs-lookup"><span data-stu-id="dcd46-114">Publisher</span></span>
 <span data-ttu-id="dcd46-115">パブリッシャーは、レプリケーションを介して他の場所でデータを使用できるようにするデータベース インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="dcd46-115">The Publisher is a database instance that makes data available to other locations through replication.</span></span> <span data-ttu-id="dcd46-116">パブリッシャーは、1 つ以上のパブリケーションを持つことができ、各パブリケーションに、論理的に関連するレプリケート対象のオブジェクトとデータのセットが定義されています。</span><span class="sxs-lookup"><span data-stu-id="dcd46-116">The Publisher can have one or more publications, each defining a logically related set of objects and data to replicate.</span></span>

## <a name="distributor"></a><span data-ttu-id="dcd46-117">ディストリビューター</span><span class="sxs-lookup"><span data-stu-id="dcd46-117">Distributor</span></span>
 <span data-ttu-id="dcd46-118">ディストリビューターは、1 つ以上のパブリッシャーに関連付けられたレプリケーション固有のデータの保存場所として機能するデータベース インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="dcd46-118">The Distributor is a database instance that acts as a store for replication specific data associated with one or more Publishers.</span></span> <span data-ttu-id="dcd46-119">各パブリッシャーは、ディストリビューターの単一のデータベース (ディストリビューション データベース) と関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-119">Each Publisher is associated with a single database (known as a distribution database) at the Distributor.</span></span> <span data-ttu-id="dcd46-120">ディストリビューション データベースには、レプリケーション状態データ、パブリケーションに関するメタデータが保存され、場合によっては、パブリッシャーからサブスクライバーへ移動するデータのキューとしても機能します。</span><span class="sxs-lookup"><span data-stu-id="dcd46-120">The distribution database stores replication status data, metadata about the publication, and, in some cases, acts as a queue for data moving from the Publisher to the Subscribers.</span></span> <span data-ttu-id="dcd46-121">多くの場合、単一のデータベース サーバー インスタンスが、パブリッシャーとディストリビューター両方の役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="dcd46-121">In many cases, a single database server instance acts as both the Publisher and the Distributor.</span></span> <span data-ttu-id="dcd46-122">これを、 *ローカル ディストリビューター*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-122">This is known as a *local Distributor*.</span></span> <span data-ttu-id="dcd46-123">パブリッシャーとディストリビューターが別のデータベース サーバー インスタンス上で構成される場合、このディストリビューターを *リモート ディストリビューター*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-123">When the Publisher and the Distributor are configured on separate database server instances, the Distributor is known as a *remote Distributor*.</span></span>

## <a name="subscribers"></a><span data-ttu-id="dcd46-124">[サブスクライバー]</span><span class="sxs-lookup"><span data-stu-id="dcd46-124">Subscribers</span></span>
 <span data-ttu-id="dcd46-125">サブスクライバーは、レプリケートされたデータを受信するデータベース インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="dcd46-125">A Subscriber is a database instance that receives replicated data.</span></span> <span data-ttu-id="dcd46-126">サブスクライバーは、複数のパブリッシャーおよびパブリケーションからデータを受信できます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-126">A Subscriber can receive data from multiple Publishers and publications.</span></span> <span data-ttu-id="dcd46-127">選択したレプリケーションの種類に応じて、サブスクライバーはパブリッシャーにデータの変更を戻したり、データを他のサブスクライバーに再パブリッシュしたりできます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-127">Depending on the type of replication chosen, the Subscriber can also pass data changes back to the Publisher or republish the data to other Subscribers.</span></span>

## <a name="article"></a><span data-ttu-id="dcd46-128">[アーティクル]</span><span class="sxs-lookup"><span data-stu-id="dcd46-128">Article</span></span>
 <span data-ttu-id="dcd46-129">アーティクルは、パブリケーションに含まれている 1 つのデータベース オブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="dcd46-129">An article identifies a database object that is included in a publication.</span></span> <span data-ttu-id="dcd46-130">パブリケーションには、テーブル、ビュー、ストアド プロシージャ、その他のオブジェクトなどさまざまな種類のアーティクルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-130">A publication can contain different types of articles, including tables, views, stored procedures, and other objects.</span></span> <span data-ttu-id="dcd46-131">テーブルがアーティクルとしてパブリッシュされている場合は、フィルターを使用してサブスクライバーに送信するデータの列と行を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-131">When tables are published as articles, filters can be used to restrict the columns and rows of the data sent to Subscribers.</span></span>

## <a name="publication"></a><span data-ttu-id="dcd46-132">パブリケーション</span><span class="sxs-lookup"><span data-stu-id="dcd46-132">Publication</span></span>
 <span data-ttu-id="dcd46-133">パブリケーションは、1 つのデータベースからの 1 つ以上のアーティクルの集合です。</span><span class="sxs-lookup"><span data-stu-id="dcd46-133">A publication is a collection of one or more articles from one database.</span></span> <span data-ttu-id="dcd46-134">複数のアーティクルを 1 つのパブリケーションにグループ化すると、1 つの単位としてレプリケートされる論理的に関連するデータベース オブジェクトとデータのセットを簡単に指定できます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-134">The grouping of multiple articles into a publication makes it easier to specify a logically related set of database objects and data that are replicated as a unit.</span></span>

## <a name="subscription"></a><span data-ttu-id="dcd46-135">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="dcd46-135">Subscription</span></span>
 <span data-ttu-id="dcd46-136">サブスクリプションは、サブスクライバーに配信されるパブリケーションのコピーの要求です。</span><span class="sxs-lookup"><span data-stu-id="dcd46-136">A subscription is a request for a copy of a publication to be delivered to a Subscriber.</span></span> <span data-ttu-id="dcd46-137">サブスクリプションでは、どのパブリケーションをいつ、どこで受信するのかが定義されます。</span><span class="sxs-lookup"><span data-stu-id="dcd46-137">The subscription defines what publication will be received, where, and when.</span></span> <span data-ttu-id="dcd46-138">サブスクリプションには、プッシュとプルの 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="dcd46-138">There are two types of subscriptions: push and pull.</span></span> <span data-ttu-id="dcd46-139">プッシュ サブスクリプションとプル サブスクリプションの詳細については、「[パブリケーションのサブスクライブ](../subscribe-to-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcd46-139">For more information about push and pull subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dcd46-140">参照</span><span class="sxs-lookup"><span data-stu-id="dcd46-140">See Also</span></span>
 <span data-ttu-id="dcd46-141">レプリケーション[エージェントの概要](../agents/replication-agents-overview.md)[レプリケーションの種類](../types-of-replication.md) [AlwaysOn 可用性グループのレプリケーションを構成する (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [AlwaysOn パブリケーションデータベースを管理する &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="dcd46-141">[Replication Agents Overview](../agents/replication-agents-overview.md) [Types of Replication](../types-of-replication.md) [Configure Replication for AlwaysOn Availability Groups (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)</span></span>


