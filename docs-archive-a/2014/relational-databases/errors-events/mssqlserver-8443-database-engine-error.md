---
title: MSSQLSERVER_8443 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae02cc0d9e5661f4069884c22bf6eea0697bd2d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719953"
---
# <a name="mssqlserver_8443"></a><span data-ttu-id="2b7fa-102">MSSQLSERVER_8443</span><span class="sxs-lookup"><span data-stu-id="2b7fa-102">MSSQLSERVER_8443</span></span>
    
## <a name="details"></a><span data-ttu-id="2b7fa-103">詳細</span><span class="sxs-lookup"><span data-stu-id="2b7fa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b7fa-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2b7fa-104">Product Name</span></span>|<span data-ttu-id="2b7fa-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2b7fa-105">SQL Server</span></span>|  
|<span data-ttu-id="2b7fa-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2b7fa-106">Event ID</span></span>|<span data-ttu-id="2b7fa-107">8443</span><span class="sxs-lookup"><span data-stu-id="2b7fa-107">8443</span></span>|  
|<span data-ttu-id="2b7fa-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2b7fa-108">Event Source</span></span>|<span data-ttu-id="2b7fa-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2b7fa-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2b7fa-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2b7fa-110">Component</span></span>|<span data-ttu-id="2b7fa-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2b7fa-111">SQLEngine</span></span>|  
|<span data-ttu-id="2b7fa-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="2b7fa-112">Symbolic Name</span></span>|<span data-ttu-id="2b7fa-113">SB_DIALOG_WO_CONV_GROUP</span><span class="sxs-lookup"><span data-stu-id="2b7fa-113">SB_DIALOG_WO_CONV_GROUP</span></span>|  
|<span data-ttu-id="2b7fa-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2b7fa-114">Message Text</span></span>|<span data-ttu-id="2b7fa-115">ID '%.\*ls' のメッセージ交換と発信側: %d は存在しないメッセージ交換グループ '%.\*ls' を参照しています。</span><span class="sxs-lookup"><span data-stu-id="2b7fa-115">The conversation with ID '%.\*ls' and initiator %d references a missing conversation group '%.\*ls'.</span></span> <span data-ttu-id="2b7fa-116">DBCC CHECKDB を実行して、データベースを分析し、修復してください。</span><span class="sxs-lookup"><span data-stu-id="2b7fa-116">Run DBCC CHECKDB to analyze and repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2b7fa-117">説明</span><span class="sxs-lookup"><span data-stu-id="2b7fa-117">Explanation</span></span>  
 <span data-ttu-id="2b7fa-118">メタデータ層から、メッセージ交換グループに対して NULL が返されました。</span><span class="sxs-lookup"><span data-stu-id="2b7fa-118">The metadata layer returned NULL for the conversation group.</span></span> <span data-ttu-id="2b7fa-119">なんらかの形でデータベースが破損しています。</span><span class="sxs-lookup"><span data-stu-id="2b7fa-119">The database has been corrupted in some way.</span></span> <span data-ttu-id="2b7fa-120">考えられる原因の 1 つは、ディスク エラーです。</span><span class="sxs-lookup"><span data-stu-id="2b7fa-120">One possible source of corruption is a disk error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2b7fa-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2b7fa-121">User Action</span></span>  
 <span data-ttu-id="2b7fa-122">修復モードで DBCC CHECKDB を実行し、データベースを一貫性のある状態に戻します。</span><span class="sxs-lookup"><span data-stu-id="2b7fa-122">Run DBCC CHECKDB in repair mode to bring the database back into a consistent state.</span></span> <span data-ttu-id="2b7fa-123">一貫性のある状態を復元するために必要であれば、メッセージは削除される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b7fa-123">It may delete messages if necessary to restore consistency.</span></span> <span data-ttu-id="2b7fa-124">システム エラー ログで、システム内の別の障害が原因でこのエラーが生じていないか調べてください。</span><span class="sxs-lookup"><span data-stu-id="2b7fa-124">Investigate system error logs to see if this error was caused by another failure in the system.</span></span>  
  
  
