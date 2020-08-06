---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ec584649842f787b1de9d2ea6d161aea6970250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736366"
---
# <a name="mssqlserver_10519"></a><span data-ttu-id="83918-102">MSSQLSERVER_10519</span><span class="sxs-lookup"><span data-stu-id="83918-102">MSSQLSERVER_10519</span></span>
    
## <a name="details"></a><span data-ttu-id="83918-103">詳細</span><span class="sxs-lookup"><span data-stu-id="83918-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83918-104">製品名</span><span class="sxs-lookup"><span data-stu-id="83918-104">Product Name</span></span>|<span data-ttu-id="83918-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="83918-105">SQL Server</span></span>|  
|<span data-ttu-id="83918-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83918-106">Event ID</span></span>|<span data-ttu-id="83918-107">10519</span><span class="sxs-lookup"><span data-stu-id="83918-107">10519</span></span>|  
|<span data-ttu-id="83918-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="83918-108">Event Source</span></span>|<span data-ttu-id="83918-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="83918-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="83918-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="83918-110">Component</span></span>|<span data-ttu-id="83918-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="83918-111">SQLEngine</span></span>|  
|<span data-ttu-id="83918-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="83918-112">Symbolic Name</span></span>|<span data-ttu-id="83918-113">PG_INCOMPATIBLE_STMT_AND_HINTS</span><span class="sxs-lookup"><span data-stu-id="83918-113">PG_INCOMPATIBLE_STMT_AND_HINTS</span></span>|  
|<span data-ttu-id="83918-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="83918-114">Message Text</span></span>|<span data-ttu-id="83918-115">プラン ガイド '%.\*ls' を作成できません。`@hints` で指定されたヒントを、`@stmt` または `@statement_start_offset` のいずれかで指定されたステートメントに適用できません。</span><span class="sxs-lookup"><span data-stu-id="83918-115">Cannot create plan guide '%.\*ls' because the hints specified in `@hints` cannot be applied to the statement specified by either `@stmt` or `@statement_start_offset`.</span></span> <span data-ttu-id="83918-116">ヒントがステートメントに適用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="83918-116">Verify that the hints can be applied to the statement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="83918-117">説明</span><span class="sxs-lookup"><span data-stu-id="83918-117">Explanation</span></span>  
 <span data-ttu-id="83918-118">`@hints` で指定されたヒントを、`@stmt` または `@statement_start_offset` のいずれかで指定されたステートメントに適用できません。</span><span class="sxs-lookup"><span data-stu-id="83918-118">The hints specified in `@hints` cannot be applied to the statement specified by either `@stmt` or `@statement_start_offset`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="83918-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="83918-119">User Action</span></span>  
 <span data-ttu-id="83918-120">ステートメントに適用できるヒントを指定します。</span><span class="sxs-lookup"><span data-stu-id="83918-120">Specify hints that can be applied to the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83918-121">参照</span><span class="sxs-lookup"><span data-stu-id="83918-121">See Also</span></span>  
 <span data-ttu-id="83918-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="83918-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="83918-123">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="83918-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="83918-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83918-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
