---
title: サブスクリプションの種類 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 614ff910b13706485ee9466c884243ff1c9027ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715186"
---
# <a name="subscription-type"></a><span data-ttu-id="09399-102">サブスクリプションの種類</span><span class="sxs-lookup"><span data-stu-id="09399-102">Subscription Type</span></span>
  <span data-ttu-id="09399-103">マージ レプリケーションでは、サーバーとクライアントという 2 つのサブスクリプションの種類がオファーされます。[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンでは、これらはグローバルとローカルと呼ばれていました。</span><span class="sxs-lookup"><span data-stu-id="09399-103">Merge replication offers two subscription types: server and client (referred to in previous versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as global and local, respectively).</span></span> <span data-ttu-id="09399-104">サブスクライバーはサーバー サブスクリプションによって次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="09399-104">Subscribers with a server subscription can:</span></span>  
  
-   <span data-ttu-id="09399-105">他のサブスクライバーにデータを再パブリッシュする。</span><span class="sxs-lookup"><span data-stu-id="09399-105">Republish data to other Subscribers.</span></span>  
  
-   <span data-ttu-id="09399-106">代わりの同期パートナーを提供する。</span><span class="sxs-lookup"><span data-stu-id="09399-106">Serve as alternate synchronization partners.</span></span>  
  
-   <span data-ttu-id="09399-107">設定された優先度に応じて競合を解決する。</span><span class="sxs-lookup"><span data-stu-id="09399-107">Resolve conflicts according to a priority you set.</span></span>  
  
 <span data-ttu-id="09399-108">ほとんどのサブスクライバーは、この機能を必要とせず、クライアント サブスクリプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="09399-108">Most Subscribers do not require this functionality and can use a client subscription.</span></span> <span data-ttu-id="09399-109">クライアント サブスクリプションは競合の検出と解決ができますが、サブスクライバーには優先度が割り当てられていません。変更によって競合が発生した場合は、変更をパブリッシャーに最初に送信したサブスクライバーが優先されます。</span><span class="sxs-lookup"><span data-stu-id="09399-109">Client subscriptions still allow conflict detection and resolution, but Subscribers are not assigned a priority: the first Subscriber to submit a change to the Publisher wins any conflicts that might arise from that change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09399-110">サブスクリプションの種類は、作成後に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="09399-110">Subscription type cannot be changed after a subscription is created.</span></span>  
  
## <a name="options"></a><span data-ttu-id="09399-111">オプション</span><span class="sxs-lookup"><span data-stu-id="09399-111">Options</span></span>  
 <span data-ttu-id="09399-112">**[サブスクリプションのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="09399-112">**Subscription properties**</span></span>  
 <span data-ttu-id="09399-113">**[サブスクリプションの種類]** 列のドロップダウン リスト ボックスで、各サブスクライバーに対して、 **[クライアント]** または **[サーバー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="09399-113">For each Subscriber, select **Client** or **Server** from the drop-down list box in the **Subscription Type** column.</span></span> <span data-ttu-id="09399-114">サブスクライバーでサーバー サブスクリプションを使用する場合は、 **[競合解決の優先度]** 列に 0 ～ 99.99 の範囲の数値を入力します。数字が大きいほどサブスクライバーに対する優先度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="09399-114">For Subscribers with server subscriptions, enter a number between 0 and 99.99 in the **Priority for Conflict Resolution** column (the higher the number, the higher the priority for the Subscriber).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09399-115">参照</span><span class="sxs-lookup"><span data-stu-id="09399-115">See Also</span></span>  
 <span data-ttu-id="09399-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="09399-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="09399-117">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="09399-117">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="09399-118">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="09399-118">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
