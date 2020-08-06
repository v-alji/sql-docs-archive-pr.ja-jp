---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6be0809b3560d94bb883cf3a4acfa3d2c484b8b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713197"
---
# <a name="mssqlserver_2516"></a><span data-ttu-id="5c60b-102">MSSQLSERVER_2516</span><span class="sxs-lookup"><span data-stu-id="5c60b-102">MSSQLSERVER_2516</span></span>
    
## <a name="details"></a><span data-ttu-id="5c60b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="5c60b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c60b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="5c60b-104">Product Name</span></span>|<span data-ttu-id="5c60b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5c60b-105">SQL Server</span></span>|  
|<span data-ttu-id="5c60b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5c60b-106">Event ID</span></span>|<span data-ttu-id="5c60b-107">2516</span><span class="sxs-lookup"><span data-stu-id="5c60b-107">2516</span></span>|  
|<span data-ttu-id="5c60b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="5c60b-108">Event Source</span></span>|<span data-ttu-id="5c60b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5c60b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5c60b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5c60b-110">Component</span></span>|<span data-ttu-id="5c60b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5c60b-111">SQLEngine</span></span>|  
|<span data-ttu-id="5c60b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="5c60b-112">Symbolic Name</span></span>|<span data-ttu-id="5c60b-113">DBCC_REPAIR_DIFF_MAP_INVALIDATED</span><span class="sxs-lookup"><span data-stu-id="5c60b-113">DBCC_REPAIR_DIFF_MAP_INVALIDATED</span></span>|  
|<span data-ttu-id="5c60b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="5c60b-114">Message Text</span></span>|<span data-ttu-id="5c60b-115">修復により、データベース NAME の差分ビットマップが無効になりました。</span><span class="sxs-lookup"><span data-stu-id="5c60b-115">Repair has invalidated the differential bitmap for database NAME.</span></span> <span data-ttu-id="5c60b-116">差分バックアップ チェーンが壊れています。</span><span class="sxs-lookup"><span data-stu-id="5c60b-116">The differential backup chain is broken.</span></span> <span data-ttu-id="5c60b-117">データベース全体をバックアップしてから、差分バックアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5c60b-117">You must perform a full database backup before you can perform a differential backup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5c60b-118">説明</span><span class="sxs-lookup"><span data-stu-id="5c60b-118">Explanation</span></span>  
 <span data-ttu-id="5c60b-119">この情報メッセージは、エラー MSSQLEngine_2515 の修復時に返されます。</span><span class="sxs-lookup"><span data-stu-id="5c60b-119">This informational message is returned when error MSSQLEngine_2515 is repaired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5c60b-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="5c60b-120">User Action</span></span>  
 <span data-ttu-id="5c60b-121">データベースの完全バックアップを実行します。</span><span class="sxs-lookup"><span data-stu-id="5c60b-121">Perform a full database backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c60b-122">参照</span><span class="sxs-lookup"><span data-stu-id="5c60b-122">See Also</span></span>  
 [<span data-ttu-id="5c60b-123">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5c60b-123">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
