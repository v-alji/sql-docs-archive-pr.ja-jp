---
title: MSSQLSERVER_5228 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5228 (Database Engine error)
ms.assetid: 5e83c617-4aa2-4755-bcc5-a798c46b97e4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eef59e62f00a44aad7bfefb1719a6d8d2b3d0290
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631978"
---
# <a name="mssqlserver_5228"></a><span data-ttu-id="2e708-102">MSSQLSERVER_5228</span><span class="sxs-lookup"><span data-stu-id="2e708-102">MSSQLSERVER_5228</span></span>
    
## <a name="details"></a><span data-ttu-id="2e708-103">詳細</span><span class="sxs-lookup"><span data-stu-id="2e708-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e708-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2e708-104">Product Name</span></span>|<span data-ttu-id="2e708-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2e708-105">SQL Server</span></span>|  
|<span data-ttu-id="2e708-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2e708-106">Event ID</span></span>|<span data-ttu-id="2e708-107">5228</span><span class="sxs-lookup"><span data-stu-id="2e708-107">5228</span></span>|  
|<span data-ttu-id="2e708-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2e708-108">Event Source</span></span>|<span data-ttu-id="2e708-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2e708-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2e708-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2e708-110">Component</span></span>|<span data-ttu-id="2e708-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2e708-111">SQLEngine</span></span>|  
|<span data-ttu-id="2e708-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="2e708-112">Symbolic Name</span></span>|<span data-ttu-id="2e708-113">DBCC4_ANTIMATTER_COLUMN_DETECTED</span><span class="sxs-lookup"><span data-stu-id="2e708-113">DBCC4_ANTIMATTER_COLUMN_DETECTED</span></span>|  
|<span data-ttu-id="2e708-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2e708-114">Message Text</span></span>|<span data-ttu-id="2e708-115">テーブル エラー:オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE)、ページ PG_ID、行 R_ID。</span><span class="sxs-lookup"><span data-stu-id="2e708-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), page PG_ID, row R_ID.</span></span> <span data-ttu-id="2e708-116">DBCC により、オンラインのインデックス構築操作で不完全なクリーンアップが検出されました。</span><span class="sxs-lookup"><span data-stu-id="2e708-116">DBCC detected incomplete cleanup from an online index build operation.</span></span> <span data-ttu-id="2e708-117">(問題のある列の値は VALUE です)。</span><span class="sxs-lookup"><span data-stu-id="2e708-117">(Antimatter column value is VALUE.)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2e708-118">説明</span><span class="sxs-lookup"><span data-stu-id="2e708-118">Explanation</span></span>  
 <span data-ttu-id="2e708-119">オブジェクト *O_ID*、インデックス *I_ID*、およびパーティション *PN_ID* に対して完了していないオンライン インデックス構築が検出されました。</span><span class="sxs-lookup"><span data-stu-id="2e708-119">An unfinished online index build was detected for object *O_ID*, index *I_ID*, and partition *PN_ID*.</span></span> <span data-ttu-id="2e708-120">この現象は、問題のある列が行 *R_ID* に存在することによって生じます。</span><span class="sxs-lookup"><span data-stu-id="2e708-120">This is manifested by the presence of an antimatter column on the row *R_ID*.</span></span> <span data-ttu-id="2e708-121">問題のある列は、オンライン インデックスの構築時に複数のソースからのレコードを調整するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="2e708-121">An antimatter column is used when reconciling records from multiple sources during an online index build.</span></span> <span data-ttu-id="2e708-122">このエラー メッセージには、問題のある列の値も示されます。</span><span class="sxs-lookup"><span data-stu-id="2e708-122">The error message also indicates the value of the antimatter column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2e708-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2e708-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="2e708-124">ハードウェア障害を調査する</span><span class="sxs-lookup"><span data-stu-id="2e708-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="2e708-125">ハードウェアの診断を実行し、問題があれば修正します。</span><span class="sxs-lookup"><span data-stu-id="2e708-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="2e708-126">また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="2e708-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="2e708-127">ログに記録されているハードウェアに関する問題があれば、それを修正します。</span><span class="sxs-lookup"><span data-stu-id="2e708-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="2e708-128">データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="2e708-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="2e708-129">システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2e708-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="2e708-130">書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="2e708-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="2e708-131">それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。</span><span class="sxs-lookup"><span data-stu-id="2e708-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="2e708-132">導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2e708-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="2e708-133">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="2e708-133">Restore from Backup</span></span>  
 <span data-ttu-id="2e708-134">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="2e708-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="2e708-135">DBCC CHECKDB の実行</span><span class="sxs-lookup"><span data-stu-id="2e708-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="2e708-136">クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。</span><span class="sxs-lookup"><span data-stu-id="2e708-136">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="2e708-137">DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、</span><span class="sxs-lookup"><span data-stu-id="2e708-137">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="2e708-138">適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。</span><span class="sxs-lookup"><span data-stu-id="2e708-138">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2e708-139">REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="2e708-139">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="2e708-140">いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="2e708-140">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="2e708-141">REPAIR オプションの実行結果</span><span class="sxs-lookup"><span data-stu-id="2e708-141">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="2e708-142">REPAIR を実行すると、指定されたインデックスとそのすべての依存インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="2e708-142">Running REPAIR will cause the specified index and all its dependent indexes to be rebuilt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e708-143">参照</span><span class="sxs-lookup"><span data-stu-id="2e708-143">See Also</span></span>  
 [<span data-ttu-id="2e708-144">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e708-144">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
