---
title: MSSQLSERVER_824 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d57b19bc8c837b92b65728fbb0046039b862d31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640954"
---
# <a name="mssqlserver_824"></a><span data-ttu-id="d4a2c-102">MSSQLSERVER_824</span><span class="sxs-lookup"><span data-stu-id="d4a2c-102">MSSQLSERVER_824</span></span>
    
## <a name="details"></a><span data-ttu-id="d4a2c-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d4a2c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d4a2c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d4a2c-104">Product Name</span></span>|<span data-ttu-id="d4a2c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d4a2c-105">SQL Server</span></span>|  
|<span data-ttu-id="d4a2c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d4a2c-106">Event ID</span></span>|<span data-ttu-id="d4a2c-107">824</span><span class="sxs-lookup"><span data-stu-id="d4a2c-107">824</span></span>|  
|<span data-ttu-id="d4a2c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d4a2c-108">Event Source</span></span>|<span data-ttu-id="d4a2c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d4a2c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d4a2c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d4a2c-110">Component</span></span>|<span data-ttu-id="d4a2c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d4a2c-111">SQLEngine</span></span>|  
|<span data-ttu-id="d4a2c-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d4a2c-112">Symbolic Name</span></span>|<span data-ttu-id="d4a2c-113">B_HARDSSERR</span><span class="sxs-lookup"><span data-stu-id="d4a2c-113">B_HARDSSERR</span></span>|  
|<span data-ttu-id="d4a2c-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d4a2c-114">Message Text</span></span>|<span data-ttu-id="d4a2c-115">SQL Server で、一貫性に基づいた論理 I/O エラーが検出されました: %ls。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-115">SQL Server detected a logical consistency-based I/O error: %ls.</span></span> <span data-ttu-id="d4a2c-116">このエラーは、ファイル '%ls' のオフセット %#016I64x にあるデータベース ID が %d のページ %S_PGID の %S_MSG 中に発生しました。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-116">It occurred during a %S_MSG of page %S_PGID in database ID %d at offset %#016I64x in file '%ls'.</span></span>  <span data-ttu-id="d4a2c-117">SQL Server エラー ログまたはシステム イベント ログ内の別のメッセージで詳細情報が報告されることもあります。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-117">Additional messages in the SQL Server error log or system event log may provide more detail.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d4a2c-118">説明</span><span class="sxs-lookup"><span data-stu-id="d4a2c-118">Explanation</span></span>  
 <span data-ttu-id="d4a2c-119">このエラーは、ディスクからページが正常に読み取られたことが Windows によって報告されたが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってそのページに異常が検出されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-119">This error indicates that Windows reports that the page is successfully read from disk, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has discovered something wrong with the page.</span></span> <span data-ttu-id="d4a2c-120">このエラーは、Windows によってエラーが検出されなかった点を除けば、エラー 823 と似ています。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-120">This error is similar to error 823 except that Windows did not detect the error.</span></span> <span data-ttu-id="d4a2c-121">通常は、ディスク ドライブの欠陥、ディスクのファームウェアの問題、デバイス ドライバーの障害など、I/O サブシステムに問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-121">This usually indicates a problem in the I/O subsystem, such as a failing disk drive, disk firmware problems, faulty device driver, and so on.</span></span> <span data-ttu-id="d4a2c-122">I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))」 (Microsoft SQL Server I/O の基礎 (第 2 章)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-122">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d4a2c-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d4a2c-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="d4a2c-124">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="d4a2c-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="d4a2c-125">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="d4a2c-126">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを参照して、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred because of hardware failure.</span></span> <span data-ttu-id="d4a2c-127">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d4a2c-128">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="d4a2c-129">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="d4a2c-130">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="d4a2c-131">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="d4a2c-132">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="d4a2c-133">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="d4a2c-133">Restore from Backup</span></span>  
 <span data-ttu-id="d4a2c-134">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-134">If the problem is not hardware-related and a known clean backup is available, restore the database from the backup.</span></span>  
  
 <span data-ttu-id="d4a2c-135">PAGE_VERIFY CHECKSUM オプションを使用するようにデータベースを変更することを検討します。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-135">Consider changing the databases to use the PAGE_VERIFY CHECKSUM option.</span></span> <span data-ttu-id="d4a2c-136">PAGE_VERIFY の詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4a2c-136">For information about PAGE_VERIFY, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a2c-137">参照</span><span class="sxs-lookup"><span data-stu-id="d4a2c-137">See Also</span></span>  
 [<span data-ttu-id="d4a2c-138">suspect_pages テーブルの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d4a2c-138">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
