---
title: '[検索と置換]'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Find and Replace dialog box
ms.assetid: 09297893-d80b-4c88-86b4-52bfb639e521
author: rothja
ms.author: jroth
ms.openlocfilehash: 9735c2c7271382e3b25ce2b50299153f16882ef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644986"
---
# <a name="find-and-replace"></a><span data-ttu-id="187a6-102">[検索と置換]</span><span class="sxs-lookup"><span data-stu-id="187a6-102">Find and Replace</span></span>
  <span data-ttu-id="187a6-103">**[検索と置換]** ダイアログ ボックスを使用すると、ファイル内のテキストを検索し、必要に応じて置換できます。</span><span class="sxs-lookup"><span data-stu-id="187a6-103">Use the **Find and Replace** dialog box to locate text within a file and optionally replace it.</span></span> <span data-ttu-id="187a6-104">**[検索と置換]** ダイアログ ボックスを開く方法に応じて、表示されるオプションが多少異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="187a6-104">Versions of the **Find and Replace** dialog box with slightly different options can appear, depending on how the dialog box was opened.</span></span> <span data-ttu-id="187a6-105">**[編集]** メニューで **[検索と置換]** をポイントし、 **[クイック検索]** をクリックすると、検索オプションがあって置換オプションがないダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="187a6-105">On the **Edit** menu, point to **Find and Replace**, and then click **Quick Find** to open the dialog box with find options, but without replace options.</span></span> <span data-ttu-id="187a6-106">**[編集]** メニューで **[検索と置換]** をポイントし、 **[クイック置換]** をクリックすると、検索オプションと置換オプションの両方が表示されるダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="187a6-106">On the **Edit** menu, point to **Find and Replace**, and then click **Quick Replace** to open the dialog box with both find options and replace options.</span></span>  
  
 <span data-ttu-id="187a6-107">ツール バー ボタンやショートカット キーを使用して **[検索と置換]** ダイアログ ボックスを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="187a6-107">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="187a6-108">[検索する文字列]</span><span class="sxs-lookup"><span data-stu-id="187a6-108">Find What</span></span>  
 <span data-ttu-id="187a6-109">次のコントロールを使用して、検索する文字列や正規表現を指定します。</span><span class="sxs-lookup"><span data-stu-id="187a6-109">These controls enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="187a6-110">**[検索する文字列]**</span><span class="sxs-lookup"><span data-stu-id="187a6-110">**Find what**</span></span>  
 <span data-ttu-id="187a6-111">検索するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="187a6-111">Type the text to search for.</span></span> <span data-ttu-id="187a6-112">ダイアログ ボックスを開く前にカーソルで選択されていたテキスト、近接するテキスト、または以前に検索したテキストが、検索テキストの候補として示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-112">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="187a6-113">ドロップダウン リストを使用して、直前の 20 回の検索文字列の中から 1 つを再選択することができます。</span><span class="sxs-lookup"><span data-stu-id="187a6-113">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="187a6-114">**ワイルドカード付き文字列**</span><span class="sxs-lookup"><span data-stu-id="187a6-114">**[string with wildcards]**</span></span>  
 <span data-ttu-id="187a6-115">アスタリスク (`*`) や疑問符 (`?`) などのワイルドカードを検索文字列内で使用する場合は、 **[検索オプション]** の下にある **[条件]** チェック ボックスをオンにして、 **[ワイルドカード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="187a6-115">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="187a6-116">**正規表現**</span><span class="sxs-lookup"><span data-stu-id="187a6-116">**[regular expression]**</span></span>  
 <span data-ttu-id="187a6-117">検索エンジンが検索文字列を正規表現として解釈するようにするには、 **[検索オプション]** の下にある **[条件]** チェック ボックスをオンにして、 **[正規表現]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="187a6-117">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="187a6-118">**式ビルダー**</span><span class="sxs-lookup"><span data-stu-id="187a6-118">**Expression Builder**</span></span>  
 <span data-ttu-id="187a6-119">**[検索オプション]** で **[条件]** チェック ボックスがオンになっている場合、 **[検索する文字列]** ボックスの横にある三角形のボタンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="187a6-119">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="187a6-120">このボタンをクリックすると、選択した **[条件]** オプションに応じて、ワイルドカードまたは正規表現の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-120">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="187a6-121">この一覧から項目を選択すると、 **[検索する文字列]** ボックスに指定した文字列にその項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-121">Choosing any item from this list adds it to the string specified in the **Find what** box.</span></span>  
  
## <a name="replace-with"></a><span data-ttu-id="187a6-122">置換後の文字列</span><span class="sxs-lookup"><span data-stu-id="187a6-122">Replace With</span></span>  
 <span data-ttu-id="187a6-123">次のコントロールを使用して、検索で一致した文字列や正規表現に置き換えて挿入する文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="187a6-123">These controls enable you to specify what will be inserted in the place of the matched string or expression.</span></span>  
  
 <span data-ttu-id="187a6-124">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="187a6-124">**Replace with**</span></span>  
 <span data-ttu-id="187a6-125">**[検索する文字列]** で指定した文字列のインスタンスを別の文字列で置き換えるには、このフィールドに置換後の文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="187a6-125">To replace instances of the string specified in **Find what** with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="187a6-126">**[検索する文字列]** で指定したテキストのインスタンスを削除するには、このフィールドを空白にしておきます。</span><span class="sxs-lookup"><span data-stu-id="187a6-126">To delete instances of the text specified in **Find what**, leave this field blank.</span></span> <span data-ttu-id="187a6-127">ドロップダウン リストを選択すると、直前の 20 回の入力項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-127">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="187a6-128">**[置換後の文字列]** ボックスで指定した文字列で正規表現を使用するには、 **[条件]** チェック ボックスをオンにしてから **[正規表現]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="187a6-128">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click **Regular Expressions**.</span></span> <span data-ttu-id="187a6-129">このボックスは、 **[クイック置換]** をクリックしてこのダイアログ ボックスを開いた場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-129">This box only appears if this dialog box was opened by clicked **Quick Replace**.</span></span>  
  
 <span data-ttu-id="187a6-130">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="187a6-130">**Replace with**</span></span>  
 <span data-ttu-id="187a6-131">**[検索する文字列]** で指定した文字列のインスタンスを別の文字列に置き換えるには、このフィールドに置換後の文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="187a6-131">To replace instances of the string specified in the **Find what** box with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="187a6-132">**[検索する文字列]** で指定した文字列のインスタンスを削除するには、このフィールドを空白にしておきます。</span><span class="sxs-lookup"><span data-stu-id="187a6-132">To delete instances of the string specified in the **Find what** box, leave this field blank.</span></span> <span data-ttu-id="187a6-133">ドロップダウン リストを選択すると、直前の 20 回の入力項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-133">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="187a6-134">**[置換後の文字列]** ボックスで指定した文字列で正規表現を使用するには、 **[条件]** チェック ボックスをオンにしてから **[正規表現]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="187a6-134">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="187a6-135">**式ビルダー**</span><span class="sxs-lookup"><span data-stu-id="187a6-135">**Expression Builder**</span></span>  
 <span data-ttu-id="187a6-136">**[検索オプション]** で **[条件]** チェック ボックスがオンになっている場合、 **[置換後の文字列]** ボックスの横にある三角形のボタンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="187a6-136">This triangular button next to the **Replace with** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="187a6-137">このボタンをクリックすると、選択した **[条件]** オプションに応じて、ワイルドカードまたは正規表現の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-137">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="187a6-138">この一覧から項目を選択すると、 **[置換後の文字列]** ボックスに指定されている文字列にその項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-138">Clicking any item in this list adds it to the string specified in the **Replace with** box.</span></span>  
  
 <span data-ttu-id="187a6-139">**Replace**</span><span class="sxs-lookup"><span data-stu-id="187a6-139">**Replace**</span></span>  
 <span data-ttu-id="187a6-140">このボタンをクリックすると、 **[検索する文字列]** ボックスで指定した文字列の現在のインスタンスが **[置換後の文字列]** ボックスで指定した文字列に置き換えられ、 **[検索対象]** で指定された範囲内で次のインスタンスが検索されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-140">Click this button to replace the current instance of the string specified in the **Find what** box with the string specified in the **Replace with** box, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="187a6-141">**[すべて置換]**</span><span class="sxs-lookup"><span data-stu-id="187a6-141">**Replace all**</span></span>  
 <span data-ttu-id="187a6-142">このボタンをクリックすると、 **[検索対象]** ボックスで指定された範囲に含まれるすべてのファイルで、 **[検索する文字列]** ボックスで指定した文字列のすべてのインスタンスが、 **[置換後の文字列]** ボックスで指定した文字列に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="187a6-142">Click this button to replace all instances of the string specified in the **Find what** box with the string specified in the **Replace with** box, in all files within the scope specified in the **Look in** box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="187a6-143">変更する対象のファイルだけが **[検索対象]** に含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="187a6-143">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
 <span data-ttu-id="187a6-144">**[変更したファイルを閉じない]** オプションを含む通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-144">A reminder is displayed that includes a **Keep modified files open** option.</span></span> <span data-ttu-id="187a6-145">**[元に戻す]** オプションを使用できるようにするには、このオプションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="187a6-145">To retain the **Undo** option, you must select this option.</span></span> <span data-ttu-id="187a6-146">**[元に戻す]** は、変更後も開いていて編集可能なファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="187a6-146">**Undo** is only available in files that remain open for editing after they are modified.</span></span>  
  
 <span data-ttu-id="187a6-147">**[ファイルのスキップ]**</span><span class="sxs-lookup"><span data-stu-id="187a6-147">**Skip File**</span></span>  
 <span data-ttu-id="187a6-148">**[検索対象]** に指定した値によって複数のファイルが検索対象になる場合、このボタンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="187a6-148">Becomes available when the value specified for **Look in** includes multiple files.</span></span> <span data-ttu-id="187a6-149">現在のファイルを検索したり変更したりしない場合に、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="187a6-149">Click this button if you do not want to search or modify the current file.</span></span> <span data-ttu-id="187a6-150">検索は、 **[検索対象]** の一覧の次のファイルから続行されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-150">The search will continue in the next file on the list in **Look in**.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="187a6-151">[検索対象]</span><span class="sxs-lookup"><span data-stu-id="187a6-151">Look In</span></span>  
 <span data-ttu-id="187a6-152">**Look in**</span><span class="sxs-lookup"><span data-stu-id="187a6-152">**Look in**</span></span>  
 <span data-ttu-id="187a6-153">**[検索する文字列]** で指定したテキストを検索する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="187a6-153">Select the location to look for the text specified in **Find what**.</span></span> <span data-ttu-id="187a6-154">**[現在のドキュメント]** オプションを選択すると、ダイアログ ボックスを開いたときにアクティブだったドキュメント ウィンドウが検索されます。 **[すべての開かれているドキュメント]** オプションを選択すると、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で現在開いているすべてのドキュメント ウィンドウが検索されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-154">Options are **Current Document**, which searches the document window that had focus when the dialog box was opened, and **All Open Documents**, which searches all document windows that are currently open in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="187a6-155">[条件]</span><span class="sxs-lookup"><span data-stu-id="187a6-155">Find Options</span></span>  
 <span data-ttu-id="187a6-156">**[検索オプション]** セクションは、展開したり折りたたんだりできます。</span><span class="sxs-lookup"><span data-stu-id="187a6-156">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="187a6-157">次のオプションをオンまたはオフに設定できます。</span><span class="sxs-lookup"><span data-stu-id="187a6-157">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="187a6-158">**[大文字と小文字を区別する]**</span><span class="sxs-lookup"><span data-stu-id="187a6-158">**Match case**</span></span>  
 <span data-ttu-id="187a6-159">このチェック ボックスをオンにすると、検索結果ウィンドウには、 **[検索する文字列]** で指定した文字列に大文字と小文字の違いを含めて完全に一致するインスタンスのみが検索結果ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-159">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="187a6-160">たとえば、 **[大文字と小文字を区別する]** チェック ボックスをオンにした状態で " **MyObject** " を検索すると、"myobject" や "MYOBJECT" ではなく "MyObject" のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-160">For example, a search for "**MyObject**" with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT."</span></span>  
  
 <span data-ttu-id="187a6-161">**[単語単位]**</span><span class="sxs-lookup"><span data-stu-id="187a6-161">**Match whole word**</span></span>  
 <span data-ttu-id="187a6-162">このチェック ボックスをオンにすると、 **[検索する文字列]** で指定した文字列に、単語単位で一致するインスタンスのみが検索結果ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-162">When selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="187a6-163">たとえば、「 **MyObject** 」を検索すると、"CMyObject" や "MyObjectC" ではなく "MyObject" のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-163">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="187a6-164">**[上へ検索]**</span><span class="sxs-lookup"><span data-stu-id="187a6-164">**Search up**</span></span>  
 <span data-ttu-id="187a6-165">カーソル位置からドキュメントの先頭までの範囲で検索します。</span><span class="sxs-lookup"><span data-stu-id="187a6-165">Search from the cursor location towards the beginning of the document.</span></span>  
  
 <span data-ttu-id="187a6-166">**[非表示のテキストを検索]**</span><span class="sxs-lookup"><span data-stu-id="187a6-166">**Search hidden text**</span></span>  
 <span data-ttu-id="187a6-167">非表示のテキストと折りたたまれているテキストのインスタンスを検索します。</span><span class="sxs-lookup"><span data-stu-id="187a6-167">Locate instances of the text that are concealed and collapsed text.</span></span>  
  
 <span data-ttu-id="187a6-168">**用途**</span><span class="sxs-lookup"><span data-stu-id="187a6-168">**Use**</span></span>  
 <span data-ttu-id="187a6-169">**[検索する文字列]** ボックスまたは **[置換後の文字列]** ボックスに入力された特殊文字を解釈する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="187a6-169">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="187a6-170">オプションは **[ワイルドカード]** と **[正規表現]** です。</span><span class="sxs-lookup"><span data-stu-id="187a6-170">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="187a6-171">**Regular Expressions**</span><span class="sxs-lookup"><span data-stu-id="187a6-171">**Regular Expressions**</span></span>  
 <span data-ttu-id="187a6-172">検索するテキストのパターンを定義する、特殊な表記です。</span><span class="sxs-lookup"><span data-stu-id="187a6-172">Special notations define patterns of text to match.</span></span> <span data-ttu-id="187a6-173">一覧については、「 [正規表現によるテキストの検索](search-text-with-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="187a6-173">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="187a6-174">**ワイルドカード**</span><span class="sxs-lookup"><span data-stu-id="187a6-174">**Wildcards**</span></span>  
 <span data-ttu-id="187a6-175">アスタリスク (`*`) や疑問符 (`?`) などの特殊文字は、1 つまたは複数の文字を表します。</span><span class="sxs-lookup"><span data-stu-id="187a6-175">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="187a6-176">一覧については、「 [ワイルドカードを使用したテキスト検索](search-text-with-wildcards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="187a6-176">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="187a6-177">**[次を検索]**</span><span class="sxs-lookup"><span data-stu-id="187a6-177">**Find Next**</span></span>  
 <span data-ttu-id="187a6-178">**[検索する文字列]** ボックス内のテキストの検索を開始します。</span><span class="sxs-lookup"><span data-stu-id="187a6-178">Begins searching for the text in the **Find what** box.</span></span>  
  
 <span data-ttu-id="187a6-179">**Replace**</span><span class="sxs-lookup"><span data-stu-id="187a6-179">**Replace**</span></span>  
 <span data-ttu-id="187a6-180">このボタンをクリックすると、 **[検索する文字列]** で指定した文字列の現在のインスタンスが **[置換後の文字列]** で指定した文字列に置き換えられ、 **[検索対象]** で指定された範囲内で次のインスタンスが検索されます。</span><span class="sxs-lookup"><span data-stu-id="187a6-180">Click this button to replace the current instance of the string specified in **Find what** with the string specified in **Replace with**, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="187a6-181">**Replace All**</span><span class="sxs-lookup"><span data-stu-id="187a6-181">**Replace All**</span></span>  
 <span data-ttu-id="187a6-182">このボタンをクリックすると、 **[検索対象]** で指定された範囲に含まれるすべてのファイルで、 **[検索する文字列]** で指定した文字列のすべてのインスタンスが、 **[置換後の文字列]** で指定した文字列に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="187a6-182">Choose this button to replace all instances of the string specified in **Find what** with the string specified in **Replace with**, in all files within the scope specified in **Look in**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="187a6-183">変更する対象のファイルだけが **[検索対象]** に含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="187a6-183">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="187a6-184">[検索と置換] のビュー</span><span class="sxs-lookup"><span data-stu-id="187a6-184">Find and Replace Views</span></span>  
 <span data-ttu-id="187a6-185">[検索と置換] ウィンドウの上部にあるタブに、 **ビュー** を切り替えるためのメニューがあります。</span><span class="sxs-lookup"><span data-stu-id="187a6-185">The tabs at the top of the Find and Replace window include **View** menus.</span></span> <span data-ttu-id="187a6-186">このメニューを使用して、アクティブなペインに表示する一連のフィールドを選択できます。</span><span class="sxs-lookup"><span data-stu-id="187a6-186">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="187a6-187">**[検索と置換]** ウィンドウを使いやすい場所にドッキングしておくと、タブを変えてビューを切り替えながら任意の検索操作や置換操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="187a6-187">You can leave the **Find and Replace** window docked in a convenient location, and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="187a6-188">**[クイック検索]**</span><span class="sxs-lookup"><span data-stu-id="187a6-188">**Quick Find**</span></span>  
 <span data-ttu-id="187a6-189">このツール バー タブを使用すると、ダイアログ ボックスが **[クイック検索]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="187a6-189">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="187a6-190">**フォルダーを指定して検索**</span><span class="sxs-lookup"><span data-stu-id="187a6-190">**Find in Files**</span></span>  
 <span data-ttu-id="187a6-191">このツール バー タブを使用すると、ダイアログ ボックスが **[フォルダーを指定して検索]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="187a6-191">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="187a6-192">**[クイック置換]**</span><span class="sxs-lookup"><span data-stu-id="187a6-192">**Quick Replace**</span></span>  
 <span data-ttu-id="187a6-193">このツール バー タブを使用すると、ダイアログ ボックスが **[クイック置換]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="187a6-193">This toolbar tab changes the dialog box to a **Quick Replace** dialog box</span></span>  
  
 <span data-ttu-id="187a6-194">**フォルダーを指定して置換**</span><span class="sxs-lookup"><span data-stu-id="187a6-194">**Replace in Files**</span></span>  
 <span data-ttu-id="187a6-195">このツール バー タブを使用すると、ダイアログ ボックスが **[フォルダーを指定して置換]** ダイアログ ボックスに変わります。</span><span class="sxs-lookup"><span data-stu-id="187a6-195">This toolbar tab changes the dialog box to a **Replace in Files** dialog box</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="187a6-196">参照</span><span class="sxs-lookup"><span data-stu-id="187a6-196">See Also</span></span>  
 [<span data-ttu-id="187a6-197">SQL Server Management Studio のキーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="187a6-197">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
