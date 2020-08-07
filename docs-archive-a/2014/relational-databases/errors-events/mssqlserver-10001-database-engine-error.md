---
title: MSSQLSERVER_10001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0542f6d52a4fd194c4b0ae5d1aad501f5e3b8c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719964"
---
# <a name="mssqlserver_10001"></a><span data-ttu-id="bc847-102">MSSQLSERVER_10001</span><span class="sxs-lookup"><span data-stu-id="bc847-102">MSSQLSERVER_10001</span></span>
    
## <a name="details"></a><span data-ttu-id="bc847-103">詳細</span><span class="sxs-lookup"><span data-stu-id="bc847-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc847-104">製品名</span><span class="sxs-lookup"><span data-stu-id="bc847-104">Product Name</span></span>|<span data-ttu-id="bc847-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bc847-105">SQL Server</span></span>|  
|<span data-ttu-id="bc847-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc847-106">Event ID</span></span>|<span data-ttu-id="bc847-107">10001</span><span class="sxs-lookup"><span data-stu-id="bc847-107">10001</span></span>|  
|<span data-ttu-id="bc847-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="bc847-108">Event Source</span></span>|<span data-ttu-id="bc847-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bc847-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bc847-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bc847-110">Component</span></span>|<span data-ttu-id="bc847-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bc847-111">SQLEngine</span></span>|  
|<span data-ttu-id="bc847-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="bc847-112">Symbolic Name</span></span>|<span data-ttu-id="bc847-113">HR_E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="bc847-113">HR_E_UNEXPECTED</span></span>|  
|<span data-ttu-id="bc847-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="bc847-114">Message Text</span></span>|<span data-ttu-id="bc847-115">プロバイダーが予期しない重大なエラーをレポートしました。</span><span class="sxs-lookup"><span data-stu-id="bc847-115">The provider reported an unexpected catastrophic failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bc847-116">説明</span><span class="sxs-lookup"><span data-stu-id="bc847-116">Explanation</span></span>  
 <span data-ttu-id="bc847-117">分散クエリ処理で、OLE DB プロバイダーを呼び出すときに一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bc847-117">Distributed query processing encountered a generic error while calling into the OLE DB provider.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bc847-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="bc847-118">User Action</span></span>  
 <span data-ttu-id="bc847-119">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して OLE DB トレース イベントを収集し、このデータを OLE DB プロバイダーの製品サポートに提供します。</span><span class="sxs-lookup"><span data-stu-id="bc847-119">Collect OLE DB trace events using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and  provide this data to product support for the OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc847-120">参照</span><span class="sxs-lookup"><span data-stu-id="bc847-120">See Also</span></span>  
 <span data-ttu-id="bc847-121">[SQL Server プロファイラーのテンプレートと権限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="bc847-121">[SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="bc847-122">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="bc847-122">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
