---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c0269322b30cee88e5ba3d50b6d391464b735f54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642836"
---
# <a name="mssqlserver_41342"></a><span data-ttu-id="6020d-102">MSSQLSERVER_41342</span><span class="sxs-lookup"><span data-stu-id="6020d-102">MSSQLSERVER_41342</span></span>
    
## <a name="details"></a><span data-ttu-id="6020d-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6020d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6020d-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6020d-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="6020d-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6020d-105">Event ID</span></span>|<span data-ttu-id="6020d-106">41342</span><span class="sxs-lookup"><span data-stu-id="6020d-106">41342</span></span>|  
|<span data-ttu-id="6020d-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6020d-107">Event Source</span></span>|<span data-ttu-id="6020d-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6020d-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6020d-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6020d-109">Component</span></span>|<span data-ttu-id="6020d-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6020d-110">SQLEngine</span></span>|  
|<span data-ttu-id="6020d-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6020d-111">Symbolic Name</span></span>|<span data-ttu-id="6020d-112">HK_HW_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="6020d-112">HK_HW_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="6020d-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6020d-113">Message Text</span></span>|<span data-ttu-id="6020d-114">システムのプロセッサのモデルは、*construct* の作成をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="6020d-114">The model of the processor on the system does not support creating *construct*.</span></span> <span data-ttu-id="6020d-115">このエラーは通常、古いプロセッサで発生します。</span><span class="sxs-lookup"><span data-stu-id="6020d-115">This error typically occurs with older processors.</span></span> <span data-ttu-id="6020d-116">サポートされているモデルについては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6020d-116">See [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online for information on supported models.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6020d-117">説明</span><span class="sxs-lookup"><span data-stu-id="6020d-117">Explanation</span></span>  
 <span data-ttu-id="6020d-118">メモリ最適化テーブルには、128 ビット値のアトミックな compare-and-exchange 操作をサポートするプロセッサ モデルが必要であり、これにはアセンブリ命令 CMPXCHG16B が必要です。</span><span class="sxs-lookup"><span data-stu-id="6020d-118">Memory-optimized tables require a processor model that supports atomic compare-and-exchange operations on 128-bit values, which require the assembly instruction CMPXCHG16B.</span></span> <span data-ttu-id="6020d-119">特定の古い AMD プロセッサ モデルでは、CMPXCHG16B 命令がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6020d-119">Certain older AMD processor models do not support the CMPXCHG16B instruction.</span></span> <span data-ttu-id="6020d-120">また、特定の仮想化環境では、既定でこの命令が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="6020d-120">Also, certain virtualization environments do not enable this instruction by default.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6020d-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6020d-121">User Action</span></span>  
 <span data-ttu-id="6020d-122">プロセッサをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="6020d-122">Upgrade your processor.</span></span> <span data-ttu-id="6020d-123">プロセッサで命令がサポートされていて、仮想マシンで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行している場合は、命令 CMPXCHG16B をサポートするように構成を変更してください。</span><span class="sxs-lookup"><span data-stu-id="6020d-123">If your processor supports the instruction and you are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a virtual machine, change the configuration to support the instruction CMPXCHG16B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6020d-124">参照</span><span class="sxs-lookup"><span data-stu-id="6020d-124">See Also</span></span>  
 [<span data-ttu-id="6020d-125">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="6020d-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
