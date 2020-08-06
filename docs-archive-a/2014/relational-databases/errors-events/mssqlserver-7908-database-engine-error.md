---
title: MSSQLSERVER_7908 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7908 (Database Engine error)
ms.assetid: 470045b0-ebe9-44a7-b456-480e7a516a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b80812e0e36e5bed542f7193b7422f2de37720f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640962"
---
# <a name="mssqlserver_7908"></a><span data-ttu-id="649a4-102">MSSQLSERVER_7908</span><span class="sxs-lookup"><span data-stu-id="649a4-102">MSSQLSERVER_7908</span></span>
    
## <a name="details"></a><span data-ttu-id="649a4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="649a4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="649a4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="649a4-104">Product Name</span></span>|<span data-ttu-id="649a4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="649a4-105">SQL Server</span></span>|  
|<span data-ttu-id="649a4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="649a4-106">Event ID</span></span>|<span data-ttu-id="649a4-107">7908</span><span class="sxs-lookup"><span data-stu-id="649a4-107">7908</span></span>|  
|<span data-ttu-id="649a4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="649a4-108">Event Source</span></span>|<span data-ttu-id="649a4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="649a4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="649a4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="649a4-110">Component</span></span>|<span data-ttu-id="649a4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="649a4-111">SQLEngine</span></span>|  
|<span data-ttu-id="649a4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="649a4-112">Symbolic Name</span></span>|<span data-ttu-id="649a4-113">DBCC2_FS_INVALID_COLUMN_LEVEL_FILE</span><span class="sxs-lookup"><span data-stu-id="649a4-113">DBCC2_FS_INVALID_COLUMN_LEVEL_FILE</span></span>|  
|<span data-ttu-id="649a4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="649a4-114">Message Text</span></span>|<span data-ttu-id="649a4-115">テーブル エラー:パーティション ID PN_ID のファイル 'FILE' は有効な FileStream ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="649a4-115">Table error: The file 'FILE' in partition ID PN_ID is not a valid Filestream file.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="649a4-116">説明</span><span class="sxs-lookup"><span data-stu-id="649a4-116">Explanation</span></span>  
 <span data-ttu-id="649a4-117">列ディレクトリにある FILESTREAM ファイルの名前は ROWGUID です。</span><span class="sxs-lookup"><span data-stu-id="649a4-117">The name of a FILESTREAM file in a column directory is a ROWGUID.</span></span> <span data-ttu-id="649a4-118">列ディレクトリにあるファイル名を ROWGUID に変換できない場合、そのファイルは有効なファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="649a4-118">If a file name in a column directory cannot be converted to a ROWGUID, the file is not a valid file.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="649a4-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="649a4-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="649a4-120">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="649a4-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="649a4-121">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="649a4-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="649a4-122">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="649a4-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="649a4-123">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="649a4-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="649a4-124">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="649a4-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="649a4-125">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="649a4-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="649a4-126">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="649a4-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="649a4-127">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="649a4-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="649a4-128">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="649a4-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="649a4-129">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="649a4-129">Restore from Backup</span></span>  
 <span data-ttu-id="649a4-130">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="649a4-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="649a4-131">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="649a4-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="649a4-132">適用不可。</span><span class="sxs-lookup"><span data-stu-id="649a4-132">Not applicable.</span></span> <span data-ttu-id="649a4-133">このエラーを修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="649a4-133">This error cannot be repaired.</span></span> <span data-ttu-id="649a4-134">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="649a4-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
