---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b39ed0d8ffe5f7f601b6cb1393596d0d6546e557
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642816"
---
# <a name="mssqlserver_8649"></a><span data-ttu-id="cf714-102">MSSQLSERVER_8649</span><span class="sxs-lookup"><span data-stu-id="cf714-102">MSSQLSERVER_8649</span></span>
    
## <a name="details"></a><span data-ttu-id="cf714-103">詳細</span><span class="sxs-lookup"><span data-stu-id="cf714-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf714-104">製品名</span><span class="sxs-lookup"><span data-stu-id="cf714-104">Product Name</span></span>|<span data-ttu-id="cf714-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cf714-105">SQL Server</span></span>|  
|<span data-ttu-id="cf714-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="cf714-106">Event ID</span></span>|<span data-ttu-id="cf714-107">8649</span><span class="sxs-lookup"><span data-stu-id="cf714-107">8649</span></span>|  
|<span data-ttu-id="cf714-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="cf714-108">Event Source</span></span>|<span data-ttu-id="cf714-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cf714-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cf714-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="cf714-110">Component</span></span>|<span data-ttu-id="cf714-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cf714-111">SQLEngine</span></span>|  
|<span data-ttu-id="cf714-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="cf714-112">Symbolic Name</span></span>|<span data-ttu-id="cf714-113">COST_TOO_HIGH</span><span class="sxs-lookup"><span data-stu-id="cf714-113">COST_TOO_HIGH</span></span>|  
|<span data-ttu-id="cf714-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="cf714-114">Message Text</span></span>|<span data-ttu-id="cf714-115">このクエリの見積コスト (%d) が設定されたしきい値 %d を超えたので、クエリは取り消されました。</span><span class="sxs-lookup"><span data-stu-id="cf714-115">The query has been canceled because the estimated cost of this query (%d) exceeds the configured threshold of %d.</span></span> <span data-ttu-id="cf714-116">システム管理者に連絡してください。</span><span class="sxs-lookup"><span data-stu-id="cf714-116">Contact the system administrator.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf714-117">説明</span><span class="sxs-lookup"><span data-stu-id="cf714-117">Explanation</span></span>  
 <span data-ttu-id="cf714-118">このクエリの見積コストは、QUERY_GOVERNOR_COST_LIMIT に対して設定されているしきい値を超えたので、クエリが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="cf714-118">The query was canceled because the estimated cost of this query exceeds the configured threshold set for the QUERY_GOVERNOR_COST_LIMIT.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf714-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="cf714-119">User Action</span></span>  
 <span data-ttu-id="cf714-120">QUERY_GOVERNOR_COST_LIMIT オプションの設定値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="cf714-120">Set the QUERY_GOVERNOR_COST_LIMIT option to a higher value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf714-121">参照</span><span class="sxs-lookup"><span data-stu-id="cf714-121">See Also</span></span>  
 [<span data-ttu-id="cf714-122">SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cf714-122">SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)  
  
  
