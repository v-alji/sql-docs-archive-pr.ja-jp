---
title: 'チュートリアル: Azure Storage サービスでのデータファイルの SQL Server |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 21a0fc11706a0c5ee35cf71e1af69f2927adc9db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645467"
---
# <a name="tutorial-sql-server-data-files-in-azure-storage-service"></a><span data-ttu-id="b195b-102">チュートリアル:Azure Storage サービス内の SQL Server データ ファイル</span><span class="sxs-lookup"><span data-stu-id="b195b-102">Tutorial: SQL Server Data Files in Azure Storage service</span></span>
  <span data-ttu-id="b195b-103">Azure Storage サービスでのデータファイルの SQL Server に関するチュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="b195b-103">Welcome to the  SQL Server Data Files in Azure Storage Service tutorial.</span></span> <span data-ttu-id="b195b-104">このチュートリアルを読むと、Azure Blob Storage サービスに SQL Server データ ファイルを直接格納する方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="b195b-104">This tutorial helps you understand how to store SQL Server data files in the Azure Blob storage service directly.</span></span>  
  
 <span data-ttu-id="b195b-105">Azure Blob ストレージサービスの SQL Server 統合サポートは、SQL Server 2014 の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b195b-105">SQL Server integration support for the Azure Blob storage service is a SQL Server 2014 enhancement.</span></span> <span data-ttu-id="b195b-106">この機能を使用する場合の機能と利点の概要については、「 [Azure でのデータファイルの SQL Server](databases/sql-server-data-files-in-microsoft-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b195b-106">For an overview of the functionality and benefits of using this functionality, see [SQL Server Data Files in Azure](databases/sql-server-data-files-in-microsoft-azure.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="b195b-107">学習する内容</span><span class="sxs-lookup"><span data-stu-id="b195b-107">What you will learn</span></span>  
 <span data-ttu-id="b195b-108">このチュートリアルでは、複数のレッスンで Azure Storage サービスに SQL Server データファイルを格納する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b195b-108">This tutorial shows you how to store SQL Server Data Files in Azure Storage service in multiple lessons.</span></span> <span data-ttu-id="b195b-109">各レッスンでは特定のタスクに重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="b195b-109">Each lesson is focused on a specific task.</span></span> <span data-ttu-id="b195b-110">まず、Azure でストレージアカウントとコンテナーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b195b-110">First, you will learn how to create a storage account and a container in Azure.</span></span> <span data-ttu-id="b195b-111">次に、SQL Server を Azure Storage と統合できるように SQL Server 資格情報を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b195b-111">Then, you will learn how to create a SQL Server credential to be able to integrate SQL Server with Azure Storage.</span></span> <span data-ttu-id="b195b-112">次に、Azure Storage でデータベースを直接作成します。</span><span class="sxs-lookup"><span data-stu-id="b195b-112">Then, you will create a database in Azure Storage directly.</span></span> <span data-ttu-id="b195b-113">さらに、暗号化、移行、およびバックアップと復元のシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="b195b-113">In addition, the tutorial will demonstrate encryption, migration, and backup and restore scenarios.</span></span>  
  
 <span data-ttu-id="b195b-114">このチュートリアルは、次の 9 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="b195b-114">This tutorial is divided into nine lessons:</span></span>  
  
 <span data-ttu-id="b195b-115">**[レッスン 1:Azure Storage アカウントとコンテナーを作成する](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-115">**[Lesson 1: Create Azure Storage Account and Container](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**</span></span>  
 <span data-ttu-id="b195b-116">このレッスンでは、Azure Storage アカウントとコンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b195b-116">In this lesson, you create an Azure Storage account and a container.</span></span>  
  
 <span data-ttu-id="b195b-117">**[レッスン2。コンテナーでポリシーを作成し、SAS&#41; キー &#40;Shared Access Signature を生成する](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-117">**[Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**</span></span>  
 <span data-ttu-id="b195b-118">このレッスンでは、BLOB コンテナーのポリシーを作成し、Shared Access Signature を生成します。</span><span class="sxs-lookup"><span data-stu-id="b195b-118">In this lesson, you create a policy on the Blob container and also generate a shared access signature.</span></span>  
  
 <span data-ttu-id="b195b-119">**[レッスン 3:SQL Server 資格情報の作成](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-119">**[Lesson 3: Create a SQL Server Credential](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**</span></span>  
 <span data-ttu-id="b195b-120">このレッスンでは、Azure ストレージ アカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="b195b-120">In this lesson, you create a Credential to store security information used to access the Azure storage account.</span></span>  
  
 <span data-ttu-id="b195b-121">**[レッスン 4:Azure Storage にデータベースを作成する](../relational-databases/lesson-3-database-backup-to-url.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-121">**[Lesson 4: Create a database in Azure Storage](../relational-databases/lesson-3-database-backup-to-url.md)**</span></span>  
 <span data-ttu-id="b195b-122">このレッスンでは、CREATE Database FILENAME オプションを使用して Azure Storage でデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="b195b-122">In this lesson, you create a database in Azure Storage using CREATE Database FILENAME option.</span></span>  
  
 <span data-ttu-id="b195b-123">**[レッスン 5.&#40;オプション&#41; TDE を使用してデータベースを暗号化する](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-123">**[Lesson 5. &#40;Optional&#41; Encrypt your database using TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**</span></span>  
 <span data-ttu-id="b195b-124">このレッスンでは、透過的なデータ暗号化 (TDE) およびサーバー証明書を使用してデータベースを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="b195b-124">In this lesson, you encrypt your database by using a transparent data encryption (TDE) and a server certificate.</span></span>  
  
 <span data-ttu-id="b195b-125">**[レッスン 6: オンプレミスのソース コンピューターから Azure のターゲット コンピューターにデータベースを移行する](lesson-5-backup-database-using-file-snapshot-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-125">**[Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**</span></span>  
 <span data-ttu-id="b195b-126">このレッスンでは、CREATE DATABASE FOR ATTACH オプションを使用して、オンプレミスから Azure の仮想マシンにデータベースを移行します。</span><span class="sxs-lookup"><span data-stu-id="b195b-126">In this lesson, you migrate a database from on-premises to a virtual machine in Azure using CREATE DATABASE FOR ATTACH option.</span></span>  
  
 <span data-ttu-id="b195b-127">**[レッスン 7: Azure Storage にデータ ファイルを移動する](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-127">**[Lesson 7: Move your data files to Azure Storage](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**</span></span>  
 <span data-ttu-id="b195b-128">このレッスンでは、ALTER DATABASE ステートメントを使用して、データファイルを Azure Storage に移動します。</span><span class="sxs-lookup"><span data-stu-id="b195b-128">In this lesson, you move your data files to Azure Storage using ALTER DATABASE statement.</span></span>  
  
 <span data-ttu-id="b195b-129">**[レッスン8。Azure Storage にデータベースを復元する](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-129">**[Lesson 8. Restore a database to Azure Storage](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**</span></span>  
 <span data-ttu-id="b195b-130">このレッスンでは、RESTORE Database MOVE オプションを使用して Azure Storage するようにデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="b195b-130">In this lesson, you restore a database to Azure Storage using RESTORE Database MOVE option.</span></span>  
  
 <span data-ttu-id="b195b-131">**[レッスン 9.Azure Storage からデータベースを復元する](lesson-8-restore-as-new-database-from-log-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="b195b-131">**[Lesson 9. Restore a database from Azure Storage](lesson-8-restore-as-new-database-from-log-backup.md)**</span></span>  
 <span data-ttu-id="b195b-132">このレッスンでは、RESTORE Database MOVE オプションを使用して Azure Storage からデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="b195b-132">In this lesson, you restore a database from Azure Storage using RESTORE Database MOVE option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b195b-133">参照</span><span class="sxs-lookup"><span data-stu-id="b195b-133">See Also</span></span>  
 [<span data-ttu-id="b195b-134">Azure 内の SQL Server データ ファイル</span><span class="sxs-lookup"><span data-stu-id="b195b-134">SQL Server Data Files in Azure</span></span>](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
