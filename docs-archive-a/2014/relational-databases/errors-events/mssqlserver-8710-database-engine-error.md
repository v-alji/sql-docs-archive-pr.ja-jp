---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 65fb6b3efb42c282347f560353a2b21edc337859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646170"
---
# <a name="mssqlserver_8710"></a><span data-ttu-id="a7079-102">MSSQLSERVER_8710</span><span class="sxs-lookup"><span data-stu-id="a7079-102">MSSQLSERVER_8710</span></span>
    
## <a name="details"></a><span data-ttu-id="a7079-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a7079-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7079-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a7079-104">Product Name</span></span>|<span data-ttu-id="a7079-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a7079-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a7079-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a7079-106">Event ID</span></span>|<span data-ttu-id="a7079-107">8710</span><span class="sxs-lookup"><span data-stu-id="a7079-107">8710</span></span>|  
|<span data-ttu-id="a7079-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a7079-108">Event Source</span></span>|<span data-ttu-id="a7079-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a7079-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a7079-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a7079-110">Component</span></span>|<span data-ttu-id="a7079-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a7079-111">SQLEngine</span></span>|  
|<span data-ttu-id="a7079-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a7079-112">Symbolic Name</span></span>|<span data-ttu-id="a7079-113">QUERY2_CUBE_ILLEGAL_AGG_FUNC</span><span class="sxs-lookup"><span data-stu-id="a7079-113">QUERY2_CUBE_ILLEGAL_AGG_FUNC</span></span>|  
|<span data-ttu-id="a7079-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a7079-114">Message Text</span></span>|<span data-ttu-id="a7079-115">CUBE、ROLLUP、または GROUPING SET クエリで使用される集計関数は、サブ集計をマージするものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7079-115">Aggregate functions that are used with CUBE, ROLLUP, or GROUPING SET queries must provide for the merging of subaggregates.</span></span> <span data-ttu-id="a7079-116">この問題を解決するには、集計関数を削除するか、UNION ALL を GROUP BY 句で使用するクエリを記述してください。</span><span class="sxs-lookup"><span data-stu-id="a7079-116">To fix this problem, remove the aggregate function or write the query using UNION ALL over GROUP BY clauses.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a7079-117">説明</span><span class="sxs-lookup"><span data-stu-id="a7079-117">Explanation</span></span>  
 <span data-ttu-id="a7079-118">サブ集計をマージできない集計関数が CUBE、ROLLUP、または GROUPING SET で使用されています。</span><span class="sxs-lookup"><span data-stu-id="a7079-118">An aggregate function has been used with CUBE, ROLLUP, or GROUPING SETS that does not provide a method for merging subaggregates.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a7079-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a7079-119">User Action</span></span>  
 <span data-ttu-id="a7079-120">この問題を解決するには、集計関数を削除するか、UNION ALL を GROUP BY 句で使用するクエリを記述してください。</span><span class="sxs-lookup"><span data-stu-id="a7079-120">To fix this problem, remove the aggregate function or write the query using UNION ALL over GROUP BY clauses.</span></span>  
  
  
