---
title: 検索結果ウィンドウ
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.findresults2
helpviewer_keywords:
- Find Results Windows dialog box
ms.assetid: 3b68dbb7-26d6-4bc9-bd2c-c27e5dc385c3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0058588c5fc1367b1070373851d58e58faec6bdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644984"
---
# <a name="find-results-windows"></a><span data-ttu-id="f9059-102">検索結果ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="f9059-102">Find Results Windows</span></span>
  <span data-ttu-id="f9059-103">2 つの検索結果ウィンドウには、 **[検索と置換]** ダイアログの **[フォルダーを指定して検索]** タブまたは **[フォルダーを指定して置換]** タブを使用して検出された項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9059-103">The two Find Results windows display matches found by using the **Find in Files** or **Replace in Files** tabs of the **Find and Replace** dialog.</span></span> <span data-ttu-id="f9059-104">**[フォルダーを指定して検索]** または **[フォルダーを指定して置換]** の **[検索結果]** コマンドを使用すると、検出された項目が表示される検索結果ウィンドウを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f9059-104">The **Result Options** command for **Find in Files** and **Replace in Files** allows you to choose the Find Results window where any matches found will be listed.</span></span>  
  
 <span data-ttu-id="f9059-105">条件に一致する項目が検出されると、選択された検索結果ウィンドウが自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="f9059-105">The selected Find Results window opens automatically whenever matches are found.</span></span> <span data-ttu-id="f9059-106">検索結果ウィンドウを手動で表示するには、 **[表示]** メニューの **[その他のウィンドウ]** をクリックし、 **[検索結果 1]** または **[検索結果 2]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9059-106">To display a Find Results window manually, click **Other Windows** on the **View** menu and then click **Find Results 1** or **Find Results 2**.</span></span>  
  
 <span data-ttu-id="f9059-107">コード ファイルを表示し、一致する項目が検出された行にジャンプするには、結果一覧内の任意の行をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9059-107">To display the code file and jump to the line where a match occurs, double-click any line in the results list.</span></span> <span data-ttu-id="f9059-108">コード エディターにソース ファイルが表示され、条件に一致するテキストの先頭にカーソルが置かれます。</span><span class="sxs-lookup"><span data-stu-id="f9059-108">The source file is displayed in the Code Editor with the insertion point placed where the matched text begins.</span></span> <span data-ttu-id="f9059-109">エディターのインジケーター マージンには、条件に一致する項目がその行に含まれることを示す記号が表示され、ステータス バーにフルテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9059-109">A symbol appears in the indicator margin of the editor to mark the line that includes the match, and the status bar displays its full text.</span></span>  
  
## <a name="toolbar-buttons"></a><span data-ttu-id="f9059-110">ツール バー ボタン</span><span class="sxs-lookup"><span data-stu-id="f9059-110">Toolbar Buttons</span></span>  
 <span data-ttu-id="f9059-111">ツール バーには、結果一覧内を移動したり、一致項目が検出されたコード行にジャンプしたりするために、次のボタンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f9059-111">The following toolbar buttons are available to help you scan through the results list and jump to lines in your code where matches were found.</span></span>  
  
 <span data-ttu-id="f9059-112">**ページ + 上方向キー**</span><span class="sxs-lookup"><span data-stu-id="f9059-112">**page flag + up arrow**</span></span>  
 <span data-ttu-id="f9059-113">選択されている一致項目が検出された行に移動します。</span><span class="sxs-lookup"><span data-stu-id="f9059-113">Go to the line where the selected match was found.</span></span>  
  
 <span data-ttu-id="f9059-114">**ページ + 左方向キー**</span><span class="sxs-lookup"><span data-stu-id="f9059-114">**page + left arrow**</span></span>  
 <span data-ttu-id="f9059-115">前の一致項目が含まれる行に移動します。</span><span class="sxs-lookup"><span data-stu-id="f9059-115">Go to the line of the previous match.</span></span>  
  
 <span data-ttu-id="f9059-116">**ページ + 右方向キー**</span><span class="sxs-lookup"><span data-stu-id="f9059-116">**page + right arrow**</span></span>  
 <span data-ttu-id="f9059-117">次の一致項目が含まれる行に移動します。</span><span class="sxs-lookup"><span data-stu-id="f9059-117">Go to the line of the next match.</span></span>  
  
 <span data-ttu-id="f9059-118">**[すべてクリア]**</span><span class="sxs-lookup"><span data-stu-id="f9059-118">**Clear all**</span></span>  
 <span data-ttu-id="f9059-119">**結果** の一覧からすべての一致項目を削除します。</span><span class="sxs-lookup"><span data-stu-id="f9059-119">Remove all matches from the **Results** list.</span></span>  
  
## <a name="shortcut-keys"></a><span data-ttu-id="f9059-120">ショートカット キー</span><span class="sxs-lookup"><span data-stu-id="f9059-120">Shortcut Keys</span></span>  
 <span data-ttu-id="f9059-121">検出された項目間をすばやく移動するために、次のショートカット キーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f9059-121">The following shortcut keys are available to help you navigate quickly through the matches found.</span></span>  
  
 <span data-ttu-id="f9059-122">Ctrl&lt;/localizedText&gt; + &lt;localizedText&gt;Home</span><span class="sxs-lookup"><span data-stu-id="f9059-122">CTRL+HOME</span></span>  
 <span data-ttu-id="f9059-123">検索結果ウィンドウの最上部までスクロールします。</span><span class="sxs-lookup"><span data-stu-id="f9059-123">Scroll to the top of the Find Results window.</span></span>  
  
 <span data-ttu-id="f9059-124">Ctrl&lt;/localizedText&gt; + &lt;localizedText&gt;End</span><span class="sxs-lookup"><span data-stu-id="f9059-124">CTRL+END</span></span>  
 <span data-ttu-id="f9059-125">検索結果ウィンドウの最下部までスクロールします。</span><span class="sxs-lookup"><span data-stu-id="f9059-125">Scroll to the bottom of the Find Results window.</span></span>  
  
 <span data-ttu-id="f9059-126">PageUp</span><span class="sxs-lookup"><span data-stu-id="f9059-126">PAGE UP</span></span>  
 <span data-ttu-id="f9059-127">次の一致項目のグループまで上にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="f9059-127">Scroll up to the next group of matches.</span></span>  
  
 <span data-ttu-id="f9059-128">PageDown</span><span class="sxs-lookup"><span data-stu-id="f9059-128">PAGE DOWN</span></span>  
 <span data-ttu-id="f9059-129">次の一致項目のグループまで下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="f9059-129">Scroll down to the next group of matches.</span></span>  
  
 <span data-ttu-id="f9059-130">↑</span><span class="sxs-lookup"><span data-stu-id="f9059-130">UP ARROW</span></span>  
 <span data-ttu-id="f9059-131">前の一致項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="f9059-131">Select the previous match.</span></span>  
  
 <span data-ttu-id="f9059-132">下方向キー</span><span class="sxs-lookup"><span data-stu-id="f9059-132">DOWN ARROW</span></span>  
 <span data-ttu-id="f9059-133">次の一致項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="f9059-133">Select the next match.</span></span>  
  
## <a name="search-result-entries"></a><span data-ttu-id="f9059-134">検索結果のエントリ</span><span class="sxs-lookup"><span data-stu-id="f9059-134">Search Result Entries</span></span>  
 <span data-ttu-id="f9059-135">結果一覧の各エントリについて、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9059-135">Each entry in the results list provides the following information:</span></span>  
  
-   <span data-ttu-id="f9059-136">完全なパス</span><span class="sxs-lookup"><span data-stu-id="f9059-136">Full path</span></span>  
  
-   <span data-ttu-id="f9059-137">ファイル名</span><span class="sxs-lookup"><span data-stu-id="f9059-137">File name</span></span>  
  
-   <span data-ttu-id="f9059-138">行番号</span><span class="sxs-lookup"><span data-stu-id="f9059-138">Line number</span></span>  
  
-   <span data-ttu-id="f9059-139">一致項目が含まれている行のフルテキスト</span><span class="sxs-lookup"><span data-stu-id="f9059-139">The full text of the line containing the match</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="f9059-140">**[クイック検索]** を使用すると、長い結果一覧内をすばやくスキャンできます。</span><span class="sxs-lookup"><span data-stu-id="f9059-140">You can use **Quick Find** to scan through a lengthy results list.</span></span> <span data-ttu-id="f9059-141">検索結果ウィンドウを開いてドッキングします。次に、 **検索** タブにある三角形の **表示** ボタンをクリックして **[クイック検索]** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="f9059-141">Open and dock the Find Results window, and then click the triangular **View** button on the **Find** tab and switch to **Quick Find**.</span></span> <span data-ttu-id="f9059-142">**[検索対象]** フィールドを **[現在のウィンドウ]** に設定します。 **[検索する文字列]** に文字列を入力し、 **[次を検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9059-142">Set the **Look in** field of the search to **Active Window**, enter a **Find what** string, and then click **Find Next**.</span></span> <span data-ttu-id="f9059-143">これにより、結果一覧をスキャンして、特定のフォルダーまたはファイル内で検出された一致項目や、他の重要な用語も一緒に現れるコード行で検出された一致項目を表示できます。</span><span class="sxs-lookup"><span data-stu-id="f9059-143">This lets you scan the results list for matches found in particular folders or files, or matches on lines of code where some other key term also occurs.</span></span>  
  
## <a name="summary-lines"></a><span data-ttu-id="f9059-144">概要行</span><span class="sxs-lookup"><span data-stu-id="f9059-144">Summary Lines</span></span>  
 <span data-ttu-id="f9059-145">検索結果の各セットは、検索パラメーターが示された行で開始され、統計情報が示された行で終了します。</span><span class="sxs-lookup"><span data-stu-id="f9059-145">Each set of search results begins with a line that states the search parameters, and ends with a line of statistics.</span></span> <span data-ttu-id="f9059-146">たとえば、すべての開いているドキュメントを対象に、正規表現 " **" を検索文字列として指定した** [フォルダーを指定して検索]`var[1-3]&par`検索の結果一覧は、次の検索パラメーターが示される行で始まります。</span><span class="sxs-lookup"><span data-stu-id="f9059-146">For example, the results list from a **Find in Files** search in all open documents for any strings matched by the regular expression "`var[1-3]&par`" might begin with this line of search parameters:</span></span>  
  
 `Find all "var[1-3]&par" Regular Expression, All Open Documents`  
  
 <span data-ttu-id="f9059-147">最後の行には、次のような統計情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f9059-147">and might conclude with this line of statistics:</span></span>  
  
 `Total found: 57  Matching files: 23  Total files searched: 59`  
  
 <span data-ttu-id="f9059-148">すべての開いているドキュメントを対象に、正規表現 " **" に一致するすべての文字列を、文字列 "** " で置換する`var[1-3]&par`[フォルダーを指定して置換]`sample`検索の結果一覧は、次の検索パラメーターが示される行で始まります。</span><span class="sxs-lookup"><span data-stu-id="f9059-148">The results list from a **Replace in Files** search in all open documents that replaced any strings matched by the regular expression "`var[1-3]&par`" with the string "`sample`" might begin with this line of search parameters:</span></span>  
  
 `Replace "var[1-3]&par", "sample", Regular Expression, All Open Documents`  
  
 <span data-ttu-id="f9059-149">最後の行には、次のような統計情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f9059-149">and might conclude with this line of statistics:</span></span>  
  
 `Total replaced: 57  Matching files: 23  Total files searched: 59`  
