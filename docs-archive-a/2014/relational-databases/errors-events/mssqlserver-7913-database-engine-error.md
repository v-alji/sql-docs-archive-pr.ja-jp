---
title: MSSQLSERVER_7913 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7913 (Database Engine error)
ms.assetid: 9d8ad456-b1a2-4f79-a252-657fbec9ad9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb4110ef3aed8697db426ebd80f6764d873944db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641677"
---
# <a name="mssqlserver_7913"></a><span data-ttu-id="cdde1-102">MSSQLSERVER_7913</span><span class="sxs-lookup"><span data-stu-id="cdde1-102">MSSQLSERVER_7913</span></span>
    
## <a name="details"></a><span data-ttu-id="cdde1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="cdde1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cdde1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="cdde1-104">Product Name</span></span>|<span data-ttu-id="cdde1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cdde1-105">SQL Server</span></span>|  
|<span data-ttu-id="cdde1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="cdde1-106">Event ID</span></span>|<span data-ttu-id="cdde1-107">7913</span><span class="sxs-lookup"><span data-stu-id="cdde1-107">7913</span></span>|  
|<span data-ttu-id="cdde1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="cdde1-108">Event Source</span></span>|<span data-ttu-id="cdde1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cdde1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cdde1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="cdde1-110">Component</span></span>|<span data-ttu-id="cdde1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cdde1-111">SQLEngine</span></span>|  
|<span data-ttu-id="cdde1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="cdde1-112">Symbolic Name</span></span>|<span data-ttu-id="cdde1-113">DBCC2_REPAIR_EXTENT_DEALLOCATED</span><span class="sxs-lookup"><span data-stu-id="cdde1-113">DBCC2_REPAIR_EXTENT_DEALLOCATED</span></span>|  
|<span data-ttu-id="cdde1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="cdde1-114">Message Text</span></span>|<span data-ttu-id="cdde1-115">修復:エクステント P_ID が、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) から割り当て解除されました。</span><span class="sxs-lookup"><span data-stu-id="cdde1-115">Repair: Extent P_ID has been deallocated from object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cdde1-116">説明</span><span class="sxs-lookup"><span data-stu-id="cdde1-116">Explanation</span></span>  
 <span data-ttu-id="cdde1-117">これは、REPAIR からの情報メッセージであり、指定のオブジェクトからエクステントが割り当て解除されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="cdde1-117">This is an informational message from REPAIR that states that an extent has been deallocated from the specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cdde1-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="cdde1-118">User Action</span></span>  
 <span data-ttu-id="cdde1-119">なし</span><span class="sxs-lookup"><span data-stu-id="cdde1-119">None</span></span>  
  
  
