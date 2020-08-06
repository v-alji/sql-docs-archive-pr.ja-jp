---
title: BULK INSERT または OPENROWSET(BULK...) を使用した一括データのインポート (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- BULK INSERT statement, importing data from a remote data file
- bulk importing [SQL Server], methods
- bulk exporting [SQL Server], methods
- OPENROWSET function, BULK INSERT
- bulk importing [SQL Server], security
- bulk rowset providers [SQL Server]
- bulk exporting [SQL Server], BULK INSERT statement
- remote data access [SQL Server], bulk importing
- bulk importing [SQL Server], BULK INSERT statement
- Transact-SQL bulk export/import operations
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: be36167020b96dba6d494685d958c38e0e6afbba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643340"
---
# <a name="import-bulk-data-by-using-bulk-insert-or-openrowsetbulk-sql-server"></a><span data-ttu-id="ffbe8-102">BULK INSERT または OPENROWSET(BULK...) を使用した一括データのインポート (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ffbe8-102">Import Bulk Data by Using BULK INSERT or OPENROWSET(BULK...) (SQL Server)</span></span>
  <span data-ttu-id="ffbe8-103">このトピックでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] の BULK INSERT ステートメントと INSERT...SELECT \* FROM OPENROWSET(BULK...) ステートメントを使用して、データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルにデータを一括インポートする方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-103">This topic provides an overview of how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT statement and the INSERT...SELECT \* FROM OPENROWSET(BULK...) statement to bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="ffbe8-104">また、BULK INSERT および OPENROWSET(BULK...) を使用する場合のセキュリティの注意点や、リモート データ ソースから一括インポートする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-104">This topic also describes security considerations for using BULK INSERT and OPENROWSET(BULK...), and using these methods to bulk import from a remote data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffbe8-105">BULK INSERT または OPENROWSET(BULK...) を使用する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンで権限の借用がどのように処理されるかを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-105">When you use BULK INSERT or OPENROWSET(BULK...), it is important to understand how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version handles impersonation.</span></span> <span data-ttu-id="ffbe8-106">詳細については、後の「セキュリティの注意点」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-106">For more information, see "Security Considerations," later in this topic.</span></span>  
  
## <a name="bulk-insert-statement"></a><span data-ttu-id="ffbe8-107">BULK INSERT ステートメント</span><span class="sxs-lookup"><span data-stu-id="ffbe8-107">BULK INSERT Statement</span></span>  
 <span data-ttu-id="ffbe8-108">BULK INSERT では、データ ファイルからテーブルにデータが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-108">BULK INSERT loads data from a data file into a table.</span></span> <span data-ttu-id="ffbe8-109">この機能は、 **bcp** コマンドの **in** オプションと似ていますが、データ ファイルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスによって読み取られる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-109">This functionality is similar to that provided by the **in** option of the **bcp** command; however, the data file is read by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="ffbe8-110">BULK INSERT の構文の説明については、「 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-110">For a description of the BULK INSERT syntax, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ffbe8-111">例</span><span class="sxs-lookup"><span data-stu-id="ffbe8-111">Examples</span></span>  
 <span data-ttu-id="ffbe8-112">BULK INSERT の例については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-112">For BULK INSERT examples, see:</span></span>  
  
-   [<span data-ttu-id="ffbe8-113">BULK INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-113">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
-   [<span data-ttu-id="ffbe8-114">XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-114">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-115">データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-115">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-116">一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-116">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-117">フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-117">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-118">データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-118">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-119">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-119">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-120">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-120">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-121">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-121">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-122">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-122">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-123">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-123">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-124">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-124">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="openrowsetbulk-function"></a><span data-ttu-id="ffbe8-125">OPENROWSET(BULK...)機能</span><span class="sxs-lookup"><span data-stu-id="ffbe8-125">OPENROWSET(BULK...) Function</span></span>  
 <span data-ttu-id="ffbe8-126">OPENROWSET 一括行セット プロバイダーには、BULK オプションを指定して OPENROWSET 関数を呼び出すことによってアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-126">The OPENROWSET bulk rowset provider is accessed by calling the OPENROWSET function and specifying the BULK option.</span></span> <span data-ttu-id="ffbe8-127">OPENROWSET(BULK...) 関数では、OLE DB プロバイダー経由でデータ ファイルなどのリモート データ ソースに接続することで、リモート データにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-127">The OPENROWSET(BULK...) function allows you to access remote data by connecting to a remote data source, such as a data file, through an OLE DB provider.</span></span>  
  
 <span data-ttu-id="ffbe8-128">データを一括インポートするには、INSERT ステートメントの SELECT...FROM 句から OPENROWSET(BULK...) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-128">To bulk import data, call OPENROWSET(BULK...) from a SELECT...FROM clause within an INSERT statement.</span></span> <span data-ttu-id="ffbe8-129">データの一括インポートの基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-129">The basic syntax for bulk importing data is:</span></span>  
  
 <span data-ttu-id="ffbe8-130">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="ffbe8-130">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="ffbe8-131">OPENROWSET(BULK...) を INSERT ステートメント内で使用する場合は、テーブル ヒントがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-131">When used in an INSERT statement, OPENROWSET(BULK...) supports table hints.</span></span> <span data-ttu-id="ffbe8-132">TABLOCK などの通常のテーブル ヒントに加えて、BULK 句では、次の特殊なテーブル ヒントを使用できます:IGNORE_CONSTRAINTS (CHECK 制約のみ無視します)、IGNORE_TRIGGERS、KEEPDEFAULTS、KEEPIDENTITY。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-132">In addition to the regular table hints, such as TABLOCK, the BULK clause can accept the following specialized table hints: IGNORE_CONSTRAINTS (ignores only the CHECK constraints), IGNORE_TRIGGERS, KEEPDEFAULTS, and KEEPIDENTITY.</span></span> <span data-ttu-id="ffbe8-133">詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-133">For more information, see [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
 <span data-ttu-id="ffbe8-134">BULK オプションの上記以外の使い方の詳細については、「 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-134">For information about additional uses of the BULK option, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ffbe8-135">例</span><span class="sxs-lookup"><span data-stu-id="ffbe8-135">Examples</span></span>  
 <span data-ttu-id="ffbe8-136">INSERT...SELECT \* FROM OPENROWSET(BULK...) ステートメントの例については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-136">For examples of INSERT...SELECT \* FROM OPENROWSET(BULK...) statements, see the following topics:</span></span>  
  
-   [<span data-ttu-id="ffbe8-137">XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-137">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-138">データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-138">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-139">一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-139">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-140">データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-140">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-141">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-141">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-142">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-142">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-143">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-143">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="ffbe8-144">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-144">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="security-considerations"></a><span data-ttu-id="ffbe8-145">セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="ffbe8-145">Security Considerations</span></span>  
 <span data-ttu-id="ffbe8-146">ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス アカウントのセキュリティ プロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-146">If a user uses a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process account is used.</span></span> <span data-ttu-id="ffbe8-147">SQL Server 認証を使用したログインは、データベース エンジン以外では認証できません。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-147">A login using SQL Server authentication cannot be authenticated outside of the Database Engine.</span></span> <span data-ttu-id="ffbe8-148">そのため、SQL Server 認証を使用したログインによって BULK INSERT コマンドが開始されると、SQL Server プロセス アカウント (SQL Server データベース エンジン サービスで使用されるアカウント) のセキュリティ コンテキストを使用してデータへの接続が行われます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-148">Therefore, when a BULK INSERT command is initiated by a login using SQL Server authentication, the connection to the data is made using the security context of the SQL Server process account (the account used by the SQL Server Database Engine service).</span></span> <span data-ttu-id="ffbe8-149">ソース データを正しく読み取るには、SQL Server データベース エンジンで使用されるアカウントに対して、ソース データへのアクセス権を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-149">To successfully read the source data you must grant the account used by the SQL Server Database Engine, access to the source data.</span></span> <span data-ttu-id="ffbe8-150">これに対して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーが Windows 認証を使用してログインした場合、そのユーザーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスのセキュリティ プロファイルに関係なく、そのユーザー アカウントでアクセス可能なファイルのみを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-150">In contrast, if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user logs on by using Windows Authentication, the user can read only those files that can be accessed by the user account, regardless of the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
 <span data-ttu-id="ffbe8-151">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに Windows 認証を使用してログインしたユーザーを考えます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-151">For example, consider a user who logged in to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="ffbe8-152">ユーザーが BULK INSERT または OPENROWSET を使用してデータ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータをインポートするには、アカウントにデータ ファイルの読み取りアクセス許可が与えられていなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-152">For the user to be able to use BULK INSERT or OPENROWSET to import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, the user account requires read access to the data file.</span></span> <span data-ttu-id="ffbe8-153">データ ファイルへのアクセスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスにそのファイルへのアクセス許可がなくても、ユーザーはそのファイルからテーブルにデータをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-153">With access to the data file, the user can import data from the file into a table even if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process does not have permission to access the file.</span></span> <span data-ttu-id="ffbe8-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスにファイル アクセス許可を与える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-154">The user does not have to grant file-access permission to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ffbe8-155">および [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows では、認証されている Windows ユーザーの資格情報を転送することで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスから別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへ接続できるように構成することが可能です。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-155">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows can be configured to enable an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by forwarding the credentials of an authenticated Windows user.</span></span> <span data-ttu-id="ffbe8-156">この設定を、" *権限借用* " または " *権限委譲*" といいます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-156">This arrangement is known as *impersonation* or *delegation*.</span></span> <span data-ttu-id="ffbe8-157">BULK INSERT または OPENROWSET を使用する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンによってユーザーの権限借用のセキュリティがどのように処理されるかを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-157">Understanding how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version handle security for user impersonation is important when you use BULK INSERT or OPENROWSET.</span></span> <span data-ttu-id="ffbe8-158">ユーザーの権限を借用することで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスまたはユーザーのいずれかが使用しているコンピューターとは異なるコンピューターにデータ ファイルを常駐させることができます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-158">User impersonation allows the data file to reside on a different computer than either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process or the user.</span></span> <span data-ttu-id="ffbe8-159">たとえば、 **Computer_A** 上のユーザーが **Computer_B**上のデータ ファイルにアクセスでき、資格情報の委任が適切に設定されている場合、このユーザーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer_C **上で実行されている**のインスタンスに接続して、 **Computer_B**上のデータ ファイルにアクセスし、そのファイルから **Computer_C**上のテーブルにデータを一括インポートできます。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-159">For example, if a user on **Computer_A** has access to a data file on **Computer_B**, and the delegation of credentials has been set appropriately, the user can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on **Computer_C**, access the data file on **Computer_B**, and bulk import data from that file into a table on **Computer_C**.</span></span>  
  
## <a name="bulk-importing-from-a-remote-data-file"></a><span data-ttu-id="ffbe8-160">リモート データ ファイルからの一括インポート</span><span class="sxs-lookup"><span data-stu-id="ffbe8-160">Bulk Importing from a Remote Data File</span></span>  
 <span data-ttu-id="ffbe8-161">BULK INSERT または INSERT...SELECT \* FROM OPENROWSET(BULK...) を使用して別のコンピューターからデータを一括インポートするには、データ ファイルを 2 台のコンピューター間で共有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-161">To use BULK INSERT or INSERT...SELECT \* FROM OPENROWSET(BULK...) to bulk import data from another computer, the data file must be shared between the two computers.</span></span> <span data-ttu-id="ffbe8-162">共有データ ファイルを指定するには、UNC (汎用名前付け規則) 名を使用します。UNC 名の一般的な形式は、 **\\\\** _Servername_ **\\** _Sharename_ **\\** _Path_ **\\** _Filename_です。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-162">To specify a shared data file, use its universal naming convention (UNC) name, which takes the general form, **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="ffbe8-163">また、データ ファイルへのアクセスに使用されるアカウントは、リモート ディスク上のファイルの読み取りに必要な権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-163">Additionally, the account used to access the data file must have the permissions that are required for reading the file on the remote disk.</span></span>  
  
 <span data-ttu-id="ffbe8-164">たとえば、次の `BULK INSERT` ステートメントでは、 `SalesOrderDetail` というデータ ファイルから `AdventureWorks` データベースの `newdata.txt`テーブルにデータの一括インポートを行います。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-164">For example, the following `BULK INSERT` statement bulk imports data into the `SalesOrderDetail` table of the `AdventureWorks` database from a data file that is named `newdata.txt`.</span></span> <span data-ttu-id="ffbe8-165">このデータ ファイルは、 `\dailyorders` というシステムの `salesforce` というネットワーク共有ディレクトリの `computer2`という共有フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-165">This data file resides in a shared folder named `\dailyorders` on a network share directory named `salesforce` on a system named `computer2`.</span></span>  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ffbe8-166">クライアントが読み取るファイルは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とは無関係であるため、**bcp** にはこの制限は適用されません。</span><span class="sxs-lookup"><span data-stu-id="ffbe8-166">This restriction does not apply to the **bcp** utility because the client reads the file independently of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffbe8-167">参照</span><span class="sxs-lookup"><span data-stu-id="ffbe8-167">See Also</span></span>  
 <span data-ttu-id="ffbe8-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffbe8-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="ffbe8-169">[SELECT 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffbe8-169">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="ffbe8-170">[データの一括インポートと一括エクスポート &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ffbe8-170">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="ffbe8-171">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffbe8-171">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="ffbe8-172">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffbe8-172">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="ffbe8-173">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffbe8-173">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span></span>  
 <span data-ttu-id="ffbe8-174">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ffbe8-174">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="ffbe8-175">BULK INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ffbe8-175">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
