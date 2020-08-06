---
title: MSSQLSERVER_10737 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df8a4de014552d3aca00b3eb244f7ff8df56756b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643404"
---
# <a name="mssqlserver_10737"></a><span data-ttu-id="40ea9-102">MSSQLSERVER_10737</span><span class="sxs-lookup"><span data-stu-id="40ea9-102">MSSQLSERVER_10737</span></span>
    
## <a name="details"></a><span data-ttu-id="40ea9-103">詳細</span><span class="sxs-lookup"><span data-stu-id="40ea9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40ea9-104">製品名</span><span class="sxs-lookup"><span data-stu-id="40ea9-104">Product Name</span></span>|<span data-ttu-id="40ea9-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="40ea9-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="40ea9-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="40ea9-106">Event ID</span></span>|<span data-ttu-id="40ea9-107">10737</span><span class="sxs-lookup"><span data-stu-id="40ea9-107">10737</span></span>|  
|<span data-ttu-id="40ea9-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="40ea9-108">Event Source</span></span>|<span data-ttu-id="40ea9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="40ea9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="40ea9-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="40ea9-110">Component</span></span>|<span data-ttu-id="40ea9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="40ea9-111">SQLEngine</span></span>|  
|<span data-ttu-id="40ea9-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="40ea9-112">Symbolic Name</span></span>|<span data-ttu-id="40ea9-113">REBUILD_PARTITION_ALL_NOT_SPECIFIED</span><span class="sxs-lookup"><span data-stu-id="40ea9-113">REBUILD_PARTITION_ALL_NOT_SPECIFIED</span></span>|  
|<span data-ttu-id="40ea9-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="40ea9-114">Message Text</span></span>|<span data-ttu-id="40ea9-115">ALTER TABLE REBUILD ステートメントまたは ALTER INDEX REBUILD ステートメントの DATA_COMPRESSION 句でパーティションを指定する場合は、PARTITION=ALL を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40ea9-115">In an ALTER TABLE REBUILD or ALTER INDEX REBUILD statement, when a partition is specified in a DATA_COMPRESSION clause, PARTITION=ALL must be specified.</span></span> <span data-ttu-id="40ea9-116">PARTITION=ALL 句を使用すると、DATA_COMPRESSION 句でサブセットのみを指定した場合でも、テーブルまたはインデックスのすべてのパーティションが必ず再構築されます。</span><span class="sxs-lookup"><span data-stu-id="40ea9-116">The PARTITION=ALL clause is used to reinforce that all partitions of the table or index will be rebuilt, even if only a subset is specified in the DATA_COMPRESSION clause.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="40ea9-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="40ea9-117">User Action</span></span>  
 <span data-ttu-id="40ea9-118">ALTER TABLE ステートメントまたは ALTER INDEX ステートメントに PARTITION=ALL 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="40ea9-118">Add the PARTITION=ALL clause to the ALTER TABLE or ALTER INDEX statement.</span></span> <span data-ttu-id="40ea9-119">または、特定のパーティションを再構築するには、REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}) を使用します。</span><span class="sxs-lookup"><span data-stu-id="40ea9-119">Or, to rebuild a specific partition, use REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}).</span></span>  
  
  
