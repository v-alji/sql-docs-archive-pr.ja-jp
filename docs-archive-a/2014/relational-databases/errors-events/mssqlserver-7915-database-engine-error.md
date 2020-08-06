---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1dc7a69023e49b48a10da9f0388cbd72fbe46be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641674"
---
# <a name="mssqlserver_7915"></a><span data-ttu-id="0fdf1-102">MSSQLSERVER_7915</span><span class="sxs-lookup"><span data-stu-id="0fdf1-102">MSSQLSERVER_7915</span></span>
    
## <a name="details"></a><span data-ttu-id="0fdf1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="0fdf1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0fdf1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="0fdf1-104">Product Name</span></span>|<span data-ttu-id="0fdf1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0fdf1-105">SQL Server</span></span>|  
|<span data-ttu-id="0fdf1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0fdf1-106">Event ID</span></span>|<span data-ttu-id="0fdf1-107">7915</span><span class="sxs-lookup"><span data-stu-id="0fdf1-107">7915</span></span>|  
|<span data-ttu-id="0fdf1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="0fdf1-108">Event Source</span></span>|<span data-ttu-id="0fdf1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0fdf1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0fdf1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0fdf1-110">Component</span></span>|<span data-ttu-id="0fdf1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0fdf1-111">SQLEngine</span></span>|  
|<span data-ttu-id="0fdf1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="0fdf1-112">Symbolic Name</span></span>|<span data-ttu-id="0fdf1-113">DBCC2_REPAIR_IAM_CHAIN_REBUILT</span><span class="sxs-lookup"><span data-stu-id="0fdf1-113">DBCC2_REPAIR_IAM_CHAIN_REBUILT</span></span>|  
|<span data-ttu-id="0fdf1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="0fdf1-114">Message Text</span></span>|<span data-ttu-id="0fdf1-115">修復:オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) の IAM チェーンがページ P_ID の前で切り捨てられました。チェーンが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="0fdf1-115">Repair: IAM chain for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), has been truncated before page P_ID and will be rebuilt.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0fdf1-116">説明</span><span class="sxs-lookup"><span data-stu-id="0fdf1-116">Explanation</span></span>  
 <span data-ttu-id="0fdf1-117">これは、REPAIR から送られた情報メッセージであり、指定の IAM (Index Allocation Map) チェーンが再構築できるように修復されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="0fdf1-117">This is an information message sent by REPAIR that indicates that the specified Index Allocation Map (IAM) chain was patched so that it could be rebuilt.</span></span> <span data-ttu-id="0fdf1-118">この修復で、IAM チェーンの新しい開始位置の割り当てや、チェーンからの不正なページの削除が必要であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0fdf1-118">This patching may have required the allocation of a new head of the IAM chain or the removal of bad pages from the chain.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0fdf1-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="0fdf1-119">User Action</span></span>  
 <span data-ttu-id="0fdf1-120">なし</span><span class="sxs-lookup"><span data-stu-id="0fdf1-120">None</span></span>  
  
  
