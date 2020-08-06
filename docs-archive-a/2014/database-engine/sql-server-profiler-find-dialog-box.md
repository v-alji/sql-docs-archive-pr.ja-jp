---
title: SQL Server プロファイラー-[検索] ダイアログボックス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cedf50930c06d211ebcee0c45a249667219f392c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736726"
---
# <a name="sql-server-profiler---find-dialog-box"></a><span data-ttu-id="dc9b6-102">[SQL Server Profiler] - [検索] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="dc9b6-102">SQL Server Profiler - Find Dialog Box</span></span>
  <span data-ttu-id="dc9b6-103">**[検索]** ダイアログ ボックスを使用すると、トレース内で特定の文字や単語を検索できます。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-103">Use the **Find** dialog box to search a trace for specific characters or words.</span></span> <span data-ttu-id="dc9b6-104">検索の実行中に取り消すには、<localizedText>Esc</localizedText> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-104">To cancel a search in progress, press ESC.</span></span>  
  
 <span data-ttu-id="dc9b6-105">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]でこのダイアログ ボックスを開くには、 **[編集]** メニューの **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-105">To open this dialog box in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], on the **Edit** menu, click **Find**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dc9b6-106">Options</span><span class="sxs-lookup"><span data-stu-id="dc9b6-106">Options</span></span>  
 <span data-ttu-id="dc9b6-107">**[検索する文字列]**</span><span class="sxs-lookup"><span data-stu-id="dc9b6-107">**Find what**</span></span>  
 <span data-ttu-id="dc9b6-108">検索するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-108">Enter the text that you want to search for.</span></span> <span data-ttu-id="dc9b6-109">指定した文字列を含むすべての文字列が検索されます。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-109">The search matches any string containing the specified string.</span></span> <span data-ttu-id="dc9b6-110">たとえば、検索文字列として "Completed" を指定すると、一致する文字列として "SQL:BatchCompleted" が検索されます。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-110">For example, searching for "Completed" matches "SQL:BatchCompleted."</span></span> <span data-ttu-id="dc9b6-111">ワイルドカード文字 (\*、? など) はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-111">Wild card characters (\*, ?, etc.) are not supported.</span></span>  
  
 <span data-ttu-id="dc9b6-112">**[検索する列]**</span><span class="sxs-lookup"><span data-stu-id="dc9b6-112">**Search in column**</span></span>  
 <span data-ttu-id="dc9b6-113">検索するデータ列をクリックするか、クリックして **\<All columns>** トレース内のすべてのデータ列を検索します。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-113">Click a data column to search, or click **\<All columns>** to search all the data columns in the trace.</span></span>  
  
 <span data-ttu-id="dc9b6-114">**[大文字と小文字を区別する]**</span><span class="sxs-lookup"><span data-stu-id="dc9b6-114">**Match case**</span></span>  
 <span data-ttu-id="dc9b6-115">**[検索する文字列]** ボックスで指定したテキストと、大文字と小文字の違いまで一致するテキストを検索します。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-115">Finds text that has the same case as the **Find what** box.</span></span> <span data-ttu-id="dc9b6-116">このチェック ボックスをオフにすると、大文字と小文字の違いが一致しないテキストも含めてトレースを検索します。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-116">Clear this check box to find examples in the trace that are in both uppercase and lowercase text characters.</span></span>  
  
 <span data-ttu-id="dc9b6-117">**[単語単位]**</span><span class="sxs-lookup"><span data-stu-id="dc9b6-117">**Match whole word**</span></span>  
 <span data-ttu-id="dc9b6-118">単語全体に一致する対象のみを検索します。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-118">Restricts the search to entire words.</span></span> <span data-ttu-id="dc9b6-119">**[単語単位]** チェック ボックスをオフにすると、単語内の文字列も検索対象になります。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-119">Clear the **Match whole word** check box to search for characters within a word.</span></span>  
  
 <span data-ttu-id="dc9b6-120">**[次を検索]**</span><span class="sxs-lookup"><span data-stu-id="dc9b6-120">**Find Next**</span></span>  
 <span data-ttu-id="dc9b6-121">次に出現する **[検索する文字列]** ボックスの文字列を検索します。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-121">Finds the next example of the characters in the **Find what** box.</span></span>  
  
 <span data-ttu-id="dc9b6-122">**[前を検索]**</span><span class="sxs-lookup"><span data-stu-id="dc9b6-122">**Find Previous**</span></span>  
 <span data-ttu-id="dc9b6-123">トレース内をさかのぼって、前に出現する **[検索する文字列]** ボックスの文字列を検索します。</span><span class="sxs-lookup"><span data-stu-id="dc9b6-123">Searches backwards in the trace, to find the previous example of the characters in the **Find what** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc9b6-124">参照</span><span class="sxs-lookup"><span data-stu-id="dc9b6-124">See Also</span></span>  
 <span data-ttu-id="dc9b6-125">[&#40;SQL Server プロファイラーのトレース中に値列またはデータ列を検索&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="dc9b6-125">[Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="dc9b6-126">[トレース &#40;SQL Server プロファイラーの作成&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="dc9b6-126">[Create a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="dc9b6-127">[トレーステーブル &#40;SQL Server プロファイラーを開き&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="dc9b6-127">[Open a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="dc9b6-128">[トレースファイル &#40;SQL Server プロファイラーを開き&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="dc9b6-128">[Open a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="dc9b6-129">[SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="dc9b6-129">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="dc9b6-130">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="dc9b6-130">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
