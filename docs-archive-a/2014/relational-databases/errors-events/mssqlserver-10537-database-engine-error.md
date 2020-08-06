---
title: MSSQLSERVER_10537 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b1baccad5236bd8c1a71024b7dd542cc9d11cbd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718230"
---
# <a name="mssqlserver_10537"></a><span data-ttu-id="8479f-102">MSSQLSERVER_10537</span><span class="sxs-lookup"><span data-stu-id="8479f-102">MSSQLSERVER_10537</span></span>
    
## <a name="details"></a><span data-ttu-id="8479f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8479f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8479f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8479f-104">Product Name</span></span>|<span data-ttu-id="8479f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8479f-105">SQL Server</span></span>|  
|<span data-ttu-id="8479f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8479f-106">Event ID</span></span>|<span data-ttu-id="8479f-107">10537</span><span class="sxs-lookup"><span data-stu-id="8479f-107">10537</span></span>|  
|<span data-ttu-id="8479f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8479f-108">Event Source</span></span>|<span data-ttu-id="8479f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8479f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8479f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8479f-110">Component</span></span>|<span data-ttu-id="8479f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8479f-111">SQLEngine</span></span>|  
|<span data-ttu-id="8479f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8479f-112">Symbolic Name</span></span>|<span data-ttu-id="8479f-113">PG_DUP_ENABLED</span><span class="sxs-lookup"><span data-stu-id="8479f-113">PG_DUP_ENABLED</span></span>|  
|<span data-ttu-id="8479f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8479f-114">Message Text</span></span>|<span data-ttu-id="8479f-115">プラン ガイド '%.\*ls' を作成できません。有効なプラン ガイド '%.\*ls' に、ステートメントと同じスコープと開始オフセット値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8479f-115">Cannot enable plan guide '%.\*ls' because the enabled plan guide '%.\*ls' contains the same scope and starting offset value as the statement.</span></span> <span data-ttu-id="8479f-116">指定したプラン ガイドを有効にする前に、既存のプラン ガイドを無効にします。</span><span class="sxs-lookup"><span data-stu-id="8479f-116">Disable the existing plan guide before enabling the specified plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8479f-117">説明</span><span class="sxs-lookup"><span data-stu-id="8479f-117">Explanation</span></span>  
 <span data-ttu-id="8479f-118">既存のプラン ガイドに、指定したプラン ガイドのステートメントと同じスコープと開始オフセット値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8479f-118">An existing plan guide contains the same scope and starting offset value as the statement in the specified plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8479f-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8479f-119">User Action</span></span>  
 <span data-ttu-id="8479f-120">指定したプラン ガイドを有効にする前に、既存のプラン ガイドを無効にします。</span><span class="sxs-lookup"><span data-stu-id="8479f-120">Disable the existing plan guide before enabling the specified plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8479f-121">参照</span><span class="sxs-lookup"><span data-stu-id="8479f-121">See Also</span></span>  
 <span data-ttu-id="8479f-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8479f-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="8479f-123">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="8479f-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="8479f-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8479f-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
