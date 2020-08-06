---
title: MSSQLSERVER_10502 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eeec3a3adf318cadc96501938f8a5565f1c07670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632000"
---
# <a name="mssqlserver_10502"></a><span data-ttu-id="d0cd7-102">MSSQLSERVER_10502</span><span class="sxs-lookup"><span data-stu-id="d0cd7-102">MSSQLSERVER_10502</span></span>
    
## <a name="details"></a><span data-ttu-id="d0cd7-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d0cd7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0cd7-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d0cd7-104">Product Name</span></span>|<span data-ttu-id="d0cd7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0cd7-105">SQL Server</span></span>|  
|<span data-ttu-id="d0cd7-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d0cd7-106">Event ID</span></span>|<span data-ttu-id="d0cd7-107">10502</span><span class="sxs-lookup"><span data-stu-id="d0cd7-107">10502</span></span>|  
|<span data-ttu-id="d0cd7-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d0cd7-108">Event Source</span></span>|<span data-ttu-id="d0cd7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d0cd7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d0cd7-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d0cd7-110">Component</span></span>|<span data-ttu-id="d0cd7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d0cd7-111">SQLEngine</span></span>|  
|<span data-ttu-id="d0cd7-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d0cd7-112">Symbolic Name</span></span>|<span data-ttu-id="d0cd7-113">PG_DUP_FOUND</span><span class="sxs-lookup"><span data-stu-id="d0cd7-113">PG_DUP_FOUND</span></span>|  
|<span data-ttu-id="d0cd7-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d0cd7-114">Message Text</span></span>|<span data-ttu-id="d0cd7-115">プラン ガイド '%.\*ls' を作成できません。@stmt と @module_or_batch または @plan_handle と @statement_start_offset で指定したステートメントがデータベース内の既存のプラン ガイド '%.\*ls' と一致しています。</span><span class="sxs-lookup"><span data-stu-id="d0cd7-115">Cannot create plan guide '%.\*ls' because the statement specified by @stmt and @module_or_batch, or by @plan_handle and @statement_start_offset, matches the existing plan guide '%.\*ls' in the database.</span></span> <span data-ttu-id="d0cd7-116">新しいプラン ガイドを作成する前に、既存のプラン ガイドを削除します。</span><span class="sxs-lookup"><span data-stu-id="d0cd7-116">Drop the existing plan guide before creating the new plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d0cd7-117">説明</span><span class="sxs-lookup"><span data-stu-id="d0cd7-117">Explanation</span></span>  
 <span data-ttu-id="d0cd7-118">指定したステートメントのプラン ガイドが存在します。</span><span class="sxs-lookup"><span data-stu-id="d0cd7-118">A plan guide exists for the specified statement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d0cd7-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d0cd7-119">User Action</span></span>  
 <span data-ttu-id="d0cd7-120">新しいプラン ガイドを作成する前に、既存のプラン ガイドを削除します。</span><span class="sxs-lookup"><span data-stu-id="d0cd7-120">Drop the existing plan guide before creating the new plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0cd7-121">参照</span><span class="sxs-lookup"><span data-stu-id="d0cd7-121">See Also</span></span>  
 <span data-ttu-id="d0cd7-122">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="d0cd7-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="d0cd7-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0cd7-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="d0cd7-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0cd7-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
