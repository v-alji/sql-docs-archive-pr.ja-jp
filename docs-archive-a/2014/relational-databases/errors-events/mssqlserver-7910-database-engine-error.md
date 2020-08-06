---
title: MSSQLSERVER_7910 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7910 (Database Engine error)
ms.assetid: 017a0113-2b17-40b3-a419-30bbc43d46b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60e7cca3f6973374ae7aeaa959a0b31207a1258e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640963"
---
# <a name="mssqlserver_7910"></a><span data-ttu-id="403f5-102">MSSQLSERVER_7910</span><span class="sxs-lookup"><span data-stu-id="403f5-102">MSSQLSERVER_7910</span></span>
    
## <a name="details"></a><span data-ttu-id="403f5-103">詳細</span><span class="sxs-lookup"><span data-stu-id="403f5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="403f5-104">製品名</span><span class="sxs-lookup"><span data-stu-id="403f5-104">Product Name</span></span>|<span data-ttu-id="403f5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="403f5-105">SQL Server</span></span>|  
|<span data-ttu-id="403f5-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="403f5-106">Event ID</span></span>|<span data-ttu-id="403f5-107">7910</span><span class="sxs-lookup"><span data-stu-id="403f5-107">7910</span></span>|  
|<span data-ttu-id="403f5-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="403f5-108">Event Source</span></span>|<span data-ttu-id="403f5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="403f5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="403f5-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="403f5-110">Component</span></span>|<span data-ttu-id="403f5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="403f5-111">SQLEngine</span></span>|  
|<span data-ttu-id="403f5-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="403f5-112">Symbolic Name</span></span>|<span data-ttu-id="403f5-113">DBCC2_REPAIR_PAGE_ALLOCATED</span><span class="sxs-lookup"><span data-stu-id="403f5-113">DBCC2_REPAIR_PAGE_ALLOCATED</span></span>|  
|<span data-ttu-id="403f5-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="403f5-114">Message Text</span></span>|<span data-ttu-id="403f5-115">修復:ページ P_ID が、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="403f5-115">Repair: The page P_ID has been allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="403f5-116">説明</span><span class="sxs-lookup"><span data-stu-id="403f5-116">Explanation</span></span>  
 <span data-ttu-id="403f5-117">単一ページ スロット配列の IAM (Index Allocation Map) ページに 1 ページが割り当てられたことを示す、REPAIR からの情報メッセージです。</span><span class="sxs-lookup"><span data-stu-id="403f5-117">This is an informational message from REPAIR that states that a page has been allocated to the single-page slot array of an Index Allocation Map (IAM) page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="403f5-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="403f5-118">User Action</span></span>  
 <span data-ttu-id="403f5-119">なし</span><span class="sxs-lookup"><span data-stu-id="403f5-119">None</span></span>  
  
  
