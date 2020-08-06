---
title: '[クエリオプション] の [結果] ([テキスト] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.text.f1
ms.assetid: fd2fb409-58f9-4ede-8349-ce007126b68d
author: rothja
ms.author: jroth
ms.openlocfilehash: 45019450c8fc959b440aac5bf1e9098e59cecefc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644125"
---
# <a name="query-options-results-text-page"></a><span data-ttu-id="24e69-102">[クエリ オプション] の [結果] ([テキスト] ページ)</span><span class="sxs-lookup"><span data-stu-id="24e69-102">Query Options Results (Text Page)</span></span>
  <span data-ttu-id="24e69-103">このページを使用すると、クエリ結果セットをテキスト形式で表示するオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="24e69-103">Use this page to specify the options for displaying a query result set in text format.</span></span> <span data-ttu-id="24e69-104">このページの設定は、 **[結果をファイルに出力]** が選択されているときにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="24e69-104">The settings on this page also apply when **Results to File** is selected.</span></span>  
  
 <span data-ttu-id="24e69-105">**出力形式**</span><span class="sxs-lookup"><span data-stu-id="24e69-105">**Output format**</span></span>  
 <span data-ttu-id="24e69-106">既定では、スペースを埋め込んで作成された結果が列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="24e69-106">By default the output is displayed in columns created by padding the results with spaces.</span></span> <span data-ttu-id="24e69-107">他のオプションは、コンマ、タブ、またはスペースを使用して列を区切るオプションです。</span><span class="sxs-lookup"><span data-stu-id="24e69-107">Other options are using commas, tabs, or spaces to separate columns.</span></span> <span data-ttu-id="24e69-108">**[独自の区切り記号]** ボックスに他の区切り記号を指定するには、 **[独自の区切り記号]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="24e69-108">Select the **Custom delimiter** check box to specify a different delimiting character in the **Custom delimiter** box.</span></span>  
  
 <span data-ttu-id="24e69-109">**[独自の区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="24e69-109">**Custom delimiter**</span></span>  
 <span data-ttu-id="24e69-110">列を区切るために使用する文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="24e69-110">Specify the character of your choice to separate columns.</span></span> <span data-ttu-id="24e69-111">このオプションは、 **[出力形式]** ボックスの **[独自の区切り記号]** チェック ボックスをオンにした場合にのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="24e69-111">This option is only available if the **Custom delimiter** check box is selected in the **Output format** box.</span></span>  
  
 <span data-ttu-id="24e69-112">**[列のヘッダーを結果セットに含める]**</span><span class="sxs-lookup"><span data-stu-id="24e69-112">**Include column headers in the result set**</span></span>  
 <span data-ttu-id="24e69-113">各列に列タイトルのラベルを付けない場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="24e69-113">Clear this check box if you do not want each column labeled with a column title.</span></span>  
  
 <span data-ttu-id="24e69-114">**[受け取った順に結果をスクロールする]**</span><span class="sxs-lookup"><span data-stu-id="24e69-114">**Scroll as results are received**</span></span>  
 <span data-ttu-id="24e69-115">末尾の最新の取得レコードに常に表示フォーカスを置く場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="24e69-115">Select this check box to keep the display focus on the most recently returned records at the bottom.</span></span> <span data-ttu-id="24e69-116">常に、取得した最初の行に表示フォーカスを置く場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="24e69-116">Clear this check box to keep the display focus on the first rows received.</span></span>  
  
 <span data-ttu-id="24e69-117">**[数値を右揃えにする]**</span><span class="sxs-lookup"><span data-stu-id="24e69-117">**Right align numeric values**</span></span>  
 <span data-ttu-id="24e69-118">数値を列の右揃えにする場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="24e69-118">Select this check box to align numeric values to the right of the column.</span></span> <span data-ttu-id="24e69-119">これにより、固定小数点数の数値を簡単に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="24e69-119">This can make it easier to review numbers with a fixed number of decimal places.</span></span>  
  
 <span data-ttu-id="24e69-120">**[クエリの実行後に結果を破棄する]**</span><span class="sxs-lookup"><span data-stu-id="24e69-120">**Discard result after query executes**</span></span>  
 <span data-ttu-id="24e69-121">画面表示が、クエリ結果を受け取った後にクエリ結果を破棄することによって、メモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="24e69-121">Frees memory by discarding the query results after the screen display has received them.</span></span>  
  
 <span data-ttu-id="24e69-122">**[結果を別のタブに表示する]**</span><span class="sxs-lookup"><span data-stu-id="24e69-122">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="24e69-123">クエリ ドキュメント ウィンドウの下部ではなく、新しいドキュメント ウィンドウに結果セットを表示する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="24e69-123">Select this check box to display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="24e69-124">**[クエリ実行後に [結果] タブに切り替える]**</span><span class="sxs-lookup"><span data-stu-id="24e69-124">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="24e69-125">画面のフォーカスを自動的に結果セットに設定するには、これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="24e69-125">Click to automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="24e69-126">**[各列に表示される最大文字数]**</span><span class="sxs-lookup"><span data-stu-id="24e69-126">**Maximum number of characters displayed in each column**</span></span>  
 <span data-ttu-id="24e69-127">この値は既定で 256 になっています。</span><span class="sxs-lookup"><span data-stu-id="24e69-127">This value defaults to 256.</span></span> <span data-ttu-id="24e69-128">この値を大きくすると、結果セットが切り詰めなしで大きく表示されます。</span><span class="sxs-lookup"><span data-stu-id="24e69-128">Increase this value to display larger result sets without truncation.</span></span>  
  
 <span data-ttu-id="24e69-129">**既定値にリセット**</span><span class="sxs-lookup"><span data-stu-id="24e69-129">**Reset to Default**</span></span>  
 <span data-ttu-id="24e69-130">このページ上のすべての値を元の既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="24e69-130">Resets all values on this page to the original default values.</span></span>  
  
## <a name="saving-a-text-result-set-with-headers"></a><span data-ttu-id="24e69-131">ヘッダーを含めたテキスト結果セットの保存</span><span class="sxs-lookup"><span data-stu-id="24e69-131">Saving a text result set with headers</span></span>  
 <span data-ttu-id="24e69-132">クエリ結果をヘッダーを含めてテキスト ファイルに保存するには、 **[列のヘッダーを結果セットに含める]** チェック ボックスをオンにし、区切り出力形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="24e69-132">To save query results as a text file with headers, select the **Include column headers in the result set** check box and a delimited output format.</span></span> <span data-ttu-id="24e69-133">これにより、ツール バーの **[結果をファイルに出力]** をクリックしたとき、またはクエリ結果を右クリックして **[結果に名前を付けて保存]** をクリックし、ファイル名を入力して **[保存]** をクリックしたときに、レポート ファイルにヘッダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="24e69-133">Now the report file will contain headers when you click **Results to File** on the toolbar, or when you right-click any query results, click **Save Results As**, type a file name, and then click **Save**.</span></span>  
  
  
