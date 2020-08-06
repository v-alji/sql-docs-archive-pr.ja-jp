---
title: 'チュートリアル: Azure Blob Storage サービスへの SQL Server のバックアップと復元 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
ms.openlocfilehash: d15200968011cdb314829736512f39730782dc0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713021"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a><span data-ttu-id="3cfcc-102">チュートリアル:Azure Blob Storage サービスへの SQL Server のバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="3cfcc-102">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>
  <span data-ttu-id="3cfcc-103">Azure Blob Storage サービスを使用した SQL Server のバックアップと復元に関するチュートリアルのはじめにへようこそ。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-103">Welcome to the Getting Started with SQL Server Backup and Restore with Azure Blob Storage Service tutorial.</span></span> <span data-ttu-id="3cfcc-104">このチュートリアルで、Azure Blob Storage サービスへのバックアップの書き込みと、Azure Blob Storage サービスからの復元を実行する方法について学習できます。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-104">This tutorial helps you understand how to write backups to and restore from the Azure Blob storage service.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="3cfcc-105">学習する内容</span><span class="sxs-lookup"><span data-stu-id="3cfcc-105">What You Will Learn</span></span>  
 <span data-ttu-id="3cfcc-106">このチュートリアルでは、Windows ストレージ アカウント、BLOB コンテナーを作成し、ストレージ アカウントにアクセスするための資格情報の作成、BLOB サービスへのバックアップの書き込み、簡単な復元の実行を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-106">This tutorial shows you how to create a Windows Storage account, a blob container, creating credentials to access the storage account, writing a backup to the blob service, and performing a simple restore.</span></span> <span data-ttu-id="3cfcc-107">このチュートリアルは、次の 4 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-107">This tutorial is divided into four lessons:</span></span>  
  
 [<span data-ttu-id="3cfcc-108">レッスン 1: Azure Storage オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="3cfcc-108">Lesson 1: Create Azure Storage Objects</span></span>](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 <span data-ttu-id="3cfcc-109">このレッスンでは、Azure ストレージ アカウントおよび BLOB コンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-109">In this lesson, you create an Azure storage account and a blob container.</span></span>  
  
 [<span data-ttu-id="3cfcc-110">レッスン 2: SQL Server 資格情報の作成</span><span class="sxs-lookup"><span data-stu-id="3cfcc-110">Lesson 2: Create a SQL Server Credential</span></span>](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 <span data-ttu-id="3cfcc-111">このレッスンでは、Azure ストレージ アカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-111">In this lesson, you create a Credential to store security information used to access the Azure storage account.</span></span>  
  
 [<span data-ttu-id="3cfcc-112">レッスン 3:Azure Blob Storage サービスに対するデータベースの完全バックアップの書き込み</span><span class="sxs-lookup"><span data-stu-id="3cfcc-112">Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service</span></span>](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 <span data-ttu-id="3cfcc-113">このレッスンでは、T-SQL ステートメントを実行して、Azure Blob Storage サービスに AdventureWorks2012 データベースのバックアップを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-113">In this lesson, you issue a T-SQL statement to write a backup of the AdventureWorks2012 database to the Azure Blob storage service.</span></span>  
  
 [<span data-ttu-id="3cfcc-114">レッスン 4:データベースの完全バックアップからの復元の実行</span><span class="sxs-lookup"><span data-stu-id="3cfcc-114">Lesson 4: Perform a Restore From a Full Database Backup</span></span>](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 <span data-ttu-id="3cfcc-115">このレッスンでは、T-SQL ステートメントを実行して、前のレッスンで作成したデータベース バックアップから復元します。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-115">In this lesson, you issue a T-SQL statement to restore from the database backup you created in the previous lesson.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="3cfcc-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="3cfcc-116">Requirements</span></span>  
 <span data-ttu-id="3cfcc-117">このチュートリアルを完了するには、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップと復元の概念と T-SQL 構文についての知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-117">To complete this tutorial, you must be familiar with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore concepts and T-SQL syntax.</span></span> <span data-ttu-id="3cfcc-118">このチュートリアルを使用するには、以下のシステム要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-118">To use this tutorial, your system must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="3cfcc-119">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンス、およびインストールされた AdventureWorks2012 データベース。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-119">An instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], and AdventureWorks2012 database installed.</span></span>  
  
     <span data-ttu-id="3cfcc-120">SQL Server インスタンスは、オンプレミスと Azure Virtual Machine のどちらに存在してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-120">The SQL Server instance can be on-premises or in an Azure Virtual Machine.</span></span>  
  
     <span data-ttu-id="3cfcc-121">AdventureWorks2012 の代わりにユーザー データベースを使用し、それに応じて TSQL コマンド構文を変更できます。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-121">You can use a user database in place of AdventureWorks2012, and modify the tsql syntax accordingly.</span></span>  
  
-   <span data-ttu-id="3cfcc-122">BACKUP コマンドまたは RESTORE コマンドの発行に使用するユーザー アカウントは、 **資格情報の変更** 権限を持つ **db_backup operator** データベース ロールに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-122">The user account that is used to issue BACKUP or RESTORE commands should be in the **db_backup operator** database role with **Alter any credential** permissions.</span></span>  
  
### <a name="additional-reading"></a><span data-ttu-id="3cfcc-123">追加の参考資料</span><span class="sxs-lookup"><span data-stu-id="3cfcc-123">Additional Reading</span></span>  
 <span data-ttu-id="3cfcc-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップに Azure Blob Storage サービスを使用する場合の概念やベスト プラクティスについて、次の推奨トピックで説明しています。</span><span class="sxs-lookup"><span data-stu-id="3cfcc-124">Following are some recommended reading to understand the concepts, best practices when using Azure Blob storage service for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backups.</span></span>  
  
1.  [<span data-ttu-id="3cfcc-125">Azure Blob Storage サービスを使った SQL Server のバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="3cfcc-125">SQL Server Backup and Restore with Azure Blob Storage Service</span></span>](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [<span data-ttu-id="3cfcc-126">SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3cfcc-126">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
