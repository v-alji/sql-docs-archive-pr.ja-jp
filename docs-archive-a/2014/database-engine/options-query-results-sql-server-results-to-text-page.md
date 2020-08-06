---
title: '[オプション] ([クエリ結果]-[SQL Server]-[結果をテキストで表示] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToText
ms.assetid: 2ccbdf17-e14f-42f1-a836-ca999a3432c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ece458e4bab9a57cb6692d4ac6dfdf2e8f4bd22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718639"
---
# <a name="options-query-results-sql-server-results-to-text-page"></a><span data-ttu-id="e2349-102">[オプション] ([クエリ結果]-[SQL Server]-[結果をテキストで表示] ページ)</span><span class="sxs-lookup"><span data-stu-id="e2349-102">Options (Query Results-SQL Server-Results to Text Page)</span></span>
  <span data-ttu-id="e2349-103">このページを使用すると、クエリ結果セットをテキスト形式で表示するオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e2349-103">Use this page to specify the options for displaying a query result set in text format.</span></span> <span data-ttu-id="e2349-104">このオプションに加えた変更は、新規の [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e2349-104">Changes to these options are applied only to new [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="e2349-105">現在のクエリのオプションを変更するには、[**クエリ**] メニューの [**クエリオプション**] をクリックするか、クエリウィンドウを右クリックし [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] て [**クエリオプション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2349-105">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window, and select **Query Options**.</span></span> <span data-ttu-id="e2349-106">**[クエリ オプション]** ダイアログ ボックスの **[結果]** で、**[テキスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2349-106">In the **Query Options** dialog box, under **Results**, click **Text**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="e2349-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="e2349-107">UI element list</span></span>  
 <span data-ttu-id="e2349-108">**出力形式**</span><span class="sxs-lookup"><span data-stu-id="e2349-108">**Output format**</span></span>  
 <span data-ttu-id="e2349-109">既定では、スペースを埋め込んで作成された結果が列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2349-109">By default the output is displayed in columns created by padding the results with spaces.</span></span> <span data-ttu-id="e2349-110">他のオプションは、コンマ、タブ、またはスペースを使用して列を区切るオプションです。</span><span class="sxs-lookup"><span data-stu-id="e2349-110">Other options are to use commas, tabs, or spaces to separate columns.</span></span> <span data-ttu-id="e2349-111">このドロップダウン リストから **[独自の区切り記号]** を選択し、**[独自の区切り記号]** テキスト ボックスで別の区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2349-111">Select **Custom delimiter** from this drop-down list to specify a different delimiting character in the **Custom delimiter** text box.</span></span>  
  
 <span data-ttu-id="e2349-112">**[独自の区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="e2349-112">**Custom delimiter**</span></span>  
 <span data-ttu-id="e2349-113">列を区切るために使用する文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2349-113">Specify the character of your choice to separate columns.</span></span> <span data-ttu-id="e2349-114">このテキスト ボックスは、**[出力形式]** ドロップダウン リスト ボックスで [独自の区切り記号] を選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2349-114">This text box is available only if you clicked Custom delimiter in the **Output format** drop-down list box.</span></span>  
  
 <span data-ttu-id="e2349-115">**[列のヘッダーを結果セットに含める]**</span><span class="sxs-lookup"><span data-stu-id="e2349-115">**Include column headers in the result set**</span></span>  
 <span data-ttu-id="e2349-116">各列に列タイトルのラベルを付けない場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="e2349-116">Clear this check box if you do not want each column labeled with a column title.</span></span>  
  
 <span data-ttu-id="e2349-117">**[結果セットにクエリを含める]**</span><span class="sxs-lookup"><span data-stu-id="e2349-117">**Include the query in the result set**</span></span>  
 <span data-ttu-id="e2349-118">結果ペインでクエリの結果の前に実行中のクエリのテキストを含める場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e2349-118">Select this check box to include the text of the query that is running in the results pane before the results of the query.</span></span>  
  
 <span data-ttu-id="e2349-119">**[受け取った順に結果をスクロールする]**</span><span class="sxs-lookup"><span data-stu-id="e2349-119">**Scroll as results are received**</span></span>  
 <span data-ttu-id="e2349-120">常に、結果セットの最後で最新の取得レコードに表示フォーカスを置く場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e2349-120">Select this check box to keep the display focus on the most recently returned records at the end of the results set.</span></span> <span data-ttu-id="e2349-121">常に、取得した最初の行に表示フォーカスを置く場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="e2349-121">Clear this check box to keep the display focus on the first rows received.</span></span>  
  
 <span data-ttu-id="e2349-122">**[数値を右揃えにする]**</span><span class="sxs-lookup"><span data-stu-id="e2349-122">**Right align numeric values**</span></span>  
 <span data-ttu-id="e2349-123">数値を列の右揃えにする場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e2349-123">Select this check box to align numeric values to the right of the column.</span></span> <span data-ttu-id="e2349-124">これにより、固定小数点数の数値を簡単に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="e2349-124">This can make it easier to review numbers with a fixed number of decimal places.</span></span>  
  
 <span data-ttu-id="e2349-125">**[クエリの実行後に結果を破棄する]**</span><span class="sxs-lookup"><span data-stu-id="e2349-125">**Discard result after query executes**</span></span>  
 <span data-ttu-id="e2349-126">クエリ結果がクエリ ウィンドウの結果ペインに表示された後、クエリ結果を破棄する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e2349-126">Select this check box to discard the query results after they are displayed in the results pane of the query window.</span></span>  
  
 <span data-ttu-id="e2349-127">**[結果を別のタブに表示する]**</span><span class="sxs-lookup"><span data-stu-id="e2349-127">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="e2349-128">クエリ ドキュメント ウィンドウの下部ではなく、新しいドキュメント ウィンドウに結果セットを表示する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e2349-128">Select this check box to display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="e2349-129">**[クエリ実行後に [結果] タブに切り替える]**</span><span class="sxs-lookup"><span data-stu-id="e2349-129">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="e2349-130">表示フォーカスを自動的に結果セットに設定する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e2349-130">Select this check box to automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="e2349-131">**[各列に表示される最大文字数]**</span><span class="sxs-lookup"><span data-stu-id="e2349-131">**Maximum number of characters displayed in each column**</span></span>  
 <span data-ttu-id="e2349-132">この値は既定で 256 になっています。</span><span class="sxs-lookup"><span data-stu-id="e2349-132">This value defaults to 256.</span></span> <span data-ttu-id="e2349-133">この値を大きくすると、結果セットが切り詰めなしで大きく表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2349-133">Increase this value to display larger result sets without truncation.</span></span> <span data-ttu-id="e2349-134">最大値は 8,192 です。</span><span class="sxs-lookup"><span data-stu-id="e2349-134">The maximum value is 8,192.</span></span>  
  
 <span data-ttu-id="e2349-135">**既定値にリセット**</span><span class="sxs-lookup"><span data-stu-id="e2349-135">**Reset to Default**</span></span>  
 <span data-ttu-id="e2349-136">このページ上のすべての値を元の既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="e2349-136">Resets all values on this page to the original default values.</span></span>  
  
  
