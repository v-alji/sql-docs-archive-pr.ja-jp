---
title: 結果一覧を使用してドキュメントを検索する方法
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], result lists
- result list searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], multiple files
- Query Editor [SQL Server Management Studio], search multiple files
ms.assetid: 275e1b6c-fbd0-4408-af77-35903f90657c
author: rothja
ms.author: jroth
ms.openlocfilehash: 58ff3754bc1667de75426e52b3ddd855e7d1a348
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644967"
---
# <a name="search-documents-using-results-lists"></a><span data-ttu-id="47507-102">結果一覧を使用してドキュメントを検索する方法</span><span class="sxs-lookup"><span data-stu-id="47507-102">Search Documents Using Results Lists</span></span>
  <span data-ttu-id="47507-103">**[検索と置換]** ダイアログ ボックスでは、プロジェクト内、ソリューション内、ファイル システム フォルダー内のすべてのファイルを対象にしてテキストの検索と置換を実行できます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で開いていないファイルも対象になります。</span><span class="sxs-lookup"><span data-stu-id="47507-103">Using the **Find and Replace** dialog box, you can search and replace text in all files in a project or solution or in a file system folder, even when they are not open in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="47507-104">**[検索と置換]** ダイアログ ボックスで実行した検索の一致項目は、[検索結果 1] ウィンドウと [検索結果 2] ウィンドウに表示されるので、一致項目を含んだ行のテキストを実際に確認できます。</span><span class="sxs-lookup"><span data-stu-id="47507-104">Matches from searches that were performed with the **Find and Replace** dialog box appear in the Find Results 1 and Find Results 2 windows, which allows you to view the exact text from the line containing the match.</span></span>  
  
### <a name="to-search-in-multiple-files"></a><span data-ttu-id="47507-105">複数のファイルで検索を実行するには</span><span class="sxs-lookup"><span data-stu-id="47507-105">To search in multiple files</span></span>  
  
1.  <span data-ttu-id="47507-106">**[編集]** メニューの **[検索と置換]** をポイントし、 **[フォルダーを指定して検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47507-106">On the **Edit** menu, point to **Find and Replace,** and then click **Find in Files**.</span></span>  
  
2.  <span data-ttu-id="47507-107">**[検索する文字列]** テキスト ボックスに検索テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="47507-107">In the **Find what** text box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="47507-108">**[検索対象]** 一覧で、 **[すべての開かれているドキュメント]** 、 **[現在のプロジェクト]** 、 **[ソリューション全体]** のいずれかをクリックするか、ディレクトリ パスを入力します。</span><span class="sxs-lookup"><span data-stu-id="47507-108">In the **Look in** list, click **All Open Documents**, **Current Project**, **Entire Solution**, or type a directory path.</span></span>  
  
4.  <span data-ttu-id="47507-109">**[次のファイルの種類を参照]** 一覧で、表示されているファイル拡張子のセットのいずれかを選択するか、検索対象のファイルの種類を示す拡張子をセミコロンで区切って入力します。</span><span class="sxs-lookup"><span data-stu-id="47507-109">In the **File types** list, select one of the listed sets of file extensions or enter the extensions for the types of files to be searched, separated by semicolons.</span></span> <span data-ttu-id="47507-110">**[検索対象]** ドロップダウン リストに表示されているディレクトリ内のすべてのファイルを検索する場合は、\*.\* を使います。</span><span class="sxs-lookup"><span data-stu-id="47507-110">Use \*.\* to search all files in the directory listed in the **Look in** drop-down list.</span></span>  
  
5.  <span data-ttu-id="47507-111">検索の精度を上げるために、他の検索オプションの中から適切な項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="47507-111">Select from the remaining search options to improve the accuracy of the search.</span></span>  
  
6.  <span data-ttu-id="47507-112">**[検索]** をクリックして検索を開始します。</span><span class="sxs-lookup"><span data-stu-id="47507-112">Click **Find** to begin the search.</span></span>  
  
 <span data-ttu-id="47507-113">既定では、[検索結果 1] ウィンドウに検索の一致項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="47507-113">The matches for the search appear in the Find Results 1 window by default.</span></span> <span data-ttu-id="47507-114">検索の一致項目を確認するには、[検索結果 1] ウィンドウ内の各項目をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="47507-114">You can browse the search matches by double-clicking each entry in the Find Results 1 window.</span></span> <span data-ttu-id="47507-115">検索結果を新しいウィンドウに表示するには、 **[検索結果 2 ウィンドウ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="47507-115">To view the search results in a new window, select **Display in Find 2**.</span></span>  
  
#### <a name="to-replace-across-multiple-files-or-folders"></a><span data-ttu-id="47507-116">複数のファイルまたはフォルダーで置換を実行するには</span><span class="sxs-lookup"><span data-stu-id="47507-116">To replace across multiple files or folders</span></span>  
  
1.  <span data-ttu-id="47507-117">**[編集]** メニューの **[検索と置換]** をポイントし、 **[フォルダーを指定して置換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47507-117">On the **Edit** menu, point to **Find and Replace,** and then click **Replace in Files**.</span></span>  
  
2.  <span data-ttu-id="47507-118">**[検索する文字列]** テキスト ボックスに検索テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="47507-118">In the **Find what** text box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="47507-119">**[置換後の文字列]** ボックスに置換後のテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="47507-119">In the **Replace with** box, enter the text to replace the search text.</span></span>  
  
4.  <span data-ttu-id="47507-120">**[検索対象]** 一覧で、 **[すべての開かれているドキュメント]** 、 **[現在のプロジェクト]** 、 **[ソリューション全体]** のいずれかをクリックするか、ディレクトリ パスを入力します。</span><span class="sxs-lookup"><span data-stu-id="47507-120">In the **Look in** list, click **All Open Documents**, **Current Project**, **Entire Solution**, or type a directory path.</span></span>  
  
5.  <span data-ttu-id="47507-121">**[置換]** をクリックすると、現在の検索一致項目が **[置換後の文字列]** ボックス内のテキストに置換されます。</span><span class="sxs-lookup"><span data-stu-id="47507-121">Click **Replace** to replace the current search match with the text in the **Replace with** box.</span></span> <span data-ttu-id="47507-122">1 つの一致項目をスキップする場合は **[次を検索]** をクリックし、ファイル全体をスキップする場合は **[ファイルのスキップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47507-122">You can skip a single match by clicking **Find Next** or skip an entire file clicking **Skip File**.</span></span>  
  
     <span data-ttu-id="47507-123">\- - または -</span><span class="sxs-lookup"><span data-stu-id="47507-123">\- or -</span></span>  
  
     <span data-ttu-id="47507-124">**[すべて置換]** をクリックすると、すべての検索一致項目が **[置換後の文字列]** ボックス内のテキストに置換されます。</span><span class="sxs-lookup"><span data-stu-id="47507-124">Choose **Replace all** to replace all search matches with the text in the **Replace with** box.</span></span> <span data-ttu-id="47507-125">後から一部の置換項目を元に戻す可能性がある場合は、 **[置換後に、変更したファイルを閉じない]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="47507-125">Select **Keep modified files open after Replace All** if you want to undo some of the replacements at another time.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="47507-126">**[すべて置換]** は、すべての検索一致項目を対象としており、その中には **[ファイルのスキップ]** や **[次を検索]** によってスキップしたファイル内の一致項目も含まれます。</span><span class="sxs-lookup"><span data-stu-id="47507-126">**Replace all** replaces all search matches, including those in files you have skipped with **Skip File** or **Find Next**.</span></span> <span data-ttu-id="47507-127">**[元に戻す]** を使用できるのは、置換操作後に開いたままにしておいたファイル内の置換項目に限られます。</span><span class="sxs-lookup"><span data-stu-id="47507-127">You can only use **Undo** for replacements made in files that remain open after the replacement operation.</span></span>  
  
 <span data-ttu-id="47507-128">既定では、[検索結果 1] ウィンドウに置換情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="47507-128">Replacement information appears in the Find Results 1 window by default.</span></span> <span data-ttu-id="47507-129">置換項目を確認するには、[検索結果 1] ウィンドウ内の各項目をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="47507-129">You can browse replacements by double-clicking each entry in the Find Results 1 window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47507-130">参照</span><span class="sxs-lookup"><span data-stu-id="47507-130">See Also</span></span>  
 <span data-ttu-id="47507-131">[検索と置換](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="47507-131">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="47507-132">[ドキュメントの対話形式の検索](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="47507-132">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="47507-133">[ワイルドカードを使用したテキスト検索](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="47507-133">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="47507-134">正規表現によるテキストの検索</span><span class="sxs-lookup"><span data-stu-id="47507-134">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
