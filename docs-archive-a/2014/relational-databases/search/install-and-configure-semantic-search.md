---
title: セマンティック検索のインストールと構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], installing
- semantic search [SQL Server], configuring
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d95e0bb2adf3bacf7057b881ab2e85afd50feef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717726"
---
# <a name="install-and-configure-semantic-search"></a><span data-ttu-id="69049-102">セマンティック検索のインストールと構成</span><span class="sxs-lookup"><span data-stu-id="69049-102">Install and Configure Semantic Search</span></span>
  <span data-ttu-id="69049-103">統計的セマンティック検索の前提条件と、これらをインストールまたは確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69049-103">Describes the prerequisites for statistical semantic search and how to install or check them.</span></span>  
  
## <a name="installing-semantic-search"></a><span data-ttu-id="69049-104">セマンティック検索のインストール</span><span class="sxs-lookup"><span data-stu-id="69049-104">Installing Semantic Search</span></span>  
  
###  <a name="how-to-check-whether-semantic-search-is-installed"></a><a name="HowToCheckInstalled"></a><span data-ttu-id="69049-105">方法: セマンティック検索がインストールされているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="69049-105">How To: Check Whether Semantic Search Is Installed</span></span>  
 <span data-ttu-id="69049-106">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) メタデータ関数の **IsFullTextInstalled** プロパティに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="69049-106">Query the **IsFullTextInstalled** property of the [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="69049-107">戻り値 1 は、データベースに対してフルテキスト検索とセマンティック検索がインストールされていることを示します。戻り値 0 は、フルテキスト検索とセマンティック検索がインストールされていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="69049-107">A return value of 1 indicates that Full-Text Search and Semantic Search are installed; a return value of 0 indicates that they are not installed.</span></span>  
  
```sql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="how-to-install-semantic-search"></a><a name="BasicsSemanticSearch"></a><span data-ttu-id="69049-108">方法: セマンティック検索をインストールする</span><span class="sxs-lookup"><span data-stu-id="69049-108">How To: Install Semantic Search</span></span>  
 <span data-ttu-id="69049-109">セマンティック検索をインストールするには、セットアップ中、 **[インストールする機能]** ページで **[検索のためのフルテキスト抽出とセマンティック抽出]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="69049-109">To install Semantic Search, select **Full-Text and Semantic Extractions for Search** on the **Features to Install** page during setup.</span></span>  
  
 <span data-ttu-id="69049-110">セマンティック検索はフルテキスト検索に依存します。</span><span class="sxs-lookup"><span data-stu-id="69049-110">Statistical Semantic Search depends on Full-Text Search.</span></span> <span data-ttu-id="69049-111">この [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の 2 つのオプション機能は一緒にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="69049-111">These two optional features of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are installed together.</span></span>  
  
## <a name="installing-or-removing-the-semantic-language-statistics-database"></a><span data-ttu-id="69049-112">セマンティック言語統計データベースをインストールまたは削除する</span><span class="sxs-lookup"><span data-stu-id="69049-112">Installing or Removing the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="69049-113">セマンティック検索は、別途、"セマンティック言語統計データベース" と呼ばれる外部の機能に依存しています。</span><span class="sxs-lookup"><span data-stu-id="69049-113">Semantic Search has an additional external dependency that is called the semantic language statistics database.</span></span> <span data-ttu-id="69049-114">このデータベースには、セマンティック検索で必要な統計的言語モデルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="69049-114">This database contains the statistical language models required by semantic search.</span></span> <span data-ttu-id="69049-115">1 つのセマンティック言語統計データベースには、セマンティック インデックス作成でサポートされるすべての言語の言語モデルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="69049-115">A single semantic language statistics database contains the language models for all the languages that are supported for semantic indexing.</span></span>  
  
###  <a name="how-to-check-whether-the-semantic-language-statistics-database-is-installed"></a><a name="HowToCheckDatabase"></a><span data-ttu-id="69049-116">方法: セマンティック言語統計データベースがインストールされているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="69049-116">How To: Check Whether the Semantic Language Statistics Database Is Installed</span></span>  
 <span data-ttu-id="69049-117">カタログ ビュー [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql) に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="69049-117">Query the catalog view [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql).</span></span>  
  
 <span data-ttu-id="69049-118">実行対象のインスタンスにセマンティック言語統計データベースがインストールされ登録されている場合、クエリ結果には、そのデータベースに関する単一行から成る情報が格納されています。</span><span class="sxs-lookup"><span data-stu-id="69049-118">If the semantic language statistics database is installed and registered for the instance, then the query results contain a single row of information about the database.</span></span>  
  
```vb  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="how-to-install-attach-and-register-the-semantic-language-statistics-database"></a><a name="HowToInstallModel"></a><span data-ttu-id="69049-119">方法: セマンティック言語統計データベースをインストール、アタッチ、および登録する</span><span class="sxs-lookup"><span data-stu-id="69049-119">How To: Install, Attach, and Register the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="69049-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のセットアップ プログラムでは、セマンティック言語統計データベースはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="69049-120">The semantic language statistics database is not installed by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup program.</span></span> <span data-ttu-id="69049-121">セマンティック インデックス作成の前提条件であるセマンティック言語統計データベースをセットアップするには、次の作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="69049-121">To set up the Semantic Language Statistics database as a prerequisite for semantic indexing, do the following tasks:</span></span>  
  
 <span data-ttu-id="69049-122">**1.セマンティック言語統計データベースをインストールします。**</span><span class="sxs-lookup"><span data-stu-id="69049-122">**1. Install the semantic language statistics database.**</span></span>  
 1.  <span data-ttu-id="69049-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストール メディアでセマンティック言語統計データベースを見つけるか、Web からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="69049-123">Locate the semantic language statistics database on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media or download it from the Web.</span></span>  
  
    -   <span data-ttu-id="69049-124">**のインストール メディアで** SemanticLanguageDatabase.msi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] という名前の Windows インストーラー パッケージを見つけます。</span><span class="sxs-lookup"><span data-stu-id="69049-124">Locate the Windows installer package named **SemanticLanguageDatabase.msi** on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="69049-125">対象のシステムに応じて、32 ビットまたは 64 ビット バージョンのインストーラー パッケージを探してください。</span><span class="sxs-lookup"><span data-stu-id="69049-125">Locate the 32-bit or 64-bit version of the installer package depending on the target system.</span></span> <span data-ttu-id="69049-126">32 ビット バージョンのファイルか 64 ビット バージョンのファイルかは、それが格納されているフォルダーの名前で判断できます。ファイル名そのものは、どちらのバージョンも同じです。</span><span class="sxs-lookup"><span data-stu-id="69049-126">The name of the containing folder identifies the 32-bit or 64-bit version of the file; the file name itself is the same for both versions.</span></span>  
  
    -   <span data-ttu-id="69049-127">Microsoft からインストーラーパッケージをダウンロードしますか? [SQL Server。。2014セマンティック言語統計](https://go.microsoft.com/fwlink/?LinkID=296743) [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ダウンロードセンターのページ。</span><span class="sxs-lookup"><span data-stu-id="69049-127">Download the installer package from the [Microsoft?? SQL Server?? 2014 Semantic Language Statistics](https://go.microsoft.com/fwlink/?LinkID=296743) page on the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Download Center.</span></span>  
  
2.  <span data-ttu-id="69049-128">**SemanticLanguageDatabase.msi** Windows インストーラーパッケージを実行して、データベースとログファイルを抽出します。</span><span class="sxs-lookup"><span data-stu-id="69049-128">Run the **SemanticLanguageDatabase.msi** Windows installer package to extract the database and log file.</span></span>  
  
     <span data-ttu-id="69049-129">抽出先のディレクトリは必要に応じて変更できます。</span><span class="sxs-lookup"><span data-stu-id="69049-129">You can optionally change the destination directory.</span></span> <span data-ttu-id="69049-130">既定では、インストーラーは、32ビットまたは64ビットの Program Files フォルダー内の**Microsoft Semantic Language Database**という名前のフォルダーにファイルを抽出します。</span><span class="sxs-lookup"><span data-stu-id="69049-130">By default, the installer extracts the files to a folder named **Microsoft Semantic Language Database** in the 32-bit or 64-bit Program Files folder.</span></span> <span data-ttu-id="69049-131">MSI ファイルには、圧縮データベース ファイルおよびログ ファイルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="69049-131">The MSI file contains a compressed database file and log file.</span></span>  
  
3.  <span data-ttu-id="69049-132">抽出されたデータベース ファイルとログ ファイルを、ファイル システム内の適切な場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="69049-132">Move the extracted database file and log file to a suitable location in the file system.</span></span>  
  
     <span data-ttu-id="69049-133">ファイルを既定の場所に残した場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の別のインスタンスのデータベースの別のコピーを抽出できません。</span><span class="sxs-lookup"><span data-stu-id="69049-133">If you leave the files in their default location, it will not be possible to extract another copy of the database for another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="69049-134">セマンティック言語統計データベースの抽出時に、ファイル システム内の既定の場所にあるデータベース ファイルおよびログ ファイルに制限付きの権限が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="69049-134">When the semantic language statistics database is extracted, restricted permissions are assigned to the database file and log file in the default location in the file system.</span></span> <span data-ttu-id="69049-135">そのため、データベースを既定の場所に残した場合、ユーザーによってはデータベースにアタッチする権限がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="69049-135">As a result, you may not have permission to attach the database if you leave it in the default location.</span></span> <span data-ttu-id="69049-136">データベースをアタッチしようとしたときにエラーが発生した場合は、ファイルを移動するか、ファイル システムの権限を確認し、必要に応じて修正してください。</span><span class="sxs-lookup"><span data-stu-id="69049-136">If an error is raised when you try to attach the database, move the files, or check and fix file system permissions as appropriate.</span></span>  
  
 <span data-ttu-id="69049-137">**2.セマンティック言語統計データベースをアタッチします。**</span><span class="sxs-lookup"><span data-stu-id="69049-137">**2. Attach the semantic language statistics database.**</span></span>  
 <span data-ttu-id="69049-138">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用するか、[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) を **FOR ATTACH** 構文で呼び出して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにデータベースをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="69049-138">Attach the database to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or by calling [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) with the **FOR ATTACH** syntax.</span></span> <span data-ttu-id="69049-139">詳細については、「[データベースのデタッチとアタッチ &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69049-139">For more information, see [Database Detach and Attach &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md).</span></span>  
  
 <span data-ttu-id="69049-140">既定では、データベースの名前は**semanticsdb になり**です。</span><span class="sxs-lookup"><span data-stu-id="69049-140">By default, the name of the database is **semanticsdb**.</span></span> <span data-ttu-id="69049-141">データベースをアタッチする際、必要に応じて、別の名前を付けてください。</span><span class="sxs-lookup"><span data-stu-id="69049-141">You can optionally give the database a different name when you attach it.</span></span> <span data-ttu-id="69049-142">この名前は、後続の手順でデータベースを登録する際に必要になります。</span><span class="sxs-lookup"><span data-stu-id="69049-142">You have to provide this name when you register the database in the subsequent step.</span></span>  
  
```sql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 <span data-ttu-id="69049-143">このコード例では、データベースを既定の場所から新しい場所に移動済みであることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="69049-143">This code sample assumes that you have moved the database from its default location to a new location.</span></span>  
  
 <span data-ttu-id="69049-144">**3.セマンティック言語統計データベースを登録します。**</span><span class="sxs-lookup"><span data-stu-id="69049-144">**3. Register the semantic language statistics database.**</span></span>  
 <span data-ttu-id="69049-145">データベースのアタッチ時に指定した名前を使用して、ストアド プロシージャ [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) を次のように呼び出します。</span><span class="sxs-lookup"><span data-stu-id="69049-145">Call the stored procedure [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) and provide the name that you gave to the database when you attached it.</span></span>  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  
  
###  <a name="how-to-unregister-detach-and-remove-the-semantic-language-statistics-database"></a><a name="HowToUnregister"></a><span data-ttu-id="69049-146">方法: セマンティック言語統計データベースを登録解除、デタッチ、および削除する</span><span class="sxs-lookup"><span data-stu-id="69049-146">How To: Unregister, Detach, and Remove the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="69049-147">**セマンティック言語統計データベースの登録を解除します。**</span><span class="sxs-lookup"><span data-stu-id="69049-147">**Unregister the semantic language statistics database.**</span></span>  
 <span data-ttu-id="69049-148">ストアド プロシージャ [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="69049-148">Call the stored procedure [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql).</span></span> <span data-ttu-id="69049-149">セマンティック言語統計データベースは 1 つのインスタンスにつき 1 つしか存在しないため、データベースの名前を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="69049-149">You do not have to provide the name of the database since an instance can have only one semantic language statistics database.</span></span>  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 <span data-ttu-id="69049-150">**セマンティック言語統計データベースをデタッチします。**</span><span class="sxs-lookup"><span data-stu-id="69049-150">**Detach the semantic language statistics database.**</span></span>  
 <span data-ttu-id="69049-151">ストアド プロシージャ [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) を呼び出し、データベース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="69049-151">Call the stored procedure [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) and provide the name of the database.</span></span>  
  
```sql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 <span data-ttu-id="69049-152">**セマンティック言語統計データベースを削除します。**</span><span class="sxs-lookup"><span data-stu-id="69049-152">**Remove the semantic language statistics database.**</span></span>  
 <span data-ttu-id="69049-153">データベースの登録を解除し、デタッチした後は、データベース ファイルを簡単に削除できます。</span><span class="sxs-lookup"><span data-stu-id="69049-153">After unregistering and detaching the database, you can simply delete the database file.</span></span> <span data-ttu-id="69049-154">アンインストール プログラムはありません。また、コントロール パネルの **[プログラムと機能]** のエントリもありません。</span><span class="sxs-lookup"><span data-stu-id="69049-154">There is no uninstall program and there is no entry in **Programs and Features** in the Control Panel.</span></span>  
  
###  <a name="requirements-and-restrictions-for-installing-and-removing-the-semantic-language-statistics-database"></a><a name="reqinstall"></a><span data-ttu-id="69049-155">セマンティック言語統計データベースをインストールおよび削除するための要件と制限</span><span class="sxs-lookup"><span data-stu-id="69049-155">Requirements and Restrictions for Installing and Removing the Semantic Language Statistics Database</span></span>  
  
-   <span data-ttu-id="69049-156">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスでアタッチおよび登録できるセマンティック言語統計データベースは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="69049-156">You can only attach and register one semantic language statistics database on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="69049-157">1 台のコンピューターに存在する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の各インスタンスには、それぞれ、セマンティック言語統計データベースの物理コピーが必要です。</span><span class="sxs-lookup"><span data-stu-id="69049-157">Each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on a single computer requires a separate physical copy of the semantic language statistics database.</span></span> <span data-ttu-id="69049-158">個々のコピーをそれぞれのインスタンスにアタッチしてください。</span><span class="sxs-lookup"><span data-stu-id="69049-158">Attach one copy to each instance.</span></span>  
  
-   <span data-ttu-id="69049-159">登録されている有効なセマンティック言語統計データベースをデタッチし、同じ名前の任意のデータベースに置き換えることはできません。</span><span class="sxs-lookup"><span data-stu-id="69049-159">You cannot detach a valid and registered semantic language statistics database and replace it with an arbitrary database that has the same name.</span></span> <span data-ttu-id="69049-160">このような操作を行うと、アクティブなインデックス作成およびそれ以降のインデックス作成が失敗します。</span><span class="sxs-lookup"><span data-stu-id="69049-160">Doing so will cause active or future index populations to fail.</span></span>  
  
-   <span data-ttu-id="69049-161">セマンティック言語統計データベースは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="69049-161">The semantic language statistics database is read-only.</span></span> <span data-ttu-id="69049-162">このデータベースはカスタマイズできません。</span><span class="sxs-lookup"><span data-stu-id="69049-162">You cannot customize this database.</span></span> <span data-ttu-id="69049-163">なんらかの方法でデータベースのコンテンツを変更すると、今後のセマンティック インデックス作成の結果が不明確になります。</span><span class="sxs-lookup"><span data-stu-id="69049-163">If you alter the content of the database in any way, the results for future semantic indexing are indeterministic.</span></span> <span data-ttu-id="69049-164">このデータの元の状態を復元するには、変更後のデータベースを削除して、データベースの変更されていない新しいコピーをダウンロードおよびアタッチします。</span><span class="sxs-lookup"><span data-stu-id="69049-164">To restore the original state of this data, you can drop the altered database, and download and attach a new and unaltered copy of the database.</span></span>  
  
-   <span data-ttu-id="69049-165">セマンティック言語統計データベースはデタッチまたは削除することができます。</span><span class="sxs-lookup"><span data-stu-id="69049-165">It is possible to detach or drop the semantic language statistics database.</span></span> <span data-ttu-id="69049-166">データベースで読み取りロックが設定されているアクティブなインデックス作成操作がある場合、デタッチまたは削除操作は失敗するか、タイムアウトします。これは、既存の動作と同じです。</span><span class="sxs-lookup"><span data-stu-id="69049-166">If there are any active indexing operations that have read locks on the database, then the detach or drop operation will fail or time out. This is consistent with existing behavior.</span></span> <span data-ttu-id="69049-167">データベースが削除された後は、セマンティック インデックス作成操作が失敗します。</span><span class="sxs-lookup"><span data-stu-id="69049-167">After the database is removed, semantic indexing operations will fail.</span></span>  
  
## <a name="installing-optional-support-for-newer-document-types"></a><span data-ttu-id="69049-168">新しいドキュメントの種類のオプション サポートをインストールする</span><span class="sxs-lookup"><span data-stu-id="69049-168">Installing Optional Support for Newer Document Types</span></span>  
  
###  <a name="how-to-install-the-latest-filters-for-microsoft-office-and-other-microsoft-document-types"></a><a name="office"></a><span data-ttu-id="69049-169">方法: Microsoft Office およびその他の Microsoft ドキュメントの種類の最新のフィルターをインストールする</span><span class="sxs-lookup"><span data-stu-id="69049-169">How to: Install the Latest Filters for Microsoft Office and other Microsoft Document Types</span></span>  
 <span data-ttu-id="69049-170">このリリースの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] の最新のワード ブレーカーとステマーがインストールされますが、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office ドキュメントおよびその他の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ドキュメントの種類の最新のフィルターはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="69049-170">This release of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installs the latest [!INCLUDE[msCoName](../../../includes/msconame-md.md)] word breakers and stemmers, but does not install the latest filters for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office documents and other [!INCLUDE[msCoName](../../../includes/msconame-md.md)] document types.</span></span> <span data-ttu-id="69049-171">これらのフィルターは、最新バージョンの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office およびその他の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] アプリケーションで作成されたドキュメントのインデックスを作成するために必要です。</span><span class="sxs-lookup"><span data-stu-id="69049-171">These filters are required for indexing documents created with recent versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office and other [!INCLUDE[msCoName](../../../includes/msconame-md.md)] applications.</span></span> <span data-ttu-id="69049-172">最新のフィルターをダウンロードするには、「 [Microsoft Office 2010 フィルター パック](https://www.microsoft.com/download/details.aspx?id=17062)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69049-172">To download the latest filters, see [Microsoft Office 2010 Filter Packs](https://www.microsoft.com/download/details.aspx?id=17062).</span></span>  
  
  
