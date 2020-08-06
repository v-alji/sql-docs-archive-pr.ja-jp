---
title: MSSQLSERVER_5233 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5233 (Database Engine error)
ms.assetid: 7a855afa-2d3b-49b7-adef-197b99fc98b1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a5e2c603652534a6d3093a01da0a926a7195954
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643851"
---
# <a name="mssqlserver_5233"></a><span data-ttu-id="0f2fe-102">MSSQLSERVER_5233</span><span class="sxs-lookup"><span data-stu-id="0f2fe-102">MSSQLSERVER_5233</span></span>
    
## <a name="details"></a><span data-ttu-id="0f2fe-103">詳細</span><span class="sxs-lookup"><span data-stu-id="0f2fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f2fe-104">製品名</span><span class="sxs-lookup"><span data-stu-id="0f2fe-104">Product Name</span></span>|<span data-ttu-id="0f2fe-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f2fe-105">SQL Server</span></span>|  
|<span data-ttu-id="0f2fe-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0f2fe-106">Event ID</span></span>|<span data-ttu-id="0f2fe-107">5233</span><span class="sxs-lookup"><span data-stu-id="0f2fe-107">5233</span></span>|  
|<span data-ttu-id="0f2fe-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="0f2fe-108">Event Source</span></span>|<span data-ttu-id="0f2fe-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0f2fe-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0f2fe-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0f2fe-110">Component</span></span>|<span data-ttu-id="0f2fe-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0f2fe-111">SQLEngine</span></span>|  
|<span data-ttu-id="0f2fe-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="0f2fe-112">Symbolic Name</span></span>|<span data-ttu-id="0f2fe-113">DBCC4_INCORRECT_VALUE_IN_PAGE_HEADER_NO_METADATA</span><span class="sxs-lookup"><span data-stu-id="0f2fe-113">DBCC4_INCORRECT_VALUE_IN_PAGE_HEADER_NO_METADATA</span></span>|  
|<span data-ttu-id="0f2fe-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="0f2fe-114">Message Text</span></span>|<span data-ttu-id="0f2fe-115">テーブル エラー: アロケーション ユニット ID A_ID、ページ P_ID。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-115">Table error: alloc unit ID A_ID, page P_ID.</span></span> <span data-ttu-id="0f2fe-116">テスト (TEST) が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-116">The test (TEST) failed.</span></span> <span data-ttu-id="0f2fe-117">値は VAL1 および VAL2 です。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-117">The values are VAL1 and VAL2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0f2fe-118">説明</span><span class="sxs-lookup"><span data-stu-id="0f2fe-118">Explanation</span></span>  
 <span data-ttu-id="0f2fe-119">ページ ヘッダーの破損により、ページ *P_ID* の監査に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-119">Page *P_ID* has failed auditing due to a corruption in its page header.</span></span> <span data-ttu-id="0f2fe-120">TEST 内の文字列は、失敗した実際のテストを示します。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-120">The string in TEST gives the actual test that failed.</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="0f2fe-121">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="0f2fe-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="0f2fe-122">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="0f2fe-123">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="0f2fe-124">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="0f2fe-125">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="0f2fe-126">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="0f2fe-127">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="0f2fe-128">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="0f2fe-129">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="0f2fe-130">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="0f2fe-130">Restore from Backup</span></span>  
 <span data-ttu-id="0f2fe-131">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="0f2fe-132">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="0f2fe-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="0f2fe-133">適用不可。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-133">Not applicable.</span></span> <span data-ttu-id="0f2fe-134">このエラーを修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-134">This error cannot be repaired.</span></span> <span data-ttu-id="0f2fe-135">バックアップからデータベースを復元できない場合は、マイクロソフト カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="0f2fe-135">If you cannot restore the database from a backup, contact Microsoft Customer Service and Support (CSS).</span></span>  
  
  
