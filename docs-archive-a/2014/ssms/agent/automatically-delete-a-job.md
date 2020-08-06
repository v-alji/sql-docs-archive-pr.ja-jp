---
title: ジョブを自動的に削除する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- dropping jobs
- SQL Server Agent jobs, removing
- automatic job removal
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 92dbb6da-5919-4bde-9354-d454e9ea3da0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07a10ec4a31d553a548bfecdcba426e3b46a1782
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642510"
---
# <a name="automatically-delete-a-job"></a><span data-ttu-id="c7bc0-102">Automatically Delete a Job</span><span class="sxs-lookup"><span data-stu-id="c7bc0-102">Automatically Delete a Job</span></span>
  <span data-ttu-id="c7bc0-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、または SQL Server 管理オブジェクトを使用して、ジョブの成功時、失敗時、または完了時にジョブが自動的に削除されるようにエージェントを構成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to automatically delete jobs when they succeed, fail, or complete by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="c7bc0-104">ジョブ応答により、データベース管理者はジョブの完了日時や実行頻度を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="c7bc0-105">以下に、一般的なジョブ応答を示します。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="c7bc0-106">電子メール、ポケットベル、または **net send** メッセージによってオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span>  
  
     <span data-ttu-id="c7bc0-107">オペレーターが事後の作業を実行する必要がある場合に、これらのジョブ応答のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="c7bc0-108">たとえば、バックアップ ジョブが正常に終了した場合、オペレーターは、バックアップ テープを取り出して、安全な場所に保管するように通知を受ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="c7bc0-109">Windows アプリケーション ログにイベント メッセージを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-109">Writing an event message to the Windows application log.</span></span>  
  
     <span data-ttu-id="c7bc0-110">この応答は、失敗したジョブに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="c7bc0-111">ジョブを自動的に削除します。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-111">Automatically deleting the job.</span></span>  
  
     <span data-ttu-id="c7bc0-112">このジョブを再実行する必要がないことが明らかな場合に、このジョブ応答を使用します。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
 <span data-ttu-id="c7bc0-113">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c7bc0-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c7bc0-114">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c7bc0-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c7bc0-115">Security</span><span class="sxs-lookup"><span data-stu-id="c7bc0-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c7bc0-116">**ジョブ応答を指定する方法:**</span><span class="sxs-lookup"><span data-stu-id="c7bc0-116">**To specify job responses, using:**</span></span>  
  
     [<span data-ttu-id="c7bc0-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c7bc0-117">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="c7bc0-118">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c7bc0-118">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c7bc0-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="c7bc0-119">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c7bc0-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c7bc0-120">Security</span></span>  
 <span data-ttu-id="c7bc0-121">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="c7bc0-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c7bc0-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-automatically-delete-a-job"></a><span data-ttu-id="c7bc0-123">ジョブを自動的に削除するには</span><span class="sxs-lookup"><span data-stu-id="c7bc0-123">To automatically delete a job</span></span>  
  
1.  <span data-ttu-id="c7bc0-124">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c7bc0-125">**[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。次に、編集するジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="c7bc0-126">**[通知]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-126">Select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="c7bc0-127">**[自動的にジョブを削除]** チェック ボックスをオンにし、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-127">Check **Automatically delete job**, and choose one of the following:</span></span>  
  
    -   <span data-ttu-id="c7bc0-128">ジョブが正常に完了したときにジョブの状態を削除する場合は、 **[ジョブ成功時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-128">Click **When the job succeeds** to delete the job status when it has completed successfully.</span></span>  
  
    -   <span data-ttu-id="c7bc0-129">ジョブが正常に完了しなかったときにジョブを削除する場合は、 **[ジョブ失敗時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-129">Click **When the job fails** to delete the job when it has completed unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="c7bc0-130">完了時の状態にかかわらずジョブを削除する場合は、 **[ジョブ完了時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-130">Click **When the job completes** to delete the job regardless of completion status.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="c7bc0-131">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="c7bc0-131">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="c7bc0-132">**ジョブを自動的に削除するには**</span><span class="sxs-lookup"><span data-stu-id="c7bc0-132">**To automatically delete a job**</span></span>  
  
 <span data-ttu-id="c7bc0-133">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `DeleteLevel` クラスの `Job` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-133">Use the `DeleteLevel` property of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="c7bc0-134">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-134">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
