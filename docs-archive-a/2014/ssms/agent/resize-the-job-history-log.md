---
title: ジョブ履歴ログのサイズの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4c25cc43295d47b2bc19d48b5b257dbbe6bcfe9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634783"
---
# <a name="resize-the-job-history-log"></a><span data-ttu-id="08d08-102">Resize the Job History Log</span><span class="sxs-lookup"><span data-stu-id="08d08-102">Resize the Job History Log</span></span>
  <span data-ttu-id="08d08-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、を使用して、でエージェントのジョブ履歴ログのサイズ制限を設定する方法について説明し [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="08d08-103">This topic describes how to set size limits for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history logs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="08d08-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="08d08-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="08d08-105">Security</span><span class="sxs-lookup"><span data-stu-id="08d08-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="08d08-106">**ジョブ履歴ログのサイズ制限を設定する方法:**</span><span class="sxs-lookup"><span data-stu-id="08d08-106">**To set size limits for job history logs, using:**</span></span>  
  
     [<span data-ttu-id="08d08-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="08d08-107">SQL Server Management Studio</span></span>](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="08d08-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="08d08-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="08d08-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="08d08-109">Security</span></span>  
 <span data-ttu-id="08d08-110">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08d08-110">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="08d08-111">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="08d08-111">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a><span data-ttu-id="08d08-112">生のサイズに基づいてジョブ履歴ログのサイズを変更するには</span><span class="sxs-lookup"><span data-stu-id="08d08-112">To resize the job history log based on raw size</span></span>  
  
1.  <span data-ttu-id="08d08-113">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="08d08-113">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="08d08-114">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d08-114">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="08d08-115">**[履歴]** ページを選択し、 **[ジョブ履歴ログのサイズを制限する]** チェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="08d08-115">Select the **History** page, and then confirm that **Limit size of job history log**is checked.</span></span>  
  
4.  <span data-ttu-id="08d08-116">**[ジョブ履歴ログの最大サイズ (行)]** ボックスで、ジョブ履歴ログに使用できる最大行数を入力します。</span><span class="sxs-lookup"><span data-stu-id="08d08-116">In the **Maximum job history log size** box, enter the maximum number of rows the job history log should allow.</span></span>  
  
5.  <span data-ttu-id="08d08-117">**[ジョブごとのジョブ履歴の最大行数]** ボックスで、1 つのジョブに使用できるジョブ履歴の最大行数を入力します。</span><span class="sxs-lookup"><span data-stu-id="08d08-117">In the **Maximum job history rows per job** box, enter the maximum number of job history rows to allow for a job.</span></span>  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a><span data-ttu-id="08d08-118">時間に基づいてジョブ履歴ログのサイズを変更するには</span><span class="sxs-lookup"><span data-stu-id="08d08-118">To resize the job history log based on time</span></span>  
  
1.  <span data-ttu-id="08d08-119">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="08d08-119">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="08d08-120">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d08-120">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="08d08-121">**[履歴]** ページを選択し、 **[自動的にエージェントの履歴を削除する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="08d08-121">Select the **History** page, and then click **Automatically remove agent history**.</span></span>  
  
4.  <span data-ttu-id="08d08-122">適切な **[日]**、 **[週]**、または **[月]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="08d08-122">Select the appropriate number of **Days(s)**, **Week(s)**, or **Month(s)**.</span></span>  
  
  
