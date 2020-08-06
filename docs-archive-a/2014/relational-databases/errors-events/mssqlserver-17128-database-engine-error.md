---
title: MSSQLSERVER_17128 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e08c668acd0a8b2decb14da338b8d1f1e650de5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714401"
---
# <a name="mssqlserver_17128"></a><span data-ttu-id="d9d4b-102">MSSQLSERVER_17128</span><span class="sxs-lookup"><span data-stu-id="d9d4b-102">MSSQLSERVER_17128</span></span>
    
## <a name="details"></a><span data-ttu-id="d9d4b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d9d4b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9d4b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d9d4b-104">Product Name</span></span>|<span data-ttu-id="d9d4b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d9d4b-105">SQL Server</span></span>|  
|<span data-ttu-id="d9d4b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d9d4b-106">Event ID</span></span>|<span data-ttu-id="d9d4b-107">17128</span><span class="sxs-lookup"><span data-stu-id="d9d4b-107">17128</span></span>|  
|<span data-ttu-id="d9d4b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d9d4b-108">Event Source</span></span>|<span data-ttu-id="d9d4b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d9d4b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d9d4b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d9d4b-110">Component</span></span>|<span data-ttu-id="d9d4b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d9d4b-111">SQLEngine</span></span>|  
|<span data-ttu-id="d9d4b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d9d4b-112">Symbolic Name</span></span>|<span data-ttu-id="d9d4b-113">INIT_NOBUFSPACE</span><span class="sxs-lookup"><span data-stu-id="d9d4b-113">INIT_NOBUFSPACE</span></span>|  
|<span data-ttu-id="d9d4b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d9d4b-114">Message Text</span></span>|<span data-ttu-id="d9d4b-115">initdata:カーネル バッファー用のメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="d9d4b-115">initdata: No memory for kernel buffers.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d9d4b-116">説明</span><span class="sxs-lookup"><span data-stu-id="d9d4b-116">Explanation</span></span>  
 <span data-ttu-id="d9d4b-117">バッファー プールの初回メモリ割り当てまたは予約に失敗しており、SQL Server が終了します。</span><span class="sxs-lookup"><span data-stu-id="d9d4b-117">The buffer pool's initial memory allocations or reservations have failed, and SQL Server exits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d9d4b-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d9d4b-118">User Action</span></span>  
 <span data-ttu-id="d9d4b-119">通常、最小システム要件を大きく下回るような非常に小規模なコンピューターで SQL Server を起動した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="d9d4b-119">Usually caused by starting SQL Server on an extremely small machine - far smaller than the minimum system requirements.</span></span>  
  
  
