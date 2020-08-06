---
title: 'レッスン 8: データベースを Azure Storage に復元する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: adec725d1b519fb67560dc572823ba0a116aaa54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645044"
---
# <a name="lesson-8-restore-a-database-to-azure-storage"></a><span data-ttu-id="d778b-103">レッスン 8:</span><span class="sxs-lookup"><span data-stu-id="d778b-103">Lesson 8.</span></span> <span data-ttu-id="d778b-104">Azure Storage にデータベースを復元する</span><span class="sxs-lookup"><span data-stu-id="d778b-104">Restore a database to Azure Storage</span></span>
  <span data-ttu-id="d778b-105">このレッスンでは、バックアップファイルをローカルに作成し、Azure Storage に復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d778b-105">In this lesson, you will learn how to create a backup file locally and then restore it to Azure Storage.</span></span> <span data-ttu-id="d778b-106">データベースは、オンプレミスまたは Azure の仮想マシンのいずれかにあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d778b-106">Note that you can have your database either on either on-premises or in a virtual machine in Azure.</span></span> <span data-ttu-id="d778b-107">このレッスンを続行するには、レッスン 4、5、6 および 7 を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d778b-107">To follow this lesson, you do not need to complete Lesson 4, 5, 6, and 7.</span></span>  
  
 <span data-ttu-id="d778b-108">このレッスンでは、次の手順を既に完了していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="d778b-108">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="d778b-109">Azure Storage アカウントを持っています。</span><span class="sxs-lookup"><span data-stu-id="d778b-109">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="d778b-110">Azure Storage アカウントでコンテナーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="d778b-110">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="d778b-111">読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="d778b-111">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="d778b-112">SAS キーも生成しました。</span><span class="sxs-lookup"><span data-stu-id="d778b-112">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="d778b-113">Shared Access Signature に基づいてソース コンピューターで SQL Server 資格情報を作成しました。</span><span class="sxs-lookup"><span data-stu-id="d778b-113">You have created a SQL Server credential on the source machine based on Shared Access Signature.</span></span>  
  
-   <span data-ttu-id="d778b-114">ソース コンピューターにデータベースを作成しました。</span><span class="sxs-lookup"><span data-stu-id="d778b-114">You have created a database in the source machine.</span></span>  
  
 <span data-ttu-id="d778b-115">データベースを Azure Storage に復元するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d778b-115">To restore a database to Azure Storage, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="d778b-116">ソース コンピューターで、SQL Server Management Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="d778b-116">In the source machine, start SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="d778b-117">新しく作成したデータベースに接続すると、クエリ ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="d778b-117">When connected to the newly created database, open the query window.</span></span> <span data-ttu-id="d778b-118">次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d778b-118">Run the following statement:</span></span>  
  
    ```sql  
  
    USE TestDB3Restore;   
    GO   
    BACKUP DATABASE TestDB3Restore   
    TO DISK = 'C:\BACKUP\TestDB3Restore.Bak'   
       WITH FORMAT,   
       NAME = 'Full Backup of TestDB3Restore'   
    GO  
  
    ```  
  
3.  <span data-ttu-id="d778b-119">次に、クエリ ウィンドウに次のステートメントをコピーして実行します。</span><span class="sxs-lookup"><span data-stu-id="d778b-119">Next, copy and run the following statements in the Query window.</span></span>  
  
    ```sql  
  
    USE master;   
    GO   
    RESTORE DATABASE TestDB3Restore    
    FROM DISK = 'C:\BACKUP\TestDB3Restore.bak'    
    WITH REPLACE,   
    MOVE 'TestDB3Restore' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore.mdf',     
    MOVE 'TestDB3Restore_log' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore_log.ldf';   
    GO  
  
    ```  
  
     <span data-ttu-id="d778b-120">この手順が終了すると、管理ポータルにコンテナーのデータ ファイル (.mdf) とログ ファイル (.ldf) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d778b-120">At the end of this step, your container should list data (.mdf) and (.ldf) files on the Management Portal.</span></span>  
  
 <span data-ttu-id="d778b-121">SQL Server Management Studio ユーザーインターフェイスを使用して Azure Storage を指すデータファイルとログファイルを含むデータベースを復元するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d778b-121">To restore a database with data and log files pointing to Azure Storage using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="d778b-122">**オブジェクトエクスプローラー**で、サーバー名をクリックしてサーバーツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="d778b-122">In **Object Explorer**, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="d778b-123">[**データベース**] を展開し、データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="d778b-123">Expand **Databases**, and, select your database.</span></span>  
  
3.  <span data-ttu-id="d778b-124">データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d778b-124">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="d778b-125">[**全般**] ページの [**復元**元] セクションで、[**ソース**デバイス] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d778b-125">On the **General** page, in the **Restore** source section, click **Source** device.</span></span>  
  
5.  <span data-ttu-id="d778b-126">[**ソース**デバイス] ボックスの参照ボタンをクリックして、[**バックアップデバイスの選択**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="d778b-126">Click the browse button for the **Source** device text box, which opens the **Select Backup Devices** dialog box.</span></span>  
  
6.  <span data-ttu-id="d778b-127">[バックアップメディア] ボックスで、[**ファイル**] を選択し、[**追加**] ボタンをクリックしてバックアップ (.bak) ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d778b-127">In the Backup media text box, select **File**, and click the **Add** button to locate the backup (.bak) file.</span></span> <span data-ttu-id="d778b-128">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d778b-128">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="d778b-129">最初のページの [**ファイル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d778b-129">Click **Files** on the first page.</span></span>  
  
8.  <span data-ttu-id="d778b-130">[**データベースファイルの復元**] セクションの [**復元元**] フィールドに、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d778b-130">In the **Restore Database Files** as section, under **Restore As** field, type the followings:</span></span>  
  
     <span data-ttu-id="d778b-131">データファイルの場合は、「」と入力 `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf` します。</span><span class="sxs-lookup"><span data-stu-id="d778b-131">For data file, type: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`.</span></span> <span data-ttu-id="d778b-132">ログファイルの場合は、「」と入力 `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf` します。</span><span class="sxs-lookup"><span data-stu-id="d778b-132">For log file, type: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`.</span></span>  
  
     <span data-ttu-id="d778b-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="d778b-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")</span></span>  
  
9. <span data-ttu-id="d778b-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d778b-134">Click **OK**.</span></span>  
  
 <span data-ttu-id="d778b-135">復元を実行したら、管理ポータルにログインします。</span><span class="sxs-lookup"><span data-stu-id="d778b-135">When the restore is done, log in to the Management Portal.</span></span> <span data-ttu-id="d778b-136">コンテナーの .mdf ファイルおよび .ldf ファイルを次のように確認できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d778b-136">You should be able to see the .mdf and .ldf files in the container as follows:</span></span>  
  
 <span data-ttu-id="d778b-137">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="d778b-137">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="d778b-138">**次のレッスン:**</span><span class="sxs-lookup"><span data-stu-id="d778b-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="d778b-139">レッスン 9.Azure Storage からデータベースを復元する</span><span class="sxs-lookup"><span data-stu-id="d778b-139">Lesson 9. Restore a database from Azure Storage</span></span>](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
