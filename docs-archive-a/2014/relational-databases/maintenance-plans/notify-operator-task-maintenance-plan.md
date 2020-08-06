---
title: '[オペレーターへの通知タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.notifyoperator.f1
helpviewer_keywords:
- Notify Operator Task dialog box
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4feb59622c2a42de67193c75d545a6b8a2a08863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642078"
---
# <a name="notify-operator-task-maintenance-plan"></a><span data-ttu-id="73f34-102">[オペレーターへの通知タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="73f34-102">Notify Operator Task (Maintenance Plan)</span></span>
  <span data-ttu-id="73f34-103">**[オペレーターへの通知タスク]** ダイアログ ボックスを使用すると、このメンテナンス プランに自動通知を追加できます。</span><span class="sxs-lookup"><span data-stu-id="73f34-103">Use the **Notify Operators Task** dialog to add an automatic notification to this maintenance plan.</span></span> <span data-ttu-id="73f34-104">このタスクを使用するには、[データベース メール] が有効になっていて、MSDB がメール ホスト データベースとして適切に構成され、有効な電子メール アドレスを持つ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのオペレーターが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="73f34-104">To use this task you must have Database Mail enabled and properly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator with a valid e-mail address.</span></span>  
  
 <span data-ttu-id="73f34-105">このタスクでは、sp_notify_operator ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="73f34-105">This task uses the sp_notify_operator stored procedure.</span></span>  
  
## <a name="options"></a><span data-ttu-id="73f34-106">オプション</span><span class="sxs-lookup"><span data-stu-id="73f34-106">Options</span></span>  
 <span data-ttu-id="73f34-107">**Connection**</span><span class="sxs-lookup"><span data-stu-id="73f34-107">**Connection**</span></span>  
 <span data-ttu-id="73f34-108">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="73f34-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="73f34-109">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="73f34-109">**New**</span></span>  
 <span data-ttu-id="73f34-110">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="73f34-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="73f34-111">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="73f34-111">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="73f34-112">**[通知するオペレーター]**</span><span class="sxs-lookup"><span data-stu-id="73f34-112">**Operators to notify**</span></span>  
 <span data-ttu-id="73f34-113">電子メールの受信者を指定します。</span><span class="sxs-lookup"><span data-stu-id="73f34-113">Specify the recipient of the e-mail.</span></span>  
  
 <span data-ttu-id="73f34-114">**[通知メッセージの件名]**</span><span class="sxs-lookup"><span data-stu-id="73f34-114">**Notification message subject**</span></span>  
 <span data-ttu-id="73f34-115">通知メッセージの件名に含めるテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="73f34-115">Specify the text to include in the notification message subject line.</span></span>  
  
 <span data-ttu-id="73f34-116">**[通知メッセージの本文]**</span><span class="sxs-lookup"><span data-stu-id="73f34-116">**Notification message body**</span></span>  
 <span data-ttu-id="73f34-117">通知メッセージの本文に含めるテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="73f34-117">Specify the text to include in the notification message body.</span></span>  
  
 <span data-ttu-id="73f34-118">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="73f34-118">**View T-SQL**</span></span>  
 <span data-ttu-id="73f34-119">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="73f34-119">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73f34-120">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="73f34-120">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="73f34-121">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="73f34-121">New Connection Dialog Box</span></span>  
 <span data-ttu-id="73f34-122">**[接続名]**</span><span class="sxs-lookup"><span data-stu-id="73f34-122">**Connection name**</span></span>  
 <span data-ttu-id="73f34-123">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="73f34-123">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="73f34-124">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="73f34-124">**Select or enter a server name**</span></span>  
 <span data-ttu-id="73f34-125">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="73f34-125">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="73f34-126">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="73f34-126">**Refresh**</span></span>  
 <span data-ttu-id="73f34-127">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="73f34-127">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="73f34-128">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="73f34-128">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="73f34-129">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="73f34-129">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="73f34-130">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="73f34-130">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="73f34-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 認証を使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73f34-131">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="73f34-132">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="73f34-132">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="73f34-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73f34-133">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="73f34-134">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="73f34-134">This option is not available.</span></span>  
  
 <span data-ttu-id="73f34-135">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="73f34-135">**User name**</span></span>  
 <span data-ttu-id="73f34-136">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="73f34-136">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="73f34-137">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="73f34-137">This option is not available.</span></span>  
  
 <span data-ttu-id="73f34-138">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="73f34-138">**Password**</span></span>  
 <span data-ttu-id="73f34-139">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="73f34-139">Provide a password to use when authenticating.</span></span> <span data-ttu-id="73f34-140">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="73f34-140">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f34-141">参照</span><span class="sxs-lookup"><span data-stu-id="73f34-141">See Also</span></span>  
 <span data-ttu-id="73f34-142">[データベース メール](../database-mail/database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="73f34-142">[Database Mail](../database-mail/database-mail.md) </span></span>  
 [<span data-ttu-id="73f34-143">sp_notify_operator &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73f34-143">sp_notify_operator &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)  
  
  
