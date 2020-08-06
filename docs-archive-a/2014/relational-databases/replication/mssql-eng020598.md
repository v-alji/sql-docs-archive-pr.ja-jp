---
title: MSSQL_ENG020598 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cef26001c353dea94ec9b658dfb38285231bc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714190"
---
# <a name="mssql_eng020598"></a><span data-ttu-id="26c91-102">MSSQL_ENG020598</span><span class="sxs-lookup"><span data-stu-id="26c91-102">MSSQL_ENG020598</span></span>
    
## <a name="message-details"></a><span data-ttu-id="26c91-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="26c91-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26c91-104">製品名</span><span class="sxs-lookup"><span data-stu-id="26c91-104">Product Name</span></span>|<span data-ttu-id="26c91-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="26c91-105">SQL Server</span></span>|  
|<span data-ttu-id="26c91-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="26c91-106">Event ID</span></span>|<span data-ttu-id="26c91-107">20598</span><span class="sxs-lookup"><span data-stu-id="26c91-107">20598</span></span>|  
|<span data-ttu-id="26c91-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="26c91-108">Event Source</span></span>|<span data-ttu-id="26c91-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="26c91-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="26c91-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="26c91-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="26c91-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="26c91-111">Symbolic Name</span></span>||  
|<span data-ttu-id="26c91-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="26c91-112">Message Text</span></span>|<span data-ttu-id="26c91-113">レプリケートされたコマンドを適用しているときに、サブスクライバーで行が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="26c91-113">The row was not found at the Subscriber when applying the replicated command.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="26c91-114">説明</span><span class="sxs-lookup"><span data-stu-id="26c91-114">Explanation</span></span>  
 <span data-ttu-id="26c91-115">このエラーは、トランザクション レプリケーションで、ディストリビューション エージェントがサブスクライバーの行を更新しようとしたときに、行が削除されていたり、行の主キーが変更されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="26c91-115">This error is raised in transactional replication if the Distribution Agent attempts to update a row at the Subscriber, but the row has been deleted or the primary key of the row has been changed.</span></span> <span data-ttu-id="26c91-116">既定では、変更はパブリッシャーには反映されないため、トランザクション パブリケーションに対するサブスクライバーは読み取り専用として処理されます。</span><span class="sxs-lookup"><span data-stu-id="26c91-116">By default, Subscribers to transactional publications should be treated as read-only, because changes are not propagated back to the Publisher.</span></span> <span data-ttu-id="26c91-117">トランザクション レプリケーションでは、更新可能なサブスクリプションまたはピア ツー ピア レプリケーションが使用されている場合にのみ、ユーザーの変更をサブスクライバーで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="26c91-117">For transactional replication, user changes should be made at the Subscriber only if updatable subscriptions or peer-to-peer replication is used.</span></span> <span data-ttu-id="26c91-118">これらのオプションの詳細については、「 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) 」および「 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26c91-118">For information about these options, see [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) and [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="26c91-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="26c91-119">User Action</span></span>  
 <span data-ttu-id="26c91-120">**この問題を解決するには、次のようにします。**</span><span class="sxs-lookup"><span data-stu-id="26c91-120">**To resolve this problem:**</span></span>  
  
1.  <span data-ttu-id="26c91-121">エラーの原因を特定している間にレプリケーションを続行する必要がある場合は、ディストリビューション エージェントで **-SkipErrors 20598** パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="26c91-121">If replication must continue while you identify the source of the error, specify the parameter **-SkipErrors 20598** for the Distribution Agent.</span></span> <span data-ttu-id="26c91-122">このパラメーターを指定すると、エージェントはエラー 20598 の原因となった変更をスキップし、他の変更をレプリケートできるようになります。</span><span class="sxs-lookup"><span data-stu-id="26c91-122">This allows the agent to skip changes that result in error 20598, while allowing other changes to be replicated.</span></span>  
  
2.  <span data-ttu-id="26c91-123">削除されている行、またはパブリッシャーの対応する行とは異なる主キーを持っているサブスクライバーの行を特定します。</span><span class="sxs-lookup"><span data-stu-id="26c91-123">Identify which rows at the Subscriber have been deleted or have a different primary key than the corresponding rows at the Publisher.</span></span> <span data-ttu-id="26c91-124">パブリケーションとサブスクリプション データベースとの間で異なる行を確認するには、 [tablediff Utility](../../tools/tablediff-utility.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="26c91-124">You can use the [tablediff Utility](../../tools/tablediff-utility.md) to determine which rows are different in the publication and subscription databases.</span></span> <span data-ttu-id="26c91-125">レプリケートされたデータベースでのこのユーティリティの使用については、「[レプリケートされたテーブルを比較して相違があるかどうかを確認する &#40;レプリケーション プログラミング&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26c91-125">For information about using this utility with replicated databases, see [Compare Replicated Tables for Differences &#40;Replication Programming&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md).</span></span>  
  
3.  <span data-ttu-id="26c91-126">**tablediff** ユーティリティまたは別の方法でサブスクライバーの行を修正します。</span><span class="sxs-lookup"><span data-stu-id="26c91-126">Correct the rows at the Subscriber using the **tablediff** utility or another method.</span></span>  
  
4.  <span data-ttu-id="26c91-127">(省略可能) **-SkipErrors** パラメーターを削除します。</span><span class="sxs-lookup"><span data-stu-id="26c91-127">(Optional) Remove the **-SkipErrors** parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c91-128">参照</span><span class="sxs-lookup"><span data-stu-id="26c91-128">See Also</span></span>  
 [<span data-ttu-id="26c91-129">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="26c91-129">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
