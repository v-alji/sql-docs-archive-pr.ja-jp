---
title: '[スナップショット エージェント] (パブリケーションの新規作成ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.configuresnapshotagent.f1
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c45fa3444fb2f81436a40a2bfb80519aea105c47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645506"
---
# <a name="snapshot-agent-new-publication-wizard"></a><span data-ttu-id="5ddc0-102">[スナップショット エージェント] (パブリケーションの新規作成ウィザード)</span><span class="sxs-lookup"><span data-stu-id="5ddc0-102">Snapshot Agent (New Publication Wizard)</span></span>
  <span data-ttu-id="5ddc0-103">[スナップショット エージェント] では、新しいサブスクリプションの初期化に使用されるパブリケーション スキーマおよびデータを含んでいるファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-103">The Snapshot Agent creates files containing the publication schema and data that are used to initialize new subscriptions.</span></span> <span data-ttu-id="5ddc0-104">既定では、スナップショット エージェントは、パブリケーションの新規作成ウィザードでパブリケーションが作成されるとすぐに実行されます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-104">By default, the Snapshot Agent runs immediately after the publication is created in the New Publication Wizard.</span></span> <span data-ttu-id="5ddc0-105">続いて、エージェントが指定したスケジュールに従って実行されます。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-105">Subsequently, the agent runs according to a schedule you specify.</span></span> <span data-ttu-id="5ddc0-106">エージェントが実行されるたびに新しいスナップショット ファイルが作成されるかどうかは、選択したレプリケーションおよびオプションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-106">Whether the agent creates new snapshot files each time it runs depends on the type of replication and options chosen.</span></span> <span data-ttu-id="5ddc0-107">詳細については、「[スナップショットの作成および適用](create-and-apply-the-snapshot.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-107">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="5ddc0-108">パラメーター化されたフィルターを使用するマージ パブリケーションでは、パブリケーション スナップショットの完了後、データの各パーティションのスナップショットを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-108">For merge publications that use parameterized filters, you must create a snapshot for each partition of data after the publication snapshot has completed.</span></span> <span data-ttu-id="5ddc0-109">詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-109">For more information, see [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5ddc0-110">Options</span><span class="sxs-lookup"><span data-stu-id="5ddc0-110">Options</span></span>  
 <span data-ttu-id="5ddc0-111">**[スナップショットをすぐに作成する]** (マージ レプリケーション) または **[スナップショットをすぐに作成し、サブスクリプションを初期化できるようにそのスナップショットを保持する]** (トランザクション レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="5ddc0-111">**Create a snapshot immediately** (merge replication) or **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** (transactional replication)</span></span>  
 <span data-ttu-id="5ddc0-112">パブリケーションの新規作成ウィザードが完了した後、すぐにスナップショットを作成する場合は、このチェック ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-112">Select this check box to create a snapshot immediately after the New Publication Wizard is completed.</span></span> <span data-ttu-id="5ddc0-113">スナップショットが生成される前に **[パブリケーションのプロパティ]** ダイアログ ボックスでスナップショットのプロパティを変更する場合、またはスナップショットを使用せずにサブスクライバーを初期化する場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-113">Clear this check box if you plan to change snapshot properties in the **Publication Properties** dialog box before generating a snapshot, or if you will initialize the Subscriber without a snapshot.</span></span> <span data-ttu-id="5ddc0-114">詳細については、「 [スナップショットを使用しないトランザクション サブスクリプションの初期化](initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-114">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ddc0-115">ディストリビューション エージェントまたはマージ エージェントの適切なジョブを開始するために、ウィザードによりディストリビューターへの接続が要求される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-115">The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.</span></span>  
  
 <span data-ttu-id="5ddc0-116">**[以下のスケジュールでスナップショット エージェントを実行する]**</span><span class="sxs-lookup"><span data-stu-id="5ddc0-116">**Schedule the Snapshot Agent to run at the following times**</span></span>  
 <span data-ttu-id="5ddc0-117">スナップショット エージェントを実行する既定のスケジュールを受け入れるか、 **[変更]** をクリックしてスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ddc0-117">Accept the default schedule for running the Snapshot Agent, or click **Change** to specify a schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ddc0-118">参照</span><span class="sxs-lookup"><span data-stu-id="5ddc0-118">See Also</span></span>  
 <span data-ttu-id="5ddc0-119">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="5ddc0-119">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="5ddc0-120">[初期スナップショットの作成および適用](create-and-apply-the-initial-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="5ddc0-120">[Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) </span></span>  
 <span data-ttu-id="5ddc0-121">[パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5ddc0-121">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="5ddc0-122">[Initialize a Subscription with a Snapshot (スナップショットを使用したサブスクリプションの初期化)](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="5ddc0-122">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="5ddc0-123">[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="5ddc0-123">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="5ddc0-124">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="5ddc0-124">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
