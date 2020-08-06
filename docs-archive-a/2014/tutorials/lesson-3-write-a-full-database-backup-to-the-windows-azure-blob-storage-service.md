---
title: 'レッスン 3: Azure Blob Storage サービスにデータベースの完全バックアップを書き込む |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 17e7e6b608d248a48cde52f1107bb910f06d64ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711201"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-azure-blob-storage-service"></a><span data-ttu-id="b66d5-102">レッスン 3:Azure Blob Storage サービスに対するデータベースの完全バックアップの書き込み</span><span class="sxs-lookup"><span data-stu-id="b66d5-102">Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service</span></span>
  <span data-ttu-id="b66d5-103">このレッスンでは、tsql ステートメントを使用して、Azure Blob ストレージサービスへのデータベースの完全バックアップを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b66d5-103">This lesson demonstrates the use of tsql statement to perform a full database backup to Azure Blob storage service.</span></span>  
  
## <a name="perform-a-full-database-backup-to-the-azure-blob-storage-service"></a><span data-ttu-id="b66d5-104">Azure Blob Storage サービスへのデータベースの完全バックアップを実行する</span><span class="sxs-lookup"><span data-stu-id="b66d5-104">Perform a Full Database Backup to the Azure Blob Storage Service</span></span>  
 <span data-ttu-id="b66d5-105">データベースの完全バックアップを実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b66d5-105">To create a full database backup, use the following steps:</span></span>  
  
1.  <span data-ttu-id="b66d5-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="b66d5-106">Connect to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b66d5-107">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="b66d5-107">In the **Object Explorer**, connect to the instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
3.  <span data-ttu-id="b66d5-108">[標準] メニュー バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b66d5-108">On the Standard menu bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="b66d5-109">次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更して、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b66d5-109">Copy and paste the following example into the query window, modify as needed, and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  <span data-ttu-id="b66d5-110">オブジェクト エクスプローラーで、Azure ストレージに接続します。</span><span class="sxs-lookup"><span data-stu-id="b66d5-110">In the object explorer, connect to Azure Storage.</span></span> <span data-ttu-id="b66d5-111">コンテナーと、新しく作成したバックアップ ファイルを参照して指定します。</span><span class="sxs-lookup"><span data-stu-id="b66d5-111">Browse to find the container and the newly created backup files.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="b66d5-112">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="b66d5-112">Next Lesson</span></span>  
 <span data-ttu-id="b66d5-113">[レッスン 4: データベースの完全バックアップから復元を実行する](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)</span><span class="sxs-lookup"><span data-stu-id="b66d5-113">[Lesson 4: Perform a Restore From a Full Database Backup](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).</span></span>  
  
  
