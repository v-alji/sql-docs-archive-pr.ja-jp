---
title: 'レッスン 4: データベースの完全バックアップからの復元を実行する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9906ea14c2f76a49644a8f76fbd894adf8b9d500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639834"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a><span data-ttu-id="a5a32-102">レッスン 4:データベースの完全バックアップからの復元の実行</span><span class="sxs-lookup"><span data-stu-id="a5a32-102">Lesson 4: Perform a Restore From a Full Database Backup</span></span>
  <span data-ttu-id="a5a32-103">このレッスンでは、TSQL ステートメントを使用して、前のレッスンで作成したデータベースの完全バックアップからの復元を実行する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="a5a32-103">This lesson demonstrates the use of a tsql statement to perform a restore from a full database backup created in the previous lesson.</span></span>  
  
## <a name="perform-a-restore-of-a-database-backup"></a><span data-ttu-id="a5a32-104">データベース バックアップの復元の実行</span><span class="sxs-lookup"><span data-stu-id="a5a32-104">Perform a Restore of a Database Backup</span></span>  
 <span data-ttu-id="a5a32-105">データベースの完全バックアップを復元するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a5a32-105">To restore a full database backup, use the following steps:</span></span>  
  
1.  <span data-ttu-id="a5a32-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="a5a32-106">Connect to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="a5a32-107">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a5a32-107">In the **Object Explorer**, connect to the instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
3.  <span data-ttu-id="a5a32-108">[標準] メニュー バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a32-108">On the Standard menu bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="a5a32-109">次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="a5a32-109">Copy and paste the following example into the query window, modify as needed.</span></span>  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  <span data-ttu-id="a5a32-110">T-sql ステートメントを確認し、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a32-110">Verify the T-SQL statement and click **Execute**</span></span>  
  
### <a name="return-to-tutorials-portal"></a><span data-ttu-id="a5a32-111">チュートリアル ポータルに戻る</span><span class="sxs-lookup"><span data-stu-id="a5a32-111">Return to Tutorials Portal</span></span>  
 <span data-ttu-id="a5a32-112">[チュートリアル: Azure Blob Storage サービスへのバックアップと復元を SQL Server](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)します。</span><span class="sxs-lookup"><span data-stu-id="a5a32-112">[Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).</span></span>  
  
  
