---
title: MSSQLSERVER_2511 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23e91b0d64140329639cf57f3a336cd2eab8e4e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715313"
---
# <a name="mssqlserver_2511"></a><span data-ttu-id="a305e-102">MSSQLSERVER_2511</span><span class="sxs-lookup"><span data-stu-id="a305e-102">MSSQLSERVER_2511</span></span>
    
## <a name="details"></a><span data-ttu-id="a305e-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a305e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a305e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a305e-104">Product Name</span></span>|<span data-ttu-id="a305e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a305e-105">SQL Server</span></span>|  
|<span data-ttu-id="a305e-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a305e-106">Event ID</span></span>|<span data-ttu-id="a305e-107">2511</span><span class="sxs-lookup"><span data-stu-id="a305e-107">2511</span></span>|  
|<span data-ttu-id="a305e-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a305e-108">Event Source</span></span>|<span data-ttu-id="a305e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a305e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a305e-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a305e-110">Component</span></span>|<span data-ttu-id="a305e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a305e-111">SQLEngine</span></span>|  
|<span data-ttu-id="a305e-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a305e-112">Symbolic Name</span></span>|<span data-ttu-id="a305e-113">DBCC_KEYS_OUT_OF_ORDER</span><span class="sxs-lookup"><span data-stu-id="a305e-113">DBCC_KEYS_OUT_OF_ORDER</span></span>|  
|<span data-ttu-id="a305e-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a305e-114">Message Text</span></span>|<span data-ttu-id="a305e-115">テーブル エラー:オブジェクト ID %d、インデックス ID %d、パーティション ID %I64d、アロケーション ユニット ID %I64d (型 %.\*ls)。</span><span class="sxs-lookup"><span data-stu-id="a305e-115">Table error: Object ID %d, index ID %d, partition ID %I64d, alloc unit ID %I64d (type %.\*ls).</span></span> <span data-ttu-id="a305e-116">ページ %S_PGID、スロット %d および %d のキーの順序が不正です。</span><span class="sxs-lookup"><span data-stu-id="a305e-116">Keys out of order on page %S_PGID, slots %d and %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a305e-117">説明</span><span class="sxs-lookup"><span data-stu-id="a305e-117">Explanation</span></span>  
 <span data-ttu-id="a305e-118">指定したインデックスで順序が不正なキーが検出されました。</span><span class="sxs-lookup"><span data-stu-id="a305e-118">Out-of-order keys were detected in the specified index.</span></span> <span data-ttu-id="a305e-119">キーを含むページが壊れている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a305e-119">The page in which the keys are contained may be corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a305e-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a305e-120">User Action</span></span>  
 <span data-ttu-id="a305e-121">ALTER INDEX REBUILD ステートメントを使用して、指定したインデックスを再構築します。</span><span class="sxs-lookup"><span data-stu-id="a305e-121">Rebuild the specified index by using the ALTER INDEX REBUILD statement.</span></span>  
  
  
