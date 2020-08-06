---
title: MSSQLSERVER_8712 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9285d4846cac5af2dd6e87ab55d5fd0610586d07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646166"
---
# <a name="mssqlserver_8712"></a><span data-ttu-id="7413a-102">MSSQLSERVER_8712</span><span class="sxs-lookup"><span data-stu-id="7413a-102">MSSQLSERVER_8712</span></span>
    
## <a name="details"></a><span data-ttu-id="7413a-103">詳細</span><span class="sxs-lookup"><span data-stu-id="7413a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7413a-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7413a-104">Product Name</span></span>|<span data-ttu-id="7413a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7413a-105">SQL Server</span></span>|  
|<span data-ttu-id="7413a-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7413a-106">Event ID</span></span>|<span data-ttu-id="7413a-107">8712</span><span class="sxs-lookup"><span data-stu-id="7413a-107">8712</span></span>|  
|<span data-ttu-id="7413a-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7413a-108">Event Source</span></span>|<span data-ttu-id="7413a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7413a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7413a-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7413a-110">Component</span></span>|<span data-ttu-id="7413a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7413a-111">SQLEngine</span></span>|  
|<span data-ttu-id="7413a-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="7413a-112">Symbolic Name</span></span>|<span data-ttu-id="7413a-113">USEPLAN_ERR_NO_INDEX</span><span class="sxs-lookup"><span data-stu-id="7413a-113">USEPLAN_ERR_NO_INDEX</span></span>|  
|<span data-ttu-id="7413a-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7413a-114">Message Text</span></span>|<span data-ttu-id="7413a-115">USE PLAN ヒントで指定したインデックス '%.\*ls' が存在しません。</span><span class="sxs-lookup"><span data-stu-id="7413a-115">Index '%.\*ls', specified in the USE PLAN hint, does not exist.</span></span> <span data-ttu-id="7413a-116">既存のインデックスを指定するか、指定した名前を持つインデックスを作成してください。</span><span class="sxs-lookup"><span data-stu-id="7413a-116">Specify an existing index, or create an index with the specified name.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7413a-117">説明</span><span class="sxs-lookup"><span data-stu-id="7413a-117">Explanation</span></span>  
 <span data-ttu-id="7413a-118">USE PLAN ヒントで指定したインデックスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="7413a-118">An index that is specified in the USE PLAN hint does not exist.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7413a-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7413a-119">User Action</span></span>  
 <span data-ttu-id="7413a-120">USE PLAN ヒントで指定したすべてのインデックスが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="7413a-120">Ensure all indexes that are specified in the USE PLAN hint exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7413a-121">参照</span><span class="sxs-lookup"><span data-stu-id="7413a-121">See Also</span></span>  
 <span data-ttu-id="7413a-122">[クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="7413a-122">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="7413a-123">プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="7413a-123">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
