---
title: 'レッスン 7: データファイルを Azure Storage に移動する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 753863d7b8b8d8fa554f1579bee6837c525efd9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643331"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a><span data-ttu-id="9a109-102">レッスン 7: Azure Storage にデータ ファイルを移動する</span><span class="sxs-lookup"><span data-stu-id="9a109-102">Lesson 7: Move your data files to Azure Storage</span></span>
  <span data-ttu-id="9a109-103">このレッスンでは、(SQL Server インスタンスではなく) Azure Storage にデータファイルを移動する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="9a109-103">In this lesson, you will learn how to move your data files to Azure Storage (but not your SQL Server instance).</span></span> <span data-ttu-id="9a109-104">このレッスンを続行するには、レッスン 4、5、および 6 を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9a109-104">To follow this lesson, you do not need to complete Lesson 4, 5, and 6.</span></span>  
  
 <span data-ttu-id="9a109-105">データファイルを Azure Storage に移動するには、ステートメントを使用し `ALTER DATABASE` ます。これは、データファイルの場所を変更するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9a109-105">To move your data files to Azure Storage, you can use the `ALTER DATABASE` statement as it helps to change the location of the data files.</span></span>  
  
 <span data-ttu-id="9a109-106">このレッスンでは、次の手順を既に完了していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="9a109-106">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="9a109-107">Azure Storage アカウントを持っています。</span><span class="sxs-lookup"><span data-stu-id="9a109-107">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="9a109-108">Azure Storage アカウントでコンテナーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="9a109-108">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="9a109-109">読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="9a109-109">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="9a109-110">SAS キーも生成しました。</span><span class="sxs-lookup"><span data-stu-id="9a109-110">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="9a109-111">ソース コンピューターで SQL Server 資格情報を作成しました。</span><span class="sxs-lookup"><span data-stu-id="9a109-111">You have created a SQL Server credential on the source machine.</span></span>  
  
 <span data-ttu-id="9a109-112">次に、次の手順を使用して、データファイルを Azure Storage に移動します。</span><span class="sxs-lookup"><span data-stu-id="9a109-112">Next, use the following steps to move your data files to Azure Storage:</span></span>  
  
1.  <span data-ttu-id="9a109-113">まず、ソース コンピューターにテスト データベースを作成し、それにデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="9a109-113">First, create a test database in the source machine and add some data to it.</span></span>  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  <span data-ttu-id="9a109-114">次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a109-114">Run the following code:</span></span>  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  <span data-ttu-id="9a109-115">これを実行すると、システムカタログで "ファイル" TestDB1Alter "が変更されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="9a109-115">When you run this, you will see this message: "The file "TestDB1Alter" has been modified in the system catalog.</span></span> <span data-ttu-id="9a109-116">新しいパスは、次回データベースを起動するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a109-116">The new path will be used the next time the database is started."</span></span>  
  
4.  <span data-ttu-id="9a109-117">続いて、データベースをオフラインにします。</span><span class="sxs-lookup"><span data-stu-id="9a109-117">Then, set the database offline.</span></span>  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  <span data-ttu-id="9a109-118">次に、 [Azcopy ツール](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs)、 [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx)、 [storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx)、またはサードパーティのストレージエクスプローラーツールのいずれかの方法を使用して、データファイルを Azure Storage にコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a109-118">Now, you need to copy the data files to Azure Storage by using one of the following methods: [AzCopy Tool](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx), or a third-party storage explorer tool.</span></span>  
  
     <span data-ttu-id="9a109-119">**重要:** この新しい機能強化を使用する場合は、必ずブロック blob ではなくページ blob を作成してください。</span><span class="sxs-lookup"><span data-stu-id="9a109-119">**Important:** When using this new enhancement, always make sure that you create a page blob not a block blob.</span></span>  
  
6.  <span data-ttu-id="9a109-120">続いて、データベースをオンラインにします。</span><span class="sxs-lookup"><span data-stu-id="9a109-120">Then, set the database online.</span></span>  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 <span data-ttu-id="9a109-121">**次のレッスン:**</span><span class="sxs-lookup"><span data-stu-id="9a109-121">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="9a109-122">レッスン8。Azure Storage にデータベースを復元する</span><span class="sxs-lookup"><span data-stu-id="9a109-122">Lesson 8. Restore a database to Azure Storage</span></span>](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
