---
title: MSSQLSERVER_7916 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21b31eedf61369d9c4d1cfdfd5f53eebd3f5341c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641675"
---
# <a name="mssqlserver_7916"></a><span data-ttu-id="c2a3c-102">MSSQLSERVER_7916</span><span class="sxs-lookup"><span data-stu-id="c2a3c-102">MSSQLSERVER_7916</span></span>
    
## <a name="details"></a><span data-ttu-id="c2a3c-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c2a3c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2a3c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c2a3c-104">Product Name</span></span>|<span data-ttu-id="c2a3c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c2a3c-105">SQL Server</span></span>|  
|<span data-ttu-id="c2a3c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c2a3c-106">Event ID</span></span>|<span data-ttu-id="c2a3c-107">7916</span><span class="sxs-lookup"><span data-stu-id="c2a3c-107">7916</span></span>|  
|<span data-ttu-id="c2a3c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c2a3c-108">Event Source</span></span>|<span data-ttu-id="c2a3c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c2a3c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c2a3c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c2a3c-110">Component</span></span>|<span data-ttu-id="c2a3c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c2a3c-111">SQLEngine</span></span>|  
|<span data-ttu-id="c2a3c-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c2a3c-112">Symbolic Name</span></span>|<span data-ttu-id="c2a3c-113">DBCC2_REPAIR_RECORD_DELETED</span><span class="sxs-lookup"><span data-stu-id="c2a3c-113">DBCC2_REPAIR_RECORD_DELETED</span></span>|  
|<span data-ttu-id="c2a3c-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c2a3c-114">Message Text</span></span>|<span data-ttu-id="c2a3c-115">修復:ページ P_ID、スロット S_ID のオブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) のレコードが削除されました。</span><span class="sxs-lookup"><span data-stu-id="c2a3c-115">Repair: Deleted record for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), on page P_ID, slot S_ID.</span></span> <span data-ttu-id="c2a3c-116">インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="c2a3c-116">Indexes will be rebuilt.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c2a3c-117">説明</span><span class="sxs-lookup"><span data-stu-id="c2a3c-117">Explanation</span></span>  
 <span data-ttu-id="c2a3c-118">これは、REPAIR からの情報メッセージであり、このページから指定のレコードが削除されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="c2a3c-118">This is an information messages from REPAIR that indicates the specified record was deleted from the page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c2a3c-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c2a3c-119">User Action</span></span>  
 <span data-ttu-id="c2a3c-120">なし</span><span class="sxs-lookup"><span data-stu-id="c2a3c-120">None</span></span>  
  
  
