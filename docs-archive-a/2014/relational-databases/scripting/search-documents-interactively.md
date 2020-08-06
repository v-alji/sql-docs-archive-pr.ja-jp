---
title: ドキュメントの対話形式の検索
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- interactive searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], interactive
- Query Editor [SQL Server Management Studio], interactive search
ms.assetid: dae65ac5-67af-45c6-a6e0-952fea26d680
author: rothja
ms.author: jroth
ms.openlocfilehash: 5603db77ea4f58d4bb036635a23ec3cfa400a818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644972"
---
# <a name="search-documents-interactively"></a><span data-ttu-id="59885-102">ドキュメントの対話形式の検索</span><span class="sxs-lookup"><span data-stu-id="59885-102">Search Documents Interactively</span></span>
  <span data-ttu-id="59885-103">**[検索と置換]** ダイアログ ボックスを使用して、1 つ以上の開いているファイルやウィンドウで検索し、検索結果の文字列に 1 つずつ移動して確認することができます。</span><span class="sxs-lookup"><span data-stu-id="59885-103">Using the **Find and Replace** dialog box, you can search one or more open files or windows and move through the search matches one by one.</span></span> <span data-ttu-id="59885-104">この方法では、検索結果の各文字列をその前後のテキストのコンテキストで個別に確認できます。</span><span class="sxs-lookup"><span data-stu-id="59885-104">This technique allows you to review each individual search match in the context of the text around the match.</span></span> <span data-ttu-id="59885-105">さらに、 **[検索と置換]** ダイアログ ボックスには、一括検索操作を実行し、結果をレポート形式で確認するオプションも用意されています。</span><span class="sxs-lookup"><span data-stu-id="59885-105">You also have the option of performing bulk find operations and reviewing search matches in report format using the **Find and Replace** dialog box.</span></span>  
  
### <a name="to-search-all-open-documents"></a><span data-ttu-id="59885-106">開いているドキュメントをすべて検索するには</span><span class="sxs-lookup"><span data-stu-id="59885-106">To search all open documents</span></span>  
  
1.  <span data-ttu-id="59885-107">検索する項目を開きます。</span><span class="sxs-lookup"><span data-stu-id="59885-107">Open the items you wish to search.</span></span>  
  
2.  <span data-ttu-id="59885-108">**[編集]** メニューの **[検索と置換]** をポイントし、 **[クイック検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59885-108">On the **Edit** menu, point to **Find and Replace,** and then click **QuickFind**.</span></span>  
  
3.  <span data-ttu-id="59885-109">**[検索と置換]** ボックスに、検索するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="59885-109">In the **Find and Replace** text box, enter the text to search for.</span></span>  
  
4.  <span data-ttu-id="59885-110">**[検索対象]** ボックスの一覧の **[すべての開かれているドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59885-110">In the **Look in** list, select **All Open Documents**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="59885-111">**[すべての開かれているドキュメント]** を選択しても、開いている特定のファイルは検索されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="59885-111">Certain open files might not be searched when **All Open Documents** is selected.</span></span> <span data-ttu-id="59885-112">検索の対象になるのは、コード ビューなどのテキスト ビューで現在開いているファイルだけです。</span><span class="sxs-lookup"><span data-stu-id="59885-112">Only files currently open in a textual view, such as Code view, are included in searches.</span></span> <span data-ttu-id="59885-113">デザイナー ビューのファイルは、検索対象に含まれません。</span><span class="sxs-lookup"><span data-stu-id="59885-113">Files in Designer view are not included in searches.</span></span>  
  
5.  <span data-ttu-id="59885-114">さらに検索精度を高めるには、検索オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="59885-114">Select additional search options to increase the accuracy of the search.</span></span>  
  
6.  <span data-ttu-id="59885-115">**[次を検索]** をクリックして検索を開始します。最後のファイルの検索が完了するまで **[次を検索]** のクリックを続けます。</span><span class="sxs-lookup"><span data-stu-id="59885-115">Click **Find Next** to start the search, and continue clicking **Find Next** until the last file has been searched.</span></span>  
  
 <span data-ttu-id="59885-116">検索がドキュメントの先頭または末尾に達すると、ステータス バーにメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="59885-116">When the search passes the beginning or end of the document, a message is displayed in the status bar.</span></span> <span data-ttu-id="59885-117">検索の開始位置に達すると、メッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="59885-117">A message box appears when the search reaches the starting point of the search.</span></span>  
  
#### <a name="to-replace-in-all-active-files-interactively"></a><span data-ttu-id="59885-118">すべてのアクティブ ファイル内で対話的に置換を行うには</span><span class="sxs-lookup"><span data-stu-id="59885-118">To replace in all active files interactively</span></span>  
  
1.  <span data-ttu-id="59885-119">**[編集]** メニューの **[検索と置換]** をポイントし、 **[クイック置換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59885-119">On the **Edit** menu, point to **Find and Replace**, and then click **QuickReplace**.</span></span>  
  
2.  <span data-ttu-id="59885-120">**[検索する文字列]** ボックスに、検索するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="59885-120">In the **Find what** box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="59885-121">**[置換後の文字列]** ボックスに置換後のテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="59885-121">In the **Replace with** box, enter the text to replace the search text.</span></span>  
  
4.  <span data-ttu-id="59885-122">**[検索対象]** ボックスの一覧の **[すべての開かれているドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59885-122">In the **Look in** list, select **All Open Documents**.</span></span>  
  
5.  <span data-ttu-id="59885-123">**[置換]** をクリックし、最後のファイル内で最後に見つかった検索結果の置換が完了するまで **[置換]** のクリックを続けます。</span><span class="sxs-lookup"><span data-stu-id="59885-123">Click **Replace**, and continue clicking **Replace** until the last match in the last file has been replaced.</span></span> <span data-ttu-id="59885-124">検索結果を置換しないでスキップする場合は、 **[次を検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59885-124">Click **Find Next** to skip a match you do not want to replace.</span></span>  
  
     <span data-ttu-id="59885-125">または</span><span class="sxs-lookup"><span data-stu-id="59885-125">-or-</span></span>  
  
     <span data-ttu-id="59885-126">**[すべて置換]** をクリックしてすべての検索結果を置換します。</span><span class="sxs-lookup"><span data-stu-id="59885-126">Choose **Replace All** to replace all matches.</span></span> <span data-ttu-id="59885-127">置換の総数を示すメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="59885-127">A message box appears, listing the total number of replacements.</span></span>  
  
 <span data-ttu-id="59885-128">**[すべて置換]** をクリックすると、 **[次を検索]** によってスキップした検索結果も含め、すべての検索結果が置換されます。</span><span class="sxs-lookup"><span data-stu-id="59885-128">The **Replace All** command replaces all search matches, including those you have skipped with the **Find Next** button.</span></span> <span data-ttu-id="59885-129">**[すべて置換]** を取り消すには、ファイルを閉じる前に **[編集]** メニューの **[元に戻す]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59885-129">To cancel **Replace All**, click **Undo** from the **Edit** menu before closing any of the files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59885-130">参照</span><span class="sxs-lookup"><span data-stu-id="59885-130">See Also</span></span>  
 <span data-ttu-id="59885-131">[アクティブ ドキュメントのインクリメンタル検索](search-an-active-document-incrementally.md) </span><span class="sxs-lookup"><span data-stu-id="59885-131">[Search an Active Document Incrementally](search-an-active-document-incrementally.md) </span></span>  
 <span data-ttu-id="59885-132">[検索と置換](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="59885-132">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="59885-133">[結果一覧を使用してドキュメントを検索する方法](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="59885-133">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="59885-134">[ワイルドカードを使用したテキスト検索](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="59885-134">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="59885-135">正規表現によるテキストの検索</span><span class="sxs-lookup"><span data-stu-id="59885-135">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
