---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 00d08f4555f38b61661a917ba94c023f9dd6c4a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718225"
---
# <a name="mssqlserver_10536"></a><span data-ttu-id="403ce-102">MSSQLSERVER_10536</span><span class="sxs-lookup"><span data-stu-id="403ce-102">MSSQLSERVER_10536</span></span>
    
## <a name="details"></a><span data-ttu-id="403ce-103">詳細</span><span class="sxs-lookup"><span data-stu-id="403ce-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="403ce-104">製品名</span><span class="sxs-lookup"><span data-stu-id="403ce-104">Product Name</span></span>|<span data-ttu-id="403ce-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="403ce-105">SQL Server</span></span>|  
|<span data-ttu-id="403ce-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="403ce-106">Event ID</span></span>|<span data-ttu-id="403ce-107">10536</span><span class="sxs-lookup"><span data-stu-id="403ce-107">10536</span></span>|  
|<span data-ttu-id="403ce-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="403ce-108">Event Source</span></span>|<span data-ttu-id="403ce-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="403ce-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="403ce-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="403ce-110">Component</span></span>|<span data-ttu-id="403ce-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="403ce-111">SQLEngine</span></span>|  
|<span data-ttu-id="403ce-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="403ce-112">Symbolic Name</span></span>|<span data-ttu-id="403ce-113">PG_TOO_MANY_STMTS</span><span class="sxs-lookup"><span data-stu-id="403ce-113">PG_TOO_MANY_STMTS</span></span>|  
|<span data-ttu-id="403ce-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="403ce-114">Message Text</span></span>|<span data-ttu-id="403ce-115">プラン ガイド '%.\*ls' を作成できません。指定された `@plan_handle` に対応するバッチまたはモジュールに含まれるステートメントが 1000 個を超えています。</span><span class="sxs-lookup"><span data-stu-id="403ce-115">Cannot create plan guide '%.\*ls' because the batch or module corresponding to the specified `@plan_handle` contains more than 1000 eligible statements.</span></span> <span data-ttu-id="403ce-116">バッチまたはモジュールの各ステートメントに対して `statement_start_offset` 値を指定して、ステートメントごとにプラン ガイドを作成します。</span><span class="sxs-lookup"><span data-stu-id="403ce-116">Create a plan guide for each statement in the batch or module by specifying a `statement_start_offset` value for each statement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="403ce-117">説明</span><span class="sxs-lookup"><span data-stu-id="403ce-117">Explanation</span></span>  
 <span data-ttu-id="403ce-118">指定した `@plan_handle` に対応するバッチまたはモジュールに、条件を満たすステートメントが 1000 以上含まれています。</span><span class="sxs-lookup"><span data-stu-id="403ce-118">The batch or module corresponding to the specified `@plan_handle` contains more than 1000 eligible statements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="403ce-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="403ce-119">User Action</span></span>  
 <span data-ttu-id="403ce-120">バッチまたはモジュールの各ステートメントに対して `statement_start_offset` 値を指定して、ステートメントごとにプラン ガイドを作成します。</span><span class="sxs-lookup"><span data-stu-id="403ce-120">Create a plan guide for each statement in the batch or module by specifying a `statement_start_offset` value for each statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="403ce-121">参照</span><span class="sxs-lookup"><span data-stu-id="403ce-121">See Also</span></span>  
 <span data-ttu-id="403ce-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="403ce-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="403ce-123">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="403ce-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="403ce-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="403ce-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
