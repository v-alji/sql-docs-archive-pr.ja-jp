---
title: MSSQLSERVER_10507 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a80e48948c03b370c07742fabbb3cf8eb3e74315
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738449"
---
# <a name="mssqlserver_10507"></a><span data-ttu-id="867b4-102">MSSQLSERVER_10507</span><span class="sxs-lookup"><span data-stu-id="867b4-102">MSSQLSERVER_10507</span></span>
    
## <a name="details"></a><span data-ttu-id="867b4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="867b4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="867b4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="867b4-104">Product Name</span></span>|<span data-ttu-id="867b4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="867b4-105">SQL Server</span></span>|  
|<span data-ttu-id="867b4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="867b4-106">Event ID</span></span>|<span data-ttu-id="867b4-107">10507</span><span class="sxs-lookup"><span data-stu-id="867b4-107">10507</span></span>|  
|<span data-ttu-id="867b4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="867b4-108">Event Source</span></span>|<span data-ttu-id="867b4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="867b4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="867b4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="867b4-110">Component</span></span>|<span data-ttu-id="867b4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="867b4-111">SQLEngine</span></span>|  
|<span data-ttu-id="867b4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="867b4-112">Symbolic Name</span></span>|<span data-ttu-id="867b4-113">PG_STMT_DOES_NOT_MATCH</span><span class="sxs-lookup"><span data-stu-id="867b4-113">PG_STMT_DOES_NOT_MATCH</span></span>|  
|<span data-ttu-id="867b4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="867b4-114">Message Text</span></span>|<span data-ttu-id="867b4-115">プラン ガイド '%.\*ls' を作成できません。`@stmt` と `@module_or_batch` または `@plan_handle` と `@statement_start_offset` で指定したステートメントが、指定したモジュールまたはバッチのステートメントと一致しません。</span><span class="sxs-lookup"><span data-stu-id="867b4-115">Cannot create plan guide '%.\*ls' because the statement specified by `@stmt` and `@module_or_batch`, or by `@plan_handle` and `@statement_start_offset`, does not match any statement in the specified module or batch.</span></span> <span data-ttu-id="867b4-116">モジュールまたはバッチのステートメントと一致するように値を変更してください。</span><span class="sxs-lookup"><span data-stu-id="867b4-116">Modify the values to match a statement in the module or batch.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="867b4-117">説明</span><span class="sxs-lookup"><span data-stu-id="867b4-117">Explanation</span></span>  
 <span data-ttu-id="867b4-118">指定したモジュールまたはバッチのステートメントが、指定したステートメントまたはステートメントのオフセット値と一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="867b4-118">A statement in the specified module or batch could not be matched to the specified statement or statement offset value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="867b4-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="867b4-119">User Action</span></span>  
 <span data-ttu-id="867b4-120">モジュールまたはバッチのステートメントと一致するように指定のパラメーター値を変更します。</span><span class="sxs-lookup"><span data-stu-id="867b4-120">Modify the specified parameter values to match a statement in the module or batch.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="867b4-121">参照</span><span class="sxs-lookup"><span data-stu-id="867b4-121">See Also</span></span>  
 <span data-ttu-id="867b4-122">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="867b4-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="867b4-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="867b4-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="867b4-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="867b4-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
