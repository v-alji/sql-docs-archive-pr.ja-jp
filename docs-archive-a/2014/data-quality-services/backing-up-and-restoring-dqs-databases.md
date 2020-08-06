---
title: DQS データベースのバックアップと復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 489664d8c64a99d1ea4dcec79b93e5b01b28f649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632729"
---
# <a name="backing-up-and-restoring-dqs-databases"></a><span data-ttu-id="c353a-102">DQS データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="c353a-102">Backing Up and Restoring DQS Databases</span></span>
  <span data-ttu-id="c353a-103">このトピックでは、DQS データベースのバックアップと復元を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c353a-103">This topic describes how to back up and restore the DQS databases.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c353a-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="c353a-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c353a-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="c353a-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="c353a-106">DQS サーバーのインストール中に入力したデータベース マスター キーのパスワードを知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c353a-106">You must know or remember the password for the database master key that you provided during the DQS server installation.</span></span>  
  
-   <span data-ttu-id="c353a-107">DQS で実行中のアクティビティまたはプロセスがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c353a-107">Ensure that there are no running activities or processes in DQS.</span></span> <span data-ttu-id="c353a-108">これは **[アクティビティ監視]** 画面を使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="c353a-108">This can be verified using the **Activity Monitoring** screen.</span></span> <span data-ttu-id="c353a-109">この画面の操作の詳細については、「 [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c353a-109">For detailed information about working in this screen, see [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).</span></span>  
  
-   <span data-ttu-id="c353a-110">DQS サーバーにログオンしているユーザーがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c353a-110">Ensure that there are no users logged on the DQS server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c353a-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c353a-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c353a-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="c353a-112">Permissions</span></span>  
  
-   <span data-ttu-id="c353a-113">バックアップおよび復元操作を実行するには、使用する Windows ユーザー アカウントが、SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c353a-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to perform the backup and restore operations.</span></span>  
  
-   <span data-ttu-id="c353a-114">DQS の実行中のアクティビティを終了させたり実行中のプロセスを停止させたりするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="c353a-114">You must have the dqs_administrator role on the DQS_MAIN database to terminate any running activities or stop any running processes in DQS.</span></span>  
  
##  <a name="backup-and-restore-dqs-databases"></a><a name="BackupRestore"></a><span data-ttu-id="c353a-115">DQS データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="c353a-115">Backup and Restore DQS Databases</span></span>  
  
1.  <span data-ttu-id="c353a-116">Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c353a-116">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="c353a-117">オブジェクト エクスプローラーで、 **[データベース]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="c353a-117">In Object Explorer, expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="c353a-118">DQS_STAGING_DATA データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="c353a-118">Back up the DQS_STAGING_DATA database.</span></span> <span data-ttu-id="c353a-119">SQL Server データベースのバックアップ手順について詳しくは、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c353a-119">For step-by-step instructions for backing a SQL Server database, see [Create a Full Database Backup &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="c353a-120">DQS_PROJECTS データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="c353a-120">Back up the DQS_PROJECTS database.</span></span>  
  
5.  <span data-ttu-id="c353a-121">DQS_MAIN データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="c353a-121">Back up the DQS_MAIN database.</span></span>  
  
6.  <span data-ttu-id="c353a-122">SQL Server の現在のインスタンスから切断し、データベースを復元する SQL Server インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c353a-122">Disconnect from the current instance of SQL Server, and connect to the SQL Server instance where you want to restore these databases.</span></span>  
  
7.  <span data-ttu-id="c353a-123">DQS_MAIN データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="c353a-123">Restore DQS_MAIN database.</span></span> <span data-ttu-id="c353a-124">SQL Server データベースを復元するための詳細な手順については、「 [restore a Database Backup &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c353a-124">For step-by-step instructions to restore a SQL Server database, see [Restore a Database Backup &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).</span></span>  
  
8.  <span data-ttu-id="c353a-125">DQS_PROJECTS データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="c353a-125">Restore the DQS_PROJECTS database.</span></span>  
  
9. <span data-ttu-id="c353a-126">DQS_STAGING_DATA データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="c353a-126">Restore the DQS_STAGING_DATA database.</span></span>  
  
10. <span data-ttu-id="c353a-127">オブジェクト エクスプローラーでサーバーを右クリックし、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c353a-127">In Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
11. <span data-ttu-id="c353a-128">クエリエディターウィンドウで、次の SQL ステートメントをコピーし、を *\<PASSWORD>* DQS のインストール時にデータベースマスターキーに対して指定したパスワードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c353a-128">In the Query Editor window, copy the following SQL statements, and replace *\<PASSWORD>* with the password that you provided during the DQS installation for the database master key:</span></span>  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
    ```  
  
12. <span data-ttu-id="c353a-129">F5 キーを押してステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="c353a-129">Press F5 to execute the statements.</span></span> <span data-ttu-id="c353a-130">**[結果]** ペインを確認してステートメントが正常に実行されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c353a-130">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c353a-131">参照</span><span class="sxs-lookup"><span data-stu-id="c353a-131">See Also</span></span>  
 [<span data-ttu-id="c353a-132">Manage DQS Databases</span><span class="sxs-lookup"><span data-stu-id="c353a-132">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
