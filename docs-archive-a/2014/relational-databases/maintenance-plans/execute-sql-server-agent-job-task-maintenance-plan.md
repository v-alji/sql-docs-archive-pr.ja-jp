---
title: '[SQL Server エージェント ジョブの実行タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b997d5144b113102ba0ed2d9d1df59b6707acbee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643317"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a><span data-ttu-id="652f2-102">[SQL Server エージェント ジョブの実行タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="652f2-102">Execute SQL Server Agent Job Task (Maintenance Plan)</span></span>
  <span data-ttu-id="652f2-103">**[SQL Server エージェント ジョブの実行タスク]** ダイアログを使用すると、メンテナンス プラン内で Microsoft SQL Server エージェント ジョブを実行できます。</span><span class="sxs-lookup"><span data-stu-id="652f2-103">Use the **Execute SQL Server Agent Job Task** dialog to execute Microsoft SQL Server Agent jobs within a maintenance plan.</span></span> <span data-ttu-id="652f2-104">選択されている接続に SQL Server エージェント ジョブが存在しない場合は、このオプションを利用できません。</span><span class="sxs-lookup"><span data-stu-id="652f2-104">This option will not be available if you have no SQL Server Agent jobs on the selected connection.</span></span>  
  
 <span data-ttu-id="652f2-105">このタスクでは、 **.sp_start_job** ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="652f2-105">This task uses the **.sp_start_job** statement.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="652f2-106">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="652f2-106">UI element list</span></span>  
 <span data-ttu-id="652f2-107">**接続**</span><span class="sxs-lookup"><span data-stu-id="652f2-107">**Connection**</span></span>  
 <span data-ttu-id="652f2-108">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="652f2-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="652f2-109">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="652f2-109">**New**</span></span>  
 <span data-ttu-id="652f2-110">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="652f2-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="652f2-111">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="652f2-111">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="652f2-112">**[使用できる SQL Server エージェント ジョブ]**</span><span class="sxs-lookup"><span data-stu-id="652f2-112">**Available SQL Agent jobs**</span></span>  
 <span data-ttu-id="652f2-113">実行するジョブを選択します。</span><span class="sxs-lookup"><span data-stu-id="652f2-113">Select the job to execute.</span></span> <span data-ttu-id="652f2-114">グリッドには、ジョブを識別するための **[ジョブ名]** と **[説明]** があります。</span><span class="sxs-lookup"><span data-stu-id="652f2-114">The grid provides the **Job name** and **Description** to identify the jobs.</span></span>  
  
 <span data-ttu-id="652f2-115">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="652f2-115">**View T-SQL**</span></span>  
 <span data-ttu-id="652f2-116">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="652f2-116">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="652f2-117">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="652f2-117">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="652f2-118">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="652f2-118">New Connection Dialog Box</span></span>  
 <span data-ttu-id="652f2-119">**接続名**</span><span class="sxs-lookup"><span data-stu-id="652f2-119">**Connection name**</span></span>  
 <span data-ttu-id="652f2-120">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="652f2-120">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="652f2-121">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="652f2-121">**Select or enter a server name**</span></span>  
 <span data-ttu-id="652f2-122">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="652f2-122">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="652f2-123">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="652f2-123">**Refresh**</span></span>  
 <span data-ttu-id="652f2-124">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="652f2-124">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="652f2-125">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="652f2-125">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="652f2-126">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="652f2-126">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="652f2-127">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="652f2-127">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="652f2-128">Microsoft Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="652f2-128">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="652f2-129">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="652f2-129">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="652f2-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="652f2-130">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="652f2-131">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="652f2-131">This option is not available.</span></span>  
  
 <span data-ttu-id="652f2-132">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="652f2-132">**User name**</span></span>  
 <span data-ttu-id="652f2-133">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="652f2-133">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="652f2-134">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="652f2-134">This option is not available.</span></span>  
  
 <span data-ttu-id="652f2-135">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="652f2-135">**Password**</span></span>  
 <span data-ttu-id="652f2-136">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="652f2-136">Provide a password to use when authenticating.</span></span> <span data-ttu-id="652f2-137">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="652f2-137">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="652f2-138">参照</span><span class="sxs-lookup"><span data-stu-id="652f2-138">See Also</span></span>  
 <span data-ttu-id="652f2-139">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="652f2-139">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span></span>  
 <span data-ttu-id="652f2-140">[ジョブの作成](../../ssms/agent/create-a-job.md) </span><span class="sxs-lookup"><span data-stu-id="652f2-140">[Create a Job](../../ssms/agent/create-a-job.md) </span></span>  
 [<span data-ttu-id="652f2-141">sp_start_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="652f2-141">sp_start_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)  
  
  
