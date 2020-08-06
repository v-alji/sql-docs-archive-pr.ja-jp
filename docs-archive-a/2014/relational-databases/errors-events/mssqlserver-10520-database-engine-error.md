---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b8bdf080703fa6bd02fc34b8c31f59407814b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715390"
---
# <a name="mssqlserver_10520"></a><span data-ttu-id="a54e1-102">MSSQLSERVER_10520</span><span class="sxs-lookup"><span data-stu-id="a54e1-102">MSSQLSERVER_10520</span></span>
    
## <a name="details"></a><span data-ttu-id="a54e1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a54e1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a54e1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a54e1-104">Product Name</span></span>|<span data-ttu-id="a54e1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a54e1-105">SQL Server</span></span>|  
|<span data-ttu-id="a54e1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a54e1-106">Event ID</span></span>|<span data-ttu-id="a54e1-107">10520</span><span class="sxs-lookup"><span data-stu-id="a54e1-107">10520</span></span>|  
|<span data-ttu-id="a54e1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a54e1-108">Event Source</span></span>|<span data-ttu-id="a54e1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a54e1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a54e1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a54e1-110">Component</span></span>|<span data-ttu-id="a54e1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a54e1-111">SQLEngine</span></span>|  
|<span data-ttu-id="a54e1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a54e1-112">Symbolic Name</span></span>|<span data-ttu-id="a54e1-113">PG_PARAM_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="a54e1-113">PG_PARAM_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="a54e1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a54e1-114">Message Text</span></span>|<span data-ttu-id="a54e1-115">プラン ガイド '%.\*ls' を作成できません。'%ls' として指定した @type のパラメーター '%ls' に NULL 以外の値を指定しています。</span><span class="sxs-lookup"><span data-stu-id="a54e1-115">Cannot create plan guide '%.\*ls' because @type was specified as '%ls' and a non-NULL value is specified for the parameter '%ls'.</span></span> <span data-ttu-id="a54e1-116">この型のパラメーターには、NULL 値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a54e1-116">This type requires a NULL value for the parameter.</span></span> <span data-ttu-id="a54e1-117">パラメーターに NULL を指定するか、パラメーターに NULL 以外の値を指定可能な型に変更します。</span><span class="sxs-lookup"><span data-stu-id="a54e1-117">Specify NULL for the parameter, or change the type to one that allows a non-NULL value for the parameter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a54e1-118">説明</span><span class="sxs-lookup"><span data-stu-id="a54e1-118">Explanation</span></span>  
 <span data-ttu-id="a54e1-119">@type で指定した型のパラメーターには、NULL 値を指定する必要がありますが、NULL 以外の値を指定しました。</span><span class="sxs-lookup"><span data-stu-id="a54e1-119">The type specified in @type requires a NULL value for the specified parameter, however a non-NULL value was supplied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a54e1-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a54e1-120">User Action</span></span>  
 <span data-ttu-id="a54e1-121">パラメーターに NULL を指定するか、パラメーターに NULL 以外の値を指定可能な型に変更します。</span><span class="sxs-lookup"><span data-stu-id="a54e1-121">Specify NULL for the parameter, or change the type to one that allows a non-NULL value for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a54e1-122">参照</span><span class="sxs-lookup"><span data-stu-id="a54e1-122">See Also</span></span>  
 <span data-ttu-id="a54e1-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a54e1-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="a54e1-124">プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="a54e1-124">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
