---
title: MSSQLSERVER_10521 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c034bd13e212b9b39bfd348353d59e23fc748079
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715386"
---
# <a name="mssqlserver_10521"></a><span data-ttu-id="afd19-102">MSSQLSERVER_10521</span><span class="sxs-lookup"><span data-stu-id="afd19-102">MSSQLSERVER_10521</span></span>
    
## <a name="details"></a><span data-ttu-id="afd19-103">詳細</span><span class="sxs-lookup"><span data-stu-id="afd19-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="afd19-104">製品名</span><span class="sxs-lookup"><span data-stu-id="afd19-104">Product Name</span></span>|<span data-ttu-id="afd19-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="afd19-105">SQL Server</span></span>|  
|<span data-ttu-id="afd19-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="afd19-106">Event ID</span></span>|<span data-ttu-id="afd19-107">10521</span><span class="sxs-lookup"><span data-stu-id="afd19-107">10521</span></span>|  
|<span data-ttu-id="afd19-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="afd19-108">Event Source</span></span>|<span data-ttu-id="afd19-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="afd19-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="afd19-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="afd19-110">Component</span></span>|<span data-ttu-id="afd19-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="afd19-111">SQLEngine</span></span>|  
|<span data-ttu-id="afd19-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="afd19-112">Symbolic Name</span></span>|<span data-ttu-id="afd19-113">PG_PARAM_NEEDED</span><span class="sxs-lookup"><span data-stu-id="afd19-113">PG_PARAM_NEEDED</span></span>|  
|<span data-ttu-id="afd19-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="afd19-114">Message Text</span></span>|<span data-ttu-id="afd19-115">プラン ガイド '%.\*ls' を作成できません。'%ls' として指定した `@type` のパラメーターが NULL です。</span><span class="sxs-lookup"><span data-stu-id="afd19-115">Cannot create plan guide '%.\*ls' because `@type` was specified as '%ls' and the parameter '%ls' is NULL.</span></span> <span data-ttu-id="afd19-116">この型のパラメーターには、NULL 以外の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afd19-116">This type requires a non-NULL value for the parameter.</span></span> <span data-ttu-id="afd19-117">NULL 以外の値をパラメーターに指定するか、パラメーターに NULL 値を指定可能な型に変更します。</span><span class="sxs-lookup"><span data-stu-id="afd19-117">Specify a non-NULL value for the parameter, or change the type to one that allows a NULL value for the parameter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="afd19-118">説明</span><span class="sxs-lookup"><span data-stu-id="afd19-118">Explanation</span></span>  
 <span data-ttu-id="afd19-119">`@type` で指定した型のパラメーターには、NULL 以外の値を指定する必要がありますが、NULL 値を指定しました。</span><span class="sxs-lookup"><span data-stu-id="afd19-119">The type specified in `@type` requires a non-NULL value for the specified parameter; however a NULL value was supplied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="afd19-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="afd19-120">User Action</span></span>  
 <span data-ttu-id="afd19-121">NULL 以外の値をパラメーターに指定するか、パラメーターに NULL 値を指定可能な型に変更します。</span><span class="sxs-lookup"><span data-stu-id="afd19-121">Specify a non-NULL value for the parameter, or change the type to one that allows a NULL value for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd19-122">参照</span><span class="sxs-lookup"><span data-stu-id="afd19-122">See Also</span></span>  
 <span data-ttu-id="afd19-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="afd19-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="afd19-124">[プランガイド](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="afd19-124">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="afd19-125">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="afd19-125">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
