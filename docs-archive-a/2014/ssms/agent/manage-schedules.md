---
title: '[スケジュールの管理] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fa18d620d630484815966372d5de83bb52e8caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634806"
---
# <a name="manage-schedules"></a><span data-ttu-id="05217-102">[スケジュールの管理]</span><span class="sxs-lookup"><span data-stu-id="05217-102">Manage Schedules</span></span>
  <span data-ttu-id="05217-103">エージェントのジョブスケジュールのプロパティを表示および変更でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="05217-103">Allows you to view and change properties for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job schedules.</span></span>  
  
## <a name="options"></a><span data-ttu-id="05217-104">Options</span><span class="sxs-lookup"><span data-stu-id="05217-104">Options</span></span>  
 <span data-ttu-id="05217-105">**[利用可能なスケジュール]**</span><span class="sxs-lookup"><span data-stu-id="05217-105">**Available schedules**</span></span>  
 <span data-ttu-id="05217-106">このユーザーが利用可能なスケジュールの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="05217-106">Lists the schedules available for this user.</span></span> <span data-ttu-id="05217-107">ジョブの所有者とスケジュールの所有者は同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="05217-107">Notice that a job and a schedule must have the same owner.</span></span> <span data-ttu-id="05217-108">したがって、この一覧には、このジョブの所有者によって所有されているスケジュールだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="05217-108">Therefore, this list only includes schedules owned by the owner of the job.</span></span>  
  
 <span data-ttu-id="05217-109">**名前**</span><span class="sxs-lookup"><span data-stu-id="05217-109">**Name**</span></span>  
 <span data-ttu-id="05217-110">スケジュールの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="05217-110">Displays the name of the schedule.</span></span>  
  
 <span data-ttu-id="05217-111">**有効**</span><span class="sxs-lookup"><span data-stu-id="05217-111">**Enabled**</span></span>  
 <span data-ttu-id="05217-112">スケジュールを有効にするには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="05217-112">Select this option to enable the schedule.</span></span>  
  
 <span data-ttu-id="05217-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="05217-113">**Description**</span></span>  
 <span data-ttu-id="05217-114">ジョブを実行するスケジュールの条件を説明します。</span><span class="sxs-lookup"><span data-stu-id="05217-114">Describes the conditions under which the schedule runs the job.</span></span>  
  
 <span data-ttu-id="05217-115">**[スケジュール済みのジョブ]**</span><span class="sxs-lookup"><span data-stu-id="05217-115">**Jobs in schedule**</span></span>  
 <span data-ttu-id="05217-116">スケジュールにアタッチされているジョブの番号を表示します。</span><span class="sxs-lookup"><span data-stu-id="05217-116">Lists the job numbers attached to the schedule.</span></span> <span data-ttu-id="05217-117">番号をクリックすると、ジョブのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="05217-117">Click a number to view the properties of the job.</span></span>  
  
 <span data-ttu-id="05217-118">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="05217-118">**New**</span></span>  
 <span data-ttu-id="05217-119">新しいスケジュールを作成するには、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="05217-119">Click this button to create a new schedule.</span></span>  
  
 <span data-ttu-id="05217-120">**削除**</span><span class="sxs-lookup"><span data-stu-id="05217-120">**Delete**</span></span>  
 <span data-ttu-id="05217-121">選択されているスケジュールを削除するには、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="05217-121">Click this button to delete the selected schedule.</span></span>  
  
 <span data-ttu-id="05217-122">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="05217-122">**Properties**</span></span>  
 <span data-ttu-id="05217-123">選択されているスケジュールのプロパティを変更するには、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="05217-123">Click this button to change the properties of the selected schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05217-124">参照</span><span class="sxs-lookup"><span data-stu-id="05217-124">See Also</span></span>  
 [<span data-ttu-id="05217-125">スケジュールの作成とジョブへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="05217-125">Create and Attach Schedules to Jobs</span></span>](create-and-attach-schedules-to-jobs.md)  
  
  
