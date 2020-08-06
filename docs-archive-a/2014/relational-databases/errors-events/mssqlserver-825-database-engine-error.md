---
title: MSSQLSERVER_825 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b17dfac371ad3c805fdbb0b5d3269fc451dd9d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640016"
---
# <a name="mssqlserver_825"></a><span data-ttu-id="89867-102">MSSQLSERVER_825</span><span class="sxs-lookup"><span data-stu-id="89867-102">MSSQLSERVER_825</span></span>
    
## <a name="details"></a><span data-ttu-id="89867-103">詳細</span><span class="sxs-lookup"><span data-stu-id="89867-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89867-104">製品名</span><span class="sxs-lookup"><span data-stu-id="89867-104">Product Name</span></span>|<span data-ttu-id="89867-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="89867-105">SQL Server</span></span>|  
|<span data-ttu-id="89867-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="89867-106">Event ID</span></span>|<span data-ttu-id="89867-107">825</span><span class="sxs-lookup"><span data-stu-id="89867-107">825</span></span>|  
|<span data-ttu-id="89867-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="89867-108">Event Source</span></span>|<span data-ttu-id="89867-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="89867-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="89867-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="89867-110">Component</span></span>|<span data-ttu-id="89867-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="89867-111">SQLEngine</span></span>|  
|<span data-ttu-id="89867-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="89867-112">Symbolic Name</span></span>|<span data-ttu-id="89867-113">B_RETRYWORKED</span><span class="sxs-lookup"><span data-stu-id="89867-113">B_RETRYWORKED</span></span>|  
|<span data-ttu-id="89867-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="89867-114">Message Text</span></span>|<span data-ttu-id="89867-115">ファイル '%ls' のオフセット %#016I64x での読み取りは、読み取りに %d 回失敗 (エラー: %ls) した後で成功しました。</span><span class="sxs-lookup"><span data-stu-id="89867-115">A read of the file '%ls' at offset %#016I64x succeeded after failing %d time(s) with error: %ls.</span></span> <span data-ttu-id="89867-116">SQL Server エラー ログとシステム イベント ログ内の別のメッセージで詳細情報が報告されることもあります。</span><span class="sxs-lookup"><span data-stu-id="89867-116">Additional messages in the SQL Server error log and system event log may provide more detail.</span></span> <span data-ttu-id="89867-117">このエラー状態はデータベースの整合性を損なうので、解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89867-117">This error condition threatens database integrity and must be corrected.</span></span> <span data-ttu-id="89867-118">完全なデータベース整合性確認 (DBCC CHECKDB) を完了させてください。</span><span class="sxs-lookup"><span data-stu-id="89867-118">Complete a full database consistency check (DBCC CHECKDB).</span></span> <span data-ttu-id="89867-119">このエラーには多くの要因があります。詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="89867-119">This error can be caused by many factors; for more information, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="89867-120">説明</span><span class="sxs-lookup"><span data-stu-id="89867-120">Explanation</span></span>  
 <span data-ttu-id="89867-121">このメッセージは、読み取り操作が少なくとも 1 回は再実行されたことを示し、ディスク ハードウェアに大きな問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="89867-121">This message indicates that the read operation had to be reissued at least one time, and indicates a major problem with the disk hardware.</span></span> <span data-ttu-id="89867-122">このメッセージは、現時点では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の問題を示していませんが、ディスクの問題を解決しないと、データの損失やデータベースの破損につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89867-122">This message does not currently indicate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problem, but the disk problem could cause data loss or database corruption if it is not resolved.</span></span> <span data-ttu-id="89867-123">システム イベント ログに、問題の診断に役立つ関連するイベントが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="89867-123">The system event log may contain related events that help to diagnose the problem.</span></span> <span data-ttu-id="89867-124">I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))」 (Microsoft SQL Server I/O の基礎 (第 2 章)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89867-124">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="89867-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="89867-125">User Action</span></span>  
 <span data-ttu-id="89867-126">次の操作を行って、原因となっている問題を特定し、解決してください。</span><span class="sxs-lookup"><span data-stu-id="89867-126">The following actions may help you identify and resolve the underlying problem:</span></span>  
  
-   <span data-ttu-id="89867-127">このメッセージのエラー ログと変数テキストを確認し、問題の原因を明らかにする手掛かりを見つける。</span><span class="sxs-lookup"><span data-stu-id="89867-127">Review the error log and the variable text in this message for clues that explain the problem.</span></span>  
  
-   <span data-ttu-id="89867-128">ディスク システムを確認してください。</span><span class="sxs-lookup"><span data-stu-id="89867-128">Check your disk system.</span></span> <span data-ttu-id="89867-129">この問題は、ディスク、ディスク コントローラー、アレイ カード、またはディスク ドライバーに関連している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89867-129">The problem could be related to the disks, the disk controllers, array cards, or disk drivers.</span></span>  
  
-   <span data-ttu-id="89867-130">ディスク システムの状態を調べる最新のユーティリティがあるかどうか、ディスクの製造元に問い合わせる。</span><span class="sxs-lookup"><span data-stu-id="89867-130">Contact the disk manufacturer for the latest utilities for checking the status of your disk system.</span></span>  
  
-   <span data-ttu-id="89867-131">ドライバーの最新の更新があるかどうか、ディスクの製造元に問い合わせる。</span><span class="sxs-lookup"><span data-stu-id="89867-131">Contact the disk manufacturer for the latest driver updates.</span></span>  
  
  
