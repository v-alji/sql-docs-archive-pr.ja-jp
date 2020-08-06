---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73194c7da553bf27acb78d8c4e7d71bc93f457d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741061"
---
# <a name="mssqlserver_10509"></a><span data-ttu-id="5989f-102">MSSQLSERVER_10509</span><span class="sxs-lookup"><span data-stu-id="5989f-102">MSSQLSERVER_10509</span></span>
    
## <a name="details"></a><span data-ttu-id="5989f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="5989f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5989f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="5989f-104">Product Name</span></span>|<span data-ttu-id="5989f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5989f-105">SQL Server</span></span>|  
|<span data-ttu-id="5989f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5989f-106">Event ID</span></span>|<span data-ttu-id="5989f-107">10509</span><span class="sxs-lookup"><span data-stu-id="5989f-107">10509</span></span>|  
|<span data-ttu-id="5989f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="5989f-108">Event Source</span></span>|<span data-ttu-id="5989f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5989f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5989f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5989f-110">Component</span></span>|<span data-ttu-id="5989f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5989f-111">SQLEngine</span></span>|  
|<span data-ttu-id="5989f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="5989f-112">Symbolic Name</span></span>|<span data-ttu-id="5989f-113">PG_INVALID_STMT</span><span class="sxs-lookup"><span data-stu-id="5989f-113">PG_INVALID_STMT</span></span>|  
|<span data-ttu-id="5989f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="5989f-114">Message Text</span></span>|<span data-ttu-id="5989f-115">プラン ガイド '%.\*ls' を作成できません。`@stmt` または `@statement_start_offset` で指定したステートメントが構文エラーを含んでいるか、またはプラン ガイドでの使用に適していません。</span><span class="sxs-lookup"><span data-stu-id="5989f-115">Cannot create plan guide '%.\*ls' because the statement specified by `@stmt` or `@statement_start_offset` either contains a syntax error or is ineligible for use in a plan guide.</span></span> <span data-ttu-id="5989f-116">有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つだけ指定するか、またはバッチ内のステートメントの有効な開始位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="5989f-116">Provide a single valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a valid starting position of the statement within the batch.</span></span> <span data-ttu-id="5989f-117">有効な開始位置を取得するには、動的管理関数 sys.dm_exec_query_stats の statement_start_offset 列のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="5989f-117">To obtain a valid starting position, query the statement_start_offset column in the sys.dm_exec_query_stats dynamic management function.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5989f-118">説明</span><span class="sxs-lookup"><span data-stu-id="5989f-118">Explanation</span></span>  
 <span data-ttu-id="5989f-119">`@stmt` または `@statement_start_offset` で指定したステートメントが構文エラーを含んでいるか、またはプラン ガイドでの使用に適していません。</span><span class="sxs-lookup"><span data-stu-id="5989f-119">The statement specified by `@stmt` or `@statement_start_offset` either contains a syntax error or is ineligible for use in a plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5989f-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="5989f-120">User Action</span></span>  
 <span data-ttu-id="5989f-121">有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つだけ指定するか、またはバッチ内のステートメントの有効な開始位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="5989f-121">Provide a single valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a valid starting position of the statement within the batch.</span></span> <span data-ttu-id="5989f-122">有効な開始位置を取得するには、動的管理関数 sys.dm_exec_query_stats の statement_start_offset 列のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="5989f-122">To obtain a valid starting position, query the statement_start_offset column in the sys.dm_exec_query_stats dynamic management function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5989f-123">参照</span><span class="sxs-lookup"><span data-stu-id="5989f-123">See Also</span></span>  
 <span data-ttu-id="5989f-124">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5989f-124">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="5989f-125">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="5989f-125">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="5989f-126">[dm_exec_query_stats &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5989f-126">[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) </span></span>  
 [<span data-ttu-id="5989f-127">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5989f-127">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
