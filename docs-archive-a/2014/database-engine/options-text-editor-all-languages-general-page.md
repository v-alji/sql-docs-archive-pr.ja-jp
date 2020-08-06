---
title: '[オプション] ([テキストエディター]/[すべての言語]/[全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bf18907c-94e2-4c09-9b2b-0925ac04c627
author: rothja
ms.author: jroth
ms.openlocfilehash: 9510ff7c8d28a084ac250c937ec01458b612ac60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644135"
---
# <a name="options-text-editor---all-languages---general-page"></a><span data-ttu-id="aed73-102">[オプション] ([テキスト エディター]/[すべての言語]/[全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="aed73-102">Options (Text Editor - All Languages - General Page)</span></span>
  <span data-ttu-id="aed73-103">このダイアログ ボックスを使用すると、全部で 5 つある [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のすべてのエディターの全般的な編集オプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="aed73-103">Use this dialog box to set general editing options in all five of the editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="aed73-104">これらのオプションを表示するには、**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aed73-104">To display these options, click **Options** on the **Tools** menu.</span></span> <span data-ttu-id="aed73-105">**[テキスト エディター]** フォルダーを選択し、**[すべての言語]** フォルダーを展開して、**[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aed73-105">Select the **Text Editor** folder, expand the **All Languages** folder and then click **General**.</span></span>  
  
## <a name="option-settings-by-editor"></a><span data-ttu-id="aed73-106">エディターのオプション設定</span><span class="sxs-lookup"><span data-stu-id="aed73-106">Option Settings by Editor</span></span>  
 <span data-ttu-id="aed73-107">DMX エディター、MDX エディター、および SQL Server Compact エディターに対するオプションは、**[すべての言語]** ダイアログを使用して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aed73-107">You must use the **All Languages** dialogs to set options for the DMX, MDX, and SQL Server Compact editors.</span></span> <span data-ttu-id="aed73-108">ここで設定したオプションは、テキスト形式、Transact-SQL、および XML の各エディターにも適用されます。ただし、対応する言語のサブフォルダーを展開し、そのオプション ページを選択すると、個々のエディター単位でオプションを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="aed73-108">Options set here are also applied to the Plain Text, Transact-SQL, and XML editors, but you can set options separately for those editors by expanding the subfolders for those languages and selecting their option pages.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="aed73-109">このダイアログを使用してオプションを設定する場合で、なおかつプレーンテキスト、Transact-SQL、XML の各エディターに対して異なる設定を使用する必要がある場合は、**[すべての言語]** ダイアログで必要な設定を適用したうえで、それぞれのエディターのオプションを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aed73-109">If you set an option using this dialog, but want a different setting for the Plain Text, Transact-SQL, or XML editors, you must set the options for those editors after applying your selections in the **All Languages** dialog.</span></span>  
  
 <span data-ttu-id="aed73-110">このページに記載されているオプションが、エディターによってはサポートされない場合があります。</span><span class="sxs-lookup"><span data-stu-id="aed73-110">Some editors may not support all of the options listed on this page.</span></span> <span data-ttu-id="aed73-111">オプションが選択されている場合は、**[オプション]** ダイアログ ボックスの **[全般]** ページで、一部のプログラミング言語に対してのみ淡色表示されたチェック マークが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aed73-111">A shaded check mark is displayed when an option has been selected on the **General** page of the **Options** dialog box for some programming languages, but not for others.</span></span>  
  
## <a name="statement-completion"></a><span data-ttu-id="aed73-112">[入力候補]</span><span class="sxs-lookup"><span data-stu-id="aed73-112">Statement Completion</span></span>  
 <span data-ttu-id="aed73-113">**[自動メンバー表示]**</span><span class="sxs-lookup"><span data-stu-id="aed73-113">**Auto list members**</span></span>  
 <span data-ttu-id="aed73-114">エディターでの入力に合わせて、使用できるメンバー、プロパティ、または値のポップアップ リストを表示します。</span><span class="sxs-lookup"><span data-stu-id="aed73-114">Display pop-up lists of available members, properties, or values as you type in the editor.</span></span> <span data-ttu-id="aed73-115">ポップアップ リストから項目を選択してコードに挿入します。</span><span class="sxs-lookup"><span data-stu-id="aed73-115">Choose any item from the pop-up list to insert the item into your code.</span></span> <span data-ttu-id="aed73-116">このチェック ボックスをオンにすると、**[メンバーの詳細を非表示]** オプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="aed73-116">Selecting this check box enables the **Hide advanced members** option.</span></span>  
  
 <span data-ttu-id="aed73-117">**[メンバーの詳細を非表示]**</span><span class="sxs-lookup"><span data-stu-id="aed73-117">**Hide advanced members**</span></span>  
 <span data-ttu-id="aed73-118">最もよく使われる項目だけを一覧に表示して、入力候補のポップアップ リストを簡潔にします。</span><span class="sxs-lookup"><span data-stu-id="aed73-118">Shorten pop-up statement completion lists by displaying only those items most commonly used.</span></span> <span data-ttu-id="aed73-119">他の項目は一覧から除外されます。</span><span class="sxs-lookup"><span data-stu-id="aed73-119">Other items are filtered from the list.</span></span> <span data-ttu-id="aed73-120">高度なメンバーとしてマークされているメンバーがない場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="aed73-120">This option will not be available if no members are marked as advanced members.</span></span>  
  
 <span data-ttu-id="aed73-121">**パラメーター情報**</span><span class="sxs-lookup"><span data-stu-id="aed73-121">**Parameter information**</span></span>  
 <span data-ttu-id="aed73-122">現在の宣言またはプロシージャの完全な構文、および使用できるすべてのパラメーターをエディター内のカーソルの左側に表示します。</span><span class="sxs-lookup"><span data-stu-id="aed73-122">Display the complete syntax for the current declaration or procedure to the left of the insertion point in the editor with all of its available parameters.</span></span> <span data-ttu-id="aed73-123">割り当て可能な次のパラメーターは、太字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="aed73-123">The next parameter you can assign is displayed in bold.</span></span>  
  
## <a name="settings"></a><span data-ttu-id="aed73-124">設定</span><span class="sxs-lookup"><span data-stu-id="aed73-124">Settings</span></span>  
 <span data-ttu-id="aed73-125">**[仮想空間を使用]**</span><span class="sxs-lookup"><span data-stu-id="aed73-125">**Enable virtual space**</span></span>  
 <span data-ttu-id="aed73-126">コードの横の一定の場所にコメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="aed73-126">Position comments at a consistent point next to your code.</span></span> <span data-ttu-id="aed73-127">このチェック ボックスがオンの場合、行の最後の文字よりも後ろの位置にカーソルを置くことができます。</span><span class="sxs-lookup"><span data-stu-id="aed73-127">When this check box is selected, you can position the cursor beyond the last character in the row.</span></span> <span data-ttu-id="aed73-128">入力時には、行を完成させるためにカーソル位置にタブまたはスペースが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="aed73-128">When you type, tabs or spaces are automatically added to complete the row to the insertion point.</span></span>  
  
 <span data-ttu-id="aed73-129">**右端で折り返す**</span><span class="sxs-lookup"><span data-stu-id="aed73-129">**Word wrap**</span></span>  
 <span data-ttu-id="aed73-130">エディターの表示領域の幅からはみ出した行を、次の行に折り返して表示します。</span><span class="sxs-lookup"><span data-stu-id="aed73-130">Display on the next line any portion of a line that extends horizontally beyond the viewable editor area.</span></span> <span data-ttu-id="aed73-131">このチェック ボックスをオンにすると、 **[右端の折り返しの記号を表示する]** オプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="aed73-131">Selecting this check box enables the **Show visual glyphs for word wrap** option.</span></span>  
  
 <span data-ttu-id="aed73-132">**[右端の折り返しの記号を表示する]**</span><span class="sxs-lookup"><span data-stu-id="aed73-132">**Show visual glyphs for word wrap**</span></span>  
 <span data-ttu-id="aed73-133">長い行が 2 行目に折り返される場所に、改行インジケーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="aed73-133">Display a return-arrow indicator where a long line wraps onto a second line.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aed73-134">改行インジケーターはコードに追加されているわけではないので、印刷されません。</span><span class="sxs-lookup"><span data-stu-id="aed73-134">These reminder arrows are not added to your code, and they do not print.</span></span> <span data-ttu-id="aed73-135">これは単に表示用です。</span><span class="sxs-lookup"><span data-stu-id="aed73-135">They are for reference only.</span></span> <span data-ttu-id="aed73-136">クエリ エディターの種類によっては、この機能が使用できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="aed73-136">This feature is not available in all types of editors.</span></span>  
  
 <span data-ttu-id="aed73-137">**[選択領域がない場合は、切り取りまたはコピー コマンドを空白行に適用する]**</span><span class="sxs-lookup"><span data-stu-id="aed73-137">**Apply Cut/Copy commands to blank lines when there is no selection**</span></span>  
 <span data-ttu-id="aed73-138">空白行にカーソルを置き、何も選択していない状態で **[コピー]** または **[切り取り]** をクリックしたときのエディターの動作を設定します。</span><span class="sxs-lookup"><span data-stu-id="aed73-138">Set the behavior of the editor when you place the insertion point on a blank line, select nothing, and then click **Copy** or **Cut**.</span></span>  
  
 <span data-ttu-id="aed73-139">このチェック ボックスがオンの場合、空白行がコピーまたは切り取られます。</span><span class="sxs-lookup"><span data-stu-id="aed73-139">When this check box is selected, the blank line is copied or cut.</span></span> <span data-ttu-id="aed73-140">その後で **[貼り付け]** をクリックすると、新しい空白行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="aed73-140">If you then click **Paste**, a new, blank line is inserted.</span></span>  
  
 <span data-ttu-id="aed73-141">このチェック ボックスがオフの場合、何もコピーまたは切り取られません。</span><span class="sxs-lookup"><span data-stu-id="aed73-141">When this check box is cleared, nothing is copied or cut.</span></span> <span data-ttu-id="aed73-142">その後で **[貼り付け]** をクリックすると、最後にコピーした内容が貼り付けられます。</span><span class="sxs-lookup"><span data-stu-id="aed73-142">If you then click **Paste**, the content most recently copied is pasted.</span></span> <span data-ttu-id="aed73-143">それまでに何もコピーされていない場合は、何も貼り付けられません。</span><span class="sxs-lookup"><span data-stu-id="aed73-143">If nothing has been copied, nothing is pasted.</span></span>  
  
 <span data-ttu-id="aed73-144">行が空白でない場合、**[コピー]** または **[切り取り]** コマンドの動作はこの設定の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="aed73-144">This setting has no effect on the **Copy** or **Cut** commands when a line is not blank.</span></span> <span data-ttu-id="aed73-145">何も選択されていない場合、行全体がコピーまたは切り取られます。</span><span class="sxs-lookup"><span data-stu-id="aed73-145">If nothing is selected, the entire line is copied or cut.</span></span> <span data-ttu-id="aed73-146">その後で **[貼り付け]** をクリックすると、行全体のテキストと行末文字が貼り付けられます。</span><span class="sxs-lookup"><span data-stu-id="aed73-146">If you then click **Paste**, the text of the entire line and its end line character are pasted.</span></span>  
  
## <a name="display"></a><span data-ttu-id="aed73-147">表示</span><span class="sxs-lookup"><span data-stu-id="aed73-147">Display</span></span>  
 <span data-ttu-id="aed73-148">**行番号**</span><span class="sxs-lookup"><span data-stu-id="aed73-148">**Line numbers**</span></span>  
 <span data-ttu-id="aed73-149">コードの各行の横に行番号を表示します。</span><span class="sxs-lookup"><span data-stu-id="aed73-149">Display a line number next to each line of code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aed73-150">この行番号はコードに追加されているわけではないので、印刷されません。</span><span class="sxs-lookup"><span data-stu-id="aed73-150">These line numbers are not added to your code, and they do not print.</span></span> <span data-ttu-id="aed73-151">これは単に表示用です。</span><span class="sxs-lookup"><span data-stu-id="aed73-151">They are for reference only.</span></span>  
  
 <span data-ttu-id="aed73-152">**[シングル クリックでの URL ナビゲーションを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="aed73-152">**Enable single-click URL navigation**</span></span>  
 <span data-ttu-id="aed73-153">エディター内で URL 上にカーソルを移動すると、カーソルが指差しカーソルに変わります。</span><span class="sxs-lookup"><span data-stu-id="aed73-153">Change the cursor to a symbol of a pointing hand when it passes over a URL in the editor.</span></span> <span data-ttu-id="aed73-154">URL をクリックすると、該当するページが Web ブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="aed73-154">You can click the URL to display the indicated page in your Web browser.</span></span>  
  
 <span data-ttu-id="aed73-155">**ナビゲーションバー**</span><span class="sxs-lookup"><span data-stu-id="aed73-155">**Navigation bar**</span></span>  
 <span data-ttu-id="aed73-156">コード エディター上部にナビゲーション バーを表示します。</span><span class="sxs-lookup"><span data-stu-id="aed73-156">Display a navigation bar at the top of the Code Editor.</span></span> <span data-ttu-id="aed73-157">**[オブジェクト]** および **[プロシージャ]** の各ドロップダウン リストで、コード内の特定のオブジェクトを選択し、プロシージャを選択して、選択したプロシージャのインスタンスを挿入します。</span><span class="sxs-lookup"><span data-stu-id="aed73-157">Use its **Objects**and **Procedures** drop-down lists to choose a particular object in your code, select from its procedures, and insert an instance of the selected procedure.</span></span> <span data-ttu-id="aed73-158">ナビゲーション バーは、すべてのコードの種類で使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="aed73-158">The navigation baris not available for all code types.</span></span>  
  
  
