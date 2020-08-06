---
title: 'レッスン 4: Azure Storage | でデータベースを作成するMicrosoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50fca85111d5897b738e577e7735049e0b055a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645047"
---
# <a name="lesson-4-create-a-database-in-azure-storage"></a><span data-ttu-id="c019f-102">レッスン 4:Azure Storage にデータベースを作成する</span><span class="sxs-lookup"><span data-stu-id="c019f-102">Lesson 4: Create a database in Azure Storage</span></span>
  <span data-ttu-id="c019f-103">このレッスンでは、Azure 機能の SQL Server データファイルを使用してデータベースを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c019f-103">In this lesson, you will learn how to create a database using the SQL Server Data Files in Azure feature.</span></span> <span data-ttu-id="c019f-104">このレッスンの前に、レッスン 1、2、および 3 を完了する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c019f-104">Note that before this lesson, you must complete the Lesson 1, 2, and 3.</span></span> <span data-ttu-id="c019f-105">レッスン3は非常に重要な手順です。レッスン4の前に、Azure ストレージコンテナーとそれに関連付けられているポリシー名と SAS キーに関する情報を SQL Server 資格情報ストアに格納する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="c019f-105">Lesson 3 is a very important step because you need to store the information about your Azure storage container and its associated policy name and SAS key in the SQL Server credential store before Lesson 4.</span></span>  
  
 <span data-ttu-id="c019f-106">データ ファイルまたはログ ファイルによって使用されるストレージ コンテナーごとに、名前がコンテナーのパスに一致する SQL Server 資格情報を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c019f-106">For each storage container used by a data or log file, you must create a SQL Server Credential whose name matches the container path.</span></span> <span data-ttu-id="c019f-107">次に、で新しいデータベースを作成でき Azure Storage</span><span class="sxs-lookup"><span data-stu-id="c019f-107">Then, you can create a new database in Azure Storage</span></span>  
  
 <span data-ttu-id="c019f-108">このレッスンでは、次の手順を既に完了していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="c019f-108">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="c019f-109">Azure Storage アカウントを持っています。</span><span class="sxs-lookup"><span data-stu-id="c019f-109">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="c019f-110">Azure Storage アカウントでコンテナーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="c019f-110">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="c019f-111">読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="c019f-111">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="c019f-112">SAS キーも生成しました。</span><span class="sxs-lookup"><span data-stu-id="c019f-112">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="c019f-113">ソース コンピューターで SQL Server 資格情報を作成しました。</span><span class="sxs-lookup"><span data-stu-id="c019f-113">You have created a SQL Server credential on the source machine.</span></span>  
  
 <span data-ttu-id="c019f-114">Azure Storage 機能の SQL Server データファイルを使用して Azure にデータベースを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c019f-114">To create a database in Azure using the SQL Server Data Files in Azure Storage feature, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c019f-115">SQL Server Management Studio に接続します。</span><span class="sxs-lookup"><span data-stu-id="c019f-115">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="c019f-116">オブジェクト エクスプローラーで、インストールしたデータベース エンジンのインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c019f-116">In Object Explorer, connect to the instance of Database Engine installed.</span></span>  
  
3.  <span data-ttu-id="c019f-117">[標準] ツール バーの [新しいクエリ]をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c019f-117">On the Standard tool bar, click New Query.</span></span>  
  
4.  <span data-ttu-id="c019f-118">次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="c019f-118">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="c019f-119">FILENAME フィールドがストレージ コンテナーにあるデータベース ファイルの URI パスを指し、先頭は https にする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c019f-119">Note that the FILENAME field refers to the URI path of the database file in storage container and it must start with https.</span></span>  
  
    ```  
  
    --Create a database that uses a SQL Server credential    
    CREATE DATABASE TestDB1    
    ON   
    (NAME = TestDB1_data,   
       FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf')   
     LOG ON   
    (NAME = TestDB1_log,   
        FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
    GO  
  
    ```  
  
     <span data-ttu-id="c019f-120">データベースにデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="c019f-120">Add some data to your database.</span></span>  
  
    ```  
  
    USE TestDB1;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
5.  <span data-ttu-id="c019f-121">内部設置型 SQL Server の新しい TestDB1 を表示するには、オブジェクト エクスプローラーでデータベースの表示を更新します。</span><span class="sxs-lookup"><span data-stu-id="c019f-121">To see the new TestDB1 in your on-premises SQL Server, refresh databases in the Object Explorer.</span></span>  
  
6.  <span data-ttu-id="c019f-122">同様に、ストレージ アカウントに新しく作成したデータベースを表示するには、SQL Server Management Studio (SSMS) 経由でストレージ アカウントに接続します。</span><span class="sxs-lookup"><span data-stu-id="c019f-122">Similarly, to see the newly created database in your storage account, connect to your storage account via SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="c019f-123">SQL Server Management Studio を使用して Azure storage に接続する方法については、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c019f-123">For information on how to connect to an Azure storage using SQL Server Management Studio, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="c019f-124">まず、ストレージ アカウント情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="c019f-124">First, get the storage account information.</span></span> <span data-ttu-id="c019f-125">管理ポータルにログインします。</span><span class="sxs-lookup"><span data-stu-id="c019f-125">Log in to the Management Portal.</span></span> <span data-ttu-id="c019f-126">次に、[**ストレージ**] をクリックし、ストレージアカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="c019f-126">Then, click **Storage** and choose your storage account.</span></span> <span data-ttu-id="c019f-127">ストレージアカウントを選択したら、ページの下部にある [**アクセスキーの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c019f-127">When a storage account is selected, click **Manage Access Keys** at the bottom of the page.</span></span> <span data-ttu-id="c019f-128">次のようなダイアログ ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="c019f-128">This opens a similar dialog window:</span></span>  
  
         <span data-ttu-id="c019f-129">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="c019f-129">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")</span></span>  
  
    2.  <span data-ttu-id="c019f-130">**ストレージアカウント名**と**プライマリアクセスキー**の値を、SSMS の [ **Azure Storage への接続**] ダイアログウィンドウにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c019f-130">Copy the **Storage Account Name** and **Primary Access Key** values to the **Connect to Azure Storage** dialog window in SSMS.</span></span> <span data-ttu-id="c019f-131">そのうえで **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c019f-131">Then, click **Connect**.</span></span> <span data-ttu-id="c019f-132">これで、次のスクリーン ショットに示すように、ストレージ アカウント コンテナーについての情報が SSMS に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c019f-132">This brings the information about storage account containers to SSMS as shown in the following screenshot:</span></span>  
  
         <span data-ttu-id="c019f-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="c019f-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="c019f-134">次のスクリーンショットは、オンプレミス環境と Azure Storage 環境の両方で作成された新しいデータベースを示しています。</span><span class="sxs-lookup"><span data-stu-id="c019f-134">The following screenshot demonstrates the new created database both in on-premises and Azure Storage environment.</span></span>  
  
 <span data-ttu-id="c019f-135">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="c019f-135">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="c019f-136">**注:** コンテナー内のデータファイルに対するアクティブな参照が存在する場合、関連付けられている SQL Server 資格情報を削除しようとすると失敗します。</span><span class="sxs-lookup"><span data-stu-id="c019f-136">**Note:** If there are any active references to data files in a container, any attempts to delete the associated SQL Server credential fails.</span></span> <span data-ttu-id="c019f-137">同様に、既に BLOB の特定のデータベース ファイルにリースが設定されていて、そのデータベースを削除する場合、まず、BLOB のリースを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c019f-137">Similarly, if there is already a lease on a specific database file in a blob and you want to delete it, first you need to break the lease on the blob.</span></span> <span data-ttu-id="c019f-138">リースを中断するには、[リース Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c019f-138">To break the lease, you can use [Lease Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx).</span></span>  
  
 <span data-ttu-id="c019f-139">この新しい機能を使用して、CREATE DATABASE ステートメントの既定値がクラウド対応データベースになるように、SQL Server を構成できます。</span><span class="sxs-lookup"><span data-stu-id="c019f-139">Using this new feature, you can configure SQL Server so that any CREATE DATABASE statement will default to a cloud enabled database.</span></span> <span data-ttu-id="c019f-140">つまり、データベースを作成するたびに、すべてのデータベースファイル (.mdf、.ldf) が Azure Storage のページ blob として作成されるように、SQL Server Management Studio サーバーインスタンスのプロパティで既定のデータとログの場所を設定できます。</span><span class="sxs-lookup"><span data-stu-id="c019f-140">In other words, you can set default data and log locations in SQL Server Management Studio Server instance properties so anytime you create a database, all database files (.mdf, .ldf) are created as page blobs in Azure Storage.</span></span>  
  
 <span data-ttu-id="c019f-141">SQL Server Management Studio ユーザーインターフェイスを使用して Azure Storage でデータベースを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c019f-141">To create a database in Azure Storage by using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="c019f-142">オブジェクト エクスプローラーで、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="c019f-142">In Object Explorer, connect to an instance of the SQL Server Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c019f-143">[データベース] を右クリックし、[新しいデータベース] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c019f-143">Right-click Databases, and then click New Database.</span></span>  
  
3.  <span data-ttu-id="c019f-144">[新しいデータベース] ダイアログ ウィンドウで、データベース名を入力します。</span><span class="sxs-lookup"><span data-stu-id="c019f-144">In the New Database dialog window, type a database name.</span></span>  
  
4.  <span data-ttu-id="c019f-145">プライマリ データ ファイルとトランザクション ログ ファイルの既定値を変更します。[データベース ファイル] グリッドで該当するセルをクリックして、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="c019f-145">Change the default values of the primary data and transaction log files, in the Database files grid, click the appropriate cell and enter the new value.</span></span> <span data-ttu-id="c019f-146">また、ファイルの場所のパスも指定します。</span><span class="sxs-lookup"><span data-stu-id="c019f-146">Also, specify the path for the file location.</span></span> <span data-ttu-id="c019f-147">パスとしては、ストレージ コンテナーの URL パスを入力します (たとえば、`https://teststorageaccnt.blob.core.windows.net/testcontainer/`)。</span><span class="sxs-lookup"><span data-stu-id="c019f-147">For Path, type the URL path of the storage container, such as `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.</span></span> <span data-ttu-id="c019f-148">ファイル名としては、データベース ファイル (.mdf、.ldf) の物理ファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="c019f-148">For FileName, type the physical file names of the database files (.mdf, .ldf).</span></span>  
  
     <span data-ttu-id="c019f-149">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="c019f-149">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")</span></span>  
  
     <span data-ttu-id="c019f-150">詳細については、「 [データベースに対するデータ ファイルまたはログ ファイルの追加](databases/add-data-or-log-files-to-a-database.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c019f-150">For more information, see [Add Data or Log Files to a Database](databases/add-data-or-log-files-to-a-database.md).</span></span>  
  
5.  <span data-ttu-id="c019f-151">その他の値は既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="c019f-151">Keep all other default values.</span></span>  
  
6.  <span data-ttu-id="c019f-152">[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c019f-152">Click OK.</span></span>  
  
 <span data-ttu-id="c019f-153">内部設置型 SQL Server の新しい TestDB1 を表示するには、オブジェクト エクスプローラーでデータベースの表示を更新します。</span><span class="sxs-lookup"><span data-stu-id="c019f-153">To see the new TestDB1 in your on-premises SQL Server, refresh databases in the Object Explorer.</span></span> <span data-ttu-id="c019f-154">同様に、ストレージ アカウントに新しく作成したデータベースを表示するには、このレッスンの前の方で説明したように、SQL Server Management Studio (SSMS) 経由でストレージ アカウントに接続します。</span><span class="sxs-lookup"><span data-stu-id="c019f-154">Similarly, to see the newly created database in your storage account, connect to your storage account via SQL Server Management Studio (SSMS) as explained earlier in this lesson.</span></span>  
  
 <span data-ttu-id="c019f-155">**次のレッスン:**</span><span class="sxs-lookup"><span data-stu-id="c019f-155">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="c019f-156">レッスン 5.&#40;オプション&#41; TDE を使用してデータベースを暗号化する</span><span class="sxs-lookup"><span data-stu-id="c019f-156">Lesson 5. &#40;Optional&#41; Encrypt your database using TDE</span></span>](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  
