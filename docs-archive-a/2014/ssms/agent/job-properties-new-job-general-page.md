---
title: '[ジョブのプロパティ] と [新しいジョブ] ([全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a5d2ab84ed211a03a3c217bd5f4cd54453a4dc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715010"
---
# <a name="job-properties-and-new-job-general-page"></a><span data-ttu-id="dcca3-102">ジョブのプロパティと新しいジョブ ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="dcca3-102">Job Properties and New Job (General Page)</span></span>
  <span data-ttu-id="dcca3-103">このページを使用すると、エージェントジョブの全般プロパティを表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-103">Use this page to view and modify the general properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dcca3-104">Options</span><span class="sxs-lookup"><span data-stu-id="dcca3-104">Options</span></span>  
 <span data-ttu-id="dcca3-105">**名前**</span><span class="sxs-lookup"><span data-stu-id="dcca3-105">**Name**</span></span>  
 <span data-ttu-id="dcca3-106">ジョブの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-106">Change the name of the job.</span></span>  
  
 <span data-ttu-id="dcca3-107">**所有者**</span><span class="sxs-lookup"><span data-stu-id="dcca3-107">**Owner**</span></span>  
 <span data-ttu-id="dcca3-108">ジョブの所有者を選択します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-108">Select the owner for the job.</span></span>  
  
 <span data-ttu-id="dcca3-109">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="dcca3-109">**Category**</span></span>  
 <span data-ttu-id="dcca3-110">ジョブのカテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-110">Select the job category for the job.</span></span>  
  
 <span data-ttu-id="dcca3-111">**...**</span><span class="sxs-lookup"><span data-stu-id="dcca3-111">**...**</span></span>  
 <span data-ttu-id="dcca3-112">選択したカテゴリのジョブを表示します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-112">View the jobs in the selected category.</span></span>  
  
 <span data-ttu-id="dcca3-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="dcca3-113">**Description**</span></span>  
 <span data-ttu-id="dcca3-114">ジョブの説明を変更します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-114">Change the description of the job.</span></span>  
  
 <span data-ttu-id="dcca3-115">**有効**</span><span class="sxs-lookup"><span data-stu-id="dcca3-115">**Enabled**</span></span>  
 <span data-ttu-id="dcca3-116">ジョブを有効にします。</span><span class="sxs-lookup"><span data-stu-id="dcca3-116">Enable the job.</span></span> <span data-ttu-id="dcca3-117">ジョブが有効ではない場合、スケジュールや警告に応じてジョブが実行されることはありませんが、 **sp_start_job** ストアド プロシージャを使用して引き続きジョブを開始することができます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-117">When the job is not enabled, the job does not run in response to a schedule or an alert, although you can still start the job using the **sp_start_job** stored procedure.</span></span>  
  
 <span data-ttu-id="dcca3-118">**ソース**</span><span class="sxs-lookup"><span data-stu-id="dcca3-118">**Source**</span></span>  
 <span data-ttu-id="dcca3-119">ジョブのマスター サーバーを表示します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-119">Displays the master server for the job.</span></span> <span data-ttu-id="dcca3-120">**[ジョブのプロパティ] の [全般]** ページでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-120">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="dcca3-121">**Created**</span><span class="sxs-lookup"><span data-stu-id="dcca3-121">**Created**</span></span>  
 <span data-ttu-id="dcca3-122">ジョブが作成された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-122">Displays the date and time that the job was created.</span></span> <span data-ttu-id="dcca3-123">**[ジョブのプロパティ] の [全般]** ページでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-123">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="dcca3-124">**[最終更新]**</span><span class="sxs-lookup"><span data-stu-id="dcca3-124">**Last modified**</span></span>  
 <span data-ttu-id="dcca3-125">ジョブが最後に変更された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-125">Displays the date and time that the job was last modified.</span></span> <span data-ttu-id="dcca3-126">**[ジョブのプロパティ] の [全般]** ページでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-126">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="dcca3-127">**[最終実行]**</span><span class="sxs-lookup"><span data-stu-id="dcca3-127">**Last executed**</span></span>  
 <span data-ttu-id="dcca3-128">ジョブの最後の実行の開始日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-128">Displays the date and time that the job last started running.</span></span> <span data-ttu-id="dcca3-129">**[ジョブのプロパティ] の [全般]** ページでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-129">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="dcca3-130">**ジョブ履歴の表示**</span><span class="sxs-lookup"><span data-stu-id="dcca3-130">**View Job History**</span></span>  
 <span data-ttu-id="dcca3-131">ジョブ履歴を表示します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-131">View the job history for the job.</span></span> <span data-ttu-id="dcca3-132">**[ジョブのプロパティ] の [全般]** ページでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-132">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcca3-133">参照</span><span class="sxs-lookup"><span data-stu-id="dcca3-133">See Also</span></span>  
 <span data-ttu-id="dcca3-134">[ジョブの実装](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="dcca3-134">[Implement Jobs](implement-jobs.md) </span></span>  
 <span data-ttu-id="dcca3-135">[[ジョブ カテゴリ]:ジョブ カテゴリの管理](job-categories-manage-job-categories.md)</span><span class="sxs-lookup"><span data-stu-id="dcca3-135">[Job Categories: Manage Job Categories](job-categories-manage-job-categories.md)</span></span>  
  
  
