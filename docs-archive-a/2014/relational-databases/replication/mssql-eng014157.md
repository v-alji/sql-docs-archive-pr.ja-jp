---
title: MSSQL_ENG014157 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0682d740d82c995d64427f56aabce24b8a48ca65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639459"
---
# <a name="mssql_eng014157"></a><span data-ttu-id="3ca52-102">MSSQL_ENG014157</span><span class="sxs-lookup"><span data-stu-id="3ca52-102">MSSQL_ENG014157</span></span>
    
## <a name="message-details"></a><span data-ttu-id="3ca52-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="3ca52-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ca52-104">製品名</span><span class="sxs-lookup"><span data-stu-id="3ca52-104">Product Name</span></span>|<span data-ttu-id="3ca52-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3ca52-105">SQL Server</span></span>|  
|<span data-ttu-id="3ca52-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3ca52-106">Event ID</span></span>|<span data-ttu-id="3ca52-107">14157</span><span class="sxs-lookup"><span data-stu-id="3ca52-107">14157</span></span>|  
|<span data-ttu-id="3ca52-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="3ca52-108">Event Source</span></span>|<span data-ttu-id="3ca52-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3ca52-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3ca52-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3ca52-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="3ca52-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="3ca52-111">Symbolic Name</span></span>||  
|<span data-ttu-id="3ca52-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="3ca52-112">Message Text</span></span>|<span data-ttu-id="3ca52-113">サブスクライバー '%s' によって作成された、パブリケーション '%s' に対するサブスクリプションは、有効期限が切れたので削除されました。</span><span class="sxs-lookup"><span data-stu-id="3ca52-113">The subscription created by Subscriber '%s' to publication '%s' has expired and has been dropped.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3ca52-114">説明</span><span class="sxs-lookup"><span data-stu-id="3ca52-114">Explanation</span></span>  
 <span data-ttu-id="3ca52-115">サブスクライバーは、パブリケーションの保有期間で指定された時間内にパブリッシャーと同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ca52-115">A Subscriber must synchronize with the Publisher within the time specified in the publication retention period.</span></span> <span data-ttu-id="3ca52-116">サブスクライバーがこの期間内に同期しないと、サブスクリプションの有効期限が切れます。</span><span class="sxs-lookup"><span data-stu-id="3ca52-116">If a Subscriber does not synchronize within this period, the subscription expires.</span></span> <span data-ttu-id="3ca52-117">詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ca52-117">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3ca52-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="3ca52-118">User Action</span></span>  
 <span data-ttu-id="3ca52-119">サブスクライバーがデータ変更の受信を再び開始するには、サブスクリプションを再作成して初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ca52-119">The subscription must be re-created and initialized before the Subscriber can begin receiving data changes again:</span></span>  
  
-   <span data-ttu-id="3ca52-120">サブスクリプションの作成については、「[パブリケーションのサブスクライブ](subscribe-to-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ca52-120">For information about creating subscriptions, see [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
-   <span data-ttu-id="3ca52-121">サブスクリプションの初期化については、「[サブスクリプションの初期化](initialize-a-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ca52-121">For information about initializing subscriptions, see [Initialize a Subscription](initialize-a-subscription.md).</span></span>  
  
 <span data-ttu-id="3ca52-122">サブスクリプション データベースに、パブリッシャーと同期していない変更が含まれる場合は、 [tablediff Utility](../../tools/tablediff-utility.md) を使用して、パブリケーションとサブスクリプション データベースとの間で異なる行を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3ca52-122">If the subscription database contains changes that have not been synchronized with the Publisher, you can use the [tablediff Utility](../../tools/tablediff-utility.md) to determine which rows are different in the publication and subscription databases.</span></span>  
  
 <span data-ttu-id="3ca52-123">サブスクリプションの有効期限が切れないように、パブリケーションの保有期間を長くすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ca52-123">You can increase the publication retention period to avoid having subscriptions expire.</span></span> <span data-ttu-id="3ca52-124">保有期間に高い値を設定すると、保存されるデータとメタデータの量が増えてパフォーマンスに影響するため注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="3ca52-124">Use caution in setting a high value, because this can result in more data and metadata being stored, which affects performance.</span></span> <span data-ttu-id="3ca52-125">詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ca52-125">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca52-126">参照</span><span class="sxs-lookup"><span data-stu-id="3ca52-126">See Also</span></span>  
 [<span data-ttu-id="3ca52-127">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="3ca52-127">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
