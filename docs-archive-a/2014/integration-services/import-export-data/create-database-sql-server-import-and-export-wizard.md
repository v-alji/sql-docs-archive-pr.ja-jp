---
title: '[データベースの作成] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createdatabase.f1
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 617b3fe10a17ae2d8659b51e85cdb3fed4470506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642899"
---
# <a name="create-database-sql-server-import-and-export-wizard"></a><span data-ttu-id="0427e-102">[データベースの作成] (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="0427e-102">Create Database (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="0427e-103">[**データベースの作成**] ページを使用すると、変換先ファイルの新しいデータベースを定義できます。</span><span class="sxs-lookup"><span data-stu-id="0427e-103">Use the **Create Database** page to define a new database for a destination file.</span></span>  
  
 <span data-ttu-id="0427e-104">このページでは、新しいデータベースの作成に利用できるオプションのサブセットが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0427e-104">This page offers a subset of the available options for creating a new database.</span></span> <span data-ttu-id="0427e-105">すべてのオプションを表示するには、を使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="0427e-105">To view all the options, use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="0427e-106">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0427e-106">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="0427e-107">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0427e-107">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="0427e-108">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="0427e-108">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="0427e-109">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="0427e-109">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="0427e-110">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="0427e-110">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="0427e-111">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0427e-111">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0427e-112">Options</span><span class="sxs-lookup"><span data-stu-id="0427e-112">Options</span></span>  
 <span data-ttu-id="0427e-113">**Name**</span><span class="sxs-lookup"><span data-stu-id="0427e-113">**Name**</span></span>  
 <span data-ttu-id="0427e-114">対象になる SQL Server データベースの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0427e-114">Provide a unique name for the destination SQL Server database.</span></span> <span data-ttu-id="0427e-115">データベースに名前を付けるときは、必ず SQL Server の規約に従ってください。</span><span class="sxs-lookup"><span data-stu-id="0427e-115">Make sure that you follow SQL Server conventions when you name this database.</span></span>  
  
 <span data-ttu-id="0427e-116">**[データ ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="0427e-116">**Data file name**</span></span>  
 <span data-ttu-id="0427e-117">データ ファイルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="0427e-117">View the name of the data file.</span></span> <span data-ttu-id="0427e-118">この名前は、指定されたデータベース名から派生されます。</span><span class="sxs-lookup"><span data-stu-id="0427e-118">This is derived from the database name you provided earlier.</span></span>  
  
 <span data-ttu-id="0427e-119">**ログファイル名**</span><span class="sxs-lookup"><span data-stu-id="0427e-119">**Log file name**</span></span>  
 <span data-ttu-id="0427e-120">ログ ファイルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="0427e-120">View the name of the log file.</span></span> <span data-ttu-id="0427e-121">この名前は、指定されたデータベース名から派生されます。</span><span class="sxs-lookup"><span data-stu-id="0427e-121">This is derived from the database name you provided earlier.</span></span>  
  
 <span data-ttu-id="0427e-122">**[初期サイズ] (データ ファイル)**</span><span class="sxs-lookup"><span data-stu-id="0427e-122">**Initial size (data file)**</span></span>  
 <span data-ttu-id="0427e-123">データ ファイルの初期サイズを MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="0427e-123">Specify the number of megabytes for the initial size of the data file.</span></span>  
  
 <span data-ttu-id="0427e-124">**[拡張を許可しない] (データ ファイル)**</span><span class="sxs-lookup"><span data-stu-id="0427e-124">**No growth allowed (data file)**</span></span>  
 <span data-ttu-id="0427e-125">指定した初期サイズを超えるデータ ファイルの拡張を許可するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="0427e-125">Indicate whether the data file can grow beyond the specified initial size.</span></span>  
  
 <span data-ttu-id="0427e-126">**[比率で拡張する] (データ ファイル)**</span><span class="sxs-lookup"><span data-stu-id="0427e-126">**Grow by percentage (data file)**</span></span>  
 <span data-ttu-id="0427e-127">データ ファイルの拡張を許可する比率を指定します。</span><span class="sxs-lookup"><span data-stu-id="0427e-127">Specify a percentage by which the data file can grow.</span></span>  
  
 <span data-ttu-id="0427e-128">**[サイズで拡張する] (データ ファイル)**</span><span class="sxs-lookup"><span data-stu-id="0427e-128">**Grow by size (data file)**</span></span>  
 <span data-ttu-id="0427e-129">データ ファイルの拡張を許可するサイズを MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="0427e-129">Specify a number of megabytes by which the data file can grow.</span></span>  
  
 <span data-ttu-id="0427e-130">**[初期サイズ] (ログ ファイル)**</span><span class="sxs-lookup"><span data-stu-id="0427e-130">**Initial size (log file)**</span></span>  
 <span data-ttu-id="0427e-131">ログ ファイルの初期サイズを MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="0427e-131">Specify the number of megabytes for the initial size of the log file.</span></span>  
  
 <span data-ttu-id="0427e-132">**[拡張を許可しない] (ログ ファイル)**</span><span class="sxs-lookup"><span data-stu-id="0427e-132">**No growth allowed (log file)**</span></span>  
 <span data-ttu-id="0427e-133">指定した初期サイズを超えるログ ファイルの拡張を許可するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="0427e-133">Indicate whether the log file can grow beyond the specified initial size.</span></span>  
  
 <span data-ttu-id="0427e-134">**[比率で拡張する] (ログ ファイル)**</span><span class="sxs-lookup"><span data-stu-id="0427e-134">**Grow by percentage (log file)**</span></span>  
 <span data-ttu-id="0427e-135">ログ ファイルの拡張を許可する比率を指定します。</span><span class="sxs-lookup"><span data-stu-id="0427e-135">Specify a percentage by which the log file can grow.</span></span>  
  
 <span data-ttu-id="0427e-136">**[サイズで拡張する] (ログ ファイル)**</span><span class="sxs-lookup"><span data-stu-id="0427e-136">**Grow by size (log file)**</span></span>  
 <span data-ttu-id="0427e-137">ログ ファイルの拡張を許可するサイズを MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="0427e-137">Specify a number of megabytes by which the log file can grow.</span></span>  
  
  
