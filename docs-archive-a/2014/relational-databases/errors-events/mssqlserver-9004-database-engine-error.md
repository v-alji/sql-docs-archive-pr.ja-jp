---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 910665b4349e5b13c5abb4fd687dcf0c6fc122cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640005"
---
# <a name="mssqlserver_9004"></a><span data-ttu-id="9430d-102">MSSQLSERVER_9004</span><span class="sxs-lookup"><span data-stu-id="9430d-102">MSSQLSERVER_9004</span></span>
    
## <a name="details"></a><span data-ttu-id="9430d-103">詳細</span><span class="sxs-lookup"><span data-stu-id="9430d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9430d-104">製品名</span><span class="sxs-lookup"><span data-stu-id="9430d-104">Product Name</span></span>|<span data-ttu-id="9430d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9430d-105">SQL Server</span></span>|  
|<span data-ttu-id="9430d-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="9430d-106">Event ID</span></span>|<span data-ttu-id="9430d-107">9004</span><span class="sxs-lookup"><span data-stu-id="9430d-107">9004</span></span>|  
|<span data-ttu-id="9430d-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="9430d-108">Event Source</span></span>|<span data-ttu-id="9430d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9430d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9430d-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9430d-110">Component</span></span>|<span data-ttu-id="9430d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9430d-111">SQLEngine</span></span>|  
|<span data-ttu-id="9430d-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="9430d-112">Symbolic Name</span></span>|<span data-ttu-id="9430d-113">LOG_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="9430d-113">LOG_CORRUPT</span></span>|  
|<span data-ttu-id="9430d-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="9430d-114">Message Text</span></span>|<span data-ttu-id="9430d-115">データベース '%.\*ls' のログを処理中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9430d-115">An error occurred while processing the log for database '%.\*ls'.</span></span>  <span data-ttu-id="9430d-116">可能な場合は、バックアップから復元してください。</span><span class="sxs-lookup"><span data-stu-id="9430d-116">If possible, restore from backup.</span></span> <span data-ttu-id="9430d-117">バックアップを使用できない場合は、ログの再構築が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="9430d-117">If a backup is not available, it might be necessary to rebuild the log.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9430d-118">説明</span><span class="sxs-lookup"><span data-stu-id="9430d-118">Explanation</span></span>  
 <span data-ttu-id="9430d-119">ロールバック、復旧、またはレプリケーションの操作で、ログの処理中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9430d-119">An error was encountered while processing the log during rollback, recovery, or replication.</span></span> <span data-ttu-id="9430d-120">オペレーティング システムで検出されたエラーか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で検出された内部的な一貫性エラーを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9430d-120">This could indicate an error detected by the operating system-or an internal consistency error detected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9430d-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="9430d-121">User Action</span></span>  
 <span data-ttu-id="9430d-122">次のいずれかのアクションでこのエラーを修正します。</span><span class="sxs-lookup"><span data-stu-id="9430d-122">One of the following actions will correct this error:</span></span>  
  
-   <span data-ttu-id="9430d-123">バックアップからの復元を実行する。</span><span class="sxs-lookup"><span data-stu-id="9430d-123">Restore from a backup.</span></span>  
  
-   <span data-ttu-id="9430d-124">ログを再構築する。</span><span class="sxs-lookup"><span data-stu-id="9430d-124">Rebuild the log.</span></span>  
  
 <span data-ttu-id="9430d-125">また、システムのイベント ログまたはエラー ログで、システム内の問題がエラーの原因になっていないか調べます。</span><span class="sxs-lookup"><span data-stu-id="9430d-125">Also, check system event and error logs to identify issues within the system that may have caused the problem.</span></span>  
  
  
