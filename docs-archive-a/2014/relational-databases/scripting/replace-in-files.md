---
title: '[フォルダーを指定して置換]'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Replace in Files dialog box
ms.assetid: 51191c0a-e022-41d6-8473-5cb3c6596862
author: rothja
ms.author: jroth
ms.openlocfilehash: ad7f23cfc8ec083d5cf2d7dcadefd3a8c27176e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633053"
---
# <a name="replace-in-files"></a><span data-ttu-id="58d7c-102">[フォルダーを指定して置換]</span><span class="sxs-lookup"><span data-stu-id="58d7c-102">Replace in Files</span></span>
  <span data-ttu-id="58d7c-103">**[検索と置換]** ウィンドウの [フォルダーを指定して置換] タブを使用すると、指定したファイル セットのコード内で文字列や正規表現を検索したり、検出された項目の一部またはすべてを置き換えたりできます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-103">The **Replace in Files** tab of the Find and Replace window enables you to search the code of a specified set of files for a string or expression and change some or all of the matches found.</span></span> <span data-ttu-id="58d7c-104">検出された項目および実行するアクションは、 **[結果オプション]** で選択された検索結果ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-104">The matches found and actions taken are listed in the Find Results window selected in **Result Options**.</span></span>  
  
 <span data-ttu-id="58d7c-105">ツール バー ボタンやショートカット キーを使用して **[検索と置換]** ダイアログ ボックスを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-105">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="58d7c-106">[検索する文字列]</span><span class="sxs-lookup"><span data-stu-id="58d7c-106">Find What</span></span>  
 <span data-ttu-id="58d7c-107">**[フォルダーを指定して置換]** タブの次のコントロールを使用して、検索する文字列または正規表現を指定します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-107">These controls on the **Replace in Files** tab enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="58d7c-108">**[検索する文字列]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-108">**Find what**</span></span>  
 <span data-ttu-id="58d7c-109">検索するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-109">Type the text to search for.</span></span> <span data-ttu-id="58d7c-110">ダイアログ ボックスを開く前にカーソルで選択されていたテキスト、近接するテキスト、または以前に検索したテキストが、検索テキストの候補として示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-110">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="58d7c-111">ドロップダウン リストを使用して、直前の 20 回の検索文字列の中から 1 つを再選択することができます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-111">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="58d7c-112">**ワイルドカード付き文字列**</span><span class="sxs-lookup"><span data-stu-id="58d7c-112">**[string with wildcards]**</span></span>  
 <span data-ttu-id="58d7c-113">アスタリスク (`*`) や疑問符 (`?`) などのワイルドカードを検索文字列内で使用する場合は、 **[検索オプション]** の下にある **[条件]** チェック ボックスをオンにして、 **[ワイルドカード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58d7c-113">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="58d7c-114">**[正規表現]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-114">**[regular expression]**</span></span>  
 <span data-ttu-id="58d7c-115">検索エンジンが検索文字列を正規表現として解釈するようにするには、 **[検索オプション]** の下にある **[条件]** チェック ボックスをオンにして、 **[正規表現]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58d7c-115">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="58d7c-116">**式ビルダー**</span><span class="sxs-lookup"><span data-stu-id="58d7c-116">**Expression Builder**</span></span>  
 <span data-ttu-id="58d7c-117">**[検索オプション]** で **[条件]** チェック ボックスがオンになっている場合、 **[検索する文字列]** ボックスの横にある三角形のボタンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-117">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="58d7c-118">このボタンをクリックすると、選択した **[条件]** オプションに応じて、ワイルドカードまたは正規表現の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-118">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="58d7c-119">この一覧から項目を選択すると、 **[検索する文字列]** ボックスに指定した文字列にその項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-119">Choosing any item from this list adds it to the string specified in the **Find what** box.</span></span>  
  
## <a name="replace-with"></a><span data-ttu-id="58d7c-120">置換後の文字列</span><span class="sxs-lookup"><span data-stu-id="58d7c-120">Replace With</span></span>  
 <span data-ttu-id="58d7c-121">次のコントロールを使用して、検索で一致した文字列や正規表現に置き換えて挿入する文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-121">These controls enable you to specify what will be inserted in the place of the matched string or expression.</span></span>  
  
 <span data-ttu-id="58d7c-122">**置換後の文字列**</span><span class="sxs-lookup"><span data-stu-id="58d7c-122">**Replace with**</span></span>  
 <span data-ttu-id="58d7c-123">**[検索する文字列]** で指定した文字列のインスタンスを別の文字列で置き換えるには、このフィールドに置換後の文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-123">To replace instances of the string specified in **Find what** with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="58d7c-124">**[検索する文字列]** で指定した文字列のインスタンスを削除するには、このボックスを空白にしておきます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-124">To delete instances of the string specified in **Find what**, leave this box blank.</span></span> <span data-ttu-id="58d7c-125">ドロップダウン リストを選択すると、直前の 20 回の入力項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-125">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="58d7c-126">**[置換後の文字列]** ボックスで指定する文字列で正規表現を使用するには、 **[条件]** チェック ボックスをオンにしてから **[正規表現]** オプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="58d7c-126">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click the **Regular Expressions** option.</span></span>  
  
 <span data-ttu-id="58d7c-127">**式ビルダー**</span><span class="sxs-lookup"><span data-stu-id="58d7c-127">**Expression Builder**</span></span>  
 <span data-ttu-id="58d7c-128">**[検索オプション]** で **[条件]** チェック ボックスがオンになっている場合、 **[置換後の文字列]** ボックスの横にある三角形のボタンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-128">This triangular button next to the **Replace with** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="58d7c-129">このボタンをクリックすると、選択した **[条件]** オプションに応じて、ワイルドカードまたは正規表現の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-129">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="58d7c-130">この一覧から項目を選択すると、 **[置換後の文字列]** ボックスに指定されている文字列にその項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-130">Clicking any item in this list adds it to the string specified in the **Replace with** box.</span></span>  
  
 <span data-ttu-id="58d7c-131">**Replace**</span><span class="sxs-lookup"><span data-stu-id="58d7c-131">**Replace**</span></span>  
 <span data-ttu-id="58d7c-132">このボタンをクリックすると、 **[検索する文字列]** に指定された文字列の現在のインスタンスが **[置換後の文字列]** ボックスで指定した文字列で置き換えられ、 **[検索対象]** で指定された範囲内で次のインスタンスが検索されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-132">Click this button to replace the current instance of the string specified in **Find what** with the string specified in the **Replace with** box, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="58d7c-133">**すべて置換**</span><span class="sxs-lookup"><span data-stu-id="58d7c-133">**Replace all**</span></span>  
 <span data-ttu-id="58d7c-134">このボタンをクリックすると、 **[検索対象]** に指定されている範囲内のすべてのファイルにおいて、 **[検索する文字列]** に指定された文字列のすべてのインスタンスが、 **[置換後の文字列]** ボックスに指定された文字列で置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-134">Click this button to replace all instances of the string specified in **Find what** with the string specified in the **Replace with** box, in all files within the scope specified in **Look in**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="58d7c-135">変更する対象のファイルだけが **[検索対象]** に含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="58d7c-135">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
 <span data-ttu-id="58d7c-136">**[変更したファイルを閉じない]** オプションを含む通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-136">A reminder is displayed that includes a **Keep modified files open** option.</span></span> <span data-ttu-id="58d7c-137">**[元に戻す]** オプションを使用できるようにするには、このオプションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-137">To retain the **Undo** option, you must select this option.</span></span> <span data-ttu-id="58d7c-138">**[元に戻す]** は、変更後も開いていて編集可能なファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-138">**Undo** is only available in files that remain open for editing after they are modified.</span></span>  
  
 <span data-ttu-id="58d7c-139">**[ファイルのスキップ]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-139">**Skip File**</span></span>  
 <span data-ttu-id="58d7c-140">**[検索対象]** に指定した値によって複数のファイルが検索対象になる場合、このボタンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-140">Becomes available when **Look in** includes multiple files.</span></span> <span data-ttu-id="58d7c-141">現在のファイルを検索したり変更したりしない場合に、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="58d7c-141">Click this button if you do not want to search or modify the current file.</span></span> <span data-ttu-id="58d7c-142">検索は、 **[検索対象]** の一覧の次のファイルから続行されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-142">The search will continue in the next file on the list in **Look in**.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="58d7c-143">[検索対象]</span><span class="sxs-lookup"><span data-stu-id="58d7c-143">Look In</span></span>  
 <span data-ttu-id="58d7c-144">**[検索対象]** ドロップダウン リストから選択したオプションで、 **[フォルダーを指定して置換]** の検索を現在アクティブなファイル内でだけ実行するか、特定のフォルダー内のすべてのファイルに対して実行するかが決まります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-144">The option chosen from the **Look in** drop-down list determines whether **Replace in Files** searches only in currently active files or searches all files stored within certain folders.</span></span> <span data-ttu-id="58d7c-145">一覧から検索範囲を選択するか、フォルダーパスを入力するか、[**参照**] ボタンをクリックして [**カスタムディレクトリセット**] ダイアログボックスを表示し、検索するフォルダーのセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-145">Select a search scope from the list, type a folder path, or click the **Browse** button to display the **Custom Directory Set** dialog box and choose a set of folders to search.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58d7c-146">選択した **[検索対象]** オプションの設定により、ソース コード管理からチェックアウトしたファイルに対して検索が行われる場合、ローカル コンピューターにダウンロードされているファイル バージョンだけが検索されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-146">If the **Look in** option selected causes you to search a file that you have checked out from source code control, only the version of that file which has been downloaded to your local computer is searched.</span></span>  
  
 <span data-ttu-id="58d7c-147">[**場所**]</span><span class="sxs-lookup"><span data-stu-id="58d7c-147">**Look in**</span></span>  
 <span data-ttu-id="58d7c-148">あらかじめ定義されている検索範囲をこの一覧から選択するか、 **[検索フォルダーの選択]** ダイアログ ボックスを使用して独自のディレクトリのセットを入力します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-148">Select a predefined search scope from this list, or use the **Custom Directory Set** dialog box to enter your own set of directories.</span></span>  
  
 <span data-ttu-id="58d7c-149">**[現在のドキュメント]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-149">**Current Document**</span></span>  
 <span data-ttu-id="58d7c-150">このオプションは、ドキュメントがエディターで開かれているときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-150">This option is available when a document is open in an editor.</span></span> <span data-ttu-id="58d7c-151">アクティブ ドキュメントだけを対象に、 **[検索する文字列]** に指定した文字列の検索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-151">Searches only the active document for the string specified in **Find what**.</span></span>  
  
 <span data-ttu-id="58d7c-152">**[すべての開かれているドキュメント]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-152">**All Open Documents**</span></span>  
 <span data-ttu-id="58d7c-153">編集のために現在開かれているすべてのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-153">Searches all files currently opened for editing.</span></span>  
  
 <span data-ttu-id="58d7c-154">**[現在のプロジェクト]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-154">**Current Project**</span></span>  
 <span data-ttu-id="58d7c-155">アクティブ プロジェクト内のすべてのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-155">Searches all files in the active project.</span></span>  
  
 <span data-ttu-id="58d7c-156">**[ソリューション全体]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-156">**Entire Solution**</span></span>  
 <span data-ttu-id="58d7c-157">アクティブ ソリューション内のすべてのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-157">Searches all files in the active solution.</span></span>  
  
 <span data-ttu-id="58d7c-158">**[サブフォルダーを含める]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-158">**Include subfolders**</span></span>  
 <span data-ttu-id="58d7c-159">**[検索対象]** に指定したフォルダーのサブフォルダーも検索対象とすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-159">Specifies that subfolders of the folder specified in **Look in** will be searched.</span></span> <span data-ttu-id="58d7c-160">[検索フォルダーの選択] を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-160">It requires a custom directory set.</span></span>  
  
 <span data-ttu-id="58d7c-161">**[...]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-161">**Browse (...)**</span></span>  
 <span data-ttu-id="58d7c-162">このボタンをクリックすると、 **[検索対象]** ボックスに入力するディレクトリの名前付きセットを作成、編集、保存、および選択するための **[検索フォルダーの選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-162">Click this button to display the **Choose Search Folders** dialog box, where you can assemble, edit, save, and select named sets of directories to enter in the **Look in** box.</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="58d7c-163">[条件]</span><span class="sxs-lookup"><span data-stu-id="58d7c-163">Find Options</span></span>  
 <span data-ttu-id="58d7c-164">**[検索オプション]** セクションは、展開したり折りたたんだりできます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-164">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="58d7c-165">次のオプションをオンまたはオフに設定できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-165">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="58d7c-166">**[大文字と小文字を区別する]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-166">**Match case**</span></span>  
 <span data-ttu-id="58d7c-167">このチェック ボックスをオンにすると、検索結果ウィンドウには、 **[検索する文字列]** で指定した文字列に大文字と小文字の違いを含めて完全に一致するインスタンスのみが検索結果ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-167">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="58d7c-168">たとえば、 **[大文字と小文字を区別する]** チェック ボックスをオンにした状態で「 **MyObject** 」を検索すると、"myobject" や "MYOBJECT" ではなく "MyObject" のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-168">For example, a search for **MyObject** with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT".</span></span>  
  
 <span data-ttu-id="58d7c-169">**[単語単位]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-169">**Match whole word**</span></span>  
 <span data-ttu-id="58d7c-170">このチェック ボックスをオンにすると、 **[検索する文字列]** で指定した文字列に単語単位で一致するインスタンスのみが検索結果ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-170">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="58d7c-171">たとえば、「 **MyObject** 」を検索すると、"CMyObject" や "MyObjectC" ではなく "MyObject" のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-171">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="58d7c-172">**用途**</span><span class="sxs-lookup"><span data-stu-id="58d7c-172">**Use**</span></span>  
 <span data-ttu-id="58d7c-173">**[検索する文字列]** ボックスまたは **[置換後の文字列]** ボックスに入力された特殊文字を解釈する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-173">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="58d7c-174">オプションは **[ワイルドカード]** と **[正規表現]** です。</span><span class="sxs-lookup"><span data-stu-id="58d7c-174">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="58d7c-175">**正規表現**</span><span class="sxs-lookup"><span data-stu-id="58d7c-175">**Regular Expressions**</span></span>  
 <span data-ttu-id="58d7c-176">検索するテキストのパターンを定義する、特殊な表記です。</span><span class="sxs-lookup"><span data-stu-id="58d7c-176">Special notations define patterns of text to match.</span></span> <span data-ttu-id="58d7c-177">一覧については、「 [正規表現によるテキストの検索](search-text-with-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58d7c-177">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="58d7c-178">**ワイルドカード**</span><span class="sxs-lookup"><span data-stu-id="58d7c-178">**Wildcards**</span></span>  
 <span data-ttu-id="58d7c-179">アスタリスク (`*`) や疑問符 (`?`) などの特殊文字は、1 つまたは複数の文字を表します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-179">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="58d7c-180">一覧については、「 [ワイルドカードを使用したテキスト検索](search-text-with-wildcards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58d7c-180">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="58d7c-181">**[次のファイルの種類を参照]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-181">**Look at these file types**</span></span>  
 <span data-ttu-id="58d7c-182">この一覧は、 **[検索対象]** で指定したディレクトリ内で検索するファイルの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-182">This list indicates the types of files to search through in the directories specified in **Look in**.</span></span> <span data-ttu-id="58d7c-183">このボックスが空の場合、 **[検索対象]** に指定されているディレクトリ内のすべてのファイルが検索の対象となります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-183">If this box is left blank, all of the files in the directories specified in **Look in** will be searched.</span></span>  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 <span data-ttu-id="58d7c-184">特定の種類のファイルを検索するには、ファイル名としてアスタリスク ワイルドカード (`*`) を入力し、ピリオド (`.`) およびファイル拡張子を順に入力します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-184">To find files of a particular type, enter an asterisk wildcard (`*`) for the file name, followed by a period (`.`) and the file extension.</span></span> <span data-ttu-id="58d7c-185">複数の種類のファイルを検索するには、複数の検索文字列をセミコロン (`;`) で区切って入力します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-185">To find more than one file type, enter multiple search strings separated by a semicolon (`;`).</span></span>  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 <span data-ttu-id="58d7c-186">一覧から項目を選択することによって、特定の種類のファイルを検索対象とする構成済みの検索文字列を入力できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-186">Select any item in the list to enter a preconfigured search string that will find files of particular types.</span></span>  
  
## <a name="result-options"></a><span data-ttu-id="58d7c-187">[結果オプション]</span><span class="sxs-lookup"><span data-stu-id="58d7c-187">Result Options</span></span>  
 <span data-ttu-id="58d7c-188">**[結果オプション]** セクションは、展開したり折りたたんだりできます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-188">You can expand or collapse the **Result Options** section.</span></span> <span data-ttu-id="58d7c-189">次のオプションをオンまたはオフに設定できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-189">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="58d7c-190">**[検索結果 1] ウィンドウ**</span><span class="sxs-lookup"><span data-stu-id="58d7c-190">**Find Results 1 window**</span></span>  
 <span data-ttu-id="58d7c-191">このチェック ボックスがオンの場合、現在の検索の結果は [検索結果 1] ウィンドウの内容に追加されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-191">When this check box is selected, the results of the current search will be appended to the content of the Find Results 1 window.</span></span> <span data-ttu-id="58d7c-192">このウィンドウは、検索結果を表示するために自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-192">This window opens automatically to display your search results.</span></span> <span data-ttu-id="58d7c-193">このウィンドウを手動で開くには、 **[表示]** メニューの **[その他のウィンドウ]** をクリックし、 **[検索結果 1]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58d7c-193">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 1**.</span></span>  
  
 <span data-ttu-id="58d7c-194">**[検索結果 2 ウィンドウ]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-194">**Find Results 2 window**</span></span>  
 <span data-ttu-id="58d7c-195">このチェック ボックスがオンの場合、現在の検索の結果は [検索結果 2] ウィンドウの内容に追加されます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-195">When this check box is selected selected, the results of the current search will be appended to the content of the Find Results 2 window.</span></span> <span data-ttu-id="58d7c-196">このウィンドウは、検索結果を表示するために自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-196">This window opens automatically to display your search results.</span></span> <span data-ttu-id="58d7c-197">このウィンドウを手動で開くには、 **[表示]** メニューの **[その他のウィンドウ]** をクリックし、 **[検索結果 2]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58d7c-197">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 2**.</span></span>  
  
 <span data-ttu-id="58d7c-198">**[ファイル名のみ表示する]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-198">**Display file names only**</span></span>  
 <span data-ttu-id="58d7c-199">一致項目ごとに 1 つのエントリではなく、一致項目を含むファイルごとに 1 つのエントリを、[検索結果 1] ウィンドウまたは [検索結果 2] ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="58d7c-199">Displays one entry per file containing a search match rather than one entry per search match in either the Find Results 1 or Find Results 2 window.</span></span> <span data-ttu-id="58d7c-200">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="58d7c-200">This option is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="58d7c-201">**[置換後に、変更したファイルを閉じない]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-201">**Keep modified files open after Replace All**</span></span>  
 <span data-ttu-id="58d7c-202">オンにすると、置換が実行されたすべてのファイルは開かれたままになります。これにより、変更内容を元に戻すか、保存するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-202">When selected, leaves open all files in which replacements have been made, so you can undo or save the changes.</span></span> <span data-ttu-id="58d7c-203">メモリの制約により、置換が実行された後に開いたままにできるファイル数が制限されることがあります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-203">Memory constraints might limit the number of files that can remain open after a replace operation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="58d7c-204">**[元に戻す]** は、編集のために開かれているファイルにだけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-204">You can use **Undo** only on files that remain open for editing.</span></span> <span data-ttu-id="58d7c-205">このオプションをオフにすると、編集のために開かれていなかったファイルは閉じたままとなるので、それらのファイルに対して **[元に戻す]** オプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="58d7c-205">If this option is not selected, files that were not already open for editing will remain closed, and no **Undo** option will be available in those files.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="58d7c-206">[検索と置換] のビュー</span><span class="sxs-lookup"><span data-stu-id="58d7c-206">Find and Replace Views</span></span>  
 <span data-ttu-id="58d7c-207">[検索と置換] ウィンドウの上部にあるタブに、 **ビュー** を切り替えるためのメニューがあります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-207">The tabs at the top of the Findand Replace window include **View** menus.</span></span> <span data-ttu-id="58d7c-208">このメニューを使用して、アクティブなペインに表示する一連のフィールドを選択できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-208">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="58d7c-209">[検索と置換] ウィンドウを使いやすい場所にドッキングしておくと、タブを変えてビューを切り替えながら任意の検索操作や置換操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="58d7c-209">You can leave the Find and Replace window docked in a convenient location, and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="58d7c-210">**[[クイック検索] に切り替える]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-210">**Switch to Quick Find**</span></span>  
 <span data-ttu-id="58d7c-211">このツール バー タブを使用すると、ダイアログ ボックスが **[クイック検索]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-211">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="58d7c-212">**[[フォルダーを指定して検索] に切り替える]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-212">**Switch to Find in Files**</span></span>  
 <span data-ttu-id="58d7c-213">このツール バー タブを使用すると、ダイアログ ボックスが **[フォルダーを指定して検索]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-213">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="58d7c-214">**[[シンボルの検索] に切り替える]**</span><span class="sxs-lookup"><span data-stu-id="58d7c-214">**Switch to Find Symbols**</span></span>  
 <span data-ttu-id="58d7c-215">このツール バー タブを使用すると、ダイアログ ボックスが **[シンボルの検索]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="58d7c-215">This toolbar tab changes the dialog box to a **Find in Symbols** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d7c-216">参照</span><span class="sxs-lookup"><span data-stu-id="58d7c-216">See Also</span></span>  
 [<span data-ttu-id="58d7c-217">SQL Server Management Studio のキーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="58d7c-217">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
