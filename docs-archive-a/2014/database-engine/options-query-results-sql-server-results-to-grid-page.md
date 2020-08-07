---
title: '[オプション] ([クエリ結果]-[SQL Server]-[結果をグリッドに表示] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f9cec7e544c295420a9ae2a25e96ea9aa82030b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718645"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a><span data-ttu-id="7e17c-102">[オプション] ([クエリ結果]-[SQL Server-グリッドへの結果] ページ)</span><span class="sxs-lookup"><span data-stu-id="7e17c-102">Options (Query Results-SQL Server-Results to Grid Page)</span></span>
  <span data-ttu-id="7e17c-103">このページを使用すると、クエリ結果セットをグリッド形式で表示するためのオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e17c-103">Use this page to specify the options for displaying a query result set in grid format.</span></span> <span data-ttu-id="7e17c-104">このオプションに加えた変更は、新規の [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="7e17c-104">Changes to these options are applied only to new [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="7e17c-105">現在のクエリのオプションを変更するには、[**クエリ**] メニューの [**クエリオプション**] をクリックするか、クエリウィンドウを右クリック [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] して [**クエリオプション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7e17c-105">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window and select **Query Options**.</span></span> <span data-ttu-id="7e17c-106">**[クエリ オプション]** ダイアログ ボックスの左ペインで、**[結果]** の **[グリッド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e17c-106">In the left pane of the **Query Options** dialog box, under **Results**, click **Grid**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="7e17c-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="7e17c-107">UI element list</span></span>  
 <span data-ttu-id="7e17c-108">**[結果セットにクエリを含める]**</span><span class="sxs-lookup"><span data-stu-id="7e17c-108">**Include the query in the result set**</span></span>  
 <span data-ttu-id="7e17c-109">クエリのテキストをクエリ出力の一部として返します。</span><span class="sxs-lookup"><span data-stu-id="7e17c-109">Returns the text of the query as part of the query output.</span></span>  
  
 <span data-ttu-id="7e17c-110">**[結果のコピーまたは保存時に列のヘッダーを含める]**</span><span class="sxs-lookup"><span data-stu-id="7e17c-110">**Include column headers when copying or saving the results**</span></span>  
 <span data-ttu-id="7e17c-111">結果をクリップボードにコピーしたりファイルに保存したりするときに列のヘッダーを含めるには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7e17c-111">Select this check box to include column headers when results are copied to the clipboard, or saved in a file.</span></span> <span data-ttu-id="7e17c-112">保存またはコピーする結果データに列のヘッダーを含めずにデータだけを含めるには、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="7e17c-112">Clear this check box if you want saved or copied result data to have only the data and not the column headings.</span></span>  
  
 <span data-ttu-id="7e17c-113">**[実行後に結果を破棄する]**</span><span class="sxs-lookup"><span data-stu-id="7e17c-113">**Discard results after execution**</span></span>  
 <span data-ttu-id="7e17c-114">クエリの結果が変更履歴ウィンドウに表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="7e17c-114">Prevents query results from being displayed in the reviewing pane.</span></span> <span data-ttu-id="7e17c-115">結果は実行後すぐに破棄されます。</span><span class="sxs-lookup"><span data-stu-id="7e17c-115">The results are discarded immediately after execution.</span></span> <span data-ttu-id="7e17c-116">このオプションを指定すると、メモリを節約できます。</span><span class="sxs-lookup"><span data-stu-id="7e17c-116">Specifying this option helps save memory.</span></span>  
  
 <span data-ttu-id="7e17c-117">**[結果を別のタブに表示する]**</span><span class="sxs-lookup"><span data-stu-id="7e17c-117">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="7e17c-118">クエリ ドキュメント ウィンドウの下部ではなく、新しいタブに結果セットを表示するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7e17c-118">Select this check box to display the result set in a new tab, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="7e17c-119">**[クエリ実行後に [結果] タブに切り替える]**</span><span class="sxs-lookup"><span data-stu-id="7e17c-119">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="7e17c-120">クエリの実行時に画面フォーカスを結果ペインに自動的に設定するには、これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e17c-120">Click to automatically set the screen focus to the results pane upon execution of a query.</span></span>  
  
 <span data-ttu-id="7e17c-121">**[取得される最大文字数]**</span><span class="sxs-lookup"><span data-stu-id="7e17c-121">**Maximum Characters Retrieved**</span></span>  
 <span data-ttu-id="7e17c-122">**XML 以外のデータ**:</span><span class="sxs-lookup"><span data-stu-id="7e17c-122">**Non XML data**:</span></span>  
  
 <span data-ttu-id="7e17c-123">1 ～ 65,535 の値を入力して、各セルに表示される最大文字数を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e17c-123">Enter a number from 1 through 65535 to specify the maximum number of characters that will be displayed in each cell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e17c-124">大きな文字数を指定すると、結果セット内のデータが切り捨てられたように見える場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e17c-124">Specifying a large number of characters may cause data in the result set to appear truncated.</span></span> <span data-ttu-id="7e17c-125">各セルに表示される最大文字数は、フォントのサイズに依存します。</span><span class="sxs-lookup"><span data-stu-id="7e17c-125">The maximum number of characters displayed in each cell is dependent on the font size.</span></span> <span data-ttu-id="7e17c-126">大きな結果セットが返された場合、このボックスに大きな値を指定していると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のメモリ上での実行速度が低下したり、システムのパフォーマンスに悪影響が及んだりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="7e17c-126">When large result sets are returned, a high value in this box can cause [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to run low on memory and hinder system performance.</span></span>  
  
 <span data-ttu-id="7e17c-127">**XML データ**:</span><span class="sxs-lookup"><span data-stu-id="7e17c-127">**XML data**:</span></span>  
  
 <span data-ttu-id="7e17c-128">**[1 MB]**、 **[2 MB]**、または **[5 MB]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7e17c-128">Select **1 MB**, **2 MB**, or **5 MB**.</span></span> <span data-ttu-id="7e17c-129">すべての文字を取得する場合は、 **[無制限]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7e17c-129">Select **Unlimited** to retrieve all characters.</span></span>  
  
 <span data-ttu-id="7e17c-130">**既定値にリセット**</span><span class="sxs-lookup"><span data-stu-id="7e17c-130">**Reset to Default**</span></span>  
 <span data-ttu-id="7e17c-131">このページ上のすべての値を元の既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="7e17c-131">Resets all values on this page to the original default values.</span></span>  
  
  
