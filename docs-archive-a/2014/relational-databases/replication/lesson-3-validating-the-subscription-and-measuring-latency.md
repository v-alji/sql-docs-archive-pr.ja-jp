---
title: 'レッスン 3 : サブスクリプションの検証と待機時間の計測 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
author: rothja
ms.author: jroth
ms.openlocfilehash: e4893c054d25d131eb2f88f32291606b0b789af7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739696"
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a><span data-ttu-id="2f4f4-102">レッスン 3 : サブスクリプションの検証と待機時間の計測</span><span class="sxs-lookup"><span data-stu-id="2f4f4-102">Lesson 3: Validating the Subscription and Measuring Latency</span></span>
  <span data-ttu-id="2f4f4-103">このレッスンでは、トレーサー トークンを使用して、変更がサブスクライバーにレプリケートされているかどうかを検証し、待機時間を計測します。待機時間とは、パブリッシャーで加えられた変更がサブスクライバーに反映されるまでの所用時間です。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-103">In this lesson, you will use tracer tokens to verify that changes are being replicated to the Subscriber and to determine latency, the time it takes for a change made at the Publisher to appear to the Subscriber.</span></span> <span data-ttu-id="2f4f4-104">このレッスンを始める前に、前のレッスンの [「レッスン 2: トランザクション パブリケーションへのサブスクリプションの作成」](lesson-2-creating-a-subscription-to-the-transactional-publication.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-104">This lesson requires that you have completed the previous lesson, [Lesson 2: Creating a Subscription to the Transactional Publication](lesson-2-creating-a-subscription-to-the-transactional-publication.md).</span></span>  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a><span data-ttu-id="2f4f4-105">トレーサー トークンを挿入してトークンの情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="2f4f4-105">To insert a tracer token and view information on the token</span></span>  
  
1.  <span data-ttu-id="2f4f4-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続します。次に、サーバー ノードを展開して **[レプリケーション]** フォルダーを右クリックし、 **[レプリケーション モニターの起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-106">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, right-click the **Replication** folder, and then click **Launch Replication Monitor**.</span></span>  
  
     <span data-ttu-id="2f4f4-107">レプリケーション モニターが起動します。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-107">Replication Monitor launches.</span></span>  
  
2.  <span data-ttu-id="2f4f4-108">左ペインでパブリッシャー グループを展開し、パブリッシャー インスタンスを展開して、 **[AdvWorksProductTrans]** パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-108">Expand a Publisher group in the left pane, expand the Publisher instance, and then click the **AdvWorksProductTrans** publication.</span></span>  
  
3.  <span data-ttu-id="2f4f4-109">**[トレーサー トークン]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-109">Click the **Tracer Tokens** tab.</span></span>  
  
4.  <span data-ttu-id="2f4f4-110">**[トレーサーの挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-110">Click **Insert Tracer**.</span></span>  
  
5.  <span data-ttu-id="2f4f4-111">**[パブリッシャーからディストリビューターまで]** 列、 **[ディストリビューターからサブスクライバーまで]** 列、および **[合計待機時間]** 列で、トレーサー トークンの経過時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-111">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="2f4f4-112">値が**Pending**の場合は、トークンが特定のポイントに到達していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-112">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2f4f4-113">次の手順</span><span class="sxs-lookup"><span data-stu-id="2f4f4-113">Next Steps</span></span>  
 <span data-ttu-id="2f4f4-114">このレッスンでは、トレーサー トークンを使用して、データの変更がパブリッシャーからスクライバへレプリケートされているかどうかを検証しました。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-114">In this lesson, you successfully used tracer tokens to validate that data changes are being replicated from the Publisher to the Subscriber.</span></span> <span data-ttu-id="2f4f4-115">パブリッシャー側の **Product** テーブルに対してデータの挿入、更新、または削除を行い、レプリケーション後、サブスクライバー側の **Product** テーブルをクエリすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-115">You can also insert, update, or delete data in the **Product** table at the Publisher and query the **Product** table at the Subscriber to view these changes after they are replicated.</span></span>  
  
 <span data-ttu-id="2f4f4-116">チュートリアル「常時接続サーバー間でのデータのレプリケーション」はこれで完了です。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-116">This completes the Replicating Data Between Continuously Connected Servers tutorial.</span></span> <span data-ttu-id="2f4f4-117">マージ レプリケーションを使用する類似のチュートリアルについては、 [「チュートリアル: モバイル クライアントとの間のデータのレプリケーション」](tutorial-replicating-data-with-mobile-clients.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-117">For a similar tutorial that uses merge replication, see [Tutorial: Replicating Data with Mobile Clients](tutorial-replicating-data-with-mobile-clients.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4f4-118">参照</span><span class="sxs-lookup"><span data-stu-id="2f4f4-118">See Also</span></span>  
 [<span data-ttu-id="2f4f4-119">待機時間を計測して Connections for Transactional Replication を検証します。</span><span class="sxs-lookup"><span data-stu-id="2f4f4-119">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
