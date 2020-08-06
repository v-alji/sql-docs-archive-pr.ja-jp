---
title: transform noise words サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- full-text queries [SQL Server], performance
- transform noise words option
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 49de4a381de3e998073a73c284e3e3e5960f4921
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738694"
---
# <a name="transform-noise-words-server-configuration-option"></a><span data-ttu-id="aa70d-102">transform noise words サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="aa70d-102">transform noise words Server Configuration Option</span></span>
  <span data-ttu-id="aa70d-103">`transform noise words`ノイズワード ([ストップワード](../../relational-databases/search/full-text-search.md)) が原因でフルテキストクエリのブール演算がゼロ行を返す場合は、サーバー構成オプションを使用してエラーメッセージを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="aa70d-103">Use the `transform noise words` server configuration option to suppress an error message if noise words, that is [stopwords](../../relational-databases/search/full-text-search.md), cause a Boolean operation on a full-text query to return zero rows.</span></span> <span data-ttu-id="aa70d-104">フルテキスト クエリに使用されている CONTAINS 述語に、ノイズ ワードを含んだブール演算または NEAR 演算が存在する場合、このオプションを使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="aa70d-104">This option is useful for full-text queries that use the CONTAINS predicate in which Boolean operations or NEAR operations include noise words.</span></span> <span data-ttu-id="aa70d-105">次の表に、このオプションで使用可能な値を示します。</span><span class="sxs-lookup"><span data-stu-id="aa70d-105">The possible values are described in the following table.</span></span>  
  
|<span data-ttu-id="aa70d-106">値</span><span class="sxs-lookup"><span data-stu-id="aa70d-106">Value</span></span>|<span data-ttu-id="aa70d-107">説明</span><span class="sxs-lookup"><span data-stu-id="aa70d-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa70d-108">0</span><span class="sxs-lookup"><span data-stu-id="aa70d-108">0</span></span>|<span data-ttu-id="aa70d-109">ノイズ ワード (ストップワード) は変換されません。</span><span class="sxs-lookup"><span data-stu-id="aa70d-109">Noise words (or stopwords) are not transformed.</span></span> <span data-ttu-id="aa70d-110">フルテキスト クエリにノイズ ワードが含まれている場合、クエリから返される行数は 0 件となり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="aa70d-110">When a full-text query contains noise words, the query returns zero rows, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] raises a warning.</span></span> <span data-ttu-id="aa70d-111">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="aa70d-111">This is the default behavior.</span></span><br /><br /> <span data-ttu-id="aa70d-112">警告は実行時の警告です。</span><span class="sxs-lookup"><span data-stu-id="aa70d-112">Note that the warning is a run-time warning.</span></span> <span data-ttu-id="aa70d-113">そのため、クエリ内のフルテキスト句が実行されていない場合、警告は発生しません。</span><span class="sxs-lookup"><span data-stu-id="aa70d-113">Therefore, if the full-text clause in the query is not executed, the warning is not raised.</span></span> <span data-ttu-id="aa70d-114">ローカル クエリの場合、複数のフルテキスト クエリ句がある場合でも、発生する警告は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="aa70d-114">For a local query, only one warning is raised, even when there are multiple full-text query clauses.</span></span> <span data-ttu-id="aa70d-115">リモート クエリの場合、リンク サーバーがエラーを中継しない場合があるので、警告が発生しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="aa70d-115">For a remote query, the linked server might not relay the error; therefore, the warning might not be raised.</span></span>|  
|<span data-ttu-id="aa70d-116">1</span><span class="sxs-lookup"><span data-stu-id="aa70d-116">1</span></span>|<span data-ttu-id="aa70d-117">ノイズ ワード (ストップワード) の変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="aa70d-117">Noise words (or stopwords) are transformed.</span></span> <span data-ttu-id="aa70d-118">これらは無視されて、残りのクエリが評価されます。</span><span class="sxs-lookup"><span data-stu-id="aa70d-118">They are ignored, and the rest of the query is evaluated.</span></span><br /><br /> <span data-ttu-id="aa70d-119">近接語句内にノイズ ワードが指定された場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって削除されます。</span><span class="sxs-lookup"><span data-stu-id="aa70d-119">If noise words are specified in a proximity term, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] removes them.</span></span> <span data-ttu-id="aa70d-120">たとえば、ノイズ ワードである " `is` " は、 `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`から削除され、検索クエリは `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`に変換されます。</span><span class="sxs-lookup"><span data-stu-id="aa70d-120">For example, the noise word `is` is removed from `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`, transforming the search query into `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`.</span></span> <span data-ttu-id="aa70d-121">`CONTAINS(<column_name>, 'NEAR(hello,is)')` は、有効な検索用語が 1 つしか存在しないため、単純に `CONTAINS(<column_name>, hello)` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="aa70d-121">Notice that `CONTAINS(<column_name>, 'NEAR(hello,is)')` would be transformed into simply `CONTAINS(<column_name>, hello)` because there is only one valid search term.</span></span>|  
  
## <a name="effects-of-the-transform-noise-words-setting"></a><span data-ttu-id="aa70d-122">transform noise words 設定の影響</span><span class="sxs-lookup"><span data-stu-id="aa70d-122">Effects of the transform noise words Setting</span></span>  
 <span data-ttu-id="aa70d-123">このセクションでは、ノイズ ワードである "`the`" を例に、`transform noise words` の設定によるクエリ動作の違いを見ていきます。</span><span class="sxs-lookup"><span data-stu-id="aa70d-123">This section illustrates the behavior of queries containing a noise word, "`the`", under the alternate settings of `transform noise words`.</span></span>  <span data-ttu-id="aa70d-124">サンプルのフルテキスト クエリ文字列は、 `[1, "The black cat"]`というデータを含んだテーブル行に対して実行するものとします。</span><span class="sxs-lookup"><span data-stu-id="aa70d-124">The sample full-text query strings are assumed to be run against a table row containing the following data: `[1, "The black cat"]`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa70d-125">このようなシナリオでは必ず、ノイズ ワードの警告が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa70d-125">All such scenarios can generate a noise word warning.</span></span>  
  
-   <span data-ttu-id="aa70d-126">transform noise words を 0 に設定した場合:</span><span class="sxs-lookup"><span data-stu-id="aa70d-126">With transform noise words set to 0:</span></span>  
  
    |<span data-ttu-id="aa70d-127">クエリ文字列</span><span class="sxs-lookup"><span data-stu-id="aa70d-127">Query string</span></span>|<span data-ttu-id="aa70d-128">結果</span><span class="sxs-lookup"><span data-stu-id="aa70d-128">Result</span></span>|  
    |------------------|------------|  
    |<span data-ttu-id="aa70d-129">"`cat`" AND "`the`"</span><span class="sxs-lookup"><span data-stu-id="aa70d-129">"`cat`" AND "`the`"</span></span>|<span data-ttu-id="aa70d-130">結果は返されません ("`the`" AND "`cat`" の場合も動作は同じ)。</span><span class="sxs-lookup"><span data-stu-id="aa70d-130">No results (The behavior is the same for "`the`" AND "`cat`".)</span></span>|  
    |<span data-ttu-id="aa70d-131">"`cat`" NEAR "`the`"</span><span class="sxs-lookup"><span data-stu-id="aa70d-131">"`cat`" NEAR "`the`"</span></span>|<span data-ttu-id="aa70d-132">結果は返されません ("`the`" NEAR "`cat`" の場合も動作は同じ)。</span><span class="sxs-lookup"><span data-stu-id="aa70d-132">No results (The behavior is the same for "`the`" NEAR "`cat`".)</span></span>|  
    |<span data-ttu-id="aa70d-133">"`the`" AND NOT "`black`"</span><span class="sxs-lookup"><span data-stu-id="aa70d-133">"`the`" AND NOT "`black`"</span></span>|<span data-ttu-id="aa70d-134">検索結果がありません</span><span class="sxs-lookup"><span data-stu-id="aa70d-134">No results</span></span>|  
    |<span data-ttu-id="aa70d-135">"`black`" AND NOT "`the`"</span><span class="sxs-lookup"><span data-stu-id="aa70d-135">"`black`" AND NOT "`the`"</span></span>|<span data-ttu-id="aa70d-136">検索結果がありません</span><span class="sxs-lookup"><span data-stu-id="aa70d-136">No results</span></span>|  
  
-   <span data-ttu-id="aa70d-137">transform noise words を 1 に設定した場合:</span><span class="sxs-lookup"><span data-stu-id="aa70d-137">With transform noise words set to 1:</span></span>  
  
    |<span data-ttu-id="aa70d-138">クエリ文字列</span><span class="sxs-lookup"><span data-stu-id="aa70d-138">Query string</span></span>|<span data-ttu-id="aa70d-139">結果</span><span class="sxs-lookup"><span data-stu-id="aa70d-139">Result</span></span>|  
    |------------------|------------|  
    |<span data-ttu-id="aa70d-140">"`cat`" AND "`the`"</span><span class="sxs-lookup"><span data-stu-id="aa70d-140">"`cat`" AND "`the`"</span></span>|<span data-ttu-id="aa70d-141">ID 1 の行がヒットします。</span><span class="sxs-lookup"><span data-stu-id="aa70d-141">Hit for row with ID 1</span></span>|  
    |<span data-ttu-id="aa70d-142">"`cat`" NEAR "`the`"</span><span class="sxs-lookup"><span data-stu-id="aa70d-142">"`cat`" NEAR "`the`"</span></span>|<span data-ttu-id="aa70d-143">ID 1 の行がヒットします。</span><span class="sxs-lookup"><span data-stu-id="aa70d-143">Hit for row with ID 1</span></span>|  
    |<span data-ttu-id="aa70d-144">"`the`" AND NOT "`black`"</span><span class="sxs-lookup"><span data-stu-id="aa70d-144">"`the`" AND NOT "`black`"</span></span>|<span data-ttu-id="aa70d-145">検索結果がありません</span><span class="sxs-lookup"><span data-stu-id="aa70d-145">No results</span></span>|  
    |<span data-ttu-id="aa70d-146">"`black`" AND NOT "`the`"</span><span class="sxs-lookup"><span data-stu-id="aa70d-146">"`black`" AND NOT "`the`"</span></span>|<span data-ttu-id="aa70d-147">ID 1 の行がヒットします。</span><span class="sxs-lookup"><span data-stu-id="aa70d-147">Hit for row with ID 1</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aa70d-148">例</span><span class="sxs-lookup"><span data-stu-id="aa70d-148">Example</span></span>  
 <span data-ttu-id="aa70d-149">次の例では、`transform noise words` を `1` に設定します。</span><span class="sxs-lookup"><span data-stu-id="aa70d-149">The following example sets `transform noise words` to `1`.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa70d-150">参照</span><span class="sxs-lookup"><span data-stu-id="aa70d-150">See Also</span></span>  
 <span data-ttu-id="aa70d-151">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aa70d-151">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="aa70d-152">CONTAINS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aa70d-152">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
  
