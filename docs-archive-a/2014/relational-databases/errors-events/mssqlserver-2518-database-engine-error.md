---
title: MSSQLSERVER_2518 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5f5517458c1014d7830c4813b95e1120bef452e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634545"
---
# <a name="mssqlserver_2518"></a><span data-ttu-id="53d4d-102">MSSQLSERVER_2518</span><span class="sxs-lookup"><span data-stu-id="53d4d-102">MSSQLSERVER_2518</span></span>
    
## <a name="details"></a><span data-ttu-id="53d4d-103">詳細</span><span class="sxs-lookup"><span data-stu-id="53d4d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53d4d-104">製品名</span><span class="sxs-lookup"><span data-stu-id="53d4d-104">Product Name</span></span>|<span data-ttu-id="53d4d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="53d4d-105">SQL Server</span></span>|  
|<span data-ttu-id="53d4d-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="53d4d-106">Event ID</span></span>|<span data-ttu-id="53d4d-107">2518</span><span class="sxs-lookup"><span data-stu-id="53d4d-107">2518</span></span>|  
|<span data-ttu-id="53d4d-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="53d4d-108">Event Source</span></span>|<span data-ttu-id="53d4d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="53d4d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="53d4d-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="53d4d-110">Component</span></span>|<span data-ttu-id="53d4d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="53d4d-111">SQLEngine</span></span>|  
|<span data-ttu-id="53d4d-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="53d4d-112">Symbolic Name</span></span>|<span data-ttu-id="53d4d-113">DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED</span><span class="sxs-lookup"><span data-stu-id="53d4d-113">DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED</span></span>|  
|<span data-ttu-id="53d4d-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="53d4d-114">Message Text</span></span>|<span data-ttu-id="53d4d-115">オブジェクト ID O_ID (オブジェクト "O_NAME"):共通言語ランタイム (CLR) が無効になっているので、このオブジェクトでは計算列とユーザー定義型を確認できません。</span><span class="sxs-lookup"><span data-stu-id="53d4d-115">Object ID O_ID (object "O_NAME"): Computed columns and user-defined types cannot be checked for this object because the common language runtime (CLR) is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="53d4d-116">説明</span><span class="sxs-lookup"><span data-stu-id="53d4d-116">Explanation</span></span>  
 <span data-ttu-id="53d4d-117">この情報メッセージは、クエリ プロセッサが、計算列と共通言語ランタイム (CLR) のユーザー定義型を評価するための内部オブジェクトを DBCC に提供できなかったことを示しています。</span><span class="sxs-lookup"><span data-stu-id="53d4d-117">This informational message indicates that the query processor could not provide DBCC with an internal object to allow for computed columns and common language runtime (CLR) user-defined types to be evaluated.</span></span> <span data-ttu-id="53d4d-118">この問題は、いずれかの列に CLR が関係しているにもかかわらず、CLR が有効化されていないために発生しました。</span><span class="sxs-lookup"><span data-stu-id="53d4d-118">This problem occurred because one of the columns involved the CLR, but the CLR is not enabled.</span></span> <span data-ttu-id="53d4d-119">内部オブジェクトはすべての列に及んでいます。</span><span class="sxs-lookup"><span data-stu-id="53d4d-119">The internal object covers all columns.</span></span> <span data-ttu-id="53d4d-120">このため、1 つの列を評価できないと、内部オブジェクトの作成ができなくなります。</span><span class="sxs-lookup"><span data-stu-id="53d4d-120">Therefore, the inability to evaluate a single column prevents creating the internal object.</span></span> <span data-ttu-id="53d4d-121">つまり、計算列の正当性チェックが行われなかったり、DBCC でインデックスとベース テーブルの整合性をチェックする際に計算列が使用されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="53d4d-121">This means that computed columns will not be checked for correctness or be used when DBCC checks the consistency between indexes and base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="53d4d-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="53d4d-122">User Action</span></span>  
 <span data-ttu-id="53d4d-123">CLR を有効にして、DBCC ステートメントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="53d4d-123">Enable CLR and rerun the DBCC statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d4d-124">参照</span><span class="sxs-lookup"><span data-stu-id="53d4d-124">See Also</span></span>  
 [<span data-ttu-id="53d4d-125">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="53d4d-125">Enabling CLR Integration</span></span>](../clr-integration/clr-integration-enabling.md)  
  
  
