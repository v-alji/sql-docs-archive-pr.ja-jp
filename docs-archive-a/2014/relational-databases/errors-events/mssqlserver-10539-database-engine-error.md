---
title: MSSQLSERVER_10539 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd1f190b8f5d3ab9755409bdd034fa374ea5314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715362"
---
# <a name="mssqlserver_10539"></a><span data-ttu-id="4da76-102">MSSQLSERVER_10539</span><span class="sxs-lookup"><span data-stu-id="4da76-102">MSSQLSERVER_10539</span></span>
    
## <a name="details"></a><span data-ttu-id="4da76-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4da76-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4da76-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4da76-104">Product Name</span></span>|<span data-ttu-id="4da76-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4da76-105">SQL Server</span></span>|  
|<span data-ttu-id="4da76-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4da76-106">Event ID</span></span>|<span data-ttu-id="4da76-107">10539</span><span class="sxs-lookup"><span data-stu-id="4da76-107">10539</span></span>|  
|<span data-ttu-id="4da76-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4da76-108">Event Source</span></span>|<span data-ttu-id="4da76-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4da76-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4da76-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4da76-110">Component</span></span>|<span data-ttu-id="4da76-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4da76-111">SQLEngine</span></span>|  
|<span data-ttu-id="4da76-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4da76-112">Symbolic Name</span></span>|<span data-ttu-id="4da76-113">PG_NO_PLAN_FOR_STMT</span><span class="sxs-lookup"><span data-stu-id="4da76-113">PG_NO_PLAN_FOR_STMT</span></span>|  
|<span data-ttu-id="4da76-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4da76-114">Message Text</span></span>|<span data-ttu-id="4da76-115">プラン ガイド '%.\*ls' をキャッシュから作成できません。開始オフセット %d のステートメントのクエリ プランを使用できません。</span><span class="sxs-lookup"><span data-stu-id="4da76-115">Cannot create plan guide '%.\*ls' from cache because a query plan is not available for the statement with start offset %d.</span></span> <span data-ttu-id="4da76-116">この問題は、存在しないデータベース オブジェクトにステートメントが依存している場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="4da76-116">This problem can occur if the statement depends on database objects that have not yet been created.</span></span> <span data-ttu-id="4da76-117">必要なデータベース オブジェクトがすべて存在することを確認し、プラン ガイドを作成する前にステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4da76-117">Make sure that all necessary database objects exist, and execute the statement before creating the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4da76-118">説明</span><span class="sxs-lookup"><span data-stu-id="4da76-118">Explanation</span></span>  
 <span data-ttu-id="4da76-119">指定した開始オフセットを持つステートメントのクエリ プランがプラン キャッシュ内にありません。</span><span class="sxs-lookup"><span data-stu-id="4da76-119">A query plan is not available in the plan cache for the statement with the specified starting offset.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4da76-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4da76-120">User Action</span></span>  
 <span data-ttu-id="4da76-121">必要なデータベース オブジェクトがすべて存在することを確認し、プラン ガイドを作成する前にステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4da76-121">Make sure that all necessary database objects exist, and execute the statement before creating the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da76-122">参照</span><span class="sxs-lookup"><span data-stu-id="4da76-122">See Also</span></span>  
 [<span data-ttu-id="4da76-123">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4da76-123">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
