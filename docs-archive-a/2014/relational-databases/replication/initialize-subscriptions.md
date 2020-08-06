---
title: サブスクリプションの初期化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8c9388138ddec275dc1abd2b75e0b0c7fc99de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632328"
---
# <a name="initialize-subscriptions"></a><span data-ttu-id="20bbd-102">サブスクリプションの初期化</span><span class="sxs-lookup"><span data-stu-id="20bbd-102">Initialize Subscriptions</span></span>
  <span data-ttu-id="20bbd-103">レプリケートされたデータをサブスクライバーで受信するためには、あらかじめサブスクライバーを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20bbd-103">Subscribers must be initialized before they can begin receiving replicated data.</span></span> <span data-ttu-id="20bbd-104">初期データセットは必要ありませんが、少なくともサブスクライバーは、レプリケートされたそれぞれのオブジェクトのスキーマと、レプリケーションに必要なメタデータ テーブルおよびプロシージャを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="20bbd-104">An initial dataset is not required, but the Subscriber must at least have the schema for each replicated object and any metadata tables and procedures required by replication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="20bbd-105">オプション</span><span class="sxs-lookup"><span data-stu-id="20bbd-105">Options</span></span>  
 <span data-ttu-id="20bbd-106">**[サブスクリプションのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="20bbd-106">**Subscription properties**</span></span>  
 <span data-ttu-id="20bbd-107">初期データセットを必要とするそれぞれのサブスクライバーの **[初期化]** 列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="20bbd-107">Select the check box in the **Initialize** column for each Subscriber that requires an initial data set.</span></span> <span data-ttu-id="20bbd-108">チェック ボックスがオフの場合は、レプリケーション メタデータおよびプロシージャのみが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="20bbd-108">If the check box is cleared, only the replication metadata and procedures will be initialized.</span></span> <span data-ttu-id="20bbd-109">スナップショットを使用せずにサブスクリプションを初期化する方法については、「[Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)」 (スナップショットを使用しないトランザクション サブスクリプションの初期化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20bbd-109">For more information about initializing a subscription without a snapshot, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
 <span data-ttu-id="20bbd-110">このウィザードが完了した後にマージ エージェントまたはディストリビューション エージェントによってスナップショット ファイルがサブスクライバーに転送されるようにするには、 **[次の場合に初期化]** 列のドロップダウン リストから **[今すぐ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="20bbd-110">Select **Immediately** from the drop-down list box in the **Initialize When** column to have the Merge Agent or Distribution Agent transfer snapshot files to the Subscriber after this wizard is completed.</span></span> <span data-ttu-id="20bbd-111">エージェントの次回の実行時にファイルが転送されるようにするには、 **[初回同期時]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="20bbd-111">Select **At first synchronization** to have the agent transfer the files the next time it is scheduled to run.</span></span> <span data-ttu-id="20bbd-112">**[今すぐ]** オプションは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] へのプル サブスクリプションに対して使用できません。</span><span class="sxs-lookup"><span data-stu-id="20bbd-112">The **Immediately** option is not available for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="20bbd-113">マージ エージェントおよびディストリビューション エージェントは、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]のインスタンス上で実行されません。したがって、サブスクリプションを別の方法で初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20bbd-113">The Merge Agent and Distribution Agent do not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]; therefore the subscription must be initialized through another method.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20bbd-114">ディストリビューション エージェントまたはマージ エージェントの適切なジョブを開始するために、ウィザードによりディストリビューターへの接続が要求される場合があります。</span><span class="sxs-lookup"><span data-stu-id="20bbd-114">The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bbd-115">参照</span><span class="sxs-lookup"><span data-stu-id="20bbd-115">See Also</span></span>  
 <span data-ttu-id="20bbd-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="20bbd-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="20bbd-117">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="20bbd-117">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="20bbd-118">[サブスクリプションの初期化](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="20bbd-118">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="20bbd-119">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="20bbd-119">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
