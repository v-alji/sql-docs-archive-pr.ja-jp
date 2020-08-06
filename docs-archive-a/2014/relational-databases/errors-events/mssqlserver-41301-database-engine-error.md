---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4fa78b334f32033f96df002aeaf039994b396cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642110"
---
# <a name="mssqlserver_41301"></a><span data-ttu-id="69443-102">MSSQLSERVER_41301</span><span class="sxs-lookup"><span data-stu-id="69443-102">MSSQLSERVER_41301</span></span>
    
## <a name="details"></a><span data-ttu-id="69443-103">詳細</span><span class="sxs-lookup"><span data-stu-id="69443-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69443-104">製品名</span><span class="sxs-lookup"><span data-stu-id="69443-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="69443-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="69443-105">Event ID</span></span>|<span data-ttu-id="69443-106">41301</span><span class="sxs-lookup"><span data-stu-id="69443-106">41301</span></span>|  
|<span data-ttu-id="69443-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="69443-107">Event Source</span></span>|<span data-ttu-id="69443-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="69443-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="69443-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="69443-109">Component</span></span>|<span data-ttu-id="69443-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="69443-110">SQLEngine</span></span>|  
|<span data-ttu-id="69443-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="69443-111">Symbolic Name</span></span>|<span data-ttu-id="69443-112">COMMIT_DEPENDENCY_FAILURE</span><span class="sxs-lookup"><span data-stu-id="69443-112">COMMIT_DEPENDENCY_FAILURE</span></span>|  
|<span data-ttu-id="69443-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="69443-113">Message Text</span></span>|<span data-ttu-id="69443-114">現在のトランザクションが依存している前のトランザクションが中止されたため、現在のトランザクションはコミットできません。</span><span class="sxs-lookup"><span data-stu-id="69443-114">A previous transaction that the current transaction took a dependency on has aborted, and the current transaction can no longer commit.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="69443-115">説明</span><span class="sxs-lookup"><span data-stu-id="69443-115">Explanation</span></span>  
 <span data-ttu-id="69443-116">依存エラーが発生したため、トランザクションに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="69443-116">The transaction encountered a dependency failure, and is now doomed.</span></span>  
  
 <span data-ttu-id="69443-117">このエラーは、従属トランザクションが多すぎるために発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="69443-117">This error can also be caused by too many dependent transactions.</span></span> <span data-ttu-id="69443-118">どの書き込みトランザクションでも、従属トランザクションの数には制限があります。</span><span class="sxs-lookup"><span data-stu-id="69443-118">Any write transaction can have a limited number of dependent transactions.</span></span> <span data-ttu-id="69443-119">たとえば、このエラーは、ある更新トランザクションに依存関係を適用しようと試みる読み取りトランザクションの数が多すぎる場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="69443-119">For example, this error can occur if too many read transactions try to take a dependency on the update transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="69443-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="69443-120">User Action</span></span>  
 <span data-ttu-id="69443-121">そのトランザクションは操作しないでください。</span><span class="sxs-lookup"><span data-stu-id="69443-121">Don't do any work on the transaction.</span></span> <span data-ttu-id="69443-122">ROLLBACK TRAN を呼び出し、トランザクションをロールバックします。</span><span class="sxs-lookup"><span data-stu-id="69443-122">Call ROLLBACK TRAN to roll back the transaction.</span></span> <span data-ttu-id="69443-123">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69443-123">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69443-124">参照</span><span class="sxs-lookup"><span data-stu-id="69443-124">See Also</span></span>  
 [<span data-ttu-id="69443-125">AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69443-125">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
