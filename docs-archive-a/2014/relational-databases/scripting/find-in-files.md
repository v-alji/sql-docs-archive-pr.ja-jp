---
title: '[フォルダーを指定して検索]'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Find in Files dialog box
ms.assetid: bf92770a-33df-43ef-85ad-5a9223649b98
author: rothja
ms.author: jroth
ms.openlocfilehash: a7bd3051817198fb22e2bf7e96393ddf2023b703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644985"
---
# <a name="find-in-files"></a><span data-ttu-id="41e3f-102">[フォルダーを指定して検索]</span><span class="sxs-lookup"><span data-stu-id="41e3f-102">Find in Files</span></span>
  <span data-ttu-id="41e3f-103"> [検索と置換] ウィンドウの **[フォルダーを指定して検索]** タブでは、指定したファイルのセットのコードで文字列や式を検索できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-103">The **Find in Files** tab of the Find and Replace window enables you to search the code of a specified set of files for a string or expression.</span></span> <span data-ttu-id="41e3f-104">検出された項目および実行するアクションは、 **[結果オプション]** で選択された検索結果ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-104">The matches found and actions taken are listed in the Find Results window selected in **Result Options**.</span></span>  
  
 <span data-ttu-id="41e3f-105">ツール バー ボタンやショートカット キーを使用して **[検索と置換]** ダイアログ ボックスを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-105">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
 <span data-ttu-id="41e3f-106">ここでは、 **[フォルダーを指定して検索]** タブで使用できるコントロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-106">The sections that follow list controls available on the **Find in Files** tab.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="41e3f-107">[検索する文字列]</span><span class="sxs-lookup"><span data-stu-id="41e3f-107">Find What</span></span>  
 <span data-ttu-id="41e3f-108">**[フォルダーを指定して検索]** タブの以下のコントロールを使用すると、検索する文字列または式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-108">These controls on the **Find in Files** tab enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="41e3f-109">**[検索する文字列]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-109">**Find what**</span></span>  
 <span data-ttu-id="41e3f-110">検索するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-110">Type the text to search for.</span></span> <span data-ttu-id="41e3f-111">ダイアログ ボックスを開く前にカーソルで選択されていたテキスト、近接するテキスト、または以前に検索したテキストが、検索テキストの候補として示されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-111">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="41e3f-112">ドロップダウン リストを使用して、直前の 20 回の検索文字列の中から 1 つを再選択することができます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-112">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="41e3f-113">**ワイルドカード付き文字列**</span><span class="sxs-lookup"><span data-stu-id="41e3f-113">**[string with wildcards]**</span></span>  
 <span data-ttu-id="41e3f-114">アスタリスク (`*`) や疑問符 (`?`) などのワイルドカードを検索文字列内で使用する場合は、 **[検索オプション]** の下にある **[条件]** チェック ボックスをオンにして、 **[ワイルドカード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41e3f-114">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="41e3f-115">**[正規表現]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-115">**[regular expression]**</span></span>  
 <span data-ttu-id="41e3f-116">検索エンジンが検索文字列を正規表現として解釈するようにするには、 **[検索オプション]** の下にある **[条件]** チェック ボックスをオンにして、 **[正規表現]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41e3f-116">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="41e3f-117">**式ビルダー**</span><span class="sxs-lookup"><span data-stu-id="41e3f-117">**Expression Builder**</span></span>  
 <span data-ttu-id="41e3f-118">**[検索オプション]** で **[条件]** チェック ボックスがオンになっている場合、 **[検索する文字列]** ボックスの横にある三角形のボタンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-118">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="41e3f-119">このボタンをクリックすると、選択した **[条件]** オプションに応じて、ワイルドカードまたは正規表現の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-119">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="41e3f-120">この一覧から項目を選択すると、 **[検索する文字列]** の文字列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-120">Choosing any item from this list adds it to the **Find what** string.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="41e3f-121">[検索対象]</span><span class="sxs-lookup"><span data-stu-id="41e3f-121">Look In</span></span>  
 <span data-ttu-id="41e3f-122">**[検索対象]** ドロップダウン リストから選択したオプションで、 **[フォルダーを指定して検索]** の検索を現在アクティブなファイル内でだけ実行するか、特定のフォルダー内のすべてのファイルに対して実行するかが決まります。</span><span class="sxs-lookup"><span data-stu-id="41e3f-122">The option chosen from the **Look in** drop-down list determines whether **Find in Files** searches only in currently active files or in all files stored within certain folders.</span></span> <span data-ttu-id="41e3f-123">一覧から検索範囲を選択するか、フォルダー パスを入力します。または、 **[参照]** ボタンをクリックして **[検索フォルダーの選択] ダイアログ ボックス** を表示し、検索対象のフォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-123">Select a search scope from the list, type a folder path, or click the **Browse** button to display the **Custom Directory Set Dialog Box** and choose a set of folders to search.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41e3f-124">選択した **[検索対象]** オプションの設定により、ソース コード管理からチェックアウトしたファイルに対して検索が行われる場合、ローカル コンピューターにダウンロードされているファイル バージョンだけが検索されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-124">If the **Look in** option selected causes you to search a file that you have checked out from source code control, only the version of that file which has been downloaded to your local computer is searched.</span></span>  
  
 <span data-ttu-id="41e3f-125">[**場所**]</span><span class="sxs-lookup"><span data-stu-id="41e3f-125">**Look in**</span></span>  
 <span data-ttu-id="41e3f-126">あらかじめ定義されている検索範囲をこの一覧から選択するか、 **[検索フォルダーの選択]** ダイアログ ボックスを使用して独自のディレクトリのセットを入力します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-126">Select a predefined search scope from this list, or use the **Custom Directory Set** dialog box to enter your own set of directories.</span></span>  
  
 <span data-ttu-id="41e3f-127">**[現在のドキュメント]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-127">**Current Document**</span></span>  
 <span data-ttu-id="41e3f-128">このオプションは、ドキュメントがエディターで開かれているときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-128">This option is available when a document is open in an editor.</span></span> <span data-ttu-id="41e3f-129">アクティブ ドキュメントだけを対象に、 **[検索する文字列]** に指定した文字列の検索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-129">It searches only the active document for the string in **Find what**.</span></span>  
  
 <span data-ttu-id="41e3f-130">**[すべての開かれているドキュメント]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-130">**All Open Documents**</span></span>  
 <span data-ttu-id="41e3f-131">編集のために現在開かれているすべてのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-131">Searches all files currently opened for editing.</span></span>  
  
 <span data-ttu-id="41e3f-132">**[現在のプロジェクト]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-132">**Current Project**</span></span>  
 <span data-ttu-id="41e3f-133">アクティブ プロジェクト内のすべてのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-133">Searches all files in the active project.</span></span>  
  
 <span data-ttu-id="41e3f-134">**[ソリューション全体]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-134">**Entire Solution**</span></span>  
 <span data-ttu-id="41e3f-135">アクティブ ソリューション内のすべてのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-135">Searches all files in the active solution.</span></span>  
  
 <span data-ttu-id="41e3f-136">**[サブフォルダーを含める]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-136">**Include subfolders**</span></span>  
 <span data-ttu-id="41e3f-137">**[検索対象]** に指定したフォルダーのサブフォルダーも検索対象とすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-137">Specifies that subfolders of the folder specified in **Look in** will be searched.</span></span> <span data-ttu-id="41e3f-138">[検索フォルダーの選択] を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41e3f-138">It requires a custom directory set.</span></span>  
  
 <span data-ttu-id="41e3f-139">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-139">**Browse**</span></span>  
 <span data-ttu-id="41e3f-140">このボタンをクリックすると、 **[検索対象]** ボックスに入力するディレクトリの名前付きセットを作成、編集、保存、および選択するための **[検索フォルダーの選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-140">Click this button to display the **Custom Directory Set** dialog box, where you can assemble, edit, save, and select named sets of directories to enter in the **Look in** box.</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="41e3f-141">[条件]</span><span class="sxs-lookup"><span data-stu-id="41e3f-141">Find Options</span></span>  
 <span data-ttu-id="41e3f-142">**[検索オプション]** セクションは、展開したり折りたたんだりできます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-142">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="41e3f-143">次のオプションをオンまたはオフに設定できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-143">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="41e3f-144">**[大文字と小文字を区別する]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-144">**Match case**</span></span>  
 <span data-ttu-id="41e3f-145">このチェック ボックスをオンにすると、検索結果ウィンドウには、 **[検索する文字列]** で指定した文字列に大文字と小文字の違いを含めて完全に一致するインスタンスのみが検索結果ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-145">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="41e3f-146">たとえば、[**大文字と小文字を区別**する] チェックボックスをオンにした状態で**myobject**を検索すると、"myobject" や "myobject" ではなく "myobject" が返されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-146">For example, a search for **MyObject** with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT."</span></span>  
  
 <span data-ttu-id="41e3f-147">**[単語単位]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-147">**Match whole word**</span></span>  
 <span data-ttu-id="41e3f-148">このチェック ボックスをオンにすると、 **[検索する文字列]** で指定した文字列に単語単位で一致するインスタンスのみが検索結果ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-148">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="41e3f-149">たとえば、「 **MyObject** 」を検索すると、"CMyObject" や "MyObjectC" ではなく "MyObject" のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-149">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="41e3f-150">**用途**</span><span class="sxs-lookup"><span data-stu-id="41e3f-150">**Use**</span></span>  
 <span data-ttu-id="41e3f-151">**[検索する文字列]** ボックスまたは **[置換後の文字列]** ボックスに入力された特殊文字を解釈する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-151">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="41e3f-152">オプションは **[ワイルドカード]** と **[正規表現]** です。</span><span class="sxs-lookup"><span data-stu-id="41e3f-152">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="41e3f-153">**正規表現**</span><span class="sxs-lookup"><span data-stu-id="41e3f-153">**Regular Expressions**</span></span>  
 <span data-ttu-id="41e3f-154">検索するテキストのパターンを定義する、特殊な表記です。</span><span class="sxs-lookup"><span data-stu-id="41e3f-154">Special notations define patterns of text to match.</span></span> <span data-ttu-id="41e3f-155">一覧については、「 [正規表現によるテキストの検索](search-text-with-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41e3f-155">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="41e3f-156">**ワイルドカード**</span><span class="sxs-lookup"><span data-stu-id="41e3f-156">**Wildcards**</span></span>  
 <span data-ttu-id="41e3f-157">アスタリスク (`*`) や疑問符 (`?`) などの特殊文字は、1 つまたは複数の文字を表します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-157">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="41e3f-158">一覧については、「 [ワイルドカードを使用したテキスト検索](search-text-with-wildcards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41e3f-158">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="41e3f-159">**[次のファイルの種類を参照]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-159">**Look at these file types**</span></span>  
 <span data-ttu-id="41e3f-160">この一覧は、 **[検索対象]** で指定したディレクトリ内で検索するファイルの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-160">This list indicates the types of files to search through in the directories specified in **Look in**.</span></span> <span data-ttu-id="41e3f-161">このフィールドが空の場合、 **[検索対象]** に指定されているディレクトリ内のすべてのファイルが検索の対象となります。</span><span class="sxs-lookup"><span data-stu-id="41e3f-161">If this field is left blank, all of the files in the directories specified in **Look in** will be searched.</span></span>  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 <span data-ttu-id="41e3f-162">特定の種類のファイルを検索するには、ファイル名としてアスタリスク ワイルドカード (`*`) を入力し、ピリオド (`.`) およびファイル拡張子を順に入力します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-162">To find files of a particular type, enter an asterisk wildcard (`*`) for the file name, followed by a period (`.`) and the file extension.</span></span> <span data-ttu-id="41e3f-163">複数の種類のファイルを検索するには、複数の検索文字列をセミコロン (`;`) で区切って入力します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-163">To find more than one file type, enter multiple search strings separated by a semicolon (`;`).</span></span>  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 <span data-ttu-id="41e3f-164">一覧から項目を選択することによって、特定の種類のファイルを検索対象とする構成済みの検索文字列を入力できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-164">Select any item in the list to enter a preconfigured search string that will find files of particular types.</span></span>  
  
## <a name="result-options"></a><span data-ttu-id="41e3f-165">[結果オプション]</span><span class="sxs-lookup"><span data-stu-id="41e3f-165">Result Options</span></span>  
 <span data-ttu-id="41e3f-166">**[すべて検索]** をクリックした場合の結果の位置を決定します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-166">Determines the location of the results when you click **Find All**.</span></span> <span data-ttu-id="41e3f-167">**[結果オプション]** セクションは、展開したり折りたたんだりできます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-167">You can expand or collapse the **Result Options** section.</span></span> <span data-ttu-id="41e3f-168">次のオプションをオンまたはオフに設定できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-168">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="41e3f-169">**[検索結果 1] ウィンドウ**</span><span class="sxs-lookup"><span data-stu-id="41e3f-169">**Find Results 1 window**</span></span>  
 <span data-ttu-id="41e3f-170">このチェック ボックスがオンの場合、現在の検索の結果は [検索結果 1] ウィンドウの内容に追加されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-170">When this check box is selected, the results of the current search will be appended to the content of the Find Results 1 window.</span></span> <span data-ttu-id="41e3f-171">このウィンドウは、検索結果を表示するために自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-171">This window opens automatically to display your search results.</span></span> <span data-ttu-id="41e3f-172">このウィンドウを手動で開くには、 **[表示]** メニューの **[その他のウィンドウ]** をクリックし、 **[検索結果 1]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41e3f-172">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 1**.</span></span>  
  
 <span data-ttu-id="41e3f-173">**[検索結果 2 ウィンドウ]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-173">**Find Results 2 window**</span></span>  
 <span data-ttu-id="41e3f-174">このチェック ボックスをオンにすると、現在の検索の結果は [検索結果 1] ウィンドウの内容に追加されます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-174">When this check box is selected, the results of the current search will be appended to the content of the Find Results 2 window.</span></span> <span data-ttu-id="41e3f-175">このウィンドウは、検索結果を表示するために自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-175">This window opens automatically to display your search results.</span></span> <span data-ttu-id="41e3f-176">このウィンドウを手動で開くには、 **[表示]** メニューの **[その他のウィンドウ]** をクリックし、 **[検索結果 2]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41e3f-176">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 2**.</span></span>  
  
 <span data-ttu-id="41e3f-177">**[ファイル名のみ表示する]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-177">**Display file names only**</span></span>  
 <span data-ttu-id="41e3f-178">一致項目ごとに 1 つのエントリではなく、一致項目を含むファイルごとに 1 つのエントリを、[検索結果 1] ウィンドウまたは [検索結果 2] ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="41e3f-178">Displays one entry per file containing a search match rather than one entry per search match in either the Find Results 1 or Find Results 2 window.</span></span> <span data-ttu-id="41e3f-179">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="41e3f-179">This option is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="41e3f-180">**[置換後に、変更したファイルを閉じない]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-180">**Keep modified files open after Replace All**</span></span>  
 <span data-ttu-id="41e3f-181">オンにすると、置換が実行されたすべてのファイルは開かれたままになります。これにより、変更内容を元に戻すか、保存するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-181">When selected, leaves open all files in which replacements have been made, so you can undo or save the changes.</span></span> <span data-ttu-id="41e3f-182">メモリの制約により、置換が実行された後に開いたままにできるファイル数が制限されることがあります。</span><span class="sxs-lookup"><span data-stu-id="41e3f-182">Memory constraints might limit the number of files that can remain open after a replace operation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="41e3f-183">**[元に戻す]** は、編集のために開かれているファイルにだけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-183">You can use **Undo** only on files that remain open for editing.</span></span> <span data-ttu-id="41e3f-184">このオプションをオフにすると、編集のために開かれていなかったファイルは閉じたままとなるので、それらのファイルに対して **[元に戻す]** オプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="41e3f-184">If this option is not selected, files that were not already open for editing will remain closed, and no **Undo** option will be available in those files.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="41e3f-185">[検索と置換] のビュー</span><span class="sxs-lookup"><span data-stu-id="41e3f-185">Find and Replace Views</span></span>  
 <span data-ttu-id="41e3f-186">[検索と置換] ウィンドウの上部にあるタブに、 **ビュー** を切り替えるためのメニューがあります。</span><span class="sxs-lookup"><span data-stu-id="41e3f-186">The tabs at the top of the Find and Replace window include **View** menus.</span></span> <span data-ttu-id="41e3f-187">このメニューを使用して、アクティブなペインに表示する一連のフィールドを選択できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-187">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="41e3f-188">[検索と置換] ウィンドウを使いやすい場所にドッキングしておくと、タブを変えてビューを切り替えながら任意の検索操作や置換操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="41e3f-188">You can leave the Find and Replace window docked in a convenient location and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="41e3f-189">**[[クイック検索] に切り替える]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-189">**Switch to Quick Find**</span></span>  
 <span data-ttu-id="41e3f-190">このツール バー タブを使用すると、ダイアログ ボックスが **[クイック検索]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="41e3f-190">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="41e3f-191">**[[フォルダーを指定して検索] に切り替える]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-191">**Switch to Find in Files**</span></span>  
 <span data-ttu-id="41e3f-192">このツール バー タブを使用すると、ダイアログ ボックスが **[フォルダーを指定して検索]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="41e3f-192">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="41e3f-193">**[[シンボルの検索] に切り替える]**</span><span class="sxs-lookup"><span data-stu-id="41e3f-193">**Switch to Find Symbols**</span></span>  
 <span data-ttu-id="41e3f-194">このツール バー タブを使用すると、ダイアログ ボックスが **[シンボルの検索]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="41e3f-194">This toolbar tab changes the dialog box to a **Find in Symbols** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e3f-195">参照</span><span class="sxs-lookup"><span data-stu-id="41e3f-195">See Also</span></span>  
 [<span data-ttu-id="41e3f-196">SQL Server Management Studio のキーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="41e3f-196">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
