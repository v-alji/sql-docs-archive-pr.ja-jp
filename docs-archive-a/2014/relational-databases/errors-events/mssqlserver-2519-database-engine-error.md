---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8577b07586553f4b03714cd31451ac755faf824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631987"
---
# <a name="mssqlserver_2519"></a><span data-ttu-id="39071-102">MSSQLSERVER_2519</span><span class="sxs-lookup"><span data-stu-id="39071-102">MSSQLSERVER_2519</span></span>
    
## <a name="details"></a><span data-ttu-id="39071-103">詳細</span><span class="sxs-lookup"><span data-stu-id="39071-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="39071-104">製品名</span><span class="sxs-lookup"><span data-stu-id="39071-104">Product Name</span></span>|<span data-ttu-id="39071-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="39071-105">SQL Server</span></span>|  
|<span data-ttu-id="39071-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="39071-106">Event ID</span></span>|<span data-ttu-id="39071-107">2519</span><span class="sxs-lookup"><span data-stu-id="39071-107">2519</span></span>|  
|<span data-ttu-id="39071-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="39071-108">Event Source</span></span>|<span data-ttu-id="39071-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="39071-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="39071-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="39071-110">Component</span></span>|<span data-ttu-id="39071-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="39071-111">SQLEngine</span></span>|  
|<span data-ttu-id="39071-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="39071-112">Symbolic Name</span></span>|<span data-ttu-id="39071-113">DBCC_NO_EXPRESSION_EVALUATOR</span><span class="sxs-lookup"><span data-stu-id="39071-113">DBCC_NO_EXPRESSION_EVALUATOR</span></span>|  
|<span data-ttu-id="39071-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="39071-114">Message Text</span></span>|<span data-ttu-id="39071-115">内部の式エバリュエーターを初期化できなかったため、オブジェクト ID O_ID (オブジェクト "O_NAME") の計算列とユーザー定義型を確認できません。</span><span class="sxs-lookup"><span data-stu-id="39071-115">Computed columns and user-defined types cannot be checked for object ID O_ID (object "O_NAME") because the internal expression evaluator could not be initialized.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="39071-116">説明</span><span class="sxs-lookup"><span data-stu-id="39071-116">Explanation</span></span>  
 <span data-ttu-id="39071-117">この情報メッセージは、クエリ プロセッサが、計算列と CLR (common language runtime) ユーザー定義型を評価するための内部オブジェクトを DBCC に提供できなかったことを示しています。</span><span class="sxs-lookup"><span data-stu-id="39071-117">This informational message indicates that the query processor could not provide DBCC with an internal object to allow for the evaluation of computed columns and common language runtime (CLR) user-defined types.</span></span> <span data-ttu-id="39071-118">つまり、計算列および CLR ユーザー定義型の正当性チェックが行われなかったり、DBCC でインデックスとベース テーブルの整合性をチェックする際に計算列が使用されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="39071-118">This means that computed columns and CLR user-defined types will not be checked for correctness or be used when DBCC checks the consistency between indexes and base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="39071-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="39071-119">User Action</span></span>  
 <span data-ttu-id="39071-120">なし</span><span class="sxs-lookup"><span data-stu-id="39071-120">None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39071-121">参照</span><span class="sxs-lookup"><span data-stu-id="39071-121">See Also</span></span>  
 [<span data-ttu-id="39071-122">MSSQLSERVER_2518</span><span class="sxs-lookup"><span data-stu-id="39071-122">MSSQLSERVER_2518</span></span>](mssqlserver-2518-database-engine-error.md)  
  
  
