---
title: MSSQLSERVER_10531 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6230c046a9eb7b900377888c59a3a492f2b89f73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715385"
---
# <a name="mssqlserver_10531"></a><span data-ttu-id="273a0-102">MSSQLSERVER_10531</span><span class="sxs-lookup"><span data-stu-id="273a0-102">MSSQLSERVER_10531</span></span>
    
## <a name="details"></a><span data-ttu-id="273a0-103">詳細</span><span class="sxs-lookup"><span data-stu-id="273a0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="273a0-104">製品名</span><span class="sxs-lookup"><span data-stu-id="273a0-104">Product Name</span></span>|<span data-ttu-id="273a0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="273a0-105">SQL Server</span></span>|  
|<span data-ttu-id="273a0-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="273a0-106">Event ID</span></span>|<span data-ttu-id="273a0-107">10531</span><span class="sxs-lookup"><span data-stu-id="273a0-107">10531</span></span>|  
|<span data-ttu-id="273a0-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="273a0-108">Event Source</span></span>|<span data-ttu-id="273a0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="273a0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="273a0-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="273a0-110">Component</span></span>|<span data-ttu-id="273a0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="273a0-111">SQLEngine</span></span>|  
|<span data-ttu-id="273a0-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="273a0-112">Symbolic Name</span></span>|<span data-ttu-id="273a0-113">PG_NO_ELIGIBLE_STMT</span><span class="sxs-lookup"><span data-stu-id="273a0-113">PG_NO_ELIGIBLE_STMT</span></span>|  
|<span data-ttu-id="273a0-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="273a0-114">Message Text</span></span>|<span data-ttu-id="273a0-115">プラン ガイド '%.\*ls' をキャッシュから作成できません。ユーザーに適切な権限がありません。</span><span class="sxs-lookup"><span data-stu-id="273a0-115">Cannot create plan guide '%.\*ls' from cache because the user does not have adequate permissions.</span></span> <span data-ttu-id="273a0-116">プラン ガイドを作成するユーザーに VIEW SERVER STATE 権限を付与してください。</span><span class="sxs-lookup"><span data-stu-id="273a0-116">Grant the VIEW SERVER STATE permission to the user creating the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="273a0-117">説明</span><span class="sxs-lookup"><span data-stu-id="273a0-117">Explanation</span></span>  
 <span data-ttu-id="273a0-118">指定したプラン ガイドをプラン キャッシュから作成するための適切な権限がユーザーにありません。</span><span class="sxs-lookup"><span data-stu-id="273a0-118">The user does not have adequate permissions to create the specified plan guide from the plan cache.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="273a0-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="273a0-119">User Action</span></span>  
 <span data-ttu-id="273a0-120">プラン ガイドを作成するユーザーに VIEW SERVER STATE 権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="273a0-120">Grant VIEW SERVER STATE permission to the user creating the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273a0-121">参照</span><span class="sxs-lookup"><span data-stu-id="273a0-121">See Also</span></span>  
 <span data-ttu-id="273a0-122">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="273a0-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="273a0-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="273a0-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="273a0-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="273a0-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
