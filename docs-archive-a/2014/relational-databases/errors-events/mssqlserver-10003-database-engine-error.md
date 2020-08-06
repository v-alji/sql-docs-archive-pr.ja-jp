---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ea44fc9591602bfc8279924e10a1803d0d5a87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632002"
---
# <a name="mssqlserver_10003"></a><span data-ttu-id="463ae-102">MSSQLSERVER_10003</span><span class="sxs-lookup"><span data-stu-id="463ae-102">MSSQLSERVER_10003</span></span>
    
## <a name="details"></a><span data-ttu-id="463ae-103">詳細</span><span class="sxs-lookup"><span data-stu-id="463ae-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="463ae-104">製品名</span><span class="sxs-lookup"><span data-stu-id="463ae-104">Product Name</span></span>|<span data-ttu-id="463ae-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="463ae-105">SQL Server</span></span>|  
|<span data-ttu-id="463ae-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="463ae-106">Event ID</span></span>|<span data-ttu-id="463ae-107">10003</span><span class="sxs-lookup"><span data-stu-id="463ae-107">10003</span></span>|  
|<span data-ttu-id="463ae-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="463ae-108">Event Source</span></span>|<span data-ttu-id="463ae-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="463ae-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="463ae-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="463ae-110">Component</span></span>|<span data-ttu-id="463ae-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="463ae-111">SQLEngine</span></span>|  
|<span data-ttu-id="463ae-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="463ae-112">Symbolic Name</span></span>|<span data-ttu-id="463ae-113">HR_E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="463ae-113">HR_E_OUTOFMEMORY</span></span>|  
|<span data-ttu-id="463ae-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="463ae-114">Message Text</span></span>|<span data-ttu-id="463ae-115">プロバイダーのメモリが不足しました。</span><span class="sxs-lookup"><span data-stu-id="463ae-115">The provider ran out of memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="463ae-116">説明</span><span class="sxs-lookup"><span data-stu-id="463ae-116">Explanation</span></span>  
 <span data-ttu-id="463ae-117">システム メモリが少ないため、OLE DB プロバイダーのメモリが不足しました。</span><span class="sxs-lookup"><span data-stu-id="463ae-117">Low system memory has caused the OLE DB provider to run out of memory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="463ae-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="463ae-118">User Action</span></span>  
 <span data-ttu-id="463ae-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="463ae-119">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="463ae-120">問題が解決しない場合は、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="463ae-120">If that does not help, restart the computer.</span></span> <span data-ttu-id="463ae-121">それでも問題が解決しない場合は、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して OLE DB トレース イベントを収集し、このデータを OLE DB プロバイダーの製品サポートに提供します。</span><span class="sxs-lookup"><span data-stu-id="463ae-121">If the problem persists, collect OLE DB trace events using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and provide this data to product support for the OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463ae-122">参照</span><span class="sxs-lookup"><span data-stu-id="463ae-122">See Also</span></span>  
 <span data-ttu-id="463ae-123">[SQL Server プロファイラーのテンプレートと権限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="463ae-123">[SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="463ae-124">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="463ae-124">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
