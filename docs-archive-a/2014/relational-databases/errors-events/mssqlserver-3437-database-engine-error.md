---
title: MSSQLSERVER_3437 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed8f2050f6f1b38bc5f3fcb7a9700b80e52f2763
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643854"
---
# <a name="mssqlserver_3437"></a><span data-ttu-id="e2449-102">MSSQLSERVER_3437</span><span class="sxs-lookup"><span data-stu-id="e2449-102">MSSQLSERVER_3437</span></span>
    
## <a name="details"></a><span data-ttu-id="e2449-103">詳細</span><span class="sxs-lookup"><span data-stu-id="e2449-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2449-104">製品名</span><span class="sxs-lookup"><span data-stu-id="e2449-104">Product Name</span></span>|<span data-ttu-id="e2449-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e2449-105">SQL Server</span></span>|  
|<span data-ttu-id="e2449-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e2449-106">Event ID</span></span>|<span data-ttu-id="e2449-107">3437</span><span class="sxs-lookup"><span data-stu-id="e2449-107">3437</span></span>|  
|<span data-ttu-id="e2449-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="e2449-108">Event Source</span></span>|<span data-ttu-id="e2449-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e2449-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e2449-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e2449-110">Component</span></span>|<span data-ttu-id="e2449-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e2449-111">SQLEngine</span></span>|  
|<span data-ttu-id="e2449-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="e2449-112">Symbolic Name</span></span>|<span data-ttu-id="e2449-113">NODTC</span><span class="sxs-lookup"><span data-stu-id="e2449-113">NODTC</span></span>|  
|<span data-ttu-id="e2449-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="e2449-114">Message Text</span></span>|<span data-ttu-id="e2449-115">データベース '%.\*ls' を復旧中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e2449-115">An error occurred while recovering database '%.\*ls'.</span></span> <span data-ttu-id="e2449-116">トランザクション %S_XID の完了状態を確認するために Microsoft 分散トランザクション コーディネーター (MS DTC) に接続できません。</span><span class="sxs-lookup"><span data-stu-id="e2449-116">Unable to connect to Microsoft Distributed Transaction Coordinator (MS DTC) to check the completion status of transaction %S_XID.</span></span> <span data-ttu-id="e2449-117">MS DTC を修正して、復旧を再実行してください。</span><span class="sxs-lookup"><span data-stu-id="e2449-117">Fix MS DTC, and run recovery again.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e2449-118">説明</span><span class="sxs-lookup"><span data-stu-id="e2449-118">Explanation</span></span>  
 <span data-ttu-id="e2449-119">データベースをシャットダウンしたときに、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) を使用する分散トランザクションの 1 つ以上が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="e2449-119">One or more distributed transactions that were using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) were incomplete when the database was shut down.</span></span> <span data-ttu-id="e2449-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではトランザクションを完了させたりロールバックしたりするために MS DTC に接続することはできないので、このデータベースを復旧できませんでした。</span><span class="sxs-lookup"><span data-stu-id="e2449-120">Recovery of this database failed because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot connect to MS DTC to complete or roll back the transactions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e2449-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="e2449-121">User Action</span></span>  
 <span data-ttu-id="e2449-122">このデータベースを復旧するには、まず MS DTC の問題を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2449-122">To recover this database, you must first resolve the problem with MS DTC.</span></span> <span data-ttu-id="e2449-123">MS DTC の問題を調査するため、Windows イベント ログを確認します。</span><span class="sxs-lookup"><span data-stu-id="e2449-123">To investigate the problem with MS DTC, examine the Windows event logs.</span></span> <span data-ttu-id="e2449-124">MS DTC の問題を解決してデータベースを復旧できない場合は、データベースのバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="e2449-124">If you cannot resolve the problem with MS DTC and recover the database, restore a backup of database.</span></span>  
  
  
