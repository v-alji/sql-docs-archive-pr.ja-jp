---
title: フルテキスト インデックスの作成のトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- indexes [full-text search]
- troubleshooting [SQL Server], full-text search
- troubleshooting [full-text search]
ms.assetid: 964c43a8-5019-4179-82aa-63cd0ef592ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eaca5fcf2dfbac57fc6d3ba6178251927d15aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645477"
---
# <a name="troubleshoot-full-text-indexing"></a><span data-ttu-id="826b2-102">フルテキスト インデックスの作成のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="826b2-102">Troubleshoot Full-Text Indexing</span></span>
     
##  <a name="troubleshoot-full-text-indexing-failures"></a><a name="failure"></a> <span data-ttu-id="826b2-103">フルテキスト インデックスの作成エラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="826b2-103">Troubleshoot Full-Text Indexing Failures</span></span>  
 <span data-ttu-id="826b2-104">フルテキスト インデックスの作成時または保守時には、後述の理由により、フルテキスト インデクサーが 1 つ以上の行のインデックス作成に失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="826b2-104">While populating or maintaining a full-text index, the full-text indexer, for reasons described below, might fail to index one or more rows.</span></span> <span data-ttu-id="826b2-105">このような行レベルのエラーでは、インデックスの作成は中止されることなく完了します。</span><span class="sxs-lookup"><span data-stu-id="826b2-105">These row-level errors do not prevent the population from completing.</span></span> <span data-ttu-id="826b2-106">インデクサーは、エラーが発生した行をスキップします。そのため、エラーが発生した行に含まれる内容のクエリはできません。</span><span class="sxs-lookup"><span data-stu-id="826b2-106">The indexer skips these rows, which means that you are not able to query for content contained in these rows.</span></span>  
  
 <span data-ttu-id="826b2-107">インデックス作成は、次の場合に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="826b2-107">Indexing failures can occur when:</span></span>  
  
-   <span data-ttu-id="826b2-108">インデクサーが、フィルター コンポーネントやワード ブレーカー コンポーネントを検出できないか、読み込むことができない。</span><span class="sxs-lookup"><span data-stu-id="826b2-108">The indexer cannot find or load a filter or word breaker component.</span></span> <span data-ttu-id="826b2-109">このエラーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに登録されていない言語のドキュメント形式や内容がテーブル行に含まれる場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="826b2-109">This failure can occur if the table row contains a document format or content in a language that has not been registered with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="826b2-110">また、登録済みのワード ブレーカー コンポーネントやフィルター コンポーネントを読み込むときに、コンポーネントに署名されていないか、署名の検証に失敗した場合にも発生します。</span><span class="sxs-lookup"><span data-stu-id="826b2-110">This failure can also happen if the registered word breaker or filter component was not signed or failed signature verification when it was being loaded.</span></span>  
  
-   <span data-ttu-id="826b2-111">ワード ブレーカーやフィルターなどのコンポーネントが失敗してインデクサーにエラーを返す。</span><span class="sxs-lookup"><span data-stu-id="826b2-111">A component, such as a word breaker or filter, fails and returns an error to the indexer.</span></span> <span data-ttu-id="826b2-112">このエラーは、インデックスが作成されたドキュメントが破損し、フィルターがドキュメントからテキストを抽出できない場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="826b2-112">This can happen if the document being indexed is corrupt and the filter is unable to extract text from the document.</span></span> <span data-ttu-id="826b2-113">また、フルテキスト フィルター デーモン ホスト (fdhost.exe) でのメモリ制限により、1 行の内容が一定サイズを超え、コンポーネントでは処理できない場合にも発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="826b2-113">This can also occur when a component is unable to handle the content of a single row above a certain size, due to memory limits on the full-text filter daemon host (fdhost.exe).</span></span>  
  
 <span data-ttu-id="826b2-114">行レベルのエラーが発生するたびに、クロール ログにエラーの理由の詳細が記録されます。</span><span class="sxs-lookup"><span data-stu-id="826b2-114">For each row-level failure, the crawl log contains details on the reason for the failure.</span></span> <span data-ttu-id="826b2-115">エラー数は、完全作成または増分作成の最後に集計されます。</span><span class="sxs-lookup"><span data-stu-id="826b2-115">The error counts are summarized at the end of a full or incremental population.</span></span>  
  
 <span data-ttu-id="826b2-116">他に、インデックス作成のプロセス自体に影響を与え、作成を完了できない次のようなエラーもあります。</span><span class="sxs-lookup"><span data-stu-id="826b2-116">There are other failures that can impact the indexing process itself and prevent the population from completing:</span></span>  
  
-   <span data-ttu-id="826b2-117">フルテキスト インデックスが、フルテキスト カタログに含むことができる行数の制限を超える。</span><span class="sxs-lookup"><span data-stu-id="826b2-117">The full-text index exceeds the limit for the number of rows that can be contained in a full-text catalog.</span></span>  
  
-   <span data-ttu-id="826b2-118">インデックスが作成されているテーブルのクラスター化インデックスまたはフルテキスト キー インデックスが変更、削除または再構築される。</span><span class="sxs-lookup"><span data-stu-id="826b2-118">A clustered index or full-text key index on the table being indexed gets altered, dropped, or rebuilt.</span></span>  
  
-   <span data-ttu-id="826b2-119">ハードウェア エラーやディスクの破損などによりフルテキスト カタログが破損する。</span><span class="sxs-lookup"><span data-stu-id="826b2-119">A hardware failure or disk corruption results in the corruption of the full-text catalog.</span></span>  
  
-   <span data-ttu-id="826b2-120">フルテキスト インデックスが作成されているテーブルを含むファイル グループがオフラインになるか、読み取り専用になる。</span><span class="sxs-lookup"><span data-stu-id="826b2-120">A file group that contains the table being full-text indexed goes offline, or is made read-only.</span></span>  
  
 <span data-ttu-id="826b2-121">すべての重要なフルテキスト インデックス作成操作の最後、または作成が完了していないことがわかったときは、クロール ログを確認してください。</span><span class="sxs-lookup"><span data-stu-id="826b2-121">You should view the crawl log at the end of any significant full-text index population operation, or when you find that a population did not complete.</span></span>  
  
### <a name="unsigned-components"></a><span data-ttu-id="826b2-122">署名されていないコンポーネント</span><span class="sxs-lookup"><span data-stu-id="826b2-122">Unsigned Components</span></span>  
 <span data-ttu-id="826b2-123">既定では、フルテキスト インデクサーでは、読み込むフィルターやワード ブレーカーに署名が必要です。</span><span class="sxs-lookup"><span data-stu-id="826b2-123">By default, the full-text indexer requires the filters and word breakers that it loads to be signed.</span></span> <span data-ttu-id="826b2-124">コンポーネントに署名されていない場合、つまり署名されていないカスタム コンポーネントをインストールする可能性がある場合は、署名の検証が無視されるようにフルテキスト インデクサーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="826b2-124">If they are not signed, which is the case sometimes when custom components are installed, you must configure the full-text indexer to ignore signature verification.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="826b2-125">署名の検証を無視すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのセキュリティが低くなります。</span><span class="sxs-lookup"><span data-stu-id="826b2-125">Ignoring signature verification makes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] less secure.</span></span> <span data-ttu-id="826b2-126">実装するすべてのコンポーネントに署名するか、入手するすべてのコンポーネントの署名を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="826b2-126">We recommend that you sign any components that you implement or ensure that any components that you acquire are signed.</span></span> <span data-ttu-id="826b2-127">コンポーネントの署名についての詳細は、「[sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)」を参照して下さい。</span><span class="sxs-lookup"><span data-stu-id="826b2-127">For information about signing components, see [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  

  
##  <a name="full-text-index-in-inconsistent-state-after-transaction-log-restored"></a><a name="state"></a> <span data-ttu-id="826b2-128">トランザクション ログの復元後のフルテキスト インデックスの一貫性の喪失</span><span class="sxs-lookup"><span data-stu-id="826b2-128">Full-Text Index in Inconsistent State after Transaction Log Restored</span></span>  
 <span data-ttu-id="826b2-129">データベースのトランザクション ログを復元する場合、フルテキスト インデックスの状態に一貫性がないという警告が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="826b2-129">When restoring the transaction log of a database, you might see a warning indicating that the full-text index is not in a consistent state.</span></span> <span data-ttu-id="826b2-130">この警告の原因は、データベースのバックアップ後にテーブルのフルテキスト インデックスが変更されたことにあります。</span><span class="sxs-lookup"><span data-stu-id="826b2-130">The reason for this is that the full-text index on a table was modified after the database was backed up.</span></span> <span data-ttu-id="826b2-131">フルテキスト インデックスを一貫性のある状態に戻すには、テーブルに対してすべてのカタログの作成 (クロール) を実行します。</span><span class="sxs-lookup"><span data-stu-id="826b2-131">To bring the full-text index to a consistent state, you must run a full population (crawl) on the table.</span></span> <span data-ttu-id="826b2-132">詳細については、「 [フルテキスト インデックスの作成](../indexes/indexes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="826b2-132">For more information, see [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="826b2-133">参照</span><span class="sxs-lookup"><span data-stu-id="826b2-133">See Also</span></span>  
 <span data-ttu-id="826b2-134">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="826b2-134">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span></span>  
 [<span data-ttu-id="826b2-135">フルテキスト インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="826b2-135">Populate Full-Text Indexes</span></span>](../indexes/indexes.md)  
  
  
