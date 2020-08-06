---
title: マークされたトランザクションへのデータベースの復元 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8de9ef5bed389f020f14e60ccd99f39698e7110f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643430"
---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a><span data-ttu-id="7554e-102">マークされたトランザクションへのデータベースの復元 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7554e-102">Restore a Database to a Marked Transaction (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7554e-103">データベースが復元中の状態である場合、 **[トランザクション ログの復元]** ダイアログ ボックスを使用して、使用可能なログ バックアップのマークされたトランザクションにデータベースを復元できます。</span><span class="sxs-lookup"><span data-stu-id="7554e-103">When a database is in the restoring state, you can use the **Restore Transaction Log** dialog box to restore the database to a marked transaction in the available log backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7554e-104">詳細については、「[マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル#41;](use-marked-transactions-to-recover-related-databases-consistently.md)」および「[マークされたトランザクションを含む関連データベースの復旧](recovery-of-related-databases-that-contain-marked-transaction.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7554e-104">For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) and [Recovery of Related  Databases That Contain Marked Transaction](recovery-of-related-databases-that-contain-marked-transaction.md).</span></span>  
  
### <a name="to-restore-a-marked-transaction"></a><span data-ttu-id="7554e-105">マークされたトランザクションを復元するには</span><span class="sxs-lookup"><span data-stu-id="7554e-105">To restore a marked transaction</span></span>  
  
1.  <span data-ttu-id="7554e-106">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7554e-106">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="7554e-107">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="7554e-107">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="7554e-108">データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7554e-108">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="7554e-109">**[トランザクション ログ]** をクリックして **[トランザクション ログの復元]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="7554e-109">Click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.</span></span>  
  
5.  <span data-ttu-id="7554e-110">**[全般]** ページの **[復元先]** で、 **[マークされたトランザクション]** をクリックします。 **[マークされたトランザクションの選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="7554e-110">On the **General** page, in the **Restore To** section, select **Marked transaction**, which opens the **Select Marked Transaction** dialog box.</span></span> <span data-ttu-id="7554e-111">このダイアログ ボックスには、選択したトランザクション ログ バックアップで使用できるマークされたトランザクションを一覧表示するグリッドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7554e-111">This dialog box displays a grid listing the marked transactions available in the selected transaction log backups.</span></span>  
  
     <span data-ttu-id="7554e-112">既定では、マークされたトランザクションの前まで復元され、マークされたトランザクションは復元されません。</span><span class="sxs-lookup"><span data-stu-id="7554e-112">By default, the restore is up to, but excluding, the marked transaction.</span></span> <span data-ttu-id="7554e-113">マークされたトランザクションも復元するには、 **[マークされたトランザクションを含める]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7554e-113">To restore the marked transaction also, select **Include marked transaction**.</span></span>  
  
     <span data-ttu-id="7554e-114">次の表は、グリッドの列ヘッダーとその値を示しています。</span><span class="sxs-lookup"><span data-stu-id="7554e-114">The following table lists the column headers of the grid and describes their values.</span></span>  
  
    |<span data-ttu-id="7554e-115">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="7554e-115">Header</span></span>|<span data-ttu-id="7554e-116">値</span><span class="sxs-lookup"><span data-stu-id="7554e-116">Value</span></span>|  
    |------------|-----------|  
    |\<blank>|<span data-ttu-id="7554e-117">マークを選択するためのチェック ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="7554e-117">Displays a checkbox for selecting the mark.</span></span>|  
    |<span data-ttu-id="7554e-118">**トランザクション マーク**</span><span class="sxs-lookup"><span data-stu-id="7554e-118">**Transaction Mark**</span></span>|<span data-ttu-id="7554e-119">トランザクションがコミットされたときにユーザーによって指定された、マークされたトランザクションの名前。</span><span class="sxs-lookup"><span data-stu-id="7554e-119">Name of the marked transaction specified by the user when the transaction was committed.</span></span>|  
    |<span data-ttu-id="7554e-120">**Date**</span><span class="sxs-lookup"><span data-stu-id="7554e-120">**Date**</span></span>|<span data-ttu-id="7554e-121">トランザクションがコミットされた日時。</span><span class="sxs-lookup"><span data-stu-id="7554e-121">Date and time of the transaction when it was committed.</span></span> <span data-ttu-id="7554e-122">トランザクションの日付と時刻は、クライアント コンピューターの日付と時刻ではなく、 **msdbgmarkhistory** テーブルに記録されたとおりに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7554e-122">Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.</span></span>|  
    |<span data-ttu-id="7554e-123">**説明**</span><span class="sxs-lookup"><span data-stu-id="7554e-123">**Description**</span></span>|<span data-ttu-id="7554e-124">トランザクションがコミットされたときにユーザーが指定したマークされたトランザクションの説明 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="7554e-124">Description of marked transaction specified by the user when the transaction was committed (if any).</span></span>|  
    |<span data-ttu-id="7554e-125">**LSN (LSN)**</span><span class="sxs-lookup"><span data-stu-id="7554e-125">**LSN**</span></span>|<span data-ttu-id="7554e-126">マークされたトランザクションのログ シーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="7554e-126">Log sequence number of the marked transaction.</span></span>|  
    |<span data-ttu-id="7554e-127">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="7554e-127">**Database**</span></span>|<span data-ttu-id="7554e-128">マークされたトランザクションがコミットされたデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="7554e-128">Name of the database where the marked transaction was committed.</span></span>|  
    |<span data-ttu-id="7554e-129">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="7554e-129">**User Name**</span></span>|<span data-ttu-id="7554e-130">マークされたトランザクションをコミットしたデータベース ユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="7554e-130">Name of the database user who committed the marked transaction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7554e-131">参照</span><span class="sxs-lookup"><span data-stu-id="7554e-131">See Also</span></span>  
 <span data-ttu-id="7554e-132">[データベースバックアップを復元する &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="7554e-132">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 [<span data-ttu-id="7554e-133">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7554e-133">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
  
