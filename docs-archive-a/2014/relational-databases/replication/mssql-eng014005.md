---
title: MSSQL_ENG014005 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d820fd26cceee72b0d08204d6f6ce73a76508e9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631822"
---
# <a name="mssql_eng014005"></a><span data-ttu-id="62a08-102">MSSQL_ENG014005</span><span class="sxs-lookup"><span data-stu-id="62a08-102">MSSQL_ENG014005</span></span>
    
## <a name="message-details"></a><span data-ttu-id="62a08-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="62a08-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62a08-104">製品名</span><span class="sxs-lookup"><span data-stu-id="62a08-104">Product Name</span></span>|<span data-ttu-id="62a08-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="62a08-105">SQL Server</span></span>|  
|<span data-ttu-id="62a08-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="62a08-106">Event ID</span></span>|<span data-ttu-id="62a08-107">14005</span><span class="sxs-lookup"><span data-stu-id="62a08-107">14005</span></span>|  
|<span data-ttu-id="62a08-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="62a08-108">Event Source</span></span>|<span data-ttu-id="62a08-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="62a08-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="62a08-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="62a08-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="62a08-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="62a08-111">Symbolic Name</span></span>||  
|<span data-ttu-id="62a08-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="62a08-112">Message Text</span></span>|<span data-ttu-id="62a08-113">パブリケーションを削除できませんでした。</span><span class="sxs-lookup"><span data-stu-id="62a08-113">Could not drop publication.</span></span> <span data-ttu-id="62a08-114">サブスクリプションが存在します。</span><span class="sxs-lookup"><span data-stu-id="62a08-114">A subscription exists to it.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="62a08-115">説明</span><span class="sxs-lookup"><span data-stu-id="62a08-115">Explanation</span></span>  
 <span data-ttu-id="62a08-116">1 つ以上のサブスクリプションが関連付けられているパブリケーションを削除しようとしました。</span><span class="sxs-lookup"><span data-stu-id="62a08-116">You have tried to drop a publication which has one or more associated subscriptions.</span></span> <span data-ttu-id="62a08-117">パブリケーションは、サブスクリプションが関連付けられていない場合にのみ削除できます。</span><span class="sxs-lookup"><span data-stu-id="62a08-117">A publication can only be dropped if there are no associated subscriptions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="62a08-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="62a08-118">User Action</span></span>  
 <span data-ttu-id="62a08-119">パブリケーションを削除する前にサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="62a08-119">Drop the subscriptions before dropping the publication.</span></span> <span data-ttu-id="62a08-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してパブリケーションを削除する場合は、パブリケーションを削除する前に関連するすべてのサブスクリプションを自動的に削除するオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="62a08-120">If you use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to drop the publication, it will give you the option to automatically drop all associated subscriptions before dropping the publication.</span></span> <span data-ttu-id="62a08-121">ストアド プロシージャを使用する場合は、最初にサブスクリプションを明示的に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62a08-121">If you use stored procedures, you must explicitly drop the subscriptions first.</span></span> <span data-ttu-id="62a08-122">詳細については、「 [Delete a Push Subscription](delete-a-push-subscription.md) 」および「 [Delete a Pull Subscription](delete-a-pull-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62a08-122">For more information, see [Delete a Push Subscription](delete-a-push-subscription.md) and [Delete a Pull Subscription](delete-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="62a08-123">パブリケーションに存在するサブスクリプションが表示されない場合や、パブリケーションの作成時にこのエラーが表示される場合は、前のサブスクリプションを削除したときに完全にクリーンアップされていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="62a08-123">If no subscriptions appear to exist for the publication or if you see this error when you create a publication, you might have a previous subscription that was not completely cleaned up when it was removed.</span></span> <span data-ttu-id="62a08-124">レプリケーションに関連するすべてのオブジェクトと設定を削除するには、データベースで [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="62a08-124">Execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) on the database to remove all objects and settings related to replication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62a08-125">参照</span><span class="sxs-lookup"><span data-stu-id="62a08-125">See Also</span></span>  
 [<span data-ttu-id="62a08-126">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="62a08-126">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
