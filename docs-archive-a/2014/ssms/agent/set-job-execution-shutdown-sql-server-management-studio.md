---
title: ジョブ実行のシャットダウンの設定 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e60807676c3c54faf1d44de318ff0a31c2e20b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644278"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a><span data-ttu-id="edecb-102">Set Job Execution Shutdown (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="edecb-102">Set Job Execution Shutdown (SQL Server Management Studio)</span></span>
  <span data-ttu-id="edecb-103">このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でを使用して、エージェント自体が終了する前に、実行中のジョブの終了をエージェントが待機する時間を設定する方法について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="edecb-103">This topic describes how to set the time that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="edecb-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="edecb-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="edecb-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="edecb-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="edecb-106">Security</span><span class="sxs-lookup"><span data-stu-id="edecb-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="edecb-107">**SQL Server エージェント ジョブのシャットダウン時間を設定する方法:**</span><span class="sxs-lookup"><span data-stu-id="edecb-107">**To set a shutdown time for a SQL Server Agent job, using:**</span></span>  
  
     [<span data-ttu-id="edecb-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="edecb-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="edecb-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="edecb-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="edecb-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="edecb-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="edecb-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="edecb-111">Permissions</span></span>  
 <span data-ttu-id="edecb-112">既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント自体が終了する前に、実行中のジョブの終了を [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが待機する時間を設定できるのは、**sysadmin** 固定サーバー ロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="edecb-112">By default, members of the **sysadmin** fixed server role can set the time that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes.</span></span> <span data-ttu-id="edecb-113">他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="edecb-113">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="edecb-114">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="edecb-114">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="edecb-115">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="edecb-115">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="edecb-116">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="edecb-116">**SQLAgentOperatorRole**</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="edecb-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="edecb-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-job-execution-shutdown"></a><span data-ttu-id="edecb-118">ジョブ実行のシャットダウンを設定するには</span><span class="sxs-lookup"><span data-stu-id="edecb-118">To set job execution shutdown</span></span>  
  
1.  <span data-ttu-id="edecb-119">**オブジェクト エクスプ ローラー** で、プラス記号をクリックして、ジョブ実行のシャットダウン間隔を設定するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="edecb-119">In **Object Explorer,** , click the plus sign to expand the server where you want to set a job execution shutdown interval.</span></span>  
  
2.  <span data-ttu-id="edecb-120">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="edecb-120">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="edecb-121">**[ページの選択]** の **[ジョブ システム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="edecb-121">Under **Select a page**, select **Job System**.</span></span>  
  
4.  <span data-ttu-id="edecb-122">**[シャットダウン タイムアウト間隔]** (秒単位) を増やすか、または減らしてシャットダウン タイムアウト間隔を調整します。</span><span class="sxs-lookup"><span data-stu-id="edecb-122">Set the **Shutdown time-out interval** in seconds to increase or decrease the shutdown time-out interval.</span></span> <span data-ttu-id="edecb-123">この値により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント自体が終了される前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行中のジョブの終了を待機する時間が決まります。</span><span class="sxs-lookup"><span data-stu-id="edecb-123">This determines how long [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes.</span></span>  
  
  
