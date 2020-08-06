---
title: '[ジョブ転送タスクエディター] ([ジョブ] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d2d506da6997965e40d66521f7dccb8218e165fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646215"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a><span data-ttu-id="1de6e-102">[ジョブ転送タスク エディター] ([ジョブ] ページ)</span><span class="sxs-lookup"><span data-stu-id="1de6e-102">Transfer Jobs Task Editor (Jobs Page)</span></span>
  <span data-ttu-id="1de6e-103">**[ジョブ転送タスク エディター]** ダイアログ ボックスの **[ジョブ]** ページを使用すると、1 つ以上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ジョブを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つのインスタンスから別のインスタンスにコピーするためのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1de6e-103">Use the **Jobs** page of the **Transfer Jobs Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="1de6e-104">ジョブ転送タスクの詳細については、「 [Transfer Jobs Task](control-flow/transfer-jobs-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1de6e-104">For more information about the Transfer Jobs task, see [Transfer Jobs Task](control-flow/transfer-jobs-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1de6e-105">コピー元サーバーのジョブにアクセスするには、少なくともサーバーの **SQLAgentUserRole** 固定データベース ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="1de6e-105">To access jobs on the source server, users must be a member of at least the **SQLAgentUserRole** fixed database role on the server.</span></span> <span data-ttu-id="1de6e-106">コピー先サーバーでジョブを正常に作成するには、 **sysadmin** 固定サーバー ロールのメンバーであるか、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント固定データベース ロールの 1 つであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="1de6e-106">To successfully create jobs on the destination server, the user must be a member of the **sysadmin** fixed server role or one of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles.</span></span> <span data-ttu-id="1de6e-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント固定データベース ロールおよびその権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../ssms/agent/sql-server-agent-fixed-database-roles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1de6e-107">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles and their permissions, see [SQL Server Agent Fixed Database Roles](../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1de6e-108">オプション</span><span class="sxs-lookup"><span data-stu-id="1de6e-108">Options</span></span>  
 <span data-ttu-id="1de6e-109">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="1de6e-109">**SourceConnection**</span></span>  
 <span data-ttu-id="1de6e-110">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送元サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1de6e-110">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="1de6e-111">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="1de6e-111">**DestinationConnection**</span></span>  
 <span data-ttu-id="1de6e-112">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送先サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1de6e-112">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="1de6e-113">**[TransferAllJobs]**</span><span class="sxs-lookup"><span data-stu-id="1de6e-113">**TransferAllJobs**</span></span>  
 <span data-ttu-id="1de6e-114">コピー元サーバーからコピー先サーバーにすべてコピーするか、指定の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ジョブのみをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="1de6e-114">Select whether the task should copy all or only the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs from the source to the destination server.</span></span>  
  
 <span data-ttu-id="1de6e-115">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1de6e-115">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="1de6e-116">値</span><span class="sxs-lookup"><span data-stu-id="1de6e-116">Value</span></span>|<span data-ttu-id="1de6e-117">説明</span><span class="sxs-lookup"><span data-stu-id="1de6e-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1de6e-118">**True** にします</span><span class="sxs-lookup"><span data-stu-id="1de6e-118">**True**</span></span>|<span data-ttu-id="1de6e-119">すべてのジョブをコピーします。</span><span class="sxs-lookup"><span data-stu-id="1de6e-119">Copy all jobs.</span></span>|  
|<span data-ttu-id="1de6e-120">**False**</span><span class="sxs-lookup"><span data-stu-id="1de6e-120">**False**</span></span>|<span data-ttu-id="1de6e-121">指定のジョブのみをコピーします。</span><span class="sxs-lookup"><span data-stu-id="1de6e-121">Copy only the specified jobs.</span></span>|  
  
 <span data-ttu-id="1de6e-122">**[JobsList]**</span><span class="sxs-lookup"><span data-stu-id="1de6e-122">**JobsList**</span></span>  
 <span data-ttu-id="1de6e-123">**[...]** ボタンをクリックして、コピーするジョブを選択します。</span><span class="sxs-lookup"><span data-stu-id="1de6e-123">Click the browse button **(...)** to select the jobs to copy.</span></span> <span data-ttu-id="1de6e-124">少なくとも 1 つのジョブを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1de6e-124">At least one job must be selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1de6e-125">コピーするジョブを選択する前に **[SourceConnection]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="1de6e-125">Specify the **SourceConnection** before selecting jobs to copy.</span></span>  
  
 <span data-ttu-id="1de6e-126">**[JobsList]** オプションは、 **[TransferAllJobs]** が **[True]** に設定されている場合は使用できません。</span><span class="sxs-lookup"><span data-stu-id="1de6e-126">The **JobsList** option is unavailable when **TransferAllJobs** is set to **True**.</span></span>  
  
 <span data-ttu-id="1de6e-127">**[IfObjectExists]**</span><span class="sxs-lookup"><span data-stu-id="1de6e-127">**IfObjectExists**</span></span>  
 <span data-ttu-id="1de6e-128">コピー先サーバーに既に存在する名前と同じ名前のジョブをどのように処理するかを選択します。</span><span class="sxs-lookup"><span data-stu-id="1de6e-128">Select how the task should handle jobs of the same name that already exist on the destination server.</span></span>  
  
 <span data-ttu-id="1de6e-129">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1de6e-129">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="1de6e-130">値</span><span class="sxs-lookup"><span data-stu-id="1de6e-130">Value</span></span>|<span data-ttu-id="1de6e-131">説明</span><span class="sxs-lookup"><span data-stu-id="1de6e-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1de6e-132">**[FailTask]**</span><span class="sxs-lookup"><span data-stu-id="1de6e-132">**FailTask**</span></span>|<span data-ttu-id="1de6e-133">ジョブの名前がコピー先サーバーに既に存在する名前と同じである場合、タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="1de6e-133">Task fails if jobs of the same name already exist on the destination server.</span></span>|  
|<span data-ttu-id="1de6e-134">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="1de6e-134">**Overwrite**</span></span>|<span data-ttu-id="1de6e-135">コピー先サーバーの同じ名前のジョブを上書きします。</span><span class="sxs-lookup"><span data-stu-id="1de6e-135">Task overwrites jobs of the same name on the destination server.</span></span>|  
|<span data-ttu-id="1de6e-136">**Skip**</span><span class="sxs-lookup"><span data-stu-id="1de6e-136">**Skip**</span></span>|<span data-ttu-id="1de6e-137">コピー先サーバーの同じ名前のジョブをスキップします。</span><span class="sxs-lookup"><span data-stu-id="1de6e-137">Task skips jobs of the same name that exist on the destination server.</span></span>|  
  
 <span data-ttu-id="1de6e-138">**[EnableJobsAtDestination]**</span><span class="sxs-lookup"><span data-stu-id="1de6e-138">**EnableJobsAtDestination**</span></span>  
 <span data-ttu-id="1de6e-139">コピー先サーバーにコピーされたジョブを有効にするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="1de6e-139">Select whether the jobs copied to the destination server should be enabled.</span></span>  
  
 <span data-ttu-id="1de6e-140">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1de6e-140">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="1de6e-141">値</span><span class="sxs-lookup"><span data-stu-id="1de6e-141">Value</span></span>|<span data-ttu-id="1de6e-142">説明</span><span class="sxs-lookup"><span data-stu-id="1de6e-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1de6e-143">**True** にします</span><span class="sxs-lookup"><span data-stu-id="1de6e-143">**True**</span></span>|<span data-ttu-id="1de6e-144">コピー先サーバーのジョブを有効にします。</span><span class="sxs-lookup"><span data-stu-id="1de6e-144">Enable jobs on destination server.</span></span>|  
|<span data-ttu-id="1de6e-145">**False**</span><span class="sxs-lookup"><span data-stu-id="1de6e-145">**False**</span></span>|<span data-ttu-id="1de6e-146">コピー先サーバーのジョブを無効にします。</span><span class="sxs-lookup"><span data-stu-id="1de6e-146">Disable jobs on destination server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1de6e-147">参照</span><span class="sxs-lookup"><span data-stu-id="1de6e-147">See Also</span></span>  
 <span data-ttu-id="1de6e-148">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1de6e-148">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1de6e-149">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="1de6e-149">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="1de6e-150">[[ジョブ転送タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="1de6e-150">[Transfer Jobs Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="1de6e-151">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="1de6e-151">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="1de6e-152">SMO 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="1de6e-152">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
