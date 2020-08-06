---
title: '[T-SQL ステートメントの実行タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.tsql.f1
helpviewer_keywords:
- Execute T-SQL Statement Task dialog box
ms.assetid: fef3e259-0c47-4f6e-ade0-aee95e3d6c1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63738758ce228a51ab6c75eb11a681eec3b27352
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643318"
---
# <a name="execute-t-sql-statement-task-maintenance-plan"></a><span data-ttu-id="a99f8-102">[T-SQL ステートメントの実行タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="a99f8-102">Execute T-SQL Statement Task (Maintenance Plan)</span></span>
  <span data-ttu-id="a99f8-103">**[T-SQL ステートメントの実行タスク]** ダイアログを使用すると、適切な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをこのメンテナンス プランに追加して、メンテナンス プランをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="a99f8-103">Use the **Execute T-SQL Statement Task** dialog to customize your maintenance plan by adding [!INCLUDE[tsql](../../includes/tsql-md.md)] statements of your choice to this maintenance plan.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a99f8-104">オプション</span><span class="sxs-lookup"><span data-stu-id="a99f8-104">Options</span></span>  
 <span data-ttu-id="a99f8-105">**Connection**</span><span class="sxs-lookup"><span data-stu-id="a99f8-105">**Connection**</span></span>  
 <span data-ttu-id="a99f8-106">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-106">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="a99f8-107">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-107">**New**</span></span>  
 <span data-ttu-id="a99f8-108">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-108">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="a99f8-109">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-109">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="a99f8-110">**[実行タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-110">**Execution time out**</span></span>  
 <span data-ttu-id="a99f8-111">タイムアウトする (タスクが終了する) までタスクの完了を待機する時間 (秒) です。</span><span class="sxs-lookup"><span data-stu-id="a99f8-111">Time (seconds) to wait for task completion before timing out (terminating task).</span></span>  
  
 <span data-ttu-id="a99f8-112">**[T-SQL ステートメント]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-112">**T-SQL statement**</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a99f8-113">実行する  ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="a99f8-113">statements to execute.</span></span>  
  
 <span data-ttu-id="a99f8-114">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-114">**View T-SQL**</span></span>  
 <span data-ttu-id="a99f8-115">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-115">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a99f8-116">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a99f8-116">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="a99f8-117">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="a99f8-117">New Connection Dialog Box</span></span>  
 <span data-ttu-id="a99f8-118">**[接続名]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-118">**Connection name**</span></span>  
 <span data-ttu-id="a99f8-119">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-119">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="a99f8-120">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-120">**Select or enter a server name**</span></span>  
 <span data-ttu-id="a99f8-121">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-121">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="a99f8-122">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-122">**Refresh**</span></span>  
 <span data-ttu-id="a99f8-123">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-123">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="a99f8-124">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-124">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="a99f8-125">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-125">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="a99f8-126">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-126">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="a99f8-127">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用して [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-127">Connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="a99f8-128">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="a99f8-128">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="a99f8-129">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-129">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="a99f8-130">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="a99f8-130">This option is not available.</span></span>  
  
 <span data-ttu-id="a99f8-131">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="a99f8-131">**User name**</span></span>  
 <span data-ttu-id="a99f8-132">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-132">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="a99f8-133">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="a99f8-133">This option is not available.</span></span>  
  
 <span data-ttu-id="a99f8-134">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="a99f8-134">**Password**</span></span>  
 <span data-ttu-id="a99f8-135">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a99f8-135">Provide a password to use when authenticating.</span></span> <span data-ttu-id="a99f8-136">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="a99f8-136">This option is not available.</span></span>  
  
  
