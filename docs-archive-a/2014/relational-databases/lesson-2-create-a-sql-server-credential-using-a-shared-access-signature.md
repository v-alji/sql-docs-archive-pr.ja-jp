---
title: 'レッスン 3: SQL Server の資格情報を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 808438e544e3beb18b2e2afa9c399b5666277483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739919"
---
# <a name="lesson-3-create-a-sql-server-credential"></a><span data-ttu-id="824c3-102">レッスン 3:SQL Server 資格情報の作成</span><span class="sxs-lookup"><span data-stu-id="824c3-102">Lesson 3: Create a SQL Server Credential</span></span>
  <span data-ttu-id="824c3-103">このレッスンでは、Azure ストレージアカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="824c3-103">In this lesson, you will create a credential to store security information used to access the Azure storage account.</span></span>  
  
 <span data-ttu-id="824c3-104">SQL Server 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="824c3-104">A SQL Server credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span> <span data-ttu-id="824c3-105">資格情報には、ストレージ コンテナーの URI パスと Shared Access Signature キー値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="824c3-105">The credential stores the URI path of the storage container and the shared access signature key values.</span></span> <span data-ttu-id="824c3-106">データ ファイルまたはログ ファイルによって使用されるストレージ コンテナーごとに、名前がコンテナーのパスに一致する SQL Server 資格情報を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="824c3-106">For each storage container used by a data or log file, you must create a SQL Server Credential whose name matches the container path.</span></span>  
  
 <span data-ttu-id="824c3-107">資格情報の全般的な情報については、「[資格情報 &#40;データベースエンジン&#41;](security/authentication-access/credentials-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="824c3-107">For general information about credentials, see [Credentials &#40;Database Engine&#41;](security/authentication-access/credentials-database-engine.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="824c3-108">以下で説明する SQL Server 資格情報を作成するための要件は、 [Azure 機能の SQL Server データファイル](databases/sql-server-data-files-in-microsoft-azure.md)に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="824c3-108">The requirements for creating a SQL Server credential described below are specific to the [SQL Server Data Files in Azure](databases/sql-server-data-files-in-microsoft-azure.md) feature.</span></span> <span data-ttu-id="824c3-109">Azure storage でのバックアッププロセス用の資格情報の作成の詳細については、「[レッスン 2: SQL Server 資格情報の作成](../tutorials/lesson-2-create-a-sql-server-credential.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="824c3-109">For information on creating credentials for backup processes in Azure storage, see [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
 <span data-ttu-id="824c3-110">SQL Server 資格情報を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="824c3-110">To create a SQL Server Credential, follow these steps:</span></span>  
  
1.  <span data-ttu-id="824c3-111">SQL Server Management Studio に接続します。</span><span class="sxs-lookup"><span data-stu-id="824c3-111">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="824c3-112">オブジェクト エクスプローラーで、インストールしたデータベース エンジンのインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="824c3-112">In Object Explorer, connect to the instance of Database Engine installed.</span></span>  
  
3.  <span data-ttu-id="824c3-113">[標準] ツール バーの [新しいクエリ]をクリックします。</span><span class="sxs-lookup"><span data-stu-id="824c3-113">On the Standard tool bar, click New Query.</span></span>  
  
4.  <span data-ttu-id="824c3-114">次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="824c3-114">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="824c3-115">次のステートメントは、ストレージコンテナーの共有アクセス証明書を格納するための SQL Server 資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="824c3-115">The following statement will create a SQL Server Credential to store your storage container's Shared Access Certificate.</span></span>  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     <span data-ttu-id="824c3-116">詳細については、SQL Server オンラインブックの「 [CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="824c3-116">For detailed information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) in SQL Server Books Online.</span></span>  
  
5.  <span data-ttu-id="824c3-117">使用可能なすべての資格情報を表示するには、クエリ ウィンドウで次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="824c3-117">To see all available credentials, you can run the following statement in the query window:</span></span>  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     <span data-ttu-id="824c3-118">詳細については、「」を参照してください。資格情報の詳細については、SQL Server オンラインブックで[&#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="824c3-118">For more information on sys.credentials, see [sys.credentials &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="824c3-119">**次のレッスン:**</span><span class="sxs-lookup"><span data-stu-id="824c3-119">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="824c3-120">レッスン 4:Azure Storage にデータベースを作成する</span><span class="sxs-lookup"><span data-stu-id="824c3-120">Lesson 4: Create a database in Azure Storage</span></span>](lesson-3-database-backup-to-url.md)  
  
  
