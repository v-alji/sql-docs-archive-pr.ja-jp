---
title: MSSQLSERVER_10534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 793bb0bf5048e30624d9566f65e7c6752bd14386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715381"
---
# <a name="mssqlserver_10534"></a><span data-ttu-id="2c6d6-102">MSSQLSERVER_10534</span><span class="sxs-lookup"><span data-stu-id="2c6d6-102">MSSQLSERVER_10534</span></span>
    
## <a name="details"></a><span data-ttu-id="2c6d6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="2c6d6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c6d6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2c6d6-104">Product Name</span></span>|<span data-ttu-id="2c6d6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2c6d6-105">SQL Server</span></span>|  
|<span data-ttu-id="2c6d6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2c6d6-106">Event ID</span></span>|<span data-ttu-id="2c6d6-107">10534</span><span class="sxs-lookup"><span data-stu-id="2c6d6-107">10534</span></span>|  
|<span data-ttu-id="2c6d6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2c6d6-108">Event Source</span></span>|<span data-ttu-id="2c6d6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2c6d6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2c6d6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2c6d6-110">Component</span></span>|<span data-ttu-id="2c6d6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2c6d6-111">SQLEngine</span></span>|  
|<span data-ttu-id="2c6d6-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="2c6d6-112">Symbolic Name</span></span>|<span data-ttu-id="2c6d6-113">PG_INVALID_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2c6d6-113">PG_INVALID_PARAMS</span></span>|  
|<span data-ttu-id="2c6d6-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2c6d6-114">Message Text</span></span>|<span data-ttu-id="2c6d6-115">プラン ガイド '%.\*ls' を作成できません。`@params` に指定した値が無効です。</span><span class="sxs-lookup"><span data-stu-id="2c6d6-115">Cannot create plan guide '%.\*ls' because the value specified for `@params` is invalid.</span></span> <span data-ttu-id="2c6d6-116">*parameter_name parameter_type* 形式の値を指定するか、NULL を指定してください。</span><span class="sxs-lookup"><span data-stu-id="2c6d6-116">Specify the value in the form *parameter_name parameter_type*, or specify NULL.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2c6d6-117">説明</span><span class="sxs-lookup"><span data-stu-id="2c6d6-117">Explanation</span></span>  
 <span data-ttu-id="2c6d6-118">`@params` に指定した値が無効です。</span><span class="sxs-lookup"><span data-stu-id="2c6d6-118">The value specified for `@params` is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2c6d6-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2c6d6-119">User Action</span></span>  
 <span data-ttu-id="2c6d6-120">*parameter_name parameter_type* 形式の値を指定するか、NULL を指定してください。</span><span class="sxs-lookup"><span data-stu-id="2c6d6-120">Specify the value in the form *parameter_name parameter_type*, or specify NULL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6d6-121">参照</span><span class="sxs-lookup"><span data-stu-id="2c6d6-121">See Also</span></span>  
 <span data-ttu-id="2c6d6-122">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="2c6d6-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="2c6d6-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2c6d6-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="2c6d6-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d6-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
