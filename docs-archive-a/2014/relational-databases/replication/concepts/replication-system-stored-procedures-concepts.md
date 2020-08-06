---
title: レプリケーション システム ストアド プロシージャの概念 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server replication], programming
- programming [SQL Server replication], system stored procedures
- programming interfaces [SQL Server replication]
- system stored procedures [SQL Server replication]
- replication [SQL Server], how-to topics
ms.assetid: 816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 50536e5b6816c84dff26c9c9f99c46d02272b7de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741853"
---
# <a name="replication-system-stored-procedures-concepts"></a><span data-ttu-id="4bf58-102">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="4bf58-102">Replication System Stored Procedures Concepts</span></span>
  <span data-ttu-id="4bf58-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、レプリケーション トポロジでユーザーが構成可能なすべての機能に、システム ストアド プロシージャを使ってプログラムからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], programmatic access to all of the user-configurable functionality in a replication topology is provided by system stored procedures.</span></span> <span data-ttu-id="4bf58-104">ストアド プロシージャは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] や sqlcmd コマンド ライン ユーティリティを使って個別に実行することもできますが、一連のレプリケーション タスクを実行する [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプト ファイルを作成することで、その利点を最大限に活かすことができます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-104">While stored procedures may be executed individually using the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or the sqlcmd command-line utility, it may be beneficial to write [!INCLUDE[tsql](../../../includes/tsql-md.md)] script files that can be executed to perform a logical sequence of replication tasks.</span></span>  
  
 <span data-ttu-id="4bf58-105">レプリケーション タスクをスクリプト化することの利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4bf58-105">Scripting replication tasks provides the following benefits:</span></span>  
  
-   <span data-ttu-id="4bf58-106">レプリケーション トポロジを配置するために必要な手順を 1 つにまとめて再利用できる。</span><span class="sxs-lookup"><span data-stu-id="4bf58-106">Keeps a permanent copy of the steps used to deploy your replication topology.</span></span>  
  
-   <span data-ttu-id="4bf58-107">単一のスクリプトを使って複数のサブスクライバーを構成できる。</span><span class="sxs-lookup"><span data-stu-id="4bf58-107">Uses a single script to configure multiple Subscribers.</span></span>  
  
-   <span data-ttu-id="4bf58-108">新人のデータベース管理者がコードを見て処理の内容を理解し、変更やトラブルシューティングに備えることで、迅速に仕事を覚えることができる。</span><span class="sxs-lookup"><span data-stu-id="4bf58-108">Quickly educates new database administrators by enabling them to evaluate, understand, change, or troubleshoot the code.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4bf58-109">スクリプトは、セキュリティ脆弱性の原因となる可能性があります。ユーザーが知らないうちに、またはユーザーが操作しなくても、スクリプトによってシステムの機能を実行することができます。また、セキュリティ資格情報が平文で含まれている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4bf58-109">Scripts can be the source of security vulnerabilities; they can invoke system functions without user knowledge or intervention and may contain security credentials in plain text.</span></span> <span data-ttu-id="4bf58-110">スクリプトを使用する前に、セキュリティの問題がないかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4bf58-110">Review scripts for security issues before you use them.</span></span>  
  
## <a name="creating-replication-scripts"></a><span data-ttu-id="4bf58-111">レプリケーション スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="4bf58-111">Creating Replication Scripts</span></span>  
 <span data-ttu-id="4bf58-112">レプリケーションの観点から言えば、スクリプトは、それぞれがレプリケーションのストアド プロシージャを実行する、1 つまたは複数の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントの集合です。</span><span class="sxs-lookup"><span data-stu-id="4bf58-112">From the standpoint of replication, a script is a series of one or more [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements where each statement executes a replication stored procedure.</span></span> <span data-ttu-id="4bf58-113">スクリプトは、sqlcmd ユーティリティを使って実行できるテキスト ファイルで、一般に、.sql という拡張子が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-113">Scripts are text files, often with a .sql file extension, that can be run using the sqlcmd utility.</span></span> <span data-ttu-id="4bf58-114">スクリプト ファイルを実行すると、そこに格納された SQL ステートメントが sqlcmd ユーティリティによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-114">When a script file is run, the utility executes the SQL statements stored in the file.</span></span> <span data-ttu-id="4bf58-115">同様に、スクリプトをクエリ オブジェクトとして [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] プロジェクトに格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-115">Similarly, a script can be stored as a query object in a [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] project.</span></span>  
  
 <span data-ttu-id="4bf58-116">レプリケーション スクリプトは、以下のような方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-116">Replication scripts can be created in the following ways:</span></span>  
  
-   <span data-ttu-id="4bf58-117">スクリプトを手動で作成する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-117">Manually create the script.</span></span>  
  
-   <span data-ttu-id="4bf58-118">レプリケーション ウィザードのスクリプト生成機能を使用する。または</span><span class="sxs-lookup"><span data-stu-id="4bf58-118">Use the script generation features that are provided in the replication wizards or</span></span>  
  
-   <span data-ttu-id="4bf58-119">[https://login.microsoftonline.com/consumers/]([!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)])</span><span class="sxs-lookup"><span data-stu-id="4bf58-119">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4bf58-120">詳しくは、「 [Scripting Replication](../scripting-replication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4bf58-120">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
-   <span data-ttu-id="4bf58-121">レプリケーション管理オブジェクト (RMO) を使用し、RMO オブジェクトを作成するためのスクリプトをプログラムから生成する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-121">Use Replication Management Objects (RMOs) to programmatically generate the script to create an RMO object.</span></span>  
  
 <span data-ttu-id="4bf58-122">レプリケーション スクリプトを手動で作成する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="4bf58-122">When you manually create replication scripts, keep the following considerations in mind:</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="4bf58-123">スクリプトは 1 つ以上のバッチを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-123">scripts have one or more batches.</span></span> <span data-ttu-id="4bf58-124">GO コマンドによってバッチの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="4bf58-124">The GO command signals the end of a batch.</span></span> <span data-ttu-id="4bf58-125">[!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトに GO ステートメントがない場合は、1 つのバッチとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-125">If a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script does not have any GO commands, it is executed as a single batch.</span></span>  
  
-   <span data-ttu-id="4bf58-126">1 つのバッチで複数のレプリケーション ストアド プロシージャを実行する場合は、そのバッチの中で、最初のプロシージャの後に続くすべてのプロシージャの先頭に EXECUTE キーワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf58-126">When executing multiple replication stored procedures in a single batch, after the first procedure, all subsequent procedures in the batch must be preceded by the EXECUTE keyword.</span></span>  
  
-   <span data-ttu-id="4bf58-127">バッチに含まれるすべてのストアド プロシージャは、バッチの実行前にコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf58-127">All stored procedures in a batch must compile before a batch will execute.</span></span> <span data-ttu-id="4bf58-128">ただし、バッチがコンパイルされ、実行プランが作成された後で、実行時エラーが発生する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="4bf58-128">However, once the batch has been compiled, and an execution plan has been created, a run-time error may or may not occur.</span></span>  
  
-   <span data-ttu-id="4bf58-129">レプリケーションの構成スクリプトを作成する場合は、セキュリティ資格情報をスクリプト ファイルに格納しなくて済むように、Windows 認証の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4bf58-129">When creating scripts to configure replication, you should use Windows Authentication to avoid storing security credentials in the script file.</span></span> <span data-ttu-id="4bf58-130">スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。</span><span class="sxs-lookup"><span data-stu-id="4bf58-130">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
## <a name="sample-replication-script"></a><span data-ttu-id="4bf58-131">サンプル レプリケーション スクリプト</span><span class="sxs-lookup"><span data-stu-id="4bf58-131">Sample Replication Script</span></span>  
 <span data-ttu-id="4bf58-132">次のスクリプトを実行すると、サーバー上にパブリッシングとディストリビューションをセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-132">The following script can be executed to setup publishing and distribution on a server.</span></span>  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
-- Specify the replication working directory.  
SET @directory = N'\\' + $(DistPubServer) + '\repldata';  
-- Specify the publication database.  
SET @publicationDB = N'AdventureWorks2012';   
  
-- Install the server MYDISTPUB as a Distributor using the defaults,  
-- including autogenerating the distributor password.  
USE master  
EXEC sp_adddistributor @distributor = @distributor;  
  
-- Create a new distribution database using the defaults, including  
-- using Windows Authentication.  
USE master  
EXEC sp_adddistributiondb @database = @distributionDB,   
    @security_mode = 1;  
GO  
  
-- Create a Publisher and enable AdventureWorks2012 for replication.  
-- Add MYDISTPUB as a publisher with MYDISTPUB as a local distributor  
-- and use Windows Authentication.  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
USE [distribution]  
EXEC sp_adddistpublisher @publisher=@publisher,   
    @distribution_db=@distributionDB,   
    @security_mode = 1;  
GO  
  
```  
  
 <span data-ttu-id="4bf58-133">その後、このスクリプトを `instdistpub.sql` としてローカルに保存しておけば必要に応じていつでも再実行できます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-133">This script can then be saved locally as `instdistpub.sql` so that it can be run or rerun when needed.</span></span>  
  
 <span data-ttu-id="4bf58-134">以前のスクリプトには **sqlcmd** スクリプト変数が含まれており、この変数は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックのレプリケーション コード サンプルの多くで使用されています。</span><span class="sxs-lookup"><span data-stu-id="4bf58-134">The previous script includes **sqlcmd** scripting variables, which are used in many of the replication code samples in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="4bf58-135">スクリプト変数は `$(MyVariable)` 構文を使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="4bf58-135">Scripting variables are defined by using `$(MyVariable)` syntax.</span></span> <span data-ttu-id="4bf58-136">変数の値は、コマンド ラインまたは [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] でスクリプトに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-136">Values for variables can be passed to a script at the command line or in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4bf58-137">詳細については、このトピックの次のセクション「レプリケーション スクリプトの実行」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bf58-137">For more information, see the next section in this topic, "Executing Replication Scripts."</span></span>  
  
## <a name="executing-replication-scripts"></a><span data-ttu-id="4bf58-138">レプリケーション スクリプトの実行</span><span class="sxs-lookup"><span data-stu-id="4bf58-138">Executing Replication Scripts</span></span>  
 <span data-ttu-id="4bf58-139">作成したレプリケーション スクリプトは、次のいずれかの方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-139">Once created, a replication script can be executed in one of the following ways:</span></span>  
  
### <a name="creating-a-sql-query-file-in-sql-server-management-studio"></a><span data-ttu-id="4bf58-140">SQL Server Management Studio を使った SQL クエリ ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="4bf58-140">Creating a SQL Query File in SQL Server Management Studio</span></span>  
 <span data-ttu-id="4bf58-141">レプリケーション [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプト ファイルは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] プロジェクトで SQL クエリ ファイルとして作成できます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-141">A replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] script file can be created as a SQL Query file in a [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] project.</span></span> <span data-ttu-id="4bf58-142">スクリプトを作成した後、このクエリ ファイルが格納されたデータベースに接続することによってスクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-142">After the script is written, a connection can be made to the database for this query file and the script can be executed.</span></span> <span data-ttu-id="4bf58-143">を使用してスクリプトを作成する方法の詳細について [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] は、「[クエリエディターとテキストエディター &#40;SQL Server Management Studio&#41;](../../scripting/query-and-text-editors-sql-server-management-studio.md))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bf58-143">For more information about how to create [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../../scripting/query-and-text-editors-sql-server-management-studio.md)).</span></span>  
  
 <span data-ttu-id="4bf58-144">スクリプト変数を含むスクリプトを使用するには、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を **sqlcmd** モードで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf58-144">To use a script that includes scripting variables, [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] must be running in **sqlcmd** mode.</span></span> <span data-ttu-id="4bf58-145">**sqlcmd** モードでは、変数の値として使用される `:setvar` などの **sqlcmd** に固有の追加の構文を Query Editor で使用できます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-145">In **sqlcmd** mode, the Query Editor accepts additional syntax specific to **sqlcmd**, such as `:setvar`, which is used to a value for a variable.</span></span> <span data-ttu-id="4bf58-146">**sqlcmd** モードの詳細については、「[クエリ エディターによる SQLCMD スクリプトの編集](../../scripting/edit-sqlcmd-scripts-with-query-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bf58-146">For more information about **sqlcmd** mode, see [Edit SQLCMD Scripts with Query Editor](../../scripting/edit-sqlcmd-scripts-with-query-editor.md).</span></span> <span data-ttu-id="4bf58-147">次のスクリプトでは、`$(DistPubServer)` 変数の値の指定に `:setvar` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="4bf58-147">In the following script, `:setvar` is used to provide a value for the `$(DistPubServer)` variable.</span></span>  
  
```  
:setvar DistPubServer N'MyPublisherAndDistributor';  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
--  
-- Additional code goes here  
--  
```  
  
### <a name="using-the-sqlcmd-utility-from-the-command-line"></a><span data-ttu-id="4bf58-148">コマンド ラインからの sqlcmd ユーティリティの使用</span><span class="sxs-lookup"><span data-stu-id="4bf58-148">Using the sqlcmd Utility from the Command Line</span></span>  
 <span data-ttu-id="4bf58-149">次の例に、[sqlcmd ユーティリティ](../../../tools/sqlcmd-utility.md)を使用してコマンド ラインから `instdistpub.sql` スクリプト ファイルを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4bf58-149">The following example shows how the command line is used to execute the `instdistpub.sql` script file using the [sqlcmd utility](../../../tools/sqlcmd-utility.md):</span></span>  
  
```  
sqlcmd.exe -E -S sqlserverinstance -i C:\instdistpub.sql -o C:\output.log -v DistPubServer="N'MyDistributorAndPublisher'"  
```  
  
 <span data-ttu-id="4bf58-150">この例の `-E` スイッチは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] との接続に Windows 認証を使用することを指定しています。</span><span class="sxs-lookup"><span data-stu-id="4bf58-150">In this example, the `-E` switch indicates that Windows Authentication is used when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4bf58-151">Windows 認証を使用した場合、ユーザー名やパスワードをスクリプト ファイルに格納する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4bf58-151">When using Windows Authentication, there is no need to store a username and password in the script file.</span></span> <span data-ttu-id="4bf58-152">スクリプト ファイルの名前とパスは `-i` スイッチで指定し、出力ファイルの名前は `-o` スイッチで指定します (このスイッチを使用した場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] からの出力はコンソールでなくこのファイルに書き込まれます)。</span><span class="sxs-lookup"><span data-stu-id="4bf58-152">The name and path of the script file is specified by the `-i` switch and the name of the output file is specified by the `-o` switch (output from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is written to this file instead of the console when this switch is used).</span></span> <span data-ttu-id="4bf58-153">`sqlcmd` ユーティリティの `-v` スイッチを使用すると、実行時にスクリプト変数を [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-153">The `sqlcmd` utility enables you to pass scripting variables to a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script at runtime using the `-v` switch.</span></span> <span data-ttu-id="4bf58-154">この例では、`sqlcmd` によって、スクリプト中に出現するすべての `$(DistPubServer)` のインスタンスが、実行前に `N'MyDistributorAndPublisher'` という値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-154">In this example, `sqlcmd` replaces every instance of `$(DistPubServer)` in the script with the value `N'MyDistributorAndPublisher'` before execution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bf58-155">`-X` スイッチを指定すると、スクリプト変数が無効化されます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-155">The `-X` switch disables scripting variables.</span></span>  
  
### <a name="automating-tasks-in-a-batch-file"></a><span data-ttu-id="4bf58-156">バッチ ファイルを使用したタスクの自動化</span><span class="sxs-lookup"><span data-stu-id="4bf58-156">Automating Tasks in a Batch File</span></span>  
 <span data-ttu-id="4bf58-157">バッチ ファイルを使用すると、レプリケーションの管理や同期などのタスクを同じバッチ ファイルにまとめることによって自動化できます。</span><span class="sxs-lookup"><span data-stu-id="4bf58-157">By using a batch file, replication administration tasks, replication synchronization tasks, and other tasks can be automated in the same batch file.</span></span> <span data-ttu-id="4bf58-158">次のバッチ ファイルでは、**sqlcmd** ユーティリティを使用して、サブスクリプション データベースの削除と再作成を行い、マージ プル サブスクリプションを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bf58-158">The following batch file uses the **sqlcmd** utility to drop and recreate the subscription database and add a merge pull subscription.</span></span> <span data-ttu-id="4bf58-159">その後、マージ エージェントを呼び出して、新しいサブスクリプションを同期しています。</span><span class="sxs-lookup"><span data-stu-id="4bf58-159">Then the file invokes the merge agent to synchronize the new subscription:</span></span>  
  
```  
REM ----------------------Script to synchronize merge subscription ----------------------  
REM -- Creates subscription database and   
REM -- synchronizes the subscription to MergeSalesPerson.  
REM -- Current computer acts as both Publisher and Subscriber.  
REM -------------------------------------------------------------------------------------  
  
SET Publisher=%computername%  
SET Subscriber=%computername%  
SET PubDb=AdventureWorks  
SET SubDb=AdventureWorksReplica  
SET PubName=AdvWorksSalesOrdersMerge  
  
REM -- Drop and recreate the subscription database at the Subscriber  
sqlcmd /S%Subscriber% /E /Q"USE master IF EXISTS (SELECT * FROM sysdatabases WHERE name='%SubDb%' ) DROP DATABASE %SubDb%"  
sqlcmd /S%Subscriber% /E /Q"USE master CREATE DATABASE %SubDb%"  
  
REM -- Add a pull subscription at the Subscriber  
sqlcmd /S%Subscriber% /E /Q"USE %SubDb% EXEC sp_addmergepullsubscription @publisher = %Publisher%, @publication = %PubName%, @publisher_db = %PubDb%"  
sqlcmd /S%Subscriber% /E /Q"USE %SubDb%  EXEC sp_addmergepullsubscription_agent @publisher = %Publisher%, @publisher_db = %PubDb%, @publication = %PubName%, @subscriber = %Subscriber%, @subscriber_db = %SubDb%, @distributor = %Publisher%"  
  
REM -- This batch file starts the merge agent at the Subscriber to   
REM -- synchronize a pull subscription to a merge publication.  
REM -- The following must be supplied on one line.  
"\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher  %Publisher% -Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB  %PubDb% -SubscriberDB %SubDb% -Publication %PubName% -PublisherSecurityMode 1 -OutputVerboseLevel 1  -Output  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1 -Validate 3  
  
```  
  
## <a name="scripting-common-replication-tasks"></a><span data-ttu-id="4bf58-160">一般的なレプリケーション タスクのスクリプト化</span><span class="sxs-lookup"><span data-stu-id="4bf58-160">Scripting Common Replication Tasks</span></span>  
 <span data-ttu-id="4bf58-161">次に、システム ストアド プロシージャを使ってスクリプト化することのできる、最も一般的なレプリケーション タスクをいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="4bf58-161">The following are some of the most common replication tasks can be scripted using system stored procedures:</span></span>  
  
-   <span data-ttu-id="4bf58-162">パブリッシングおよびディストリビューションを構成する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-162">Configuring publishing and distribution</span></span>  
  
-   <span data-ttu-id="4bf58-163">パブリッシャーとディストリビューターのプロパティを変更する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-163">Modifying Publisher and Distributor properties</span></span>  
  
-   <span data-ttu-id="4bf58-164">パブリッシングおよびディストリビューションを無効化する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-164">Disabling publishing and distribution</span></span>  
  
-   <span data-ttu-id="4bf58-165">パブリケーションを作成し、アーティクルを定義する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-165">Creating publications and defining articles</span></span>  
  
-   <span data-ttu-id="4bf58-166">パブリケーションおよびアーティクルを削除する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-166">Deleting publications and articles</span></span>  
  
-   <span data-ttu-id="4bf58-167">プル サブスクリプションを作成する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-167">Creating a pull subscription</span></span>  
  
-   <span data-ttu-id="4bf58-168">プル サブスクリプションを変更する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-168">Modifying a pull subscription</span></span>  
  
-   <span data-ttu-id="4bf58-169">プル サブスクリプションを削除する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-169">Deleting a pull subscription</span></span>  
  
-   <span data-ttu-id="4bf58-170">プッシュ サブスクリプションを作成する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-170">Creating a push subscription</span></span>  
  
-   <span data-ttu-id="4bf58-171">プッシュ サブスクリプションを変更する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-171">Modifying a push subscription</span></span>  
  
-   <span data-ttu-id="4bf58-172">プッシュ サブスクリプションを削除する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-172">Deleting a push subscription</span></span>  
  
-   <span data-ttu-id="4bf58-173">プル サブスクリプションを同期する。</span><span class="sxs-lookup"><span data-stu-id="4bf58-173">Synchronizing a pull subscription</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf58-174">参照</span><span class="sxs-lookup"><span data-stu-id="4bf58-174">See Also</span></span>  
 <span data-ttu-id="4bf58-175">[レプリケーションのプログラミング概念](replication-programming-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="4bf58-175">[Replication Programming Concepts](replication-programming-concepts.md) </span></span>  
 <span data-ttu-id="4bf58-176">[レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4bf58-176">[Replication Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="4bf58-177">レプリケーションのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="4bf58-177">Scripting Replication</span></span>](../scripting-replication.md)  
  
  
