---
title: フルテキスト検索に使用する類義語辞典ファイルの構成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], configuring
- thesaurus [full-text search]
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67f0a5af7be4f41ce33692e5f28ad5adf676980c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743182"
---
# <a name="configure-and-manage-thesaurus-files-for-full-text-search"></a><span data-ttu-id="a6426-102">フルテキスト検索に使用する類義語辞典ファイルの構成と管理</span><span class="sxs-lookup"><span data-stu-id="a6426-102">Configure and Manage Thesaurus Files for Full-Text Search</span></span>
  <span data-ttu-id="a6426-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ではフルテキスト クエリで類義語辞典を使用し、指定した用語のシノニムを検索できます。</span><span class="sxs-lookup"><span data-stu-id="a6426-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], full-text queries can search for synonyms of user-specified terms through the use of a thesaurus.</span></span> <span data-ttu-id="a6426-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *類義語辞典* では、特定の言語の一連のシノニムを定義します。</span><span class="sxs-lookup"><span data-stu-id="a6426-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *thesaurus* defines a set of synonyms for a specific language.</span></span> <span data-ttu-id="a6426-105">システム管理者は、拡張セットと置換セットという 2 つの形式のシノニムを定義できます。</span><span class="sxs-lookup"><span data-stu-id="a6426-105">System administrators can define two forms of synonyms: expansion sets and replacement sets.</span></span> <span data-ttu-id="a6426-106">フルテキスト データに合わせた類義語辞典を作成すると、そのデータのフルテキスト クエリのスコープを効果的に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="a6426-106">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="a6426-107">類義語辞典の照合は、FORMSOF THESAURUS 句を指定する [CONTAINS](/sql/t-sql/queries/freetext-transact-sql) クエリと [CONTAINSTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) クエリの場合、およびすべての [FREETEXT](/sql/t-sql/queries/contains-transact-sql) クエリと [FREETEXTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) クエリの場合に行われます。</span><span class="sxs-lookup"><span data-stu-id="a6426-107">Thesaurus matching occurs for all [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) queries and for any [CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) queries that specify the FORMSOF THESAURUS clause.</span></span>  
  
##  <a name="basic-tasks-for-setting-up-a-thesaurus-file"></a><a name="tasks"></a><span data-ttu-id="a6426-108">類義語辞典ファイルを設定するための基本的なタスク</span><span class="sxs-lookup"><span data-stu-id="a6426-108">Basic Tasks for Setting Up a Thesaurus File</span></span>  
 <span data-ttu-id="a6426-109">サーバー インスタンス上のフルテキスト検索クエリで特定の言語のシノニムを検索するには、その言語の類義語辞典のマッピング (シノニム) を定義しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6426-109">Before full-text search queries on your server instance can look for synonyms in a given language, you must define thesaurus mappings (synonyms) for that language.</span></span> <span data-ttu-id="a6426-110">各類義語辞典は、次の内容を定義するために手動で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6426-110">Each thesaurus must be manually configured to define the following:</span></span>  
  
-   <span data-ttu-id="a6426-111">分音文字の設定</span><span class="sxs-lookup"><span data-stu-id="a6426-111">Diacritics setting</span></span>  
  
     <span data-ttu-id="a6426-112">類義語辞典によっては、すべての検索パターンが、チルダ ( **~** )、アキュートアクセント記号 (**??**)、ウムラウト (**??**) などの分音記号と区別されるか、または区別されません。(*アクセントを区別*するか、*アクセントを区別*しない)。</span><span class="sxs-lookup"><span data-stu-id="a6426-112">For a given thesaurus, all search patterns are either sensitive or insensitive to diacritical marks such as a tilde (**~**), acute accent mark (**??**), or umlaut (**??**) (that is, *accent sensitive* or *accent insensitive*).</span></span> <span data-ttu-id="a6426-113">たとえば、"caf??" というパターンを指定したとします。</span><span class="sxs-lookup"><span data-stu-id="a6426-113">For example, suppose you specify the pattern "caf??"</span></span> <span data-ttu-id="a6426-114">他のパターンに置き換えられるように指定するとします。</span><span class="sxs-lookup"><span data-stu-id="a6426-114">to be replaced by other patterns in a full-text query.</span></span> <span data-ttu-id="a6426-115">類義語辞典でアクセントを区別しない場合、フルテキスト検索では "caf??" というパターンが置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a6426-115">If the thesaurus is accent-insensitive, full-text search replaces the patterns "caf??"</span></span> <span data-ttu-id="a6426-116">と "cafe" が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a6426-116">and "cafe".</span></span> <span data-ttu-id="a6426-117">類義語辞典でアクセントが区別される場合、フルテキスト検索では "caf??" というパターンのみが置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a6426-117">If the thesaurus is accent-sensitive, full-text search replaces only the pattern "caf??".</span></span> <span data-ttu-id="a6426-118">既定では、類義語辞典でアクセントは区別されません。</span><span class="sxs-lookup"><span data-stu-id="a6426-118">By default, a thesaurus is accent-insensitive.</span></span>  
  
-   <span data-ttu-id="a6426-119">拡張セット</span><span class="sxs-lookup"><span data-stu-id="a6426-119">Expansion set</span></span>  
  
     <span data-ttu-id="a6426-120">拡張セットには、フルテキスト クエリで相互に置き換えられる "writer"、"author"、"journalist" などのシノニムのグループが格納されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-120">An expansion set contains a group of synonyms such as "writer", "author", and "journalist" that are substituted for one another by a full-text query.</span></span> <span data-ttu-id="a6426-121">拡張セット内のシノニムと一致するクエリは、拡張セット内の他のシノニムもすべて含むように拡張されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-121">Queries that contain a match for any synonym in an expansion set are expanded to include every other synonym in the expansion set.</span></span>  
  
     <span data-ttu-id="a6426-122">詳細については、このトピックの後半の「拡張セットの XML 構造」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6426-122">For more information, see "XML Structure of an Expansion Set," later in this topic.</span></span>  
  
-   <span data-ttu-id="a6426-123">置換セット</span><span class="sxs-lookup"><span data-stu-id="a6426-123">Replacement set</span></span>  
  
     <span data-ttu-id="a6426-124">置換セットには、代替セットによって置き換えられるテキストのパターンが格納されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-124">A replacement set contains a text pattern to be replaced by a substitution set.</span></span> <span data-ttu-id="a6426-125">このトピックの後半で説明する「置換セットの XML 構造」の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6426-125">For an example, see the section "XML Structure of a Replacement Set" later in this topic.</span></span>  
  
  
##  <a name="initial-content-of-the-thesaurus-files"></a><a name="initial_thesaurus_files"></a><span data-ttu-id="a6426-126">類義語辞典ファイルの初期コンテンツ</span><span class="sxs-lookup"><span data-stu-id="a6426-126">Initial Content of the Thesaurus Files</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a6426-127">には XML 類義語辞典ファイルのセットが用意されており、サポートされている各言語に対して 1 つのファイルが存在します。</span><span class="sxs-lookup"><span data-stu-id="a6426-127">provides a set of XML thesaurus files, one for each supported language.</span></span> <span data-ttu-id="a6426-128">これらのファイルは基本的に空です。</span><span class="sxs-lookup"><span data-stu-id="a6426-128">These files are essentially empty.</span></span> <span data-ttu-id="a6426-129">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類義語辞典およびコメント アウトされたサンプル類義語辞典に共通する最上位の XML 構造のみが格納されています。</span><span class="sxs-lookup"><span data-stu-id="a6426-129">They contain only the top-level XML structure that is common to all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] thesauruses and a commented-out sample thesaurus.</span></span>  
  
 <span data-ttu-id="a6426-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でリリースされている類義語辞典ファイルには、すべて次の XML コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a6426-130">The thesaurus files that are released with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all contain the following XML code:</span></span>  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
  
##  <a name="location-of-the-thesaurus-files"></a><a name="location"></a><span data-ttu-id="a6426-131">類義語辞典ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="a6426-131">Location of the Thesaurus Files</span></span>  
 <span data-ttu-id="a6426-132">類義語辞典ファイルの既定の場所は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a6426-132">The default location of the thesaurus files is:</span></span>  
  
 <span data-ttu-id="a6426-133">*<SQL_Server_data_files_path>* \MSSQL12.MSSQLSERVER\MSSQL\FTDATA</span><span class="sxs-lookup"><span data-stu-id="a6426-133">*<SQL_Server_data_files_path>* \MSSQL12.MSSQLSERVER\MSSQL\FTDATA</span></span>\  
  
 <span data-ttu-id="a6426-134">この既定の場所には、次のファイルが格納されています。</span><span class="sxs-lookup"><span data-stu-id="a6426-134">This default location contains the following files:</span></span>  
  
-   <span data-ttu-id="a6426-135">言語固有の類義語辞典ファイル</span><span class="sxs-lookup"><span data-stu-id="a6426-135">Language-specific thesaurus files</span></span>  
  
     <span data-ttu-id="a6426-136">セットアップ中に、空の類義語辞典ファイルが前述の場所にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a6426-136">During setup, empty thesaurus files are installed in the above location.</span></span> <span data-ttu-id="a6426-137">サポートされている言語ごとに個別のファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a6426-137">A separate file is provided for each supported language.</span></span> <span data-ttu-id="a6426-138">システム管理者は、これらのファイルをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="a6426-138">A system administrator can customize these files.</span></span>  
  
     <span data-ttu-id="a6426-139">類義語辞典ファイルの既定のファイル名には、次の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-139">The default file names of the thesaurus files use following format:</span></span>  
  
     <span data-ttu-id="a6426-140">' ts ' + \<three-letter language-abbreviation> + ' .xml '</span><span class="sxs-lookup"><span data-stu-id="a6426-140">'ts' + \<three-letter language-abbreviation> + '.xml'</span></span>  
  
     <span data-ttu-id="a6426-141">特定の言語の類義語辞典ファイルの名前は、レジストリで HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev> と指定されています。</span><span class="sxs-lookup"><span data-stu-id="a6426-141">The name of the thesaurus file for a given language is specified in the registry in the following value HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev>.</span></span>  
  
-   <span data-ttu-id="a6426-142">グローバル類義語辞典ファイル</span><span class="sxs-lookup"><span data-stu-id="a6426-142">The global thesaurus file</span></span>  
  
     <span data-ttu-id="a6426-143">tsGlobal.xml は空のグローバル類義語辞典ファイルです。</span><span class="sxs-lookup"><span data-stu-id="a6426-143">An empty global thesaurus file, tsGlobal.xml.</span></span>  
  
 <span data-ttu-id="a6426-144">類義語辞典ファイルの場所および名前を変更するには、そのレジストリ キーを変更します。</span><span class="sxs-lookup"><span data-stu-id="a6426-144">You can change the location and names of a thesaurus file by changing its registry key.</span></span> <span data-ttu-id="a6426-145">各言語の類義語辞典ファイルの場所は、レジストリで次のように指定されています。</span><span class="sxs-lookup"><span data-stu-id="a6426-145">For each language, the location of the thesaurus file is specified in the following value in the registry:</span></span>  
  
 <span data-ttu-id="a6426-146">HKLM/SOFTWARE/Microsoft/Microsoft SQL Server// \<instance name> Mssearch/言語/ \<language-abbreviation> /TsaurusFile</span><span class="sxs-lookup"><span data-stu-id="a6426-146">HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/\<instance name>/MSSearch/Language/\<language-abbreviation>/TsaurusFile</span></span>  
  
 <span data-ttu-id="a6426-147">グローバル類義語辞典ファイルは、LCID 0 のニュートラル言語に対応します。</span><span class="sxs-lookup"><span data-stu-id="a6426-147">The global thesaurus file corresponds to the Neutral language with LCID 0.</span></span> <span data-ttu-id="a6426-148">この値は、管理者のみが変更できます。</span><span class="sxs-lookup"><span data-stu-id="a6426-148">This value can be changed by administrators only.</span></span>  
  
  
##  <a name="how-queries-use-thesaurus-files"></a><a name="how_queries_use_tf"></a><span data-ttu-id="a6426-149">クエリで類義語辞典ファイルを使用する方法</span><span class="sxs-lookup"><span data-stu-id="a6426-149">How Queries Use Thesaurus Files</span></span>  
 <span data-ttu-id="a6426-150">類義語辞典クエリでは、言語固有の類義語辞典とグローバル類義語辞典の両方が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-150">A thesaurus query uses both a language-specific thesaurus and the global thesaurus.</span></span> <span data-ttu-id="a6426-151">まず、言語固有のファイルが参照されて処理のために読み込まれ (まだ読み込まれていない場合)、</span><span class="sxs-lookup"><span data-stu-id="a6426-151">First, the query looks up the language-specific file and loads it for processing (unless it is already loaded).</span></span> <span data-ttu-id="a6426-152">類義語辞典ファイル内の拡張セットおよび置換セットのルールで指定された言語固有のシノニムを含むようにクエリが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-152">The query is expanded to include the language-specific synonyms specified by the expansion set and replacement set rules in the thesaurus file.</span></span> <span data-ttu-id="a6426-153">この手順がグローバル類義語辞典に対して繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-153">These steps are then repeated for the global thesaurus.</span></span> <span data-ttu-id="a6426-154">ただし、言語固有の類義語辞典ファイルで既に一致するものが見つかった用語は、グローバル類義語辞典では照合されません。</span><span class="sxs-lookup"><span data-stu-id="a6426-154">However, if a term is already part of a match in the language specific thesaurus file, the term is ineligible for matching in the global thesaurus.</span></span>  
  
  
##  <a name="understanding-the-structure-of-a-thesaurus-file"></a><a name="structure"></a><span data-ttu-id="a6426-155">類義語辞典ファイルの構造について</span><span class="sxs-lookup"><span data-stu-id="a6426-155">Understanding the Structure of a Thesaurus File</span></span>  
 <span data-ttu-id="a6426-156">各類義語辞典ファイルでは、ID が `Microsoft Search Thesaurus` の XML コンテナー、およびサンプル類義語辞典を含むコメント `<!--`...`-->` が定義されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-156">Each thesaurus file defines an XML container whose ID is `Microsoft Search Thesaurus`, and a comment, `<!--` ... `-->`, that contains a sample thesaurus.</span></span> <span data-ttu-id="a6426-157">類義語辞典は、次のように、分音文字の \<thesaurus> 設定、拡張セット、および置換セットを定義する子要素のサンプルを含む要素で定義されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-157">The thesaurus is defined in a \<thesaurus> element that contains samples of the child elements that define the diacritics setting, expansion sets, and replacement sets, as follows:</span></span>  
  
-   <span data-ttu-id="a6426-158">分音文字の設定の XML 構造</span><span class="sxs-lookup"><span data-stu-id="a6426-158">XML Structure of the Diacritical Setting</span></span>  
  
     <span data-ttu-id="a6426-159">類義語辞典の分音文字の設定は、単一の <diacritics_sensitive> 要素で指定されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-159">The diacritics setting of a thesaurus is specified in a single <diacritics_sensitive> element.</span></span> <span data-ttu-id="a6426-160">この要素には、次のようにアクセントの区別を制御する整数値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6426-160">This element contains an integer value that controls accent sensitivity, as follows:</span></span>  
  
    |<span data-ttu-id="a6426-161">分音文字の設定</span><span class="sxs-lookup"><span data-stu-id="a6426-161">Diacritics Setting</span></span>|<span data-ttu-id="a6426-162">値</span><span class="sxs-lookup"><span data-stu-id="a6426-162">Value</span></span>|<span data-ttu-id="a6426-163">XML</span><span class="sxs-lookup"><span data-stu-id="a6426-163">XML</span></span>|  
    |------------------------|-----------|---------|  
    |<span data-ttu-id="a6426-164">アクセントを区別しない</span><span class="sxs-lookup"><span data-stu-id="a6426-164">Accent insensitive</span></span>|<span data-ttu-id="a6426-165">0</span><span class="sxs-lookup"><span data-stu-id="a6426-165">0</span></span>|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |<span data-ttu-id="a6426-166">アクセントを区別する</span><span class="sxs-lookup"><span data-stu-id="a6426-166">Accent sensitive</span></span>|<span data-ttu-id="a6426-167">1</span><span class="sxs-lookup"><span data-stu-id="a6426-167">1</span></span>|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  <span data-ttu-id="a6426-168">この設定はファイルで 1 回のみ適用でき、ファイル内のすべての検索パターンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-168">This setting can only be applied one time in the file, and it applies to all search patterns in the file.</span></span> <span data-ttu-id="a6426-169">この設定は個別のパターンには指定できません。</span><span class="sxs-lookup"><span data-stu-id="a6426-169">This setting cannot be specified for individual patterns.</span></span>  
  
-   <span data-ttu-id="a6426-170">拡張セットの XML 構造</span><span class="sxs-lookup"><span data-stu-id="a6426-170">XML Structure of an Expansion Set</span></span>  
  
     <span data-ttu-id="a6426-171">各拡張セットは \<expansion> 要素で囲みます。</span><span class="sxs-lookup"><span data-stu-id="a6426-171">Each expansion set is enclosed within an \<expansion> element.</span></span> <span data-ttu-id="a6426-172">この要素内に、\<sub> 要素で囲んだ 1 つまたは複数の代替文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="a6426-172">Within this element, you specify one or more substitutions in a \<sub> element.</span></span> <span data-ttu-id="a6426-173">拡張セットでは、互いにシノニムとなる代替文字列のグループを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a6426-173">In the expansion set, you can specify a group of substitutions that are synonyms of each other.</span></span>  
  
     <span data-ttu-id="a6426-174">たとえば、拡張のセクションを編集して、代替文字列 "writer"、"author"、および "journalist" をシノニムとして扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="a6426-174">For example, you can edit the expansion section to treat the substitutions "writer", "author", and "journalist" as synonyms.</span></span> <span data-ttu-id="a6426-175">1 つの代替文字列と一致するフルテキスト検索クエリは、拡張セット内の他の代替文字列もすべて含むように拡張されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-175">full-text search queries that contain matches in one substitution are expanded to include all other substitutions specified in the expansion set.</span></span> <span data-ttu-id="a6426-176">したがって、上記の例では、"author" という語に対して FORMS OF THESAURUS クエリまたは FREETEXT クエリを実行すると、フルテキスト検索では "writer" と "journalist" という語も含む検索結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-176">Therefore, in the preceding example, when you issue a FORMS OF THESAURUS or a FREETEXT query for the word "author", full-text search also returns search results containing the words "writer" and "journalist".</span></span>  
  
     <span data-ttu-id="a6426-177">上記の例の拡張セットのセクションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6426-177">This is what the expansion set section would look like for the above example:</span></span>  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   <span data-ttu-id="a6426-178">置換セットの XML 構造</span><span class="sxs-lookup"><span data-stu-id="a6426-178">XML Structure of a Replacement Set</span></span>  
  
     <span data-ttu-id="a6426-179">各置換セットは \<replacement> 要素で囲みます。</span><span class="sxs-lookup"><span data-stu-id="a6426-179">Each replacement set is enclosed within a \<replacement> element.</span></span> <span data-ttu-id="a6426-180">この要素内に、\<pat> 要素で囲んだ 1 つ以上のパターンと \<sub> 要素で囲んだ 0 個以上の代替文字列 (シノニムごとに 1 つ) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a6426-180">Within this element you can specify one or more patterns in a \<pat> element and zero or more substitutions in \<sub> elements, one per synonym.</span></span> <span data-ttu-id="a6426-181">ここで指定するパターンが代替セットで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a6426-181">You can specify a pattern to be replaced by a substitution set.</span></span> <span data-ttu-id="a6426-182">パターンと代替文字列には、語または語の並びを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a6426-182">Patterns and substitutions can contain a word, or a sequence of words.</span></span> <span data-ttu-id="a6426-183">パターンに対して代替文字列が指定されていない場合は、ユーザー クエリからパターンが削除されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-183">If there is no substitution specified for a pattern, it has the effect of removing the pattern from the user query.</span></span>  
  
     <span data-ttu-id="a6426-184">たとえば、"Win8" というパターンを検索するクエリを、"Windows Server 2012" または "Windows 8.0" という代替文字列に置き換えるとします。</span><span class="sxs-lookup"><span data-stu-id="a6426-184">For example, suppose you want queries for "Win8", the pattern, to be replaced by "Windows Server 2012" or "Windows 8.0", the substitutions.</span></span> <span data-ttu-id="a6426-185">この場合、"Win8" に対してフルテキスト クエリを実行すると、フルテキスト検索からは "Windows Server 201" または "Windows 8.0" だけを含む検索結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-185">If you run a full-text query for "Win8", full-text search only returns search results containing "Windows Server 2012" or "Windows 8.0".</span></span> <span data-ttu-id="a6426-186">"Win8" を含む結果は返されません。</span><span class="sxs-lookup"><span data-stu-id="a6426-186">It does not return results containing "Win8".</span></span> <span data-ttu-id="a6426-187">これは、"Win8" が "Windows Server 2012" と "Windows 8.0" というパターンに置換されるためです。</span><span class="sxs-lookup"><span data-stu-id="a6426-187">This is because the pattern "Win8" has been "replaced" by the patterns "Windows Server 2012" and "Windows 8.0".</span></span>  
  
     <span data-ttu-id="a6426-188">上記の例の置換セットのセクションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6426-188">This is what the replacement set section would look like for the above example:</span></span>  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     <span data-ttu-id="a6426-189">類似するパターンを含む 2 つの置換セットが一致する場合、2 つのうちで長い置換セットが優先されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-189">If you have two replacement sets with similar patterns being matched, the longer of the two takes precedence.</span></span> <span data-ttu-id="a6426-190">たとえば、"Internet Explorer online community" に対して FORMS OF THESAURUS クエリを実行し、次の置換セットを使用すると、"Internet Explorer" 置換セットの方が "Internet" 置換セットよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-190">For example, if you run a FORMS OF THESAURUS query for "Internet Explorer online community" and you have the following replacement sets, the "Internet Explorer" replacement set takes precedence over the "Internet" replacement set.</span></span> <span data-ttu-id="a6426-191">したがって、このクエリは "IE online community" または "IE 9 online community" として処理されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-191">The query will therefore be processed as "IE online community" or "IE 9 online community".</span></span>  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     <span data-ttu-id="a6426-192">and</span><span class="sxs-lookup"><span data-stu-id="a6426-192">and</span></span>  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
  
##  <a name="working-with-thesaurus-files"></a><a name="working_with_thesaurus_files"></a><span data-ttu-id="a6426-193">類義語辞典ファイルの操作</span><span class="sxs-lookup"><span data-stu-id="a6426-193">Working with Thesaurus Files</span></span>  
 <span data-ttu-id="a6426-194">**類義語辞典ファイルを編集するには**</span><span class="sxs-lookup"><span data-stu-id="a6426-194">**To edit a thesaurus file**</span></span>  
  
-   [<span data-ttu-id="a6426-195">類義語辞典ファイルの編集</span><span class="sxs-lookup"><span data-stu-id="a6426-195">Editing a Thesaurus File</span></span>](#editing)  
  
 <span data-ttu-id="a6426-196">**更新された類義語辞典ファイルを読み込むには**</span><span class="sxs-lookup"><span data-stu-id="a6426-196">**To load an updated thesaurus file**</span></span>  
  
-   [<span data-ttu-id="a6426-197">sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a6426-197">sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
 <span data-ttu-id="a6426-198">**ワード ブレーカー、類語辞典、およびストップリストの組み合わせによるトークン化の結果を表示するには**</span><span class="sxs-lookup"><span data-stu-id="a6426-198">**To view the tokenization result of a word breaker, thesaurus, and stoplist combination**</span></span>  
  
-   [<span data-ttu-id="a6426-199">dm_fts_parser &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="a6426-199">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="editing-a-thesaurus-file"></a><a name="editing"></a><span data-ttu-id="a6426-200">類義語辞典ファイルの編集</span><span class="sxs-lookup"><span data-stu-id="a6426-200">Editing a Thesaurus File</span></span>  
 <span data-ttu-id="a6426-201">特定の言語の類義語辞典は、類義語辞典ファイル (XML ファイル) を編集することによって構成できます。</span><span class="sxs-lookup"><span data-stu-id="a6426-201">The thesaurus for a given language can be configured by editing its thesaurus file (an XML file).</span></span> <span data-ttu-id="a6426-202">セットアップ中に、コンテナーとコメントアウトされた sample 要素のみを含む空の類義語辞典ファイル \<xml> \<thesaurus> がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a6426-202">During setup, empty thesaurus files that contain only the \<xml> container and a commented-out sample \<thesaurus> element are installed.</span></span> <span data-ttu-id="a6426-203">シノニムが正常に機能するかどうかを確認するフルテキスト検索クエリを実行するには、一連のシノニムを定義する実際の要素を作成する必要があり \<thesaurus> ます。</span><span class="sxs-lookup"><span data-stu-id="a6426-203">In order for full-text search queries that look for synonyms to work properly, you must create an actual \<thesaurus> element that defines a set of synonyms.</span></span> <span data-ttu-id="a6426-204">シノニムの定義には、拡張セットと置換セットという 2 つの形式があります。</span><span class="sxs-lookup"><span data-stu-id="a6426-204">You can define two forms of synonyms, expansion sets and replacement sets.</span></span>  
  
 <span data-ttu-id="a6426-205">**類義語辞典ファイルの制限**</span><span class="sxs-lookup"><span data-stu-id="a6426-205">**Restrictions for thesaurus files**</span></span>  
  
 <span data-ttu-id="a6426-206">類義語辞典ファイルの編集には、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a6426-206">The following restrictions apply to editing a thesaurus file:</span></span>  
  
-   <span data-ttu-id="a6426-207">類義語辞典ファイルを更新、変更、または削除できるのはシステム管理者だけです。</span><span class="sxs-lookup"><span data-stu-id="a6426-207">Only system administrators can update, modify, or delete thesaurus files.</span></span>  
  
-   <span data-ttu-id="a6426-208">テキスト エディター ツールを使用して類義語辞典ファイルを編集する場合、ファイルが Unicode 形式で保存され、バイト順マークが指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6426-208">When editing thesaurus files using text editor tools, the files must be saved in Unicode format, and Byte Order Marks must be specified.</span></span>  
  
-   <span data-ttu-id="a6426-209">類義語辞典のエントリを空にしたり、空の文字列の単語に区切ったりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a6426-209">Thesaurus entries cannot be empty or word break to an empty string.</span></span>  
  
-   <span data-ttu-id="a6426-210">類義語辞典ファイルの語句は 512 文字以下にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6426-210">Phrases in the thesaurus file must be no longer than 512 characters.</span></span>  
  
-   <span data-ttu-id="a6426-211">類義語辞典には、拡張セットの \<sub> エントリと置換セットの \<pat> 要素間で重複したエントリを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="a6426-211">A thesaurus must not contain any duplicate entries among the \<sub> entries of expansion sets and the \<pat> elements of replacement sets.</span></span>  
  
 <span data-ttu-id="a6426-212">**類義語辞典ファイルに関する推奨事項**</span><span class="sxs-lookup"><span data-stu-id="a6426-212">**Recommendations for thesaurus files**</span></span>  
  
 <span data-ttu-id="a6426-213">類義語辞典ファイル内のエントリには特殊文字を含めないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a6426-213">We recommend that entries in the thesaurus file contain no special characters.</span></span> <span data-ttu-id="a6426-214">これは、特殊文字に対するワード ブレーカーの動作がわかりづらいためです。</span><span class="sxs-lookup"><span data-stu-id="a6426-214">This is because word breakers have subtle behaviors with respect to special characters.</span></span> <span data-ttu-id="a6426-215">類義語辞典のエントリに特殊文字が含まれる場合、そのエントリと組み合わせて使用されるワード ブレーカーの動作がフルテキスト クエリに与える影響がわかりづらくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a6426-215">If a thesaurus entry contains any special characters, word breakers used in combination with that entry can have subtle behavioral implications for a full-text query.</span></span>  
  
 <span data-ttu-id="a6426-216">ストップワードはフルテキスト インデックスから省略されるため、\<sub> エントリにはストップワードを含めないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a6426-216">We recommend that \<sub> entries contain no stopwords since stopwords are omitted from the full-text index.</span></span> <span data-ttu-id="a6426-217">クエリは類義語辞典ファイルの \<sub> エントリを含むように拡張されるため、\<sub> エントリにストップワードが含まれる場合は、クエリのサイズが不必要に大きくなります。</span><span class="sxs-lookup"><span data-stu-id="a6426-217">Queries are expanded to include the \<sub> entries from a thesaurus file, and if a \<sub> entry contains stopwords, query size increases unnecessarily.</span></span>  
  
#### <a name="to-edit-a-thesaurus-file"></a><span data-ttu-id="a6426-218">類義語辞典ファイルを編集するには</span><span class="sxs-lookup"><span data-stu-id="a6426-218">To edit a thesaurus file</span></span>  
  
1.  <span data-ttu-id="a6426-219">類義語辞典ファイルをメモ帳で開きます。</span><span class="sxs-lookup"><span data-stu-id="a6426-219">Open the thesaurus file in Notepad.</span></span>  
  
2.  <span data-ttu-id="a6426-220">初めて類義語辞典ファイルを編集する場合は、ファイルの先頭と末尾の次のコメント行をそれぞれ削除します。</span><span class="sxs-lookup"><span data-stu-id="a6426-220">If you are editing the thesaurus file for the first time, remove the following comment lines at the beginning and end of the file, respectively:</span></span>  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  <span data-ttu-id="a6426-221">置換セットまたは拡張セットを追加、変更、または削除します。</span><span class="sxs-lookup"><span data-stu-id="a6426-221">Add, modify, or delete a replacement set, or expansion set.</span></span>  
  
4.  <span data-ttu-id="a6426-222">ファイルを保存し、メモ帳を閉じます。</span><span class="sxs-lookup"><span data-stu-id="a6426-222">Save the file and close Notepad.</span></span>  
  
5.  <span data-ttu-id="a6426-223">類義語辞典ファイルの内容を tempdb に読み込むために [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) を使用し、類義語辞典ファイルの言語に対応するロケール識別子 (LCID) を指定します。</span><span class="sxs-lookup"><span data-stu-id="a6426-223">Use [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) to load the content of the thesaurus file into tempdb, specifying the local identifier (LCID) that corresponds to the language of the thesaurus file.</span></span> <span data-ttu-id="a6426-224">たとえば、英語の類義語辞典ファイル tsenu.xml の場合、対応する LCID は 1033 です。</span><span class="sxs-lookup"><span data-stu-id="a6426-224">For example, for the English thesaurus file, tsenu.xml, the corresponding LCID is 1033.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
  
## <a name="see-also"></a><span data-ttu-id="a6426-225">参照</span><span class="sxs-lookup"><span data-stu-id="a6426-225">See Also</span></span>  
 <span data-ttu-id="a6426-226">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6426-226">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="a6426-227">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6426-227">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="a6426-228">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6426-228">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="a6426-229">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6426-229">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 [<span data-ttu-id="a6426-230">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="a6426-230">Full-Text Search</span></span>](full-text-search.md)  
  
  
