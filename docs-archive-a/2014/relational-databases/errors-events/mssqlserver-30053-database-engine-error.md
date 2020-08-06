---
title: MSSQLSERVER_30053 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 8ad23889-e243-4bd7-bc3e-150403399d89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02d6262f93ef3dbbc9834053f864046b4dca30f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640999"
---
# <a name="mssqlserver_30053"></a><span data-ttu-id="f8884-102">MSSQLSERVER_30053</span><span class="sxs-lookup"><span data-stu-id="f8884-102">MSSQLSERVER_30053</span></span>
    
## <a name="details"></a><span data-ttu-id="f8884-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f8884-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f8884-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f8884-104">Product Name</span></span>|<span data-ttu-id="f8884-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f8884-105">SQL Server</span></span>|  
|<span data-ttu-id="f8884-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f8884-106">Event ID</span></span>|<span data-ttu-id="f8884-107">30053</span><span class="sxs-lookup"><span data-stu-id="f8884-107">30053</span></span>|  
|<span data-ttu-id="f8884-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f8884-108">Event Source</span></span>|<span data-ttu-id="f8884-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f8884-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f8884-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f8884-110">Component</span></span>|<span data-ttu-id="f8884-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f8884-111">SQLEngine</span></span>|  
|<span data-ttu-id="f8884-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f8884-112">Symbolic Name</span></span>|<span data-ttu-id="f8884-113">FTXT_QUERY_E_WORDBREAKINGTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8884-113">FTXT_QUERY_E_WORDBREAKINGTIMEOUT</span></span>|  
|<span data-ttu-id="f8884-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f8884-114">Message Text</span></span>|<span data-ttu-id="f8884-115">フルテキスト クエリ文字列の単語区切り処理がタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f8884-115">Word breaking timed out for the full-text query string.</span></span> <span data-ttu-id="f8884-116">このタイムアウトは、ワード ブレーカーによるフルテキスト クエリ文字列の処理が長時間かかったか、サーバー上で実行されているクエリ数が多い場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f8884-116">This can happen if the wordbreaker took a long time to process the full-text query string, or if a large number of queries are running on the server.</span></span> <span data-ttu-id="f8884-117">負荷を少なくしてクエリの再実行を試みてください。</span><span class="sxs-lookup"><span data-stu-id="f8884-117">Try running the query again under a lighter load.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f8884-118">説明</span><span class="sxs-lookup"><span data-stu-id="f8884-118">Explanation</span></span>  
 <span data-ttu-id="f8884-119">単語区切りのタイムアウト エラーは、次の状況で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f8884-119">A word-breaking timeout error can occur in the following situations:</span></span>  
  
-   <span data-ttu-id="f8884-120">クエリ言語のワード ブレーカーが正しく構成されていない場合。たとえば、レジストリ設定が正しくない場合です。</span><span class="sxs-lookup"><span data-stu-id="f8884-120">The word breaker for the query language is configured incorrectly; for example, its registry settings are incorrect.</span></span>  
  
-   <span data-ttu-id="f8884-121">ワード ブレーカーが特定のクエリ文字列に対して誤動作する。</span><span class="sxs-lookup"><span data-stu-id="f8884-121">The word breaker malfunctions for a specific query string.</span></span>  
  
-   <span data-ttu-id="f8884-122">ワード ブレーカーが特定のクエリ文字列に対して過剰なデータを返す。</span><span class="sxs-lookup"><span data-stu-id="f8884-122">The word breaker returns too much data for a specific query string.</span></span> <span data-ttu-id="f8884-123">過剰なデータは、バッファー オーバーラン攻撃を引き起こす可能性のあるものとして処理されます。これにより、単語区切りサービスをホストする、フィルター デーモン プロセス (fdhost.exe) がシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="f8884-123">Excess data is treated as a potential buffer overrun attack, and shuts down the filter daemon process (fdhost.exe), which hosts the word-breaking services.</span></span>  
  
-   <span data-ttu-id="f8884-124">フィルター デーモン プロセスの構成が正しくない。</span><span class="sxs-lookup"><span data-stu-id="f8884-124">The filter daemon process configuration is incorrect.</span></span>  
  
     <span data-ttu-id="f8884-125">パスワードの期限が切れている場合、またはドメイン ポリシーが原因でフィルター デーモン アカウントがログオンできない場合。この 2 つは、最も一般的な構成上の問題です。</span><span class="sxs-lookup"><span data-stu-id="f8884-125">The most common configuration problems are password expiration or a domain policy that prevents the filter daemon account from logging on.</span></span>  
  
-   <span data-ttu-id="f8884-126">クエリが集中的に行われるワークロードをサーバー インスタンスで実行している場合。たとえば、ワード ブレーカーによるフルテキスト クエリ文字列の処理が長時間かかったり、多数のクエリがサーバー上で実行されている場合です。</span><span class="sxs-lookup"><span data-stu-id="f8884-126">A very heavy query workload is running on the server instance; for example, the word-breaker took a long time to process the full-text query string, or a large number of queries are running on the server.</span></span> <span data-ttu-id="f8884-127">この状況がエラーの原因になることはまれです。</span><span class="sxs-lookup"><span data-stu-id="f8884-127">Note that this is the least likely cause.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f8884-128">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f8884-128">User Action</span></span>  
 <span data-ttu-id="f8884-129">次に示すように、タイムアウトについて考えられる原因に適した、ユーザーのアクションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="f8884-129">Select the user action that is appropriate to the probable cause of the timeout, as follows:</span></span>  
  
|<span data-ttu-id="f8884-130">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="f8884-130">Probable cause</span></span>|<span data-ttu-id="f8884-131">ユーザー アクション</span><span class="sxs-lookup"><span data-stu-id="f8884-131">User action</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f8884-132">クエリ言語のワード ブレーカーが正しく構成されていない。</span><span class="sxs-lookup"><span data-stu-id="f8884-132">The word breaker for the query language is configured incorrectly.</span></span>|<span data-ttu-id="f8884-133">サード パーティ製のワード ブレーカーを使用しているとき、ワード ブレーカーがオペレーティング システムに正しく登録されていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8884-133">If you are using a third-party word breaker it might be incorrectly registered with the operating system.</span></span> <span data-ttu-id="f8884-134">この場合は、ワード ブレーカーを再登録してください。</span><span class="sxs-lookup"><span data-stu-id="f8884-134">In this case, re-register the word breaker.</span></span> <span data-ttu-id="f8884-135">詳細については、「[Revert the Word Breakers Used by Search to the Previous Version](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)」(検索で使用するワード ブレーカーを以前のバージョンに戻す) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8884-135">For more information, see [Revert the Word Breakers Used by Search to the Previous Version](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md).</span></span>|  
|<span data-ttu-id="f8884-136">ワード ブレーカーが特定のクエリ文字列に対して誤動作する。</span><span class="sxs-lookup"><span data-stu-id="f8884-136">The word breaker malfunctions for a specific query string.</span></span>|<span data-ttu-id="f8884-137">ワード ブレーカーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされている場合は、マイクロソフト カスタマー サポート サービスに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="f8884-137">If the word breaker is supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contact Microsoft Customer Service and Support.</span></span>|  
|<span data-ttu-id="f8884-138">ワード ブレーカーが特定のクエリ文字列に対して過剰なデータを返す。</span><span class="sxs-lookup"><span data-stu-id="f8884-138">The word breaker returns too much data for a specific query string.</span></span>|<span data-ttu-id="f8884-139">ワード ブレーカーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされている場合は、マイクロソフト カスタマー サポート サービスに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="f8884-139">If the word breaker is supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contact Microsoft Customer Service and Support.</span></span>|  
|<span data-ttu-id="f8884-140">フィルター デーモン プロセスの構成が正しくない。</span><span class="sxs-lookup"><span data-stu-id="f8884-140">The filter daemon process configuration is incorrect.</span></span>|<span data-ttu-id="f8884-141">正しいパスワードを使用していることと、フィルター デーモン アカウントのログオンがドメイン ポリシーによって拒否されていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f8884-141">Ensure that you are using the current password and that a domain policy is not preventing the filter daemon account from logging on.</span></span>|  
|<span data-ttu-id="f8884-142">クエリが集中的に行われるワークロードをサーバー インスタンスで実行している。</span><span class="sxs-lookup"><span data-stu-id="f8884-142">A very heavy query workload is running on the server instance.</span></span>|<span data-ttu-id="f8884-143">負荷を少なくしてクエリの再実行を試みてください。</span><span class="sxs-lookup"><span data-stu-id="f8884-143">Try running the query again under a lighter load.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8884-144">参照</span><span class="sxs-lookup"><span data-stu-id="f8884-144">See Also</span></span>  
 <span data-ttu-id="f8884-145">[フルテキストフィルターデーモンランチャーのサービスアカウントの設定](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="f8884-145">[Set the Service Account for the Full-text Filter Daemon Launcher](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 <span data-ttu-id="f8884-146">[フルテキスト検索](../search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="f8884-146">[Full-Text Search](../search/full-text-search.md) </span></span>  
 <span data-ttu-id="f8884-147">[sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f8884-147">[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span></span>  
 <span data-ttu-id="f8884-148">[検索用のワードブレーカーとステミング機能の構成と管理](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="f8884-148">[Configure and Manage Word Breakers and Stemmers for Search](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span></span>  
 [<span data-ttu-id="f8884-149">検索用フィルターの構成と管理</span><span class="sxs-lookup"><span data-stu-id="f8884-149">Configure and Manage Filters for Search</span></span>](../search/configure-and-manage-filters-for-search.md)  
  
  
