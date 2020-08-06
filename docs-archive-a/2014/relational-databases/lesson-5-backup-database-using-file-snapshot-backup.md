---
title: 'レッスン 6: オンプレミスのソースマシンから Azure のターゲットコンピューターにデータベースを移行する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9af8a260493561f9728d1677b7667bd3f36cb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643332"
---
# <a name="lesson-6-migrate-a-database-from-a-source-machine-on-premises-to-a-destination-machine-in-azure"></a><span data-ttu-id="4070e-102">レッスン 6: オンプレミスのソース コンピューターから Azure のターゲット コンピューターにデータベースを移行する</span><span class="sxs-lookup"><span data-stu-id="4070e-102">Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure</span></span>
  <span data-ttu-id="4070e-103">このレッスンでは、別のオンプレミスコンピューターまたは Azure の仮想マシンに存在する可能性がある別の SQL Server が既にあることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="4070e-103">This lesson assumes that you already have another SQL Server, which might reside in another on-premises computer or in a virtual machine in Azure.</span></span> <span data-ttu-id="4070e-104">Azure で SQL Server 仮想マシンを作成する方法の詳細については、「 [azure での SQL Server 仮想マシンのプロビジョニング](https://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4070e-104">For information on how to create a SQL Server virtual machine in Azure, see [Provisioning a SQL Server Virtual Machine on Azure](https://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/).</span></span> <span data-ttu-id="4070e-105">Azure に SQL Server 仮想マシンをプロビジョニングした後、別のコンピューターの SQL Server Management Studio を使用して、この仮想マシンの SQL Server のインスタンスに接続できることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4070e-105">After provisioning a SQL Server virtual machine in Azure, make sure that you can connect to an instance of SQL Server in this virtual machine via SQL Server Management Studio in another computer.</span></span>  
  
 <span data-ttu-id="4070e-106">このレッスンは、次の手順を完了済みであることも前提としています。</span><span class="sxs-lookup"><span data-stu-id="4070e-106">This lesson also assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="4070e-107">Azure Storage アカウントを持っています。</span><span class="sxs-lookup"><span data-stu-id="4070e-107">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="4070e-108">Azure Storage アカウントでコンテナーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="4070e-108">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="4070e-109">読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="4070e-109">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="4070e-110">SAS キーも生成しました。</span><span class="sxs-lookup"><span data-stu-id="4070e-110">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="4070e-111">ソース コンピューターで SQL Server 資格情報を作成しました。</span><span class="sxs-lookup"><span data-stu-id="4070e-111">You have created a SQL Server credential on the source machine.</span></span>  
  
-   <span data-ttu-id="4070e-112">Azure に仮想マシン SQL Server 仮想マシンが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="4070e-112">You already have created a destination SQL Server virtual machine in Azure.</span></span> <span data-ttu-id="4070e-113">仮想マシンは、SQL Server 2014 を含んでいるプラットフォーム イメージを選択して作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4070e-113">We recommend that you create it by selecting a platform image that includes SQL Server 2014.</span></span>  
  
 <span data-ttu-id="4070e-114">オンプレミスの SQL Server から Azure の別の仮想マシンにデータベースを移行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4070e-114">To migrate a database from SQL Server on-premises to another virtual machine in Azure, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="4070e-115">ソース コンピューター (このチュートリアルでは内部設置型コンピューター) で、SQL Server Management Studio のクエリ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="4070e-115">In the source machine (which is an on-premises computer in this tutorial), open a query window in SQL Server Management Studio.</span></span> <span data-ttu-id="4070e-116">次のステートメントを実行して、データベースをデタッチし、別のコンピューターに移動します。</span><span class="sxs-lookup"><span data-stu-id="4070e-116">Detach your database to move it to another machine by executing these statements:</span></span>  
  
    ```  
    -- Detach the database in the source machine   
    USE master  
    EXEC sp_detach_db 'TestDB1', 'true';  
    ```  
  
2.  <span data-ttu-id="4070e-117">ターゲット コンピューターにデータベースを転送する必要がある場合は、まずデータベースを準備しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4070e-117">If you need to transfer a database to a destination machine, first you must prepare it.</span></span> <span data-ttu-id="4070e-118">ターゲット コンピューターを準備するには、まずターゲット コンピューターで SQL Server 資格情報を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4070e-118">To prepare your destination machine, first you need to create a SQL Server credential in the destination machine.</span></span> <span data-ttu-id="4070e-119">暗号化されたデータベースの場合は、証明書もソース コンピューターからターゲット コンピューターにインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4070e-119">If it is an encrypted database, you need to import the certificate from the source machine to the destination machine as well.</span></span>  
  
    1.  <span data-ttu-id="4070e-120">ターゲット コンピューターで SQL Server 資格情報を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4070e-120">To create a SQL Server Credential in the destination machine, follow these steps:</span></span>  
  
        1.  <span data-ttu-id="4070e-121">ソース コンピューターの SQL Server Management Studio 経由でターゲット コンピューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="4070e-121">Connect to the destination machine via SQL Server Management Studio in your source computer.</span></span>  <span data-ttu-id="4070e-122">または、ターゲット コンピューターで SQL Server Management Studio を直接起動します。</span><span class="sxs-lookup"><span data-stu-id="4070e-122">Or, start SQL Server Management Studio in your destination computer directly.</span></span>  
  
        2.  <span data-ttu-id="4070e-123">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-123">On the Standard tool bar, click **New Query**.</span></span>  
  
        3.  <span data-ttu-id="4070e-124">次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="4070e-124">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="4070e-125">次のステートメントは、ストレージコンテナーの共有アクセス証明書を格納するための SQL Server 資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="4070e-125">The following statement creates a SQL Server Credential to store your storage container's Shared Access Certificate.</span></span>  
  
            ```sql  
  
            USE master   
            GO   
            CREATE CREDENTIAL [http://teststorageaccnt.blob.core.windows.net/testcontainer]   
            WITH IDENTITY='SHARED ACCESS SIGNATURE',   
            SECRET = 'your SAS key'   
            GO  
  
            ```  
  
        4.  <span data-ttu-id="4070e-126">使用可能なすべての資格情報を表示するには、クエリ ウィンドウで次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4070e-126">To see all available credentials, you can run the following statement in the query window:</span></span>  
  
            ```sql  
            SELECT * from sys.credentials   
            ```  
  
        5.  <span data-ttu-id="4070e-127">ターゲット サーバーに接続して、クエリ ウィンドウを開き、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4070e-127">When connected to the destination server, open query window, and run:</span></span>  
  
            ```sql  
  
            -- Create a master key and a server certificate   
            USE master   
            GO   
            CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01'; -- You may use a different password.   
            GO   
            CREATE CERTIFICATE MySQLCert   
            FROM FILE = 'C:\certs\MySQLCert.CER'   
            WITH PRIVATE KEY   
            (   
            FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
            DECRYPTION BY PASSWORD = 'MySQLKey01'   
            );   
            GO  
  
            ```  
  
             <span data-ttu-id="4070e-128">この手順が終了すると、ソース コンピューターからバックアップされた暗号化証明書がターゲット コンピューターにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="4070e-128">At the end of this step, the destination machine has imported the encryption certificate that was backed up from the source machine.</span></span> <span data-ttu-id="4070e-129">次に、ターゲット コンピューターでデータ ファイルをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="4070e-129">Next, you can attach the data files in the destination machine.</span></span>  
  
    2.  <span data-ttu-id="4070e-130">次に、FOR ATTACH オプションを使用して Azure Storage 内の既存のファイルを指すデータファイルとログファイルを含むデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="4070e-130">Then, create a database with data and log files pointing to the existing files in Azure Storage by using FOR ATTACH option.</span></span> <span data-ttu-id="4070e-131">クエリ ウィンドウで、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4070e-131">In the query window, run the following statement:</span></span>  
  
        ```sql  
  
        --Create a database on the destination server   
        CREATE DATABASE TestDB1onDest   
        ON   
        (NAME = TestDB1_data,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf' )   
        LOG ON   
         (NAME = TestDB1_log,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
        FOR ATTACH   
        GO  
  
        ```  
  
    3.  <span data-ttu-id="4070e-132">オブジェクト エクスプローラーで、[データベース] を右クリックし、[更新] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-132">On the Object Explorer, click Databases, right-click Refresh.</span></span> <span data-ttu-id="4070e-133">新しく作成したデータベース TestDB1onDest が一覧に表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4070e-133">You should be able to see the newly created database TestDB1onDest listed.</span></span>  
  
    4.  <span data-ttu-id="4070e-134">次に、クエリ ウィンドウで次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4070e-134">Next, run the following statement in the query window:</span></span>  
  
        ```sql  
  
        USE TestDB1onDest   
        SELECT * FROM Table1;   
        GO  
  
        ```  
  
         <span data-ttu-id="4070e-135">これでレッスン 4 で入力したデータがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="4070e-135">This should list all the data you entered in Lesson 4.</span></span>  
  
 <span data-ttu-id="4070e-136">暗号化されたデータベースがデータ移動なしで別のコンピューター インスタンスに転送されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4070e-136">Note that the encrypted database was transferred to another compute instance with no data movement.</span></span>  
  
 <span data-ttu-id="4070e-137">SQL Server Management Studio ユーザーインターフェイスを使用して Azure Storage 内の既存のファイルを指すデータファイルとログファイルを含むデータベースを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4070e-137">To create a database with data and log files pointing to the existing files in Azure Storage using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="4070e-138">**オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="4070e-138">In **Object Explorer**, connect to an instance of the SQL Server Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4070e-139">**[データベース]** を右クリックし、 **[新しいデータベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-139">Right-click **Databases**, and then click **New Database**.</span></span> <span data-ttu-id="4070e-140">次に [TestDB1] を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-140">Then, right-click TestDB1.</span></span> <span data-ttu-id="4070e-141">[タスク] をクリックし、[デタッチ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-141">Click Tasks, and then click Detach.</span></span> <span data-ttu-id="4070e-142">[デタッチ] ダイアログ ウィンドウで、[接続の削除] チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4070e-142">In the Detach dialog window, check Drop Connections.</span></span> <span data-ttu-id="4070e-143">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-143">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="4070e-144">SQL Server 2014 CTP2 以降がインストールされたターゲット コンピューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="4070e-144">Connect to the destination machine, which has SQL Server 2014 CTP2 or later.</span></span> <span data-ttu-id="4070e-145">ターゲット コンピューターを準備するには、ターゲット コンピューターで、TestDB1 を格納した同じコンテナーを指す SQL Server 資格情報を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4070e-145">To prepare your destination machine, you need to create a SQL Server credential in the destination machine to point to the same container that you put TestDB1 in.</span></span> <span data-ttu-id="4070e-146">同じコンピューターで再アタッチする場合、別の資格情報を作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4070e-146">If you are going to re-attach in the same computer, you do not need to create another credential.</span></span>  
  
4.  <span data-ttu-id="4070e-147">**オブジェクトエクスプローラー**で、[**データベース**] を右クリックし、[**アタッチ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-147">In **Object Explorer**, right-click **Databases** and click **Attach**.</span></span>  
  
5.  <span data-ttu-id="4070e-148">[**データベースのアタッチ**] ダイアログボックスで、アタッチするデータベースを指定するために、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-148">In the **Attach Databases** dialog box, to specify the database to be attached, click **Add**.</span></span> <span data-ttu-id="4070e-149">[**データベースファイルの検索**] ダイアログウィンドウで次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4070e-149">In the **Locate Database Files** dialog window:</span></span>  
  
     <span data-ttu-id="4070e-150">[データベースデータファイルの場所] に、「」と入力 `https://teststorageaccnt.blob.core.windows.net/testcontainer/` します。</span><span class="sxs-lookup"><span data-stu-id="4070e-150">For Database Data File Location, type: `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.</span></span>  
  
     <span data-ttu-id="4070e-151">[ファイル名] に「」と入力 `TestDB1Data.mdf` します。</span><span class="sxs-lookup"><span data-stu-id="4070e-151">For File name, type: `TestDB1Data.mdf`.</span></span>  
  
6.  <span data-ttu-id="4070e-152">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4070e-152">Click **OK**.</span></span>  
  
     <span data-ttu-id="4070e-153">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="4070e-153">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="4070e-154">**次のレッスン:**</span><span class="sxs-lookup"><span data-stu-id="4070e-154">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="4070e-155">レッスン 7: Azure Storage にデータ ファイルを移動する</span><span class="sxs-lookup"><span data-stu-id="4070e-155">Lesson 7: Move your data files to Azure Storage</span></span>](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
