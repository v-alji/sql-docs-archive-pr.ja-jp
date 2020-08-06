---
title: MSSQLSERVER_3431 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9b62047a25d71ca05dc3ab03651e5672353bc0a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643859"
---
# <a name="mssqlserver_3431"></a><span data-ttu-id="89eff-102">MSSQLSERVER_3431</span><span class="sxs-lookup"><span data-stu-id="89eff-102">MSSQLSERVER_3431</span></span>
    
## <a name="details"></a><span data-ttu-id="89eff-103">詳細</span><span class="sxs-lookup"><span data-stu-id="89eff-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89eff-104">製品名</span><span class="sxs-lookup"><span data-stu-id="89eff-104">Product Name</span></span>|<span data-ttu-id="89eff-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="89eff-105">SQL Server</span></span>|  
|<span data-ttu-id="89eff-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="89eff-106">Event ID</span></span>|<span data-ttu-id="89eff-107">3431</span><span class="sxs-lookup"><span data-stu-id="89eff-107">3431</span></span>|  
|<span data-ttu-id="89eff-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="89eff-108">Event Source</span></span>|<span data-ttu-id="89eff-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="89eff-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="89eff-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="89eff-110">Component</span></span>|<span data-ttu-id="89eff-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="89eff-111">SQLEngine</span></span>|  
|<span data-ttu-id="89eff-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="89eff-112">Symbolic Name</span></span>|<span data-ttu-id="89eff-113">UNRESOLVED_XACT</span><span class="sxs-lookup"><span data-stu-id="89eff-113">UNRESOLVED_XACT</span></span>|  
|<span data-ttu-id="89eff-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="89eff-114">Message Text</span></span>|<span data-ttu-id="89eff-115">トランザクションの結果を解決できないので、データベース '%.\*ls' (データベース ID %d) を復旧できませんでした。</span><span class="sxs-lookup"><span data-stu-id="89eff-115">Could not recover database '%.\*ls' (database ID %d) because of unresolved transaction outcomes.</span></span> <span data-ttu-id="89eff-116">Microsoft 分散トランザクション コーディネーター (MS DTC) のトランザクションは準備されていましたが、MS DTC では解決策を決定できませんでした。</span><span class="sxs-lookup"><span data-stu-id="89eff-116">Microsoft Distributed Transaction Coordinator (MS DTC) transactions were prepared, but MS DTC was unable to determine the resolution.</span></span> <span data-ttu-id="89eff-117">解決するには、MS DTC の修正、完全バックアップからの復元、またはデータベースの修復のいずれかを実行してください。</span><span class="sxs-lookup"><span data-stu-id="89eff-117">To resolve, either fix MS DTC, restore from a full backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="89eff-118">説明</span><span class="sxs-lookup"><span data-stu-id="89eff-118">Explanation</span></span>  
 <span data-ttu-id="89eff-119">データベースをシャットダウンしたときに、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) を使用する分散トランザクションの 1 つ以上が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="89eff-119">One or more distributed transactions that were using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) were incomplete when the database was shut down.</span></span> <span data-ttu-id="89eff-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、MS DTC からの詳細な情報がないとトランザクションの完了やロールバックを行うことができないので、このデータベースの復旧は失敗します。</span><span class="sxs-lookup"><span data-stu-id="89eff-120">Recovery of this database failed because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot complete the transactions or roll back the transactions without more information from MS DTC.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="89eff-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="89eff-121">User Action</span></span>  
 <span data-ttu-id="89eff-122">このデータベースを復旧するには、まず MS DTC の問題を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89eff-122">To recover this database, you must first resolve the problem with MS DTC.</span></span> <span data-ttu-id="89eff-123">MS DTC の問題を調査するため、Windows イベント ログを確認します。</span><span class="sxs-lookup"><span data-stu-id="89eff-123">To investigate the problem with MS DTC, examine the Windows event logs.</span></span> <span data-ttu-id="89eff-124">MS DTC の問題を解決してデータベースを復旧できない場合は、データベースのバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="89eff-124">If you cannot resolve the problem with MS DTC and recover the database, restore a backup of database.</span></span>  
  
  
