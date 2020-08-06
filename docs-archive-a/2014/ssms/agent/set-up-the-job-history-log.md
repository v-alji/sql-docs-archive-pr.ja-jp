---
title: ジョブ履歴ログのセットアップ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb42e1daaee8a3a9e5ae9cc3c09a8cc42dcbff56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711570"
---
# <a name="set-up-the-job-history-log"></a><span data-ttu-id="e3f33-102">Set Up the Job History Log</span><span class="sxs-lookup"><span data-stu-id="e3f33-102">Set Up the Job History Log</span></span>
  <span data-ttu-id="e3f33-103">このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] エージェントのジョブ履歴ログをセットアップする方法について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e3f33-103">This topic describes how to set up the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log.</span></span>  
  
-   <span data-ttu-id="e3f33-104">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="e3f33-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="e3f33-105">**ジョブ履歴ログをセットアップする方法:**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="e3f33-105">**To setup the job history log, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e3f33-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="e3f33-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e3f33-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e3f33-107">Security</span></span>  
 <span data-ttu-id="e3f33-108">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e3f33-108">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="e3f33-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e3f33-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e3f33-110">**ジョブ履歴ログをセットアップするには**</span><span class="sxs-lookup"><span data-stu-id="e3f33-110">**To set up the job history log**</span></span>  
  
1.  <span data-ttu-id="e3f33-111">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="e3f33-111">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e3f33-112">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3f33-112">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e3f33-113">**[SQL Server エージェントのプロパティ]** ダイアログ ボックスで **[履歴]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3f33-113">In the **SQL Server Agent Properties** dialog box, select the **History** page.</span></span>  
  
4.  <span data-ttu-id="e3f33-114">次のオプションから選択します。</span><span class="sxs-lookup"><span data-stu-id="e3f33-114">Choose from the following options:</span></span>  
  
    1.  <span data-ttu-id="e3f33-115">**[ジョブ履歴ログのサイズを制限する]** チェック ボックスをオンにして、ジョブ履歴ログの最大行数と、ジョブあたりの最大行数を入力します。</span><span class="sxs-lookup"><span data-stu-id="e3f33-115">Check **Limit size of job history log**, and then type the maximum number of rows for the job history log, and the maximum number of rows per job.</span></span>  
  
    2.  <span data-ttu-id="e3f33-116">**[自動的にエージェントの履歴を削除する]** チェック ボックスをオンにして、期間を指定します。この期間を過ぎると、履歴がログから削除されます。</span><span class="sxs-lookup"><span data-stu-id="e3f33-116">Check **Automatically remove agent history**, and specify a time period, such that history older than this period will be purged from the log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f33-117">参照</span><span class="sxs-lookup"><span data-stu-id="e3f33-117">See Also</span></span>  
 <span data-ttu-id="e3f33-118">[ジョブの実装](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="e3f33-118">[Implement Jobs](implement-jobs.md) </span></span>  
 <span data-ttu-id="e3f33-119">[ジョブの利用状況の監視](monitor-job-activity.md) </span><span class="sxs-lookup"><span data-stu-id="e3f33-119">[Monitor Job Activity](monitor-job-activity.md) </span></span>  
 [<span data-ttu-id="e3f33-120">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="e3f33-120">Create Jobs</span></span>](create-jobs.md)  
  
  
