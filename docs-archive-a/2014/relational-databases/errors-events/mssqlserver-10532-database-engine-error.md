---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26ab34c319eff62737eae337828247fdfd7e901b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740009"
---
# <a name="mssqlserver_10532"></a><span data-ttu-id="c4a57-102">MSSQLSERVER_10532</span><span class="sxs-lookup"><span data-stu-id="c4a57-102">MSSQLSERVER_10532</span></span>
    
## <a name="details"></a><span data-ttu-id="c4a57-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c4a57-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4a57-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c4a57-104">Product Name</span></span>|<span data-ttu-id="c4a57-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c4a57-105">SQL Server</span></span>|  
|<span data-ttu-id="c4a57-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c4a57-106">Event ID</span></span>|<span data-ttu-id="c4a57-107">10532</span><span class="sxs-lookup"><span data-stu-id="c4a57-107">10532</span></span>|  
|<span data-ttu-id="c4a57-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c4a57-108">Event Source</span></span>|<span data-ttu-id="c4a57-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c4a57-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c4a57-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c4a57-110">Component</span></span>|<span data-ttu-id="c4a57-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c4a57-111">SQLEngine</span></span>|  
|<span data-ttu-id="c4a57-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c4a57-112">Symbolic Name</span></span>|<span data-ttu-id="c4a57-113">PG_NO_ELIGIBLE_STMT</span><span class="sxs-lookup"><span data-stu-id="c4a57-113">PG_NO_ELIGIBLE_STMT</span></span>|  
|<span data-ttu-id="c4a57-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c4a57-114">Message Text</span></span>|<span data-ttu-id="c4a57-115">プラン ガイド '%.\*ls' を作成できません。`@plan_handle` で指定されたバッチまたはモジュールに、プラン ガイドに適したステートメントが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="c4a57-115">Cannot create plan guide '%.\*ls' because the batch or module specified by `@plan_handle` does not contain a statement that is eligible for a plan guide.</span></span> <span data-ttu-id="c4a57-116">`@plan_handle` に別の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-116">Specify a different value for `@plan_handle`.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c4a57-117">説明</span><span class="sxs-lookup"><span data-stu-id="c4a57-117">Explanation</span></span>  
 <span data-ttu-id="c4a57-118">`@plan_handle` で指定されたバッチまたはモジュールに、プラン ガイドに適したステートメントが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="c4a57-118">The batch or module specified by `@plan_handle` does not contain a statement that is eligible for a plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c4a57-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c4a57-119">User Action</span></span>  
 <span data-ttu-id="c4a57-120">`@plan_handle` に別の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-120">Specify a different value for `@plan_handle`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a57-121">参照</span><span class="sxs-lookup"><span data-stu-id="c4a57-121">See Also</span></span>  
 <span data-ttu-id="c4a57-122">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="c4a57-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="c4a57-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4a57-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="c4a57-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c4a57-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
