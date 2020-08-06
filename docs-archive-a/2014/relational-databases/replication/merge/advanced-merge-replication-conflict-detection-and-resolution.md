---
title: マージ レプリケーションの競合検出および解決の詳細 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- column-level conflict tracking
- row-level conflict tracking
- viewing merge replication conflicts
- resolving merge replication conflicts
- logical record-level conflict tracking [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 063d3d9c-ccb5-4fab-9d0c-c675997428b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9122f0d704db948a0a8134da2b86e34ea6426dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630976"
---
# <a name="advanced-merge-replication-conflict-detection-and-resolution"></a><span data-ttu-id="3f3e3-102">マージ レプリケーションの競合検出および解決の詳細</span><span class="sxs-lookup"><span data-stu-id="3f3e3-102">Advanced Merge Replication Conflict Detection and Resolution</span></span>
  <span data-ttu-id="3f3e3-103">パブリッシャーとサブスクライバーが接続され、同期が発生すると、マージ エージェントによって競合の検出が行われます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-103">When a Publisher and a Subscriber are connected and synchronization occurs, the Merge Agent detects if there are any conflicts.</span></span> <span data-ttu-id="3f3e3-104">競合が検出された場合、マージ エージェントは競合回避モジュール (アーティクルをパブリケーションに追加するときに指定) を使用して、他のサイトに反映する許容データを決定します。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-104">If conflicts are detected, the Merge Agent uses a conflict resolver (which is specified when an article is added to a publication) to determine which data is accepted and propagated to other sites.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f3e3-105">サブスクライバーとパブリッシャーの同期が取られていても、異なるサブスクライバーで行われた更新の間に競合が発生する場合があります。これに比べ、サブスクライバーとパブリッシャーにおける更新では、競合はあまり発生しません。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-105">Although a Subscriber synchronizes with the Publisher, conflicts typically occur between updates that are made at different Subscribers, instead of updates being made at a Subscriber and at the Publisher.</span></span>  
  
 <span data-ttu-id="3f3e3-106">競合検出および解決の動作は、次のオプションによって異なります。これらのオプションについては、このトピックで解説します。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-106">The behavior of conflict detection and resolution depends on the following options, which are described in this topic:</span></span>  
  
-   <span data-ttu-id="3f3e3-107">列レベルの追跡、行レベルの追跡、または論理レコードレベルの追跡のいずれかを指定しているかどうか。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-107">Whether you specify column-level tracking, row-level tracking, or logical record-level tracking.</span></span>  
  
-   <span data-ttu-id="3f3e3-108">優先度に基づく解決メカニズムを指定しているかどうか、またはアーティクル競合回避モジュールを指定しているかどうか。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-108">Whether you specify the default priority-based resolution mechanism or specify an article resolver.</span></span> <span data-ttu-id="3f3e3-109">アーティクル競合回避モジュールは次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-109">An article resolver can be:</span></span>  
  
    -   <span data-ttu-id="3f3e3-110">マネージド コードで記述された *ビジネス ロジック ハンドラー*</span><span class="sxs-lookup"><span data-stu-id="3f3e3-110">A *business logic handler* written in managed code.</span></span>  
  
    -   <span data-ttu-id="3f3e3-111">COM ベースの *カスタム競合回避モジュール*</span><span class="sxs-lookup"><span data-stu-id="3f3e3-111">A COM-based *custom resolver*.</span></span>  
  
    -   <span data-ttu-id="3f3e3-112">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]によって提供される COM ベースの競合回避モジュール</span><span class="sxs-lookup"><span data-stu-id="3f3e3-112">A COM-based resolver supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)].</span></span>  
  
     <span data-ttu-id="3f3e3-113">既定の解決メカニズムを使用する場合、クライアントまたはサーバーのどちらのサブスクリプションが使用されるかによっても動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-113">If the default resolution mechanism is used, behavior is further determined by the type of subscription used: client or server.</span></span>  
  
## <a name="conflict-detection"></a><span data-ttu-id="3f3e3-114">競合検出</span><span class="sxs-lookup"><span data-stu-id="3f3e3-114">Conflict Detection</span></span>  
 <span data-ttu-id="3f3e3-115">データの変更が競合と見なされるかどうかは、アーティクルに対して設定した競合の追跡の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-115">Whether a data change qualifies as a conflict or not depends on the type of conflict tracking you set for an article:</span></span>  
  
-   <span data-ttu-id="3f3e3-116">列レベルの追跡を選択している場合、複数のレプリケーション ノードで行われた同一行の同一列に対する変更が競合と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-116">If you select column-level conflict tracking, it is considered a conflict if changes are made to the same column in the same row at more than one replication node.</span></span>  
  
-   <span data-ttu-id="3f3e3-117">行レベルの追跡を選択している場合、複数のレプリケーション ノードで行われた同一行の任意の列に対する変更が競合と見なされます (該当する行で影響を受ける列が同一である必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-117">If you select row-level tracking, it is considered a conflict if changes are made to any columns in the same row at more than one replication node (the columns affected in the corresponding rows need not be the same).</span></span>  
  
-   <span data-ttu-id="3f3e3-118">論理レコードレベルの追跡を選択している場合、複数のレプリケーション ノードで行われた同一論理レコードの任意の行に対する変更が競合と見なされます (該当する行で影響を受ける列が同一である必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-118">If you select logical record-level tracking, it is considered a conflict if changes are made to any row in the same logical record at more than one replication node (the columns affected in the corresponding rows need not be the same).</span></span>  
  
 <span data-ttu-id="3f3e3-119">詳しくは、「 [論理レコードの競合の検出および解決](advanced-merge-replication-conflict-resolving-in-logical-record.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-119">For more information, see [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>  
  
 <span data-ttu-id="3f3e3-120">アーティクルに対して競合の追跡と競合解決のレベルを指定するには、「 [マージ アーティクルの競合追跡と解決のレベルを指定](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-120">To specify the conflict tracking and resolution level for an article, see [Specify the Conflict Tracking and Resolution Level for Merge Articles](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>  
  
## <a name="conflict-resolution"></a><span data-ttu-id="3f3e3-121">競合解決</span><span class="sxs-lookup"><span data-stu-id="3f3e3-121">Conflict Resolution</span></span>  
 <span data-ttu-id="3f3e3-122">競合が検出されると、選択した競合回避モジュールがマージ エージェントによって起動され、この競合回避モジュールを使用して、競合で優先するデータを決定します。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-122">After a conflict is detected, the Merge Agent launches the selected conflict resolver and uses the resolver to determine the conflict winner.</span></span> <span data-ttu-id="3f3e3-123">競合で優先された行がパブリッシャーおよびサブスクライバーで適用され、優先されなかった行のデータは競合テーブルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-123">The winning row is applied at the Publisher and Subscriber, and the data from the losing row is written to a conflict table.</span></span> <span data-ttu-id="3f3e3-124">対話型操作による競合解決を選択しなかった場合、競合はモジュールの実行直後に解決されます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-124">Conflicts are resolved immediately after the resolver executes, unless you select to resolve conflicts interactively.</span></span>  
  
### <a name="resolver-types"></a><span data-ttu-id="3f3e3-125">競合回避モジュールの種類</span><span class="sxs-lookup"><span data-stu-id="3f3e3-125">Resolver Types</span></span>  
 <span data-ttu-id="3f3e3-126">マージ レプリケーションでは、アーティクル レベルで競合解決が行われます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-126">In merge replication, conflict resolution takes place at the article level.</span></span> <span data-ttu-id="3f3e3-127">複数のアーティクルで構成されているパブリケーションの場合、複数の競合回避モジュールで各アーティクルに対応するか、1 つの競合回避モジュールで 1 つのアーティクル、複数のアーティクル、またはパブリケーションを構成するすべてのアーティクルに対応できます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-127">For publications composed of several articles, you can have different conflict resolvers serving different articles, or the same conflict resolver serving one article, several articles, or all the articles comprising a publication.</span></span>  
  
 <span data-ttu-id="3f3e3-128">既定の優先度に基づく競合回避モジュールを使用する場合、アーティクルに対して競合回避モジュール プロパティを設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-128">If you plan to use the default priority-based conflict resolver, you do not have to set the resolver property of an article.</span></span> <span data-ttu-id="3f3e3-129">既定の競合回避モジュールではなくアーティクル競合回避モジュールを使用する場合、パブリッシャーで使用できる競合回避モジュールを選択し、アーティクルに対して競合回避モジュールのプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-129">If you want to use an article resolver instead of the default resolver, you must set the resolver property for the article that will use it by selecting an available resolver on the Publisher.</span></span> <span data-ttu-id="3f3e3-130">競合回避モジュールに渡す必要がある特定の情報を、競合回避モジュール情報のプロパティに指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-130">Any specific information that needs to be passed to the resolver can also be specified in the resolver information property.</span></span>  
  
 <span data-ttu-id="3f3e3-131">マージ レプリケーションでは、次に示す 4 つの競合回避モジュールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-131">Merge replication offers four types of conflict resolvers:</span></span>  
  
-   <span data-ttu-id="3f3e3-132">既定の優先度に基づく競合回避モジュール</span><span class="sxs-lookup"><span data-stu-id="3f3e3-132">The default priority-based conflict resolver</span></span>  
  
     <span data-ttu-id="3f3e3-133">既定の解決メカニズムの動作は、クライアント サブスクリプションまたはサーバー サブスクリプションのどちらが使用されているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-133">The default resolution mechanism behaves differently, depending on whether a subscription is a client subscription or a server subscription.</span></span> <span data-ttu-id="3f3e3-134">サーバー サブスクリプションを使用する個々のサブスクライバーに優先度値を割り当てると、最も優先度の高いノードで行われた変更が競合で最優先されます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-134">You assign priority values to individual Subscribers that use server subscriptions; changes made at the node with the highest priority win any conflicts.</span></span> <span data-ttu-id="3f3e3-135">クライアント サブスクリプションの場合は、パブリッシャーに書き込まれた最初の変更が優先されます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-135">For client subscriptions, the first change written to the Publisher wins the conflict.</span></span>  
  
     <span data-ttu-id="3f3e3-136">サブスクリプションの作成後にその種類を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-136">After a subscription is created, it cannot be changed from one type to another.</span></span>  
  
-   <span data-ttu-id="3f3e3-137">ビジネス ロジック ハンドラー</span><span class="sxs-lookup"><span data-stu-id="3f3e3-137">A business logic handler</span></span>  
  
     <span data-ttu-id="3f3e3-138">ビジネス ロジック ハンドラー フレームワークを使用すると、マネージド コードのアセンブリを記述して、マージ同期処理中に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-138">The business logic handler framework allows you to write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="3f3e3-139">このアセンブリには、競合など同期中に発生するさまざまな状況に対処するためのビジネス ロジックを記述できます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-139">The assembly includes business logic that can respond to conflicts and a number of other conditions during synchronization.</span></span> <span data-ttu-id="3f3e3-140">詳細については、「[Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md)」(マージ同期中のビジネス ロジックの実行) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-140">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
-   <span data-ttu-id="3f3e3-141">COM ベースのカスタム競合回避モジュール</span><span class="sxs-lookup"><span data-stu-id="3f3e3-141">A COM-based custom resolver</span></span>  
  
     <span data-ttu-id="3f3e3-142">マージ レプリケーションには、競合回避モジュールを COM オブジェクトとして作成するための API が用意されています。この COM オブジェクトは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] や [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] などの言語で記述します。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-142">Merge replication provides an API for writing resolvers as COM objects in languages such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="3f3e3-143">詳細については、「 [COM-Based Custom Resolvers](advanced-merge-replication-conflict-com-based-custom-resolvers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-143">For more information, see [COM-Based Custom Resolvers](advanced-merge-replication-conflict-com-based-custom-resolvers.md).</span></span>  
  
-   <span data-ttu-id="3f3e3-144">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3e3-144">A COM-based resolver supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)]</span></span>  
  
     [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="3f3e3-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、COM ベースの競合回避モジュールが各種用意されています。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] includes a number of COM-based resolvers.</span></span> <span data-ttu-id="3f3e3-146">詳細については、「 [Microsoft COM ベースの競合回避モジュール](advanced-merge-replication-conflict-com-based-resolvers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-146">For more information, see [Microsoft COM-Based Resolvers](advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
 <span data-ttu-id="3f3e3-147">適切な競合回避モジュールの種類の選択方法は、「[競合回避モジュールの選択](advanced-merge-replication-conflict-choose-a-resolver.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-147">For information about how to select the appropriate type of resolver, see [Choose a Resolver](advanced-merge-replication-conflict-choose-a-resolver.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f3e3-148">アーティクル競合回避モジュールの中には、特定の操作が行われた場合のみ競合を処理するように作成されているものもあります。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-148">Some article resolvers are written to handle conflicts only for certain operations.</span></span> <span data-ttu-id="3f3e3-149">たとえば、更新については処理するが、挿入や削除については処理しない競合回避モジュールがあります。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-149">For example a resolver might handle updates, but not inserts or deletes.</span></span> <span data-ttu-id="3f3e3-150">既定の優先度に基づく競合回避モジュールでは、アーティクル競合回避モジュールで処理されない競合が処理されます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-150">The default priority-based conflict resolver handles any conflicts not handled by the article resolver.</span></span>  
  
 <span data-ttu-id="3f3e3-151">マージ サブスクリプションの種類と競合解決の優先度を指定するには、「</span><span class="sxs-lookup"><span data-stu-id="3f3e3-151">To specify a merge subscription type and conflict resolution priority, see</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="3f3e3-152">:[マージ サブスクリプションの種類と競合解決の優先度の指定 &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)</span><span class="sxs-lookup"><span data-stu-id="3f3e3-152">: [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)</span></span>  
  
-   <span data-ttu-id="3f3e3-153">レプリケーション [!INCLUDE[tsql](../../../includes/tsql-md.md)] プログラミングおよびレプリケーション管理オブジェクト (RMO) プログラミング:「[プル サブスクリプションの作成](../create-a-pull-subscription.md)」と「[プッシュ サブスクリプションの作成](../create-a-push-subscription.md)」</span><span class="sxs-lookup"><span data-stu-id="3f3e3-153">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming and Replication Management Objects (RMO) programming: [Create a Pull Subscription](../create-a-pull-subscription.md) and [Create a Push Subscription](../create-a-push-subscription.md)</span></span>  
  
### <a name="interactive-resolver"></a><span data-ttu-id="3f3e3-154">インタラクティブ競合回避モジュール</span><span class="sxs-lookup"><span data-stu-id="3f3e3-154">Interactive Resolver</span></span>  
 <span data-ttu-id="3f3e3-155">レプリケーションにはインタラクティブ競合回避モジュールのユーザー インターフェイスが用意されており、既定の優先度に基づく競合回避モジュールやアーティクル競合回避モジュールと併用できます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-155">Replication supplies an Interactive Resolver user interface that can be used in conjunction with either the default priority-based conflict resolver or an article resolver.</span></span> <span data-ttu-id="3f3e3-156">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同期マネージャーを使用して要求時同期を実行すると、インタラクティブ競合回避モジュールに実行時の競合データが表示され、競合の解決方法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-156">When performing on-demand synchronization through [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager, the Interactive Resolver displays conflict data at run-time, and lets you choose how to resolve conflicts.</span></span> <span data-ttu-id="3f3e3-157">対話型解決を有効にする方法およびインタラクティブ競合回避モジュールの起動方法の詳細については、「 [Interactive Conflict Resolution](advanced-merge-replication-conflict-interactive-resolution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-157">For more information about how to enable interactive resolution and launch the Interactive Resolver, see [Interactive Conflict Resolution](advanced-merge-replication-conflict-interactive-resolution.md).</span></span>  
  
## <a name="viewing-conflicts"></a><span data-ttu-id="3f3e3-158">競合の表示</span><span class="sxs-lookup"><span data-stu-id="3f3e3-158">Viewing Conflicts</span></span>  
 <span data-ttu-id="3f3e3-159">競合を表示する最も簡単な方法はレプリケーション競合表示モジュールを使用することです。このモジュールは [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] から使用できます ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、競合テーブルに対してクエリを実行するためのストアド プロシージャも用意されています)。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-159">The most straightforward way to view conflicts is to use the Replication Conflict Viewer, available from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also provides stored procedures that allow the conflict tables to be queried.).</span></span> <span data-ttu-id="3f3e3-160">競合表示モジュールはインタラクティブ競合回避モジュールに似たツールです。ただし、インタラクティブ競合回避モジュールが同期実行時の競合の解決に使用されるのに対し、競合表示モジュールは解決後の競合の表示を目的として設計されています。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-160">The Conflict Viewer and Interactive Resolver are similar tools, but the Interactive Resolver allows you to resolve conflicts as synchronization occurs, whereas the Conflict Viewer is designed for viewing conflicts after they have been resolved.</span></span> <span data-ttu-id="3f3e3-161">競合メタデータがシステム テーブルでまだ利用可能な場合 (競合メタデータの既定の保持期間は 14 日間)、競合表示モジュールを使用して競合の解決結果をオーバーライドできます。ただし、直接的な介入が定期的に必要となる場合は、インタラクティブ競合回避モジュールの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-161">If the conflict metadata is still available in the system tables (conflict metadata is retained for 14 days by default), you can override conflict resolution outcomes in the Conflict Viewer, but if direct intervention is regularly required, consider using the Interactive Resolver.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f3e3-162">論理レコードに関連する競合は、競合表示モジュールに表示されません。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-162">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="3f3e3-163">これらの競合に関する情報を表示するには、レプリケーション ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-163">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="3f3e3-164">詳細については、「[マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)](../view-conflict-information-for-merge-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-164">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>  
  
 <span data-ttu-id="3f3e3-165">競合表示モジュールには、次に示す 3 つのシステム テーブルの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-165">The Conflict Viewer displays information from three system tables:</span></span>  
  
-   <span data-ttu-id="3f3e3-166">レプリケーションは、マージ アーティクルの各テーブルに対して競合テーブルを作成し、そのテーブルに **MSmerge_conflict_\<PublicationName>_\<ArticleName>** という形式の名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-166">Replication creates a conflict table for each table in a merge article, with a name in the form **MSmerge_conflict_\<PublicationName>_\<ArticleName>**.</span></span>  
  
     <span data-ttu-id="3f3e3-167">競合テーブルには、基になるテーブルと同じ構造があります。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-167">Conflict tables have the same structure as the tables on which they are based.</span></span> <span data-ttu-id="3f3e3-168">これらのテーブルの行は競合で優先されなかった行で構成されています (競合で優先された行は実際のユーザー テーブルにあります)。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-168">A row in one of these tables consists of the losing version of a conflict row (the winning version of the row is in the actual user table).</span></span>  
  
-   <span data-ttu-id="3f3e3-169">**MSmerge_conflicts_info** テーブルは、競合の種類など各競合に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-169">The **MSmerge_conflicts_info** table provides information about each conflict, including the conflict type.</span></span>  
  
-   <span data-ttu-id="3f3e3-170">**sysmergearticles** テーブルは、競合テーブルを持つユーザー テーブルを示し、競合テーブルに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-170">The **sysmergearticles** table identifies which user tables have conflict tables and provides information about the conflict tables.</span></span>  
  
 <span data-ttu-id="3f3e3-171">競合情報の既定の保存先は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-171">By default, conflict information is stored:</span></span>  
  
-   <span data-ttu-id="3f3e3-172">パブリケーションの互換性レベルが 90 RTM 以上の場合は、パブリッシャーおよびサブスクライバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-172">At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.</span></span>  
  
-   <span data-ttu-id="3f3e3-173">パブリケーションの互換性レベルが 80 RTM 未満の場合は、パブリッシャーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-173">At the Publisher if the publication compatibility level is lower than 80RTM.</span></span>  
  
-   <span data-ttu-id="3f3e3-174">サブスクライバーが [!INCLUDE[ssEW](../../../includes/ssew-md.md)]を実行している場合は、パブリッシャーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-174">At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../../includes/ssew-md.md)].</span></span> <span data-ttu-id="3f3e3-175">競合データを [!INCLUDE[ssEW](../../../includes/ssew-md.md)] サブスクライバーに保存することはできません。</span><span class="sxs-lookup"><span data-stu-id="3f3e3-175">Conflict data cannot be stored on [!INCLUDE[ssEW](../../../includes/ssew-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="3f3e3-176">**競合を表示するには**</span><span class="sxs-lookup"><span data-stu-id="3f3e3-176">**To view conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="3f3e3-177">:[マージ パブリケーションでのデータの競合の表示および解決 &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="3f3e3-177">: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)</span></span>  
  
-   <span data-ttu-id="3f3e3-178">レプリケーション [!INCLUDE[tsql](../../../includes/tsql-md.md)] プログラミング:[マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)](../view-conflict-information-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="3f3e3-178">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] Programming: [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3e3-179">参照</span><span class="sxs-lookup"><span data-stu-id="3f3e3-179">See Also</span></span>  
 [<span data-ttu-id="3f3e3-180">データの同期</span><span class="sxs-lookup"><span data-stu-id="3f3e3-180">Synchronize Data</span></span>](../synchronize-data.md)  
  
  
