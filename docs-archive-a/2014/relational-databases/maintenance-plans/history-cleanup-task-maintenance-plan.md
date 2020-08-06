---
title: '[履歴クリーンアップ タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.historycleanup.f1
helpviewer_keywords:
- History Cleanup Task dialog box
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
ms.reviewer: ''
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 03ff35b14fc13d2b4446b15501114489b52c421e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643316"
---
# <a name="history-cleanup-task-maintenance-plan"></a><span data-ttu-id="69e5e-102">[履歴クリーンアップ タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="69e5e-102">History Cleanup Task (Maintenance Plan)</span></span>

  <span data-ttu-id="69e5e-103">**[履歴クリーンアップ タスク]** ダイアログ ボックスを使用すると、msdb データベースのテーブルに含まれる古い履歴情報を破棄できます。</span><span class="sxs-lookup"><span data-stu-id="69e5e-103">Use the **History Cleanup Task** dialog to discard old historical information from tables in the msdb database.</span></span> <span data-ttu-id="69e5e-104">このタスクでは、バックアップと復元の履歴、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ履歴、メンテナンス プランの履歴の削除がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="69e5e-104">This task supports deleting backup and restore history, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job history, and maintenance plan history.</span></span>  
  
 <span data-ttu-id="69e5e-105">このステートメントでは、 **sp_purge_jobhistory** ステートメントおよび **sp_delete_backuphistory** ステートメントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="69e5e-105">This statement uses the **sp_purge_jobhistory** and **sp_delete_backuphistory** statements.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="69e5e-106">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="69e5e-106">UI element list</span></span>  
 <span data-ttu-id="69e5e-107">**接続**</span><span class="sxs-lookup"><span data-stu-id="69e5e-107">**Connection**</span></span>  
 <span data-ttu-id="69e5e-108">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="69e5e-109">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-109">**New**</span></span>  
 <span data-ttu-id="69e5e-110">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="69e5e-111">**[新しい接続]** ダイアログ ボックスについては、このトピックで説明しています。</span><span class="sxs-lookup"><span data-stu-id="69e5e-111">The **New Connection** dialog box is described later in this topic.</span></span>  
  
 <span data-ttu-id="69e5e-112">**[バックアップおよび復元の履歴]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-112">**Backup and restore history**</span></span>  
 <span data-ttu-id="69e5e-113">最新のバックアップを作成したときのレコードを保存しておくと、データベースの復元時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で復元プランを作成するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="69e5e-113">Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] create a recovery plan when you want to restore a database.</span></span> <span data-ttu-id="69e5e-114">保存期間は、データベースの完全バックアップを実行する間隔以上にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="69e5e-114">The retention period should be at least the frequency of full database back ups.</span></span>  
  
 <span data-ttu-id="69e5e-115">**[SQL Server エージェントのジョブ履歴]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-115">**SQL Server Agent Job history**</span></span>  
 <span data-ttu-id="69e5e-116">この履歴を利用して、失敗したジョブをトラブルシューティングしたり、データベース アクションの発生原因を調べたりできます。</span><span class="sxs-lookup"><span data-stu-id="69e5e-116">This history can help you troubleshoot failed jobs, or determine why database actions occurred.</span></span>  
  
 <span data-ttu-id="69e5e-117">**[メンテナンス プランの履歴]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-117">**Maintenance plan history**</span></span>  
 <span data-ttu-id="69e5e-118">この履歴を利用して、失敗したメンテナンス プラン ジョブをトラブルシューティングしたり、データベース アクションの発生原因を調べたりできます。</span><span class="sxs-lookup"><span data-stu-id="69e5e-118">This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.</span></span>  
  
 <span data-ttu-id="69e5e-119">**[これより古い履歴データの削除]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-119">**Remove historical data older than**</span></span>  
 <span data-ttu-id="69e5e-120">削除するアイテムの古さを指定します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-120">Specify age of items that you want to delete.</span></span>  
  
 <span data-ttu-id="69e5e-121">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-121">**View T-SQL**</span></span>  
 <span data-ttu-id="69e5e-122">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-122">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69e5e-123">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="69e5e-123">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="69e5e-124">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="69e5e-124">New Connection Dialog Box</span></span>  
 <span data-ttu-id="69e5e-125">**接続名**</span><span class="sxs-lookup"><span data-stu-id="69e5e-125">**Connection name**</span></span>  
 <span data-ttu-id="69e5e-126">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-126">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="69e5e-127">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-127">**Select or enter a server name**</span></span>  
 <span data-ttu-id="69e5e-128">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-128">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="69e5e-129">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-129">**Refresh**</span></span>  
 <span data-ttu-id="69e5e-130">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-130">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="69e5e-131">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-131">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="69e5e-132">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-132">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="69e5e-133">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-133">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="69e5e-134">Microsoft Windows 認証を使用して、SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-134">Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="69e5e-135">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="69e5e-135">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="69e5e-136">SQL Server 認証を使用して、SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-136">Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] using SQL Server Authentication.</span></span> <span data-ttu-id="69e5e-137">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="69e5e-137">This option is not available.</span></span>  
  
 <span data-ttu-id="69e5e-138">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="69e5e-138">**User name**</span></span>  
 <span data-ttu-id="69e5e-139">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-139">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="69e5e-140">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="69e5e-140">This option is not available.</span></span>  
  
 <span data-ttu-id="69e5e-141">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="69e5e-141">**Password**</span></span>  
 <span data-ttu-id="69e5e-142">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="69e5e-142">Provide a password to use when authenticating.</span></span> <span data-ttu-id="69e5e-143">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="69e5e-143">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e5e-144">参照</span><span class="sxs-lookup"><span data-stu-id="69e5e-144">See Also</span></span>  
 <span data-ttu-id="69e5e-145">[sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="69e5e-145">[sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql) </span></span>  
 [<span data-ttu-id="69e5e-146">sp_delete_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69e5e-146">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
  
