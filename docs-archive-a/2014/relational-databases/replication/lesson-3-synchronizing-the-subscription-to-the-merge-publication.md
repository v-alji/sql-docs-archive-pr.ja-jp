---
title: 'レッスン 3: マージ パブリケーションへのサブスクリプションの同期 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
author: rothja
ms.author: jroth
ms.openlocfilehash: bf0256c69d69d1236869fa83285bf4dbf5c462da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739697"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a><span data-ttu-id="3070d-102">レッスン 3:マージ パブリケーションへのサブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="3070d-102">Lesson 3: Synchronizing the Subscription to the Merge Publication</span></span>
  <span data-ttu-id="3070d-103">このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でマージ エージェントを起動して、サブスクリプションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="3070d-103">In this lesson, you will start the Merge Agent to initialize the subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3070d-104">この手順を使用して、パブリッシャーと同期することもできます。</span><span class="sxs-lookup"><span data-stu-id="3070d-104">You also use this procedure to synchronize with the Publisher.</span></span> <span data-ttu-id="3070d-105">このレッスンを始める前に、前のレッスンの「 [レッスン 2: マージ パブリケーションへのサブスクリプションの作成](lesson-2-creating-a-subscription-to-the-merge-publication.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3070d-105">This lesson requires that you have completed the previous lesson, [Lesson 2: Creating a Subscription to the Merge Publication](lesson-2-creating-a-subscription-to-the-merge-publication.md).</span></span>  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a><span data-ttu-id="3070d-106">同期を開始しサブスクリプションを初期化するには</span><span class="sxs-lookup"><span data-stu-id="3070d-106">To start synchronization and initialize the subscription</span></span>  
  
1.  <span data-ttu-id="3070d-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、サーバー ノードを展開して、 **[レプリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="3070d-107">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="3070d-108">**[ローカル サブスクリプション]** フォルダーで、 **SalesOrdersReplica** データベースのサブスクリプションを右クリックし、 **[同期の状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3070d-108">In the **Local Subscriptions** folder, right-click the subscription in the **SalesOrdersReplica** database, and then click **View Synchronization Status**.</span></span>  
  
3.  <span data-ttu-id="3070d-109">**[開始]** をクリックして、サブスクリプションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="3070d-109">Click **Start** to initialize the subscription.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3070d-110">次の手順</span><span class="sxs-lookup"><span data-stu-id="3070d-110">Next Steps</span></span>  
 <span data-ttu-id="3070d-111">ここでは、マージ エージェントを実行し、同期の開始とサブスクリプションの初期化を行いました。</span><span class="sxs-lookup"><span data-stu-id="3070d-111">You have successfully run the Merge Agent to start synchronization and initialize the subscription.</span></span> <span data-ttu-id="3070d-112">パブリッシャーまたはサブスクライバー側で、 **SalesOrderHeader** テーブルまたは **SalesOrderDetail** テーブルに対しデータの挿入、変更、削除を行い、ネットワーク接続が使用できるときにこの手順でパブリッシャーとサブスクライバーの間のデータを同期した後、もう一方のサーバーの **SalesOrderHeader** テーブルまたは **SalesOrderDetail** テーブルにクエリを実行すると、レプリケートされた変更を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="3070d-112">You can also insert, update, or delete data in the **SalesOrderHeader** or **SalesOrderDetail** tables at the Publisher or Subscriber, repeat this procedure when network connectivity is available to synchronize data between the Publisher and the Subscriber, and then query the **SalesOrderHeader** or **SalesOrderDetail** tables at the other server to view the replicated changes.</span></span>  
  
 <span data-ttu-id="3070d-113">以上で、モバイル クライアントとの間のデータのレプリケーションに関するチュートリアルは完了です。</span><span class="sxs-lookup"><span data-stu-id="3070d-113">This completes the Replicating Data with Mobile Clients tutorial.</span></span> <span data-ttu-id="3070d-114">トランザクション レプリケーションを使用する類似のチュートリアルとして、「 [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="3070d-114">For a similar tutorial that uses transactional replication, see [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3070d-115">参照</span><span class="sxs-lookup"><span data-stu-id="3070d-115">See Also</span></span>  
 <span data-ttu-id="3070d-116">[Initialize a Subscription with a Snapshot (スナップショットを使用したサブスクリプションの初期化)](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="3070d-116">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="3070d-117">[データの同期](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="3070d-117">[Synchronize Data](synchronize-data.md) </span></span>  
 [<span data-ttu-id="3070d-118">プル サブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="3070d-118">Synchronize a Pull Subscription</span></span>](synchronize-a-pull-subscription.md)  
  
  
