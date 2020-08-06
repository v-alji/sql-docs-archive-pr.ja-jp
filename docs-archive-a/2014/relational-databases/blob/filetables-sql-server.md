---
title: FileTables (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/06/2016
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], overview
- FileTables [SQL Server]
- FileTable [SQL Server], see FileTables [SQL Server]
- FileTable [SQL Server]
ms.assetid: a57b629c-e9ed-48fd-9a48-ed3787d80c8f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c0a38f0e947b0c4f68a49e13a40071f6a30cd07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740062"
---
# <a name="filetables-sql-server"></a><span data-ttu-id="8fcd6-102">FileTables (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8fcd6-102">FileTables (SQL Server)</span></span>
  <span data-ttu-id="8fcd6-103">FileTable 機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納されているファイル データに対して Windows ファイル名前空間のサポートと Windows アプリケーションとの互換性を提供します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-103">The FileTable feature brings support for the Windows file namespace and compatibility with Windows applications to the file data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8fcd6-104">FileTable により、アプリケーションは、ストレージとデータ管理コンポーネントを統合し、非構造化データおよびメタデータに対する統合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス (フルテキスト検索、セマンティック検索など) を提供できます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-104">FileTable lets an application integrate its storage and data management components, and provides integrated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services - including full-text search and semantic search - over unstructured data and metadata.</span></span>  
  
 <span data-ttu-id="8fcd6-105">つまり、ファイルおよびドキュメントを FileTable と呼ばれる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特殊なテーブルに保存しておき、ファイル システムに格納されているかのように、Windows アプリケーションからこれらのファイルおよびドキュメントにアクセスできるということです。このとき、クライアント アプリケーションに変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-105">In other words, you can store files and documents in special tables in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] called FileTables, but access them from Windows applications as if they were stored in the file system, without making any changes to your client applications.</span></span>  
  
 <span data-ttu-id="8fcd6-106">FileTable の機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の FILESTREAM テクノロジをベースとして構築されています。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-106">The FileTable feature builds on top of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] FILESTREAM technology.</span></span> <span data-ttu-id="8fcd6-107">FILESTREAM の詳細については、「[FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-107">To learn more about FILESTREAM, see [FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md).</span></span>  
  
##  <a name="benefits-of-the-filetable-feature"></a><a name="Goals"></a> <span data-ttu-id="8fcd6-108">FileTable 機能の利点</span><span class="sxs-lookup"><span data-stu-id="8fcd6-108">Benefits of the FileTable Feature</span></span>  
 <span data-ttu-id="8fcd6-109">FileTable 機能の目的は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-109">The goals of the FileTable feature include the following:</span></span>  
  
-   <span data-ttu-id="8fcd6-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース内に格納されたファイル データに対する Windows API の互換性。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-110">Windows API compatibility for file data stored within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="8fcd6-111">Windows API の互換性は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-111">Windows API compatibility includes the following:</span></span>  
  
    -   <span data-ttu-id="8fcd6-112">非トランザクション ストリーム アクセスと FILESTREAM データのインプレース更新。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-112">Non-transactional streaming access and in-place updates to FILESTREAM data.</span></span>  
  
    -   <span data-ttu-id="8fcd6-113">ディレクトリおよびファイルの階層構造の名前空間。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-113">A hierarchical namespace of directories and files.</span></span>  
  
    -   <span data-ttu-id="8fcd6-114">作成日や更新日などのファイル属性の保管。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-114">Storage of file attributes, such as created date and modified date.</span></span>  
  
    -   <span data-ttu-id="8fcd6-115">Windows ファイルおよびディレクトリ管理 API のサポート。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-115">Support for Windows file and directory management APIs.</span></span>  
  
-   <span data-ttu-id="8fcd6-116">FILESTREAM およびファイル属性データに対する管理ツール、サービス、リレーショナル クエリなど、他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能との互換性。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-116">Compatibility with other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features including management tools, services, and relational query capabilities over FILESTREAM and file attribute data.</span></span>  
  
 <span data-ttu-id="8fcd6-117">このようにして、FileTable は、現在ファイル サーバーにファイルとして格納されている非構造化データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で保管および管理するうえでの大きな障壁を取り除きます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-117">Thus FileTables remove a significant barrier to the use of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the storage and management of unstructured data that is currently residing as files on file servers.</span></span> <span data-ttu-id="8fcd6-118">企業は、このデータをファイル サーバーから FileTable に移動して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が提供する統合管理およびサービスを活用できます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-118">Enterprises can move this data from file servers into FileTables to take advantage of integrated administration and services provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8fcd6-119">それと同時に、ファイル システムでこのデータをファイルとして認識する既存の Windows アプリケーションとの互換性を維持することもできます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-119">At the same time, they can maintain Windows application compatibility for their existing Windows applications that see this data as files in the file system.</span></span>  
    
##  <a name="what-is-a-filetable"></a><a name="Description"></a> <span data-ttu-id="8fcd6-120">FileTable とは</span><span class="sxs-lookup"><span data-stu-id="8fcd6-120">What Is a FileTable?</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8fcd6-121">は、データベース内のファイルとディレクトリのストレージを必要とするアプリケーションに対して、Windows API の互換性および非トランザクション アクセスによって、特殊な **ファイルのテーブル**( **FileTable**と呼ばれます) を提供します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-121">provides a special **table of files**, also referred to as a **FileTable**, for applications that require file and directory storage in the database, with Windows API compatibility and non-transactional access.</span></span> <span data-ttu-id="8fcd6-122">FileTable は、FILESTREAM データ、ファイルとディレクトリの階層の情報、およびファイル属性を保存するための定義済みのスキーマを持つ、特殊なユーザー テーブルです。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-122">A FileTable is a specialized user table with a pre-defined schema that stores FILESTREAM data, as well as file and directory hierarchy information and file attributes.</span></span>  
  
 <span data-ttu-id="8fcd6-123">FileTable には、次の機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-123">A FileTable provides the following functionality:</span></span>  
  
-   <span data-ttu-id="8fcd6-124">FileTable は、ディレクトリおよびファイルの階層を表します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-124">A FileTable represents a hierarchy of directories and files.</span></span> <span data-ttu-id="8fcd6-125">含まれるディレクトリおよびファイルの両方について、その階層のすべてのノードに関連するデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-125">It stores data related to all the nodes in that hierarchy, for both directories and the files they contain.</span></span> <span data-ttu-id="8fcd6-126">この階層は、FileTable を作成するときに指定するルート ディレクトリから始まります。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-126">This hierarchy starts from a root directory that you specify when you create the FileTable.</span></span>  
  
-   <span data-ttu-id="8fcd6-127">FileTable のどの行も、ファイルまたはディレクトリを表します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-127">Every row in a FileTable represents a file or a directory.</span></span>  
  
-   <span data-ttu-id="8fcd6-128">各行には次のアイテムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-128">Every row contains the following items.</span></span> <span data-ttu-id="8fcd6-129">FileTable のスキーマの詳細については、「 [FileTable スキーマ](filetable-schema.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-129">For more information about the schema of a FileTable, see [FileTable Schema](filetable-schema.md).</span></span>  
  
    -   <span data-ttu-id="8fcd6-130">ストリーム データ用の**file_stream** 列、および **stream_id** (GUID) 識別子</span><span class="sxs-lookup"><span data-stu-id="8fcd6-130">A**file_stream** column for stream data and a **stream_id** (GUID) identifier.</span></span> <span data-ttu-id="8fcd6-131">( **file_stream** 列はディレクトリでは NULL です)。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-131">(The **file_stream** column is NULL for a directory.)</span></span>  
  
    -   <span data-ttu-id="8fcd6-132">ファイルおよびディレクトリの階層を表し、それを維持する **path_locator** 列と **parent_path_locator** 列。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-132">Both **path_locator** and **parent_path_locator** columns for representing and maintaining the file and directory hierarchy.</span></span>  
  
    -   <span data-ttu-id="8fcd6-133">ファイル I/O API で便利な、作成日や更新日などの 10 のファイル属性。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-133">10 file attributes such as created date and modified date that are useful with file I/O APIs.</span></span>  
  
    -   <span data-ttu-id="8fcd6-134">ファイルやドキュメント全体に対するフルテキスト検索およびセマンティック検索をサポートする型列。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-134">A type column that supports full-text search and semantic search over files and documents.</span></span>  
  
-   <span data-ttu-id="8fcd6-135">FileTable は、ファイル名前空間のセマンティクスを維持するため、特定のシステム定義の制約とトリガーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-135">A FileTable enforces certain system-defined constraints and triggers to maintain file namespace semantics.</span></span>  
  
-   <span data-ttu-id="8fcd6-136">非トランザクション アクセスでデータベースが構成されている場合、FileTable で表されるファイルおよびディレクトリの階層は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに構成された FILESTREAM 共有の下で公開されます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-136">When the database is configured for non-transactional access, the file and directory hierarchy represented in the FileTable is exposed under the FILESTREAM share configured for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="8fcd6-137">これにより、Windows アプリケーションはファイル システムにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-137">This provides file system access for Windows applications.</span></span>  
  
 <span data-ttu-id="8fcd6-138">FileTable の他の特性は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-138">Some additional characteristics of FileTables include the following:</span></span>  
  
-   <span data-ttu-id="8fcd6-139">FileTable に格納されているファイルおよびディレクトリ データは、Windows API ベースのアプリケーションが非トランザクション ファイル アクセスを行うための Windows 共有によって公開されます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-139">The file and directory data stored in a FileTable is exposed through a Windows share for non-transactional file access for Windows API based applications.</span></span> <span data-ttu-id="8fcd6-140">Windows アプリケーションでは、これは通常のファイルおよびディレクトリの共有のように見えます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-140">For a Windows application, this looks like a normal share with its files and directories.</span></span> <span data-ttu-id="8fcd6-141">アプリケーションは、豊富な Windows API のセットを使用して、この共有のファイルおよびディレクトリを管理できます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-141">Applications can use a rich set of Windows APIs to manage the files and directories under this share.</span></span>  
  
-   <span data-ttu-id="8fcd6-142">共有によって公開されるディレクトリ階層は、FileTable 内で保持されている、純粋に論理的なディレクトリ構造です。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-142">The directory hierarchy surfaced through the share is a purely logical directory structure that is maintained within the FileTable.</span></span>  
  
-   <span data-ttu-id="8fcd6-143">Windows 共有によるファイルまたはディレクトリの作成または変更の呼び出しは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントによってインターセプトされ、FileTable の対応するリレーショナル データに影響します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-143">Calls to create or change a file or directory through the Windows share are intercepted by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component and reflected in the corresponding relational data in the FileTable.</span></span>  
  
-   <span data-ttu-id="8fcd6-144">Windows API の操作は、本質的には非トランザクションであり、ユーザー トランザクションに関連しません。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-144">Windows API operations are non-transactional in nature, and are not associated with user transactions.</span></span> <span data-ttu-id="8fcd6-145">ただし、通常のテーブルの FILESTREAM 列の場合のように、FileTable に格納されている FILESTREAM データへのトランザクション アクセスは、完全にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-145">However, transactional access to FILESTREAM data stored in a FileTable is fully supported, as is the case for any FILESTREAM column in a regular table.</span></span>  
  
-   <span data-ttu-id="8fcd6-146">FileTable に対して、通常の [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスによってクエリおよび更新を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-146">FileTables can also be queried and updated through normal [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="8fcd6-147">また、FileTable は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理ツールや、バックアップなどの機能と統合されています。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-147">They are also integrated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management tools, and features such as backup.</span></span>  
  
  
##  <a name="additional-considerations-for-using-filetables"></a><a name="additional"></a> <span data-ttu-id="8fcd6-148">FileTable の使用に関するその他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="8fcd6-148">Additional Considerations for Using FileTables</span></span>  
  
###  <a name="administrative-considerations"></a><a name="DBA"></a> <span data-ttu-id="8fcd6-149">管理上の注意点</span><span class="sxs-lookup"><span data-stu-id="8fcd6-149">Administrative Considerations</span></span>  
 <span data-ttu-id="8fcd6-150">**FILESTREAM と FileTable について**</span><span class="sxs-lookup"><span data-stu-id="8fcd6-150">**About FILESTREAM and FileTables**</span></span>  
  
-   <span data-ttu-id="8fcd6-151">FileTable は FILESTREAM とは別に構成します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-151">You configure FileTables separately from FILESTREAM.</span></span> <span data-ttu-id="8fcd6-152">したがって、非トランザクション アクセスの有効化や FileTable の作成を行うことなく、FILESTREAM 機能を使用し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-152">Therefore you can continue to use the FILESTREAM feature without enabling non-transactional access or creating FileTables.</span></span>  
  
-   <span data-ttu-id="8fcd6-153">FileTable を介した場合を除き、FILESTREAM データへの非トランザクション アクセスは存在しません。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-153">There is no non-transactional access to FILESTREAM data except through FileTables.</span></span> <span data-ttu-id="8fcd6-154">そのため、非トランザクション アクセスを有効にしても、既存の FILESTREAM 列およびアプリケーションの動作は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-154">Therefore, when you enable non-transactional access, the behavior of existing FILESTREAM columns and applications is not affected.</span></span>  
  
 <span data-ttu-id="8fcd6-155">**FileTable と非トランザクション アクセスについて**</span><span class="sxs-lookup"><span data-stu-id="8fcd6-155">**About FileTables and non-transactional access**</span></span>  
  
-   <span data-ttu-id="8fcd6-156">非トランザクション アクセスは、データベース レベルで有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-156">You can enable or disable non-transactional access at the database level.</span></span>  
  
-   <span data-ttu-id="8fcd6-157">非トランザクション アクセスをオフにしたり、読み取り専用または完全な読み取り/書き込みアクセスを有効にしたりすることによって、データベース レベルで非トランザクション アクセスを構成または調整することができます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-157">You can configure or fine-tune non-transactional access at the database level by turning it off, or by enabling read only or full read/write access.</span></span>  
  
  
###  <a name="filetables-do-not-support-memory-mapped-files"></a><a name="memory"></a> <span data-ttu-id="8fcd6-158">FileTable ではメモリ マップ ファイルはサポートされていません</span><span class="sxs-lookup"><span data-stu-id="8fcd6-158">FileTables Do Not Support Memory-Mapped Files</span></span>  
 <span data-ttu-id="8fcd6-159">FileTable ではメモリ マップ ファイルはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-159">FileTables do not support memory-mapped files.</span></span> <span data-ttu-id="8fcd6-160">メモ帳とペイントの 2 つは、メモリ マップ ファイルを使用するアプリケーションの一般的な例です。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-160">Notepad and Paint are two common examples of applications that use memory-mapped files.</span></span> <span data-ttu-id="8fcd6-161">これらのアプリケーションを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と同じコンピューターで使用して、FileTable に保存されているファイルを開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-161">You cannot use these applications on the same computer as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to open files that are stored in a FileTable.</span></span> <span data-ttu-id="8fcd6-162">ただし、これらのアプリケーションをリモート コンピューターで使用すると、メモリ マッピング機能が使用されないため、FileTable に保存されているファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-162">However you can use these applications from a remote computer to open files that are stored in a FileTable, because in these circumstances the memory-mapping feature is not used.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="8fcd6-163">関連タスク</span><span class="sxs-lookup"><span data-stu-id="8fcd6-163">Related Tasks</span></span>  
 [<span data-ttu-id="8fcd6-164">FileTable の前提条件の有効化</span><span class="sxs-lookup"><span data-stu-id="8fcd6-164">Enable the Prerequisites for FileTable</span></span>](enable-the-prerequisites-for-filetable.md)  
 <span data-ttu-id="8fcd6-165">FileTable を作成および使用するための前提条件を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-165">Describes how to enable the prerequisites for creating and using FileTables.</span></span>  
  
 [<span data-ttu-id="8fcd6-166">FileTable の作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="8fcd6-166">Create, Alter, and Drop FileTables</span></span>](create-alter-and-drop-filetables.md)  
 <span data-ttu-id="8fcd6-167">新しい FileTable の作成や、既存の FileTable の変更または削除を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-167">Describes how to create a new FileTable, or alter or drop an existing FileTable.</span></span>  
  
 [<span data-ttu-id="8fcd6-168">FileTable へのファイルの読み込み</span><span class="sxs-lookup"><span data-stu-id="8fcd6-168">Load Files into FileTables</span></span>](load-files-into-filetables.md)  
 <span data-ttu-id="8fcd6-169">FileTable にファイルを読み込むまたは移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-169">Describes how to load or migrate files into FileTables.</span></span>  
  
 [<span data-ttu-id="8fcd6-170">FileTable 内のディレクトリとパスの操作</span><span class="sxs-lookup"><span data-stu-id="8fcd6-170">Work with Directories and Paths in FileTables</span></span>](work-with-directories-and-paths-in-filetables.md)  
 <span data-ttu-id="8fcd6-171">FileTable 内でファイルが格納されるディレクトリ構造について説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-171">Describes the directory structure in which the files are stored in FileTables.</span></span>  
  
 [<span data-ttu-id="8fcd6-172">Transact SQL を使用した FileTable へのアクセス</span><span class="sxs-lookup"><span data-stu-id="8fcd6-172">Access FileTables with Transact-SQL</span></span>](access-filetables-with-transact-sql.md)  
 <span data-ttu-id="8fcd6-173">Transact SQL データ操作言語 (DML) コマンドでどのように FileTable が操作されるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-173">Describes how Transact-SQL data manipulation language (DML) commands work with FileTables.</span></span>  
  
 [<span data-ttu-id="8fcd6-174">ファイル I/O API を使用した FileTable へのアクセス</span><span class="sxs-lookup"><span data-stu-id="8fcd6-174">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
 <span data-ttu-id="8fcd6-175">FileTable でファイル システム I/O が動作するしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-175">Describes how file system I/O works on a FileTable.</span></span>  
  
 [<span data-ttu-id="8fcd6-176">FileTable の管理</span><span class="sxs-lookup"><span data-stu-id="8fcd6-176">Manage FileTables</span></span>](manage-filetables.md)  
 <span data-ttu-id="8fcd6-177">FileTable を管理するための一般的な管理タスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-177">Describes common administrative tasks for managing FileTables.</span></span>  
  
  
##  <a name="related-content"></a><a name="relcontent"></a> <span data-ttu-id="8fcd6-178">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="8fcd6-178">Related Content</span></span>  
 [<span data-ttu-id="8fcd6-179">FileTable スキーマ</span><span class="sxs-lookup"><span data-stu-id="8fcd6-179">FileTable Schema</span></span>](filetable-schema.md)  
 <span data-ttu-id="8fcd6-180">FileTable の定義済みスキーマおよび固定スキーマについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-180">Describes the pre-defined and fixed schema of a FileTable.</span></span>  
  
 [<span data-ttu-id="8fcd6-181">FileTable と他の SQL Server 機能の互換性</span><span class="sxs-lookup"><span data-stu-id="8fcd6-181">FileTable Compatibility with Other SQL Server Features</span></span>](filetable-compatibility-with-other-sql-server-features.md)  
 <span data-ttu-id="8fcd6-182">FileTable と他の SQL Server 機能との連携について説明します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-182">Describes how FileTables work with other features of SQL Server.</span></span>  
  
 [<span data-ttu-id="8fcd6-183">FileTable DDL、関数、ストアド プロシージャ、およびビュー</span><span class="sxs-lookup"><span data-stu-id="8fcd6-183">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
 <span data-ttu-id="8fcd6-184">FileTable 機能をサポートするために追加または変更された [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース オブジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="8fcd6-184">Lists the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects that have been added or changed to support the FileTable feature.</span></span>  
  
 
  
