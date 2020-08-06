---
title: 'ジョブのプロパティ: [新しいジョブ] ([通知] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30eca88943b48bd81bd38e236711d19ee7ec4503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632258"
---
# <a name="job-properties-new-job-notifications-page"></a><span data-ttu-id="2761d-102">[ジョブのプロパティ]:[新しいジョブ] ([通知] ページ)</span><span class="sxs-lookup"><span data-stu-id="2761d-102">Job Properties: New Job (Notifications Page)</span></span>
  <span data-ttu-id="2761d-103">このページを使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と、ジョブの完了時にエージェントが実行するアクションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="2761d-103">Use this page to set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2761d-104">Options</span><span class="sxs-lookup"><span data-stu-id="2761d-104">Options</span></span>  
 <span data-ttu-id="2761d-105">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="2761d-105">**E-mail**</span></span>  
 <span data-ttu-id="2761d-106">このオプションを選択すると、ジョブの完了時に電子メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="2761d-106">Select this option to send e-mail when the job completes.</span></span> <span data-ttu-id="2761d-107">このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から選択します。</span><span class="sxs-lookup"><span data-stu-id="2761d-107">After selecting this option, choose the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="2761d-108">**ページ**</span><span class="sxs-lookup"><span data-stu-id="2761d-108">**Page**</span></span>  
 <span data-ttu-id="2761d-109">このオプションを選択すると、ジョブの完了時にオペレーターのポケットベルに電子メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="2761d-109">Select this option to send e-mail to an operator's pager when the job completes.</span></span> <span data-ttu-id="2761d-110">このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から指定します。</span><span class="sxs-lookup"><span data-stu-id="2761d-110">After selecting this option, specify the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="2761d-111">**Net send**</span><span class="sxs-lookup"><span data-stu-id="2761d-111">**Net send**</span></span>  
 <span data-ttu-id="2761d-112">このオプションを選択すると、ジョブの完了時に Net Send を使用してオペレーターに通知が送られます。</span><span class="sxs-lookup"><span data-stu-id="2761d-112">Select this option to use net send to notify an operator when the job completes.</span></span> <span data-ttu-id="2761d-113">このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から指定します。</span><span class="sxs-lookup"><span data-stu-id="2761d-113">After selecting this option, specify the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="2761d-114">**[Windows アプリケーション イベント ログに書き込む]**</span><span class="sxs-lookup"><span data-stu-id="2761d-114">**Write to the Windows Application event log**</span></span>  
 <span data-ttu-id="2761d-115">このオプションを選択すると、ジョブの完了時にアプリケーション イベント ログにエントリが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="2761d-115">Select this option to write an entry in the application event log when the job completes.</span></span> <span data-ttu-id="2761d-116">このオプションを選択した後、エントリの書き込みを実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から選択します。</span><span class="sxs-lookup"><span data-stu-id="2761d-116">After selecting this option, specify the condition that will cause the entry to be written: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="2761d-117">**[自動的にジョブを削除]**</span><span class="sxs-lookup"><span data-stu-id="2761d-117">**Automatically delete job**</span></span>  
 <span data-ttu-id="2761d-118">このオプションを選択すると、ジョブの完了時にジョブが削除されます。</span><span class="sxs-lookup"><span data-stu-id="2761d-118">Select this option to delete the job when the job completes.</span></span> <span data-ttu-id="2761d-119">このオプションを選択した後、ジョブの削除を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から選択します。</span><span class="sxs-lookup"><span data-stu-id="2761d-119">After selecting this option, specify the condition that will trigger deletion of the job: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2761d-120">参照</span><span class="sxs-lookup"><span data-stu-id="2761d-120">See Also</span></span>  
 <span data-ttu-id="2761d-121">[ジョブの実装](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="2761d-121">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="2761d-122">データベース メールを使用するように SQL Server エージェント メールを構成する</span><span class="sxs-lookup"><span data-stu-id="2761d-122">Configure SQL Server Agent Mail to Use Database Mail</span></span>](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
