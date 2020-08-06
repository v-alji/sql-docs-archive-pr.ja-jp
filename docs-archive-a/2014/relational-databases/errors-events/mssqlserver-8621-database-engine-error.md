---
title: MSSQLSERVER_8621 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48c36cf936475e3deea37a172c7dc59f88d0a31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642820"
---
# <a name="mssqlserver_8621"></a><span data-ttu-id="3fd5b-102">MSSQLSERVER_8621</span><span class="sxs-lookup"><span data-stu-id="3fd5b-102">MSSQLSERVER_8621</span></span>
    
## <a name="details"></a><span data-ttu-id="3fd5b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="3fd5b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3fd5b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="3fd5b-104">Product Name</span></span>|<span data-ttu-id="3fd5b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3fd5b-105">SQL Server</span></span>|  
|<span data-ttu-id="3fd5b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3fd5b-106">Event ID</span></span>|<span data-ttu-id="3fd5b-107">8621</span><span class="sxs-lookup"><span data-stu-id="3fd5b-107">8621</span></span>|  
|<span data-ttu-id="3fd5b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="3fd5b-108">Event Source</span></span>|<span data-ttu-id="3fd5b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3fd5b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3fd5b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3fd5b-110">Component</span></span>|<span data-ttu-id="3fd5b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3fd5b-111">SQLEngine</span></span>|  
|<span data-ttu-id="3fd5b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="3fd5b-112">Symbolic Name</span></span>|<span data-ttu-id="3fd5b-113">OPTIMIZER_STACK_OVERFLOW_ERR</span><span class="sxs-lookup"><span data-stu-id="3fd5b-113">OPTIMIZER_STACK_OVERFLOW_ERR</span></span>|  
|<span data-ttu-id="3fd5b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="3fd5b-114">Message Text</span></span>|<span data-ttu-id="3fd5b-115">クエリ プロセッサはクエリ最適化実行中にスタック領域不足になりました。</span><span class="sxs-lookup"><span data-stu-id="3fd5b-115">The query processor ran out of stack space during query optimization.</span></span> <span data-ttu-id="3fd5b-116">クエリを簡単にしてください。</span><span class="sxs-lookup"><span data-stu-id="3fd5b-116">Please simplify the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3fd5b-117">説明</span><span class="sxs-lookup"><span data-stu-id="3fd5b-117">Explanation</span></span>  
 <span data-ttu-id="3fd5b-118">このエラーの原因として最も多いのは、クエリのサイズが大きくなったことです。</span><span class="sxs-lookup"><span data-stu-id="3fd5b-118">The size of the expanded query is the most likely cause of the error.</span></span> <span data-ttu-id="3fd5b-119">大きくなったクエリでは、各ビューの定義、計算列、[!INCLUDE[tsql](../../includes/tsql-md.md)] 関数、参照している共通テーブル式や、セカンダリ インデックス、ビュー、およびトリガーの更新などの連鎖動作が、元のクエリに置き換わっています。</span><span class="sxs-lookup"><span data-stu-id="3fd5b-119">The expanded query substitutes into the original query the definitions of each of the views, computed columns, [!INCLUDE[tsql](../../includes/tsql-md.md)] functions, and common table expressions it references, as well as cascading actions like updating secondary indexes, views, and triggers.</span></span>  
  
 <span data-ttu-id="3fd5b-120">ビュー定義で参照しているテーブルの数や、非常に大きなスカラー式など、特定の項目によりクエリのサイズが大きくなっていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="3fd5b-120">Most likely the query is large in some dimension; for example, the number of tables referenced by view definitions, or a very large scalar expression.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3fd5b-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="3fd5b-121">User Action</span></span>  
 <span data-ttu-id="3fd5b-122">最も大きい項目に関してクエリを複数に分割することにより、クエリを単純化します。</span><span class="sxs-lookup"><span data-stu-id="3fd5b-122">Simplify the query by breaking the query into multiple queries along the largest dimension.</span></span> <span data-ttu-id="3fd5b-123">まず不要なクエリ要素を削除し、次に一時テーブルを追加して、クエリを 2 つに分割します。</span><span class="sxs-lookup"><span data-stu-id="3fd5b-123">First remove any query elements that are not really necessary, then try adding a temp table and splitting the query in two.</span></span>  <span data-ttu-id="3fd5b-124">クエリの一部をサブクエリまたは関数や共通テーブルに移動するだけでは、十分ではありません。これらは [!INCLUDE[tsql](../../includes/tsql-md.md)] コンパイラを実行すると結合されるからです。</span><span class="sxs-lookup"><span data-stu-id="3fd5b-124">Merely moving a part of the query to a subquery, function, or common table expression is insufficient because they get recombined by the [!INCLUDE[tsql](../../includes/tsql-md.md)] compiler.</span></span>  
  
  
