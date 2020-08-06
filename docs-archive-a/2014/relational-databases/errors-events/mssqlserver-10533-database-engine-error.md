---
title: MSSQLSERVER_10533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccef25bc8f594cb6ea0b60aefab838ef27cda6f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641020"
---
# <a name="mssqlserver_10533"></a><span data-ttu-id="416ea-102">MSSQLSERVER_10533</span><span class="sxs-lookup"><span data-stu-id="416ea-102">MSSQLSERVER_10533</span></span>
    
## <a name="details"></a><span data-ttu-id="416ea-103">詳細</span><span class="sxs-lookup"><span data-stu-id="416ea-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="416ea-104">製品名</span><span class="sxs-lookup"><span data-stu-id="416ea-104">Product Name</span></span>|<span data-ttu-id="416ea-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="416ea-105">SQL Server</span></span>|  
|<span data-ttu-id="416ea-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="416ea-106">Event ID</span></span>|<span data-ttu-id="416ea-107">10533</span><span class="sxs-lookup"><span data-stu-id="416ea-107">10533</span></span>|  
|<span data-ttu-id="416ea-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="416ea-108">Event Source</span></span>|<span data-ttu-id="416ea-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="416ea-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="416ea-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="416ea-110">Component</span></span>|<span data-ttu-id="416ea-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="416ea-111">SQLEngine</span></span>|  
|<span data-ttu-id="416ea-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="416ea-112">Symbolic Name</span></span>|<span data-ttu-id="416ea-113">PG_NAME_TOO_BIG</span><span class="sxs-lookup"><span data-stu-id="416ea-113">PG_NAME_TOO_BIG</span></span>|  
|<span data-ttu-id="416ea-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="416ea-114">Message Text</span></span>|<span data-ttu-id="416ea-115">プラン ガイド '%.\*ls' を作成できません。プラン ガイドの名前が最大長である 124 文字を超えています。</span><span class="sxs-lookup"><span data-stu-id="416ea-115">Cannot create plan guide '%.\*ls' because the plan guide name exceeds 124 characters, the maximum number allowed.</span></span> <span data-ttu-id="416ea-116">124 文字以下の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="416ea-116">Specify a name that contains fewer than 125 characters.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="416ea-117">説明</span><span class="sxs-lookup"><span data-stu-id="416ea-117">Explanation</span></span>  
 <span data-ttu-id="416ea-118">プラン ガイドの名前が最大長である 124 文字を超えています。</span><span class="sxs-lookup"><span data-stu-id="416ea-118">The plan guide name exceeds 124 characters, the maximum number allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="416ea-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="416ea-119">User Action</span></span>  
 <span data-ttu-id="416ea-120">124 文字以下の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="416ea-120">Specify a name that contains fewer than 125 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="416ea-121">参照</span><span class="sxs-lookup"><span data-stu-id="416ea-121">See Also</span></span>  
 <span data-ttu-id="416ea-122">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="416ea-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="416ea-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="416ea-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="416ea-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="416ea-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
