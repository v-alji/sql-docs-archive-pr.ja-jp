---
title: ジョブ応答の指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d41c5e1552a1ff16343bdb2c4e9feaafb51c5783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711574"
---
# <a name="specify-job-responses"></a><span data-ttu-id="66e76-102">ジョブ応答の指定</span><span class="sxs-lookup"><span data-stu-id="66e76-102">Specify Job Responses</span></span>
  <span data-ttu-id="66e76-103">ジョブ応答では、ジョブの完了後に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスで実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="66e76-103">Job responses specify actions that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service will take after a job completes.</span></span> <span data-ttu-id="66e76-104">ジョブ応答により、データベース管理者はジョブの完了日時や実行頻度を確認できます。</span><span class="sxs-lookup"><span data-stu-id="66e76-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="66e76-105">以下に、一般的なジョブ応答を示します。</span><span class="sxs-lookup"><span data-stu-id="66e76-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="66e76-106">電子メール、ポケットベル、または **net send** メッセージによってオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="66e76-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span>  
  
     <span data-ttu-id="66e76-107">オペレーターが事後の作業を実行する必要がある場合に、これらのジョブ応答のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="66e76-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="66e76-108">たとえば、バックアップ ジョブが正常に終了した場合、オペレーターは、バックアップ テープを取り出して、安全な場所に保管するように通知を受ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="66e76-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="66e76-109">Windows アプリケーション ログにイベント メッセージを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="66e76-109">Writing an event message to the Windows application log.</span></span>  
  
     <span data-ttu-id="66e76-110">この応答は、失敗したジョブに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="66e76-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="66e76-111">ジョブを自動的に削除します。</span><span class="sxs-lookup"><span data-stu-id="66e76-111">Automatically deleting the job.</span></span>  
  
     <span data-ttu-id="66e76-112">このジョブを再実行する必要がないことが明らかな場合に、このジョブ応答を使用します。</span><span class="sxs-lookup"><span data-stu-id="66e76-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="66e76-113">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="66e76-113">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66e76-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="66e76-114">**Description**</span></span>|<span data-ttu-id="66e76-115">**トピック**</span><span class="sxs-lookup"><span data-stu-id="66e76-115">**Topic**</span></span>|  
|<span data-ttu-id="66e76-116">オペレーターにジョブの状態を通知する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66e76-116">Describes how to notify an operator of job status.</span></span>|[<span data-ttu-id="66e76-117">Notify an Operator of Job Status</span><span class="sxs-lookup"><span data-stu-id="66e76-117">Notify an Operator of Job Status</span></span>](notify-an-operator-of-job-status.md)|  
|<span data-ttu-id="66e76-118">ジョブの状態を Windows アプリケーション ログに書き込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66e76-118">Describes how to write job status to the Windows application log.</span></span>|[<span data-ttu-id="66e76-119">Write the Job Status to the Windows Application Log</span><span class="sxs-lookup"><span data-stu-id="66e76-119">Write the Job Status to the Windows Application Log</span></span>](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="66e76-120">参照</span><span class="sxs-lookup"><span data-stu-id="66e76-120">See Also</span></span>  
 [<span data-ttu-id="66e76-121">イベントの監視と応答</span><span class="sxs-lookup"><span data-stu-id="66e76-121">Monitor and Respond to Events</span></span>](monitor-and-respond-to-events.md)  
  
  
