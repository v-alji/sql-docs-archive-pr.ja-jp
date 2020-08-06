---
title: 'レッスン 9: Azure Storage からのデータベースの復元 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5e7c2350bb2a9b1f8c31da8e094459b5bc8ccd90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645043"
---
# <a name="lesson-9-restore-a-database-from-azure-storage"></a><span data-ttu-id="f325e-103">レッスン 9:</span><span class="sxs-lookup"><span data-stu-id="f325e-103">Lesson 9.</span></span> <span data-ttu-id="f325e-104">Azure Storage からデータベースを復元する</span><span class="sxs-lookup"><span data-stu-id="f325e-104">Restore a database from Azure Storage</span></span>
  <span data-ttu-id="f325e-105">このレッスンでは、データベースバックアップファイルを Azure Storage からデータベースに復元する方法について説明します。このデータベースは、オンプレミスまたは Azure の仮想マシンに存在します。</span><span class="sxs-lookup"><span data-stu-id="f325e-105">In this lesson, you will learn how to restore a database backup file from Azure Storage to a database, which either resides on-premises or in a virtual machine in Azure.</span></span> <span data-ttu-id="f325e-106">このレッスンを続行するには、レッスン 4、5、6、7 および 8 を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f325e-106">To follow this lesson, you do not need to complete Lesson 4, 5, 6, 7, and 8.</span></span>  
  
 <span data-ttu-id="f325e-107">このレッスンでは、次の手順を既に完了していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f325e-107">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="f325e-108">ソース コンピューターにデータベースを作成しました。</span><span class="sxs-lookup"><span data-stu-id="f325e-108">You have created a database in the source machine.</span></span>  
  
-   <span data-ttu-id="f325e-109">「 [Azure Blob Storage サービスを使用したバックアップと復元](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」機能を使用して SQL Server、Azure Storage でデータベース (.bak) のバックアップを作成しました。</span><span class="sxs-lookup"><span data-stu-id="f325e-109">You have created a backup of your database (.bak) in Azure Storage by using the [SQL Server Backup and Restore with Azure Blob Storage Service](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) feature.</span></span> <span data-ttu-id="f325e-110">この手順では、SQL Server 資格情報をもう 1 つ作成する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f325e-110">Note that you will need to create another SQL Server Credential in this step.</span></span> <span data-ttu-id="f325e-111">この資格情報はストレージ アカウント キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f325e-111">This credential uses storage account keys.</span></span>  
  
-   <span data-ttu-id="f325e-112">Azure Storage アカウントを持っています。</span><span class="sxs-lookup"><span data-stu-id="f325e-112">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="f325e-113">Azure Storage アカウントでコンテナーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="f325e-113">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="f325e-114">読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="f325e-114">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="f325e-115">SAS キーも生成しました。</span><span class="sxs-lookup"><span data-stu-id="f325e-115">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="f325e-116">Azure Storage 統合機能用のコンピューターに SQL Server 資格情報を作成しました。</span><span class="sxs-lookup"><span data-stu-id="f325e-116">You have created a SQL Server credential on your machine for Azure Storage Integration feature.</span></span> <span data-ttu-id="f325e-117">この資格情報には Shared Access Signature (SAS) キーが必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f325e-117">Note that this credential requires a Shared Access Signature (SAS) key.</span></span>  
  
 <span data-ttu-id="f325e-118">Azure Storage からデータベースを復元するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f325e-118">To restore a database from Azure Storage, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="f325e-119">SQL Server Management Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="f325e-119">Start SQL Server Management Studio.</span></span> <span data-ttu-id="f325e-120">既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f325e-120">Connect to the default instance.</span></span>  
  
2.  <span data-ttu-id="f325e-121">[標準] ツールバーの [**新しいクエリ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f325e-121">Click **New Query** on the Standard Toolbar.</span></span>  
  
3.  <span data-ttu-id="f325e-122">次の完全なスクリプトをコピーして、クエリ ウィンドウに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f325e-122">Copy and paste the following complete script to the query window.</span></span> <span data-ttu-id="f325e-123">必要に応じて、スクリプトを変更します。</span><span class="sxs-lookup"><span data-stu-id="f325e-123">Modify the script as needed.</span></span>  
  
     <span data-ttu-id="f325e-124">**注:** ステートメントを実行して、 `RESTORE` Azure Storage 内のデータベースバックアップ (.bak) を別のコンピューターのデータベースインスタンスに復元します。</span><span class="sxs-lookup"><span data-stu-id="f325e-124">**Note:** You run the `RESTORE` statement to restore the database backup (.bak) in Azure Storage to a database instance in another machine.</span></span>  
  
    ```sql  
  
    USE master   
    GO   
    -- Create a new database to be backed up.   
    CREATE DATABASE TestDbRestoreFrom;   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    SELECT * from dbo.Table1;   
    GO   
    -- Create a credential to be used by SQL Server Backup and Restore with Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Azure Storage.   
    BACKUP DATABASE TestDBRestoreFrom    
    TO URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
          WITH CREDENTIAL = 'BackupCredential'    
         ,COMPRESSION   
         ,STATS = 5;   
    GO    
    -- Create a Shared Access Signature credential   
    CREATE CREDENTIAL [https://teststorageaccnt.blob.core.windows.net/testrestorefrom]   
    WITH IDENTITY='SHARED ACCESS SIGNATURE',   
    SECRET = 'sv=2012-02-12&sr=c&si=policy_resfrom&sig=EhVpzLUXjG4ThAMLmVhrnoiCt8IfmD3BsuYiMawGzxc%3D'   
    GO   
    USE master;   
    GO   
    RESTORE DATABASE TestDBRestoreFrom    
    FROM URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
    WITH    
    CREDENTIAL = 'BackupCredential',    
    REPLACE,   
    MOVE 'TestDBRestoreFrom' TO 'C:\Backup\TestDBRestoreFrom.mdf',     
    MOVE 'TestDBRestoreFrom_log' TO 'C:\Backup\TestDBRestoreFrom_log.ldf';   
    GO  
  
    ```  
  
 <span data-ttu-id="f325e-125">**チュートリアルの最後: Azure Storage サービスのデータファイルの SQL Server**</span><span class="sxs-lookup"><span data-stu-id="f325e-125">**End of Tutorial: SQL Server Data Files in Azure Storage service**</span></span>  
  
  
