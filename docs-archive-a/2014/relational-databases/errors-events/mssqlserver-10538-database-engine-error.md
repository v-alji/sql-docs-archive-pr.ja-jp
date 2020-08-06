---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: edc6abf192a3341f9b84c99e99071343cc882c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715369"
---
# <a name="mssqlserver_10538"></a><span data-ttu-id="f5d14-102">MSSQLSERVER_10538</span><span class="sxs-lookup"><span data-stu-id="f5d14-102">MSSQLSERVER_10538</span></span>
    
## <a name="details"></a><span data-ttu-id="f5d14-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f5d14-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5d14-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f5d14-104">Product Name</span></span>|<span data-ttu-id="f5d14-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f5d14-105">SQL Server</span></span>|  
|<span data-ttu-id="f5d14-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f5d14-106">Event ID</span></span>|<span data-ttu-id="f5d14-107">10538</span><span class="sxs-lookup"><span data-stu-id="f5d14-107">10538</span></span>|  
|<span data-ttu-id="f5d14-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f5d14-108">Event Source</span></span>|<span data-ttu-id="f5d14-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f5d14-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f5d14-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f5d14-110">Component</span></span>|<span data-ttu-id="f5d14-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f5d14-111">SQLEngine</span></span>|  
|<span data-ttu-id="f5d14-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f5d14-112">Symbolic Name</span></span>|<span data-ttu-id="f5d14-113">PG_INVALID_PLANGUIDE_HANDLE</span><span class="sxs-lookup"><span data-stu-id="f5d14-113">PG_INVALID_PLANGUIDE_HANDLE</span></span>|  
|<span data-ttu-id="f5d14-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f5d14-114">Message Text</span></span>|<span data-ttu-id="f5d14-115">指定したプラン ガイドの ID が NULL または無効であるか、またはプラン ガイドが参照しているオブジェクトに対する権限がないため、プラン ガイドを見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="f5d14-115">Cannot find the plan guide either because the specified plan guide ID is NULL or invalid, or you do not have permission on the object referenced by the plan guide.</span></span> <span data-ttu-id="f5d14-116">プラン ガイドの ID が有効であること、現在のセッションが適切なデータベース コンテキストに設定されていること、およびプラン ガイドが参照しているオブジェクトに対する ALTER DATABASE 権限または ALTER 権限のいずれかがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f5d14-116">Verify that the plan guide ID is valid, the current session is set to the correct database context, and you have either ALTER DATABASE permission or ALTER permission on the object referenced by the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f5d14-117">説明</span><span class="sxs-lookup"><span data-stu-id="f5d14-117">Explanation</span></span>  
 <span data-ttu-id="f5d14-118">指定したプラン ガイドの ID が NULL または無効であるか、またはプラン ガイドが参照しているオブジェクトに対する権限がありません。</span><span class="sxs-lookup"><span data-stu-id="f5d14-118">The ID of the specified plan guide is NULL or invalid, or you do not have permission on the object referenced by the plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f5d14-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f5d14-119">User Action</span></span>  
 <span data-ttu-id="f5d14-120">プラン ガイドの ID が有効であること、現在のセッションが適切なデータベース コンテキストに設定されていること、およびプラン ガイドが参照しているオブジェクトに対する ALTER DATABASE 権限または ALTER 権限があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f5d14-120">Verify that the plan guide ID is valid, the current session is set to the correct database context, and you have ALTER DATABASE permission or ALTER permission on the object referenced by the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d14-121">参照</span><span class="sxs-lookup"><span data-stu-id="f5d14-121">See Also</span></span>  
 <span data-ttu-id="f5d14-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5d14-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="f5d14-123">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="f5d14-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="f5d14-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5d14-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
