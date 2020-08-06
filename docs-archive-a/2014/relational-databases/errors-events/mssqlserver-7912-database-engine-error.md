---
title: MSSQLSERVER_7912 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7912 (Database Engine error)
ms.assetid: 8e6157c2-7e84-49f2-965a-c7426c2b23fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 634ed43a4a8bcd2edde03fe5f6b9f052346ddb8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641679"
---
# <a name="mssqlserver_7912"></a><span data-ttu-id="2f102-102">MSSQLSERVER_7912</span><span class="sxs-lookup"><span data-stu-id="2f102-102">MSSQLSERVER_7912</span></span>
    
## <a name="details"></a><span data-ttu-id="2f102-103">詳細</span><span class="sxs-lookup"><span data-stu-id="2f102-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f102-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2f102-104">Product Name</span></span>|<span data-ttu-id="2f102-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2f102-105">SQL Server</span></span>|  
|<span data-ttu-id="2f102-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2f102-106">Event ID</span></span>|<span data-ttu-id="2f102-107">7912</span><span class="sxs-lookup"><span data-stu-id="2f102-107">7912</span></span>|  
|<span data-ttu-id="2f102-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2f102-108">Event Source</span></span>|<span data-ttu-id="2f102-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2f102-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2f102-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2f102-110">Component</span></span>|<span data-ttu-id="2f102-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2f102-111">SQLEngine</span></span>|  
|<span data-ttu-id="2f102-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="2f102-112">Symbolic Name</span></span>|<span data-ttu-id="2f102-113">DBCC2_REPAIR_EXTENT_ALLOCATED</span><span class="sxs-lookup"><span data-stu-id="2f102-113">DBCC2_REPAIR_EXTENT_ALLOCATED</span></span>|  
|<span data-ttu-id="2f102-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2f102-114">Message Text</span></span>|<span data-ttu-id="2f102-115">修復:エクステント P_ID が、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="2f102-115">Repair: Extent P_ID has been allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2f102-116">説明</span><span class="sxs-lookup"><span data-stu-id="2f102-116">Explanation</span></span>  
 <span data-ttu-id="2f102-117">これは、REPAIR からの情報メッセージであり、指定のオブジェクトにエクステントが割り当てられたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="2f102-117">This is an informational message from REPAIR that states that an extent has been allocated to the specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2f102-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2f102-118">User Action</span></span>  
 <span data-ttu-id="2f102-119">なし</span><span class="sxs-lookup"><span data-stu-id="2f102-119">None</span></span>  
  
  
