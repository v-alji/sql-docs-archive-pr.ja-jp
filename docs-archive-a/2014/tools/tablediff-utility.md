---
title: tablediff ユーティリティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- comparing data
- tablediff utility
- tables [SQL Server replication]
- table comparisons [SQL Server]
- command prompt utilities [SQL Server], tablediff
- troubleshooting [SQL Server replication], non-convergence
- non-convergence [SQL Server]
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a23465a7d2c7db53475a6dca81a8471a3b78b50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720600"
---
# <a name="tablediff-utility"></a><span data-ttu-id="fd5ba-102">tablediff ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="fd5ba-102">tablediff Utility</span></span>
  <span data-ttu-id="fd5ba-103">**tablediff** ユーティリティは、2 つのテーブル内のデータを比較して非収束の発生を調べる場合に使用されます。これは、レプリケーション トポロジ内の非収束に対するトラブルシューティングを行うときに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-103">The **tablediff** utility is used to compare the data in two tables for non-convergence, and is particularly useful for troubleshooting non-convergence in a replication topology.</span></span> <span data-ttu-id="fd5ba-104">このユーティリティは、コマンド プロンプトから、またはバッチ ファイル内で使用して、次のタスクを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-104">This utility can be used from the command prompt or in a batch file to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="fd5ba-105">レプリケーション パブリッシャーとして動作する [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンス内のソース テーブルと、レプリケーション サブスクライバーとして動作する 1 つ以上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスにある対象テーブルの間で、1 行単位の比較を行う。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-105">A row by row comparison between a source table in an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acting as a replication Publisher and the destination table at one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acting as replication Subscribers.</span></span>  
  
-   <span data-ttu-id="fd5ba-106">行数とスキーマのみを比較することによる高速比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-106">Perform a fast comparison by only comparing row counts and schema.</span></span>  
  
-   <span data-ttu-id="fd5ba-107">列レベルでの比較の実行。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-107">Perform column-level comparisons.</span></span>  
  
-   <span data-ttu-id="fd5ba-108">対象サーバーでの相違点を修正し、ソース テーブルと対象テーブルを収束させる [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプトの作成。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-108">Generate a [!INCLUDE[tsql](../includes/tsql-md.md)] script to fix discrepancies at the destination server to bring the source and destination tables into convergence.</span></span>  
  
-   <span data-ttu-id="fd5ba-109">出力ファイルへの結果の記録、または対象データベース内にあるテーブルへの結果の記録。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-109">Log results to an output file or into a table in the destination database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5ba-110">構文</span><span class="sxs-lookup"><span data-stu-id="fd5ba-110">Syntax</span></span>  
  
```  
  
      tablediff   
[ -? ] |   
{  
        -sourceserversource_server_name[\instance_name]  
        -sourcedatabasesource_database-sourcetablesource_table_name   
    [ -sourceschemasource_schema_name ]  
    [ -sourcepasswordsource_password ]  
    [ -sourceusersource_login ]  
    [ -sourcelocked ]  
        -destinationserverdestination_server_name[\instance_name]  
        -destinationdatabasesubscription_database-destinationtabledestination_table   
    [ -destinationschemadestination_schema_name ]  
    [ -destinationpassworddestination_password ]  
    [ -destinationuserdestination_login ]  
    [ -destinationlocked ]  
    [ -blarge_object_bytes ]   
    [ -bfnumber_of_statements ]   
    [ -c ]   
    [ -dt ]   
    [ -ettable_name ]   
    [ -f [ file_name ] ]   
    [ -ooutput_file_name ]   
    [ -q ]   
    [ -rcnumber_of_retries ]   
    [ -riretry_interval ]   
    [ -strict ]  
    [ -tconnection_timeouts ]   
}  
```  
  
## <a name="arguments"></a><span data-ttu-id="fd5ba-111">引数</span><span class="sxs-lookup"><span data-stu-id="fd5ba-111">Arguments</span></span>  
 <span data-ttu-id="fd5ba-112">[ **-?**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-112">[ **-?**</span></span> <span data-ttu-id="fd5ba-113">]</span><span class="sxs-lookup"><span data-stu-id="fd5ba-113">]</span></span>  
 <span data-ttu-id="fd5ba-114">サポートされているパラメーターのリストを返します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-114">Returns the list of supported parameters.</span></span>  
  
 <span data-ttu-id="fd5ba-115">**-sourceserver** *source_server_name*[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="fd5ba-115">**-sourceserver** *source_server_name*[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="fd5ba-116">ソース サーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-116">Is the name of the source server.</span></span> <span data-ttu-id="fd5ba-117">の既定のインスタンスの_ソース \_ サーバー \_ 名_を指定し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-117">Specify _source\_server\_name_ for the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fd5ba-118">の名前付きインスタンスの_ソース \_ サーバー \_ 名_の **\\** _インスタンス \_ 名_を指定し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-118">Specify _source\_server\_name_**\\**_instance\_name_ for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="fd5ba-119">**-sourcedatabase** *source_database*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-119">**-sourcedatabase** *source_database*</span></span>  
 <span data-ttu-id="fd5ba-120">ソース データベース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-120">Is the name of the source database.</span></span>  
  
 <span data-ttu-id="fd5ba-121">**-sourcetable** *source_table_name*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-121">**-sourcetable** *source_table_name*</span></span>  
 <span data-ttu-id="fd5ba-122">調査するソース テーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-122">Is the name of the source table being checked.</span></span>  
  
 <span data-ttu-id="fd5ba-123">**-sourceschema** *source_schema_name*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-123">**-sourceschema** *source_schema_name*</span></span>  
 <span data-ttu-id="fd5ba-124">ソース テーブルのスキーマ所有者を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-124">The schema owner of the source table.</span></span> <span data-ttu-id="fd5ba-125">既定では、テーブル所有者は dbo と見なされます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-125">By default, the table owner is assumed to be dbo.</span></span>  
  
 <span data-ttu-id="fd5ba-126">**-sourcepassword** *source_password*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-126">**-sourcepassword** *source_password*</span></span>  
 <span data-ttu-id="fd5ba-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証でソース サーバーに接続する場合に使用するログインのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-127">Is the password for the login used to connect to the source server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fd5ba-128">可能である場合は、実行時にセキュリティ資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-128">When possible, supply security credentials at runtime.</span></span> <span data-ttu-id="fd5ba-129">資格情報をスクリプト ファイルに格納する必要がある場合は、不正アクセスを防ぐためにファイルを保護してください。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-129">If you must store credentials in a script file, you should secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="fd5ba-130">**-sourceuser** *source_login*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-130">**-sourceuser** *source_login*</span></span>  
 <span data-ttu-id="fd5ba-131">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証でソース サーバーに接続する場合に使用するログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-131">Is the login used to connect to the source server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="fd5ba-132">*source_login* を省略すると、Windows 認証がソース サーバーへの接続時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-132">If *source_login* is not supplied, then Windows Authentication is used when connecting to the source server.</span></span> [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="fd5ba-133">**-sourcelocked**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-133">**-sourcelocked**</span></span>  
 <span data-ttu-id="fd5ba-134">比較中は、TABLOCK および HOLDLOCK テーブル ヒントを使用して、ソース テーブルがロックされます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-134">The source table is locked during the comparison using the TABLOCK and HOLDLOCK table hints.</span></span>  
  
 <span data-ttu-id="fd5ba-135">**-destinationserver** *destination_server_name*[ **\\** _インスタンス \_ 名_]</span><span class="sxs-lookup"><span data-stu-id="fd5ba-135">**-destinationserver** *destination_server_name*[**\\**_instance\_name_]</span></span>  
 <span data-ttu-id="fd5ba-136">対象サーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-136">Is the name of the destination server.</span></span> <span data-ttu-id="fd5ba-137">*の既定のインスタンスの場合は、* destination_server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-137">Specify *destination_server_name* for the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fd5ba-138">の名前付きインスタンスの_宛先 \_ サーバー \_ 名_の **\\** _インスタンス \_ 名_を指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-138">Specify _destination\_server\_name_**\\**_instance\_name_ for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="fd5ba-139">**-destinationdatabase** *subscription_database*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-139">**-destinationdatabase** *subscription_database*</span></span>  
 <span data-ttu-id="fd5ba-140">対象データベース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-140">Is the name of the destination database.</span></span>  
  
 <span data-ttu-id="fd5ba-141">**-destinationtable** *destination_table*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-141">**-destinationtable** *destination_table*</span></span>  
 <span data-ttu-id="fd5ba-142">対象テーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-142">Is the name of the destination table.</span></span>  
  
 <span data-ttu-id="fd5ba-143">**-destinationschema** *destination_schema_name*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-143">**-destinationschema** *destination_schema_name*</span></span>  
 <span data-ttu-id="fd5ba-144">対象テーブルのスキーマ所有者を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-144">The schema owner of the destination table.</span></span> <span data-ttu-id="fd5ba-145">既定では、テーブル所有者は dbo と見なされます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-145">By default, the table owner is assumed to be dbo.</span></span>  
  
 <span data-ttu-id="fd5ba-146">**-destinationpassword** *destination_password*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-146">**-destinationpassword** *destination_password*</span></span>  
 <span data-ttu-id="fd5ba-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で対象サーバーに接続する場合に使用するログインのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-147">Is the password for the login used to connect to the destination server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fd5ba-148">可能である場合は、実行時にセキュリティ資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-148">When possible, supply security credentials at runtime.</span></span> <span data-ttu-id="fd5ba-149">資格情報をスクリプト ファイルに格納する必要がある場合は、不正アクセスを防ぐためにファイルを保護してください。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-149">If you must store credentials in a script file, you should secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="fd5ba-150">**-destinationuser** *destination_login*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-150">**-destinationuser** *destination_login*</span></span>  
 <span data-ttu-id="fd5ba-151">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で対象サーバーに接続する場合に使用するログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-151">Is the login used to connect to the destination server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="fd5ba-152">*destination_login* を省略すると、Windows 認証がサーバーへの接続時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-152">If *destination_login* is not supplied, then Windows Authentication is used when connecting to the server.</span></span> [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="fd5ba-153">**-destinationlocked**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-153">**-destinationlocked**</span></span>  
 <span data-ttu-id="fd5ba-154">比較中は、TABLOCK および HOLDLOCK テーブル ヒントを使用して、対象テーブルがロックされます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-154">The destination table is locked during the comparison using the TABLOCK and HOLDLOCK table hints.</span></span>  
  
 <span data-ttu-id="fd5ba-155">**-b** *large_object_bytes*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-155">**-b** *large_object_bytes*</span></span>  
 <span data-ttu-id="fd5ba-156">ラージ オブジェクト データ型の列に対して比較するバイト数を指定します。列の型は、`text`、`ntext`、`image`、`varchar(max)`、`nvarchar(max)`、および `varbinary(max)` です。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-156">Is the number of bytes to compare for large object data type columns, which includes: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)` and `varbinary(max)`.</span></span> <span data-ttu-id="fd5ba-157">*large_object_bytes* の既定値は、列のサイズです。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-157">*large_object_bytes* defaults to the size of the column.</span></span> <span data-ttu-id="fd5ba-158">*large_object_bytes* を超えるデータは比較されません。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-158">Any data above *large_object_bytes* will not be compared.</span></span>  
  
 <span data-ttu-id="fd5ba-159">**-bf** *number_of_statements*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-159">**-bf**  *number_of_statements*</span></span>  
 <span data-ttu-id="fd5ba-160">[!INCLUDE[tsql](../includes/tsql-md.md)] -f [!INCLUDE[tsql](../includes/tsql-md.md)] オプションを使用する場合に、現在の **スクリプト ファイルに書き込む** ステートメントの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-160">Is the number of [!INCLUDE[tsql](../includes/tsql-md.md)] statements to write to the current [!INCLUDE[tsql](../includes/tsql-md.md)] script file when the **-f** option is used.</span></span> <span data-ttu-id="fd5ba-161">[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの数が *number_of_statements*で指定した値を超えると、新しい [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプト ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-161">When the number of [!INCLUDE[tsql](../includes/tsql-md.md)] statements exceeds *number_of_statements*, a new [!INCLUDE[tsql](../includes/tsql-md.md)] script file is created.</span></span>  
  
 <span data-ttu-id="fd5ba-162">**-c**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-162">**-c**</span></span>  
 <span data-ttu-id="fd5ba-163">列レベルでの違いを比較します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-163">Compare column-level differences.</span></span>  
  
 <span data-ttu-id="fd5ba-164">**-dt**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-164">**-dt**</span></span>  
 <span data-ttu-id="fd5ba-165">テーブルが既に存在している場合は、 *table_name*で指定された結果テーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-165">Drop the result table specified by *table_name*, if the table already exists.</span></span>  
  
 <span data-ttu-id="fd5ba-166">**-et** *table_name*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-166">**-et** *table_name*</span></span>  
 <span data-ttu-id="fd5ba-167">作成する結果テーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-167">Specifies the name of the result table to create.</span></span> <span data-ttu-id="fd5ba-168">このテーブルが既に存在する場合は、 **-DT** を使用する必要があります。使用しない場合、この処理は失敗します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-168">If this table already exists, **-DT** must be used or the operation will fail.</span></span>  
  
 <span data-ttu-id="fd5ba-169">**-f** [ *file_name* ]</span><span class="sxs-lookup"><span data-stu-id="fd5ba-169">**-f** [ *file_name* ]</span></span>  
 <span data-ttu-id="fd5ba-170">対象サーバーにあるテーブルを、ソース サーバーにあるテーブルと収束させる [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-170">Generates a [!INCLUDE[tsql](../includes/tsql-md.md)] script to bring the table at the destination server into convergence with the table at the source server.</span></span> <span data-ttu-id="fd5ba-171">作成される [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプト ファイルの名前とパスを指定できます (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-171">You can optionally specify a name and path for the generated [!INCLUDE[tsql](../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="fd5ba-172">*file_name* を指定しない場合は、ユーティリティが実行されているディレクトリに [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプト ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-172">If *file_name* is not specified, the [!INCLUDE[tsql](../includes/tsql-md.md)] script file is generated in the directory where the utility runs.</span></span>  
  
 <span data-ttu-id="fd5ba-173">**-o** *output_file_name*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-173">**-o** *output_file_name*</span></span>  
 <span data-ttu-id="fd5ba-174">出力ファイルの完全な名前およびフル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-174">Is the full name and path of the output file.</span></span>  
  
 <span data-ttu-id="fd5ba-175">**-q**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-175">**-q**</span></span>  
 <span data-ttu-id="fd5ba-176">行数とスキーマのみを比較することによる高速比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-176">Perform a fast comparison by only comparing row counts and schema.</span></span>  
  
 <span data-ttu-id="fd5ba-177">**-rc** *number_of_retries*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-177">**-rc** *number_of_retries*</span></span>  
 <span data-ttu-id="fd5ba-178">操作が失敗した場合に、ユーティリティが再試行する回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-178">Number of times that the utility retries a failed operation.</span></span>  
  
 <span data-ttu-id="fd5ba-179">**-ri** *retry_interval*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-179">**-ri**  *retry_interval*</span></span>  
 <span data-ttu-id="fd5ba-180">再試行間隔を指定します (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-180">Interval, in seconds, to wait between retries.</span></span>  
  
 <span data-ttu-id="fd5ba-181">**-strict**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-181">**-strict**</span></span>  
 <span data-ttu-id="fd5ba-182">ソース スキーマと対象スキーマを厳密に比較することを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-182">Source and destination schema are strictly compared.</span></span>  
  
 <span data-ttu-id="fd5ba-183">**-t** *connection_timeouts*</span><span class="sxs-lookup"><span data-stu-id="fd5ba-183">**-t** *connection_timeouts*</span></span>  
 <span data-ttu-id="fd5ba-184">ソース サーバーと対象サーバーへの接続に関する接続タイムアウト時間を設定します (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-184">Sets the connection timeout period, in seconds, for connections to the source server and destination server.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd5ba-185">戻り値</span><span class="sxs-lookup"><span data-stu-id="fd5ba-185">Return Value</span></span>  
  
|<span data-ttu-id="fd5ba-186">値</span><span class="sxs-lookup"><span data-stu-id="fd5ba-186">Value</span></span>|<span data-ttu-id="fd5ba-187">説明</span><span class="sxs-lookup"><span data-stu-id="fd5ba-187">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd5ba-188">**0**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-188">**0**</span></span>|<span data-ttu-id="fd5ba-189">Success</span><span class="sxs-lookup"><span data-stu-id="fd5ba-189">Success</span></span>|  
|<span data-ttu-id="fd5ba-190">**1**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-190">**1**</span></span>|<span data-ttu-id="fd5ba-191">重大なエラー</span><span class="sxs-lookup"><span data-stu-id="fd5ba-191">Critical error</span></span>|  
|<span data-ttu-id="fd5ba-192">**2**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-192">**2**</span></span>|<span data-ttu-id="fd5ba-193">テーブルの差分</span><span class="sxs-lookup"><span data-stu-id="fd5ba-193">Table differences</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd5ba-194">解説</span><span class="sxs-lookup"><span data-stu-id="fd5ba-194">Remarks</span></span>  
 <span data-ttu-id="fd5ba-195">**Tablediff**ユーティリティは、以外のサーバーでは使用できません [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-195">The **tablediff** utility cannot be used with non-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="fd5ba-196">`sql_variant` データ型列を含むテーブルはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-196">Tables with `sql_variant` data type columns are not supported.</span></span>  
  
 <span data-ttu-id="fd5ba-197">**tablediff** ユーティリティでは、既定により、ソース列と対象列の間で次のデータ型のマッピングがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-197">By default, the **tablediff** utility supports the following data type mappings between source and destination columns.</span></span>  
  
|<span data-ttu-id="fd5ba-198">ソースのデータ型</span><span class="sxs-lookup"><span data-stu-id="fd5ba-198">Source data type</span></span>|<span data-ttu-id="fd5ba-199">対象のデータ型</span><span class="sxs-lookup"><span data-stu-id="fd5ba-199">Destination data type</span></span>|  
|----------------------|---------------------------|  
|`tinyint`|<span data-ttu-id="fd5ba-200">`smallint`、`int`、または `bigint`</span><span class="sxs-lookup"><span data-stu-id="fd5ba-200">`smallint`, `int`, or `bigint`</span></span>|  
|`smallint`|<span data-ttu-id="fd5ba-201">`int` または `bigint`</span><span class="sxs-lookup"><span data-stu-id="fd5ba-201">`int` or `bigint`</span></span>|  
|`int`|`bigint`|  
|`timestamp`|`varbinary`|  
|`varchar(max)`|`text`|  
|`nvarchar(max)`|`ntext`|  
|`varbinary(max)`|`image`|  
|`text`|`varchar(max)`|  
|`ntext`|`nvarchar(max)`|  
|`image`|`varbinary(max)`|  
  
 <span data-ttu-id="fd5ba-202">これらのマッピングを行わず、厳密な検証を行う場合は、 **-strict** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-202">Use the **-strict** option to disallow these mappings and perform a strict validation.</span></span>  
  
 <span data-ttu-id="fd5ba-203">比較のソース テーブルには、主キー列、ID 列、または ROWGUID 列が少なくとも 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-203">The source table in the comparison must contain at least one primary key, identity, or ROWGUID column.</span></span> <span data-ttu-id="fd5ba-204">**-strict** オプションを使用する場合は、対象テーブルにも主キー列、ID 列、または ROWGUID 列が必要です。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-204">When you use the **-strict** option, the destination table must also have a primary key, identity, or ROWGUID column.</span></span>  
  
 <span data-ttu-id="fd5ba-205">対象テーブルを収束させるため作成される [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプトには、次のデータ型は含められません。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-205">The [!INCLUDE[tsql](../includes/tsql-md.md)] script generated to bring the destination table into convergence does not include the following data types:</span></span>  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `timestamp`  
  
-   <span data-ttu-id="fd5ba-206">**xml**</span><span class="sxs-lookup"><span data-stu-id="fd5ba-206">**xml**</span></span>  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
## <a name="permissions"></a><span data-ttu-id="fd5ba-207">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="fd5ba-207">Permissions</span></span>  
 <span data-ttu-id="fd5ba-208">テーブルを比較するには、比較するテーブル オブジェクトに対する SELECT ALL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-208">To compare tables, you need SELECT ALL permissions on the table objects being compared.</span></span>  
  
 <span data-ttu-id="fd5ba-209">**-et** オプションを使用するには、db_owner 固定データベース ロールのメンバーであることが必要です。または、少なくともサブスクリプション データベースでの CREATE TABLE 権限、および対象サーバーにある対象所有者スキーマに対する ALTER 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-209">To use the **-et** option, you must be a member of the db_owner fixed database role, or at least have CREATE TABLE permission in the subscription database and ALTER permission on the destination owner schema at the destination server.</span></span>  
  
 <span data-ttu-id="fd5ba-210">**-dt** オプションを使用するには、db_owner 固定データベース ロールのメンバーであることが必要です。または、少なくとも対象サーバーにある対象所有者スキーマに対する ALTER 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-210">To use the **-dt** option, you must be a member of the db_owner fixed database role, or at least have ALTER permission on the destination owner schema at the destination server.</span></span>  
  
 <span data-ttu-id="fd5ba-211">**-o** または **-f** オプションを使用するには、指定されたファイル ディレクトリの場所に対する書き込み権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd5ba-211">To use the **-o** or **-f** options, you must have write permissions to the specified file directory location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5ba-212">参照</span><span class="sxs-lookup"><span data-stu-id="fd5ba-212">See Also</span></span>  
 [<span data-ttu-id="fd5ba-213">レプリケートされたテーブルを比較して相違があるかどうかを確認する &#40;レプリケーション プログラミング&#41;</span><span class="sxs-lookup"><span data-stu-id="fd5ba-213">Compare Replicated Tables for Differences &#40;Replication Programming&#41;</span></span>](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  
