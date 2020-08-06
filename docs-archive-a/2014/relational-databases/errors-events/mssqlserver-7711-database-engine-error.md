---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e29b2ea993e8e5332ef03b05f628dc791e20aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640980"
---
# <a name="mssqlserver_7711"></a><span data-ttu-id="faa51-102">MSSQLSERVER_7711</span><span class="sxs-lookup"><span data-stu-id="faa51-102">MSSQLSERVER_7711</span></span>
    
## <a name="details"></a><span data-ttu-id="faa51-103">詳細</span><span class="sxs-lookup"><span data-stu-id="faa51-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="faa51-104">製品名</span><span class="sxs-lookup"><span data-stu-id="faa51-104">Product Name</span></span>|<span data-ttu-id="faa51-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="faa51-105">SQL Server</span></span>|  
|<span data-ttu-id="faa51-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="faa51-106">Event ID</span></span>|<span data-ttu-id="faa51-107">7711</span><span class="sxs-lookup"><span data-stu-id="faa51-107">7711</span></span>|  
|<span data-ttu-id="faa51-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="faa51-108">Event Source</span></span>|<span data-ttu-id="faa51-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="faa51-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="faa51-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="faa51-110">Component</span></span>|<span data-ttu-id="faa51-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="faa51-111">SQLEngine</span></span>|  
|<span data-ttu-id="faa51-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="faa51-112">Symbolic Name</span></span>|<span data-ttu-id="faa51-113">PRT_RANGE_OVERLAP</span><span class="sxs-lookup"><span data-stu-id="faa51-113">PRT_RANGE_OVERLAP</span></span>|  
|<span data-ttu-id="faa51-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="faa51-114">Message Text</span></span>|<span data-ttu-id="faa51-115">テーブル、インデックス、またはパーティションの 1 つに DATA_COMPRESSION オプションが複数回指定されました。</span><span class="sxs-lookup"><span data-stu-id="faa51-115">The DATA_COMPRESSION option was specified more than once for the table or index or one of its partitions.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="faa51-116">説明</span><span class="sxs-lookup"><span data-stu-id="faa51-116">Explanation</span></span>  
 <span data-ttu-id="faa51-117">次のステートメントのいずれかの DATA_COMPRESSION オプションでエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="faa51-117">An error occurred in the DATA_COMPRESSION option in one of the following statements:</span></span>  
  
-   <span data-ttu-id="faa51-118">CREATE TABLE</span><span class="sxs-lookup"><span data-stu-id="faa51-118">CREATE TABLE</span></span>  
  
-   <span data-ttu-id="faa51-119">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="faa51-119">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="faa51-120">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="faa51-120">CREATE INDEX</span></span>  
  
-   <span data-ttu-id="faa51-121">ALTER INDEX</span><span class="sxs-lookup"><span data-stu-id="faa51-121">ALTER INDEX</span></span>  
  
 <span data-ttu-id="faa51-122">引用されたテーブルまたはインデックスがパーティション分割されている場合、少なくとも 1 つのパーティションで DATA_COMPRESSION オプションが 2 回以上指定されました。</span><span class="sxs-lookup"><span data-stu-id="faa51-122">If the table or index cited is partitioned, the DATA_COMPRESSION option was listed more than one time for at least one of the partitions.</span></span> <span data-ttu-id="faa51-123">テーブルまたはインデックスがパーティション分割されていない場合、DATA_COMPRESSION オプションが 2 回以上引用されました。</span><span class="sxs-lookup"><span data-stu-id="faa51-123">If the table or index is not partitioned, the DATA_COMPRESSION option was cited more than one time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="faa51-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="faa51-124">User Action</span></span>  
 <span data-ttu-id="faa51-125">パーティション分割されたテーブルまたはインデックスの場合、各パーティションに DATA_COMPRESSION オプションを 1 回だけ指定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="faa51-125">For a partitioned table or index, make sure that the DATA_COMPRESSION option is specified only one time for each partition.</span></span> <span data-ttu-id="faa51-126">パーティション分割されていないテーブルまたはインデックスの場合、ステートメントに DATA_COMPRESSION オプションを 1 回だけ使用してください。</span><span class="sxs-lookup"><span data-stu-id="faa51-126">For a table or index that is not partitioned, use the DATA_COMPRESSION option only one time in the statement.</span></span>  
  
  
