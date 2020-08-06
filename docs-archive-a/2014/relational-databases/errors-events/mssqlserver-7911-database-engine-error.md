---
title: MSSQLSERVER_7911 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d37ce2dc11f231e8a6f8ae6cc8b95d8b2f87c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640961"
---
# <a name="mssqlserver_7911"></a><span data-ttu-id="94764-102">MSSQLSERVER_7911</span><span class="sxs-lookup"><span data-stu-id="94764-102">MSSQLSERVER_7911</span></span>
    
## <a name="details"></a><span data-ttu-id="94764-103">詳細</span><span class="sxs-lookup"><span data-stu-id="94764-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94764-104">製品名</span><span class="sxs-lookup"><span data-stu-id="94764-104">Product Name</span></span>|<span data-ttu-id="94764-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="94764-105">SQL Server</span></span>|  
|<span data-ttu-id="94764-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="94764-106">Event ID</span></span>|<span data-ttu-id="94764-107">7911</span><span class="sxs-lookup"><span data-stu-id="94764-107">7911</span></span>|  
|<span data-ttu-id="94764-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="94764-108">Event Source</span></span>|<span data-ttu-id="94764-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="94764-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="94764-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="94764-110">Component</span></span>|<span data-ttu-id="94764-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="94764-111">SQLEngine</span></span>|  
|<span data-ttu-id="94764-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="94764-112">Symbolic Name</span></span>|<span data-ttu-id="94764-113">DBCC2_REPAIR_PAGE_DEALLOCATED</span><span class="sxs-lookup"><span data-stu-id="94764-113">DBCC2_REPAIR_PAGE_DEALLOCATED</span></span>|  
|<span data-ttu-id="94764-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="94764-114">Message Text</span></span>|<span data-ttu-id="94764-115">修復:ページ P_ID が、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) から割り当て解除されました。</span><span class="sxs-lookup"><span data-stu-id="94764-115">Repair: The page P_ID has been deallocated from object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="94764-116">説明</span><span class="sxs-lookup"><span data-stu-id="94764-116">Explanation</span></span>  
 <span data-ttu-id="94764-117">単一ページ スロット配列の IAM (Index Allocation Map) ページから 1 ページが割り当て解除されたことを示す、REPAIR からの情報メッセージです。</span><span class="sxs-lookup"><span data-stu-id="94764-117">This is an informational message from REPAIR that states that a page has been deallocated from the single-page slot array of an Index Allocation Map (IAM) page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="94764-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="94764-118">User Action</span></span>  
 <span data-ttu-id="94764-119">なし</span><span class="sxs-lookup"><span data-stu-id="94764-119">None</span></span>  
  
  
